# Terraform Local File to Object

## Inputs

| Name              | Description                                                         | Type   | Default | Required |
|-------------------|---------------------------------------------------------------------|--------|---------|----------|
| inline_delimiter  | Character which splits key and value pairs (e.g. `MY_KEY=MY_VALUE`) | string | `=`     | Yes      |
| filename          | Path and filename that will be parsed                               | string |         | Yes      |
| newline_delimiter | Character which separates keys                                      | string | `\n`    | Yes      |

## Usage

```bash
# my-bash-file.bash
MY_API_KEY=123456
SOME_KEY=SOME_VALUE
```

```hcl
module "file_to_object" {
  source  = "1Mill/file-to-object/local"
  version = "0.0.1"

  filename = "${path.module}/my-bash-file.bash"
}
output "my_api_key" {
  value = module.file_to_object.data.MY_API_KEY
}
output "some_key" {
  value = module.file_to_object.data["SOME_KEY"]
}
```
