### Task

The Nautilus DevOps team needs to set up an SNS topic for sending notifications. They need to create an SNS topic with the following specifications:

1. The topic name should be `nautilus-notifications`.

### Solution

#### main.tf

```terraform
resource "aws_sns_topic" "nautilus" {
  name = "nautilus-notifications"
}
```

```bash
terraform init
terraform apply
```
