# Terraform Cheat Sheet

- `terraform plan -var-file=secrets.tfvars` : View what would change if you `apply` the terraform config, reading variables from a `secrets.tfvars` file.
- `terraform apply -var-file=secrets.tfvars` : Terraform apply with variables read from a `.tfvars` vars file.
- `terraform destroy -var-file=secrets.tfvars` : Destroy all the defined resources.

An example `.tfvars` file:

```
# Comment
single_line_var = ""

multi_line_var = <<EOF
...
EOF

```

## Providing variables via env vars instead of `-var-file` or `-var` flag

You can provide value for variables via env vars, by setting `TF_VAR_varname` environment variables before running `terraform` commands. Basically use the variable's name, and prefix it with `TF_VAR_` as the environment variable key (the value will be the value). E.g. if the variable in the `.tf` file is `project_id` then you can provide a value for it by setting the `TF_VAR_project_id` env var.

Docs for more info: https://www.terraform.io/docs/configuration/variables.html#environment-variables
