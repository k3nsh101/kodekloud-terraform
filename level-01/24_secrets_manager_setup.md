### Task

The Nautilus DevOps team needs to store sensitive data securely using AWS Secrets Manager. They need to create a secret with the following specifications:

1. The secret name should be `devops-secret`.
2. The secret value should contain a key-value pair with `username: admin` and `password: Namin123`.
3. Use `Terraform` to create the secret in AWS Secrets Manager.

The Terraform working directory is `/home/bob/terraform`. Create the `main.tf` file (do not create a different `.tf` file) to accomplish this task.

### Solution

#### main.tf

```terraform
resource "aws_secretsmanager_secret" "nautilus" {
  name = "devops-secret"
}

variable "devops_credentials" {
  default = {
    username = "admin"
    password = "Namin123"
  }

  type = map(string)
}

resource "aws_secretsmanager_secret_version" "nautilus" {
  secret_id     = aws_secretsmanager_secret.nautilus.id
  secret_string = jsonencode(var.devops_credentials)
}
```

```bash
terraform init
terraform apply
```
