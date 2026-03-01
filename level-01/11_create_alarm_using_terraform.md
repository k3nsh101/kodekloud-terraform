### Task

The Nautilus DevOps team is setting up monitoring in their AWS account. As part of this, they need to create a CloudWatch alarm.

Using Terraform, perform the following:

Task Details:
1. Create a CloudWatch alarm named `xfusion-alarm`.
2. The alarm should monitor **CPU utilization** of an EC2 instance.
3. Trigger the alarm when **CPU utilization exceeds 80%**.
4. Set the evaluation period to **5 minutes**.
5. Use a **single evaluation period**.

### Solution

#### main.tf
```terraform
resource "aws_cloudwatch_metric_alarm" "xfusion-alarm" {
  alarm_name                = "xfusion-alarm"
  comparison_operator       = "GreaterThanThreshold"
  evaluation_periods        = 1
  metric_name               = "CPUUtilization"
  namespace                 = "AWS/EC2"
  period                    = 300
  statistic                 = "Average"
  threshold                 = 80
}
```