### Task

The Nautilus DevOps team has been creating a couple of services on AWS cloud. They have been breaking down the migration into smaller tasks, allowing for better control, risk mitigation, and optimization of resources throughout the migration process. Recently they came up with requirements mentioned below.

An IAM user named `iamuser_yousuf` and a policy named `iampolicy_yousuf` already exists. Use `Terraform` to attach the IAM policy `iampolicy_yousuf` to the IAM user `iamuser_yousuf`. The Terraform working directory is `/home/bob/terraform`. Update the `main.tf` file (do not create a separate `.tf` file) to attach the specified IAM policy to the IAM user.

### Solution

```terraform
# Create IAM user
resource "aws_iam_user" "user" {
  name = "iamuser_yousuf"

  tags = {
    Name = "iamuser_yousuf"
  }
}

# Create IAM Policy
resource "aws_iam_policy" "policy" {
  name        = "iampolicy_yousuf"
  description = "IAM policy allowing EC2 read actions for yousuf"

  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Effect   = "Allow"
        Action   = ["ec2:Read*"]
        Resource = "*"
      }
    ]
  })
}

resource "aws_iam_user_policy_attachment" "policy_attach" {
  user       = aws_iam_user.user.name
  policy_arn = aws_iam_policy.policy.arn
}
```

```bash
terraform apply
```
