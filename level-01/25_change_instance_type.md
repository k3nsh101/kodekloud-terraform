### Task

During the migration process, the Nautilus DevOps team created several EC2 instances in different regions. They are currently in the process of identifying the correct resources and utilization and are making continuous changes to ensure optimal resource utilization. Recently, they discovered that one of the EC2 instances was underutilized, prompting them to decide to change the instance type. Please make sure the `Status check` is completed (if it's still in `Initializing` state) before making any changes to the instance.

1. Change the instance type from `t2.micro` to `t2.nano` for `xfusion-ec2` instance using `terraform`.
2. Make sure the EC2 instance `xfusion-ec2` is in running state after the change.
3. The Terraform working directory is `/home/bob/terraform`. Update the `main.tf` file (do not create a separate `.tf` file) to change the instance type.

### Solution

#### main.tf

```terraform
# Provision EC2 instance
resource "aws_instance" "ec2" {
  ami           = "ami-0c101f26f147fa7fd"
  instance_type = "t2.nano"
  subnet_id     = ""
  vpc_security_group_ids = [
    "sg-191abbccd7765b744"
  ]

  tags = {
    Name = "xfusion-ec2"
  }
}
```

```bash
terraform apply
```

Verify the state is running using aws client

```bash
aws ec2 describe-instances
```
