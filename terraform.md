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
