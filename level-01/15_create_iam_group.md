### Task

The javed DevOps team has been creating a couple of services on AWS cloud. They have been breaking down the migration into smaller tasks, allowing for better control, risk mitigation, and optimization of resources throughout the migration process. Recently they came up with requirements mentioned below.

Create an IAM group named `iamgroup_javed` using terraform.

The Terraform working directory is `/home/bob/terraform`. Create the `main.tf` file (do not create a different `.tf` file) to accomplish this task.


### Solution

#### main.tf

```terraform
resource "aws_iam_group" "javed" {
  name = "iamgroup_javed"
}
```

```bash
terraform init
terraform apply
```
