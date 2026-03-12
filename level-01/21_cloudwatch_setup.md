### Task

The Nautilus DevOps team needs to set up CloudWatch logging for their application. They need to create a CloudWatch log group and log stream with the following specifications:

1. The log group name should be `xfusion-log-group`.
2. The log stream name should be `xfusion-log-stream`.

Use `Terraform` to create the CloudWatch log group and log stream. The Terraform working directory is `/home/bob/terraform`. Create the `main.tf` file (do not create a different `.tf` file) to accomplish this task.

### Solution

#### main.tf

```terraform
resource "aws_cloudwatch_log_group" "nautilus" {
  name = "xfusion-log-group"
}

resource "aws_cloudwatch_log_stream" "nautilus" {
  name           = "xfusion-log-stream"
  log_group_name = aws_cloudwatch_log_group.nautilus.name
}
```

```bash
terraform init
terraform apply
```
