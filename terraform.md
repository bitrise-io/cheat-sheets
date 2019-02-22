# Terraform Cheat Sheet

## Providing variables via env vars instead of `-var-file` or `-var` flag

You can provide value for variables via env vars, by setting `TF_VAR_varname` environment variables before running `terraform` commands. Basically use the variable's name, and prefix it with `TF_VAR_` as the environment variable key (the value will be the value). E.g. if the variable in the `.tf` file is `project_id` then you can provide a value for it by setting the `TF_VAR_project_id` env var.

Docs for more info: https://www.terraform.io/docs/configuration/variables.html#environment-variables

## Commands

- `terraform plan` : View what would change if you `apply` the terraform config.
    - `terraform plan -var-file=secrets.tfvars` : You can provide values for variables using a `tfvars` file with the `-var-file` flag. NOTE: Prefer Env Vars instead of storing secrets in an unencrypted local file!
- `terraform apply` : Apply (perform) the changes (that you saw in `terraform plan`).
- `terraform destroy` : Destroy all the defined resources.


## An example `.tfvars` file

If for some reason you'd still have to use a `.tfvars` file you can use this as a template/example:

```
# Comment
single_line_var = ""

multi_line_var = <<EOF
...
EOF

```
