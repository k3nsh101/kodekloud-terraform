### Task

The Nautilus DevOps team needs to set up a DynamoDB table for storing user data. They need to create a DynamoDB table with the following specifications:

1. The table name should be `devops-users`.
2. The primary key should be `devops_id` (String).
3. The table should use `PAY_PER_REQUEST` billing mode.

Use `Terraform` to create this DynamoDB table. The Terraform working directory is `/home/bob/terraform`. Create the `main.tf` file (do not create a different `.tf` file) to create the DynamoDB table.

### Solution

#### main.tf

```terraform
resource "aws_dynamodb_table" "nautilus" {
  name         = "devops-users"
  hash_key     = "devops_id"
  billing_mode = "PAY_PER_REQUEST"

  attribute {
      name = "devops_id"
      type = "S"
  }
}
```

```bash
terraform init
terraform apply
```
