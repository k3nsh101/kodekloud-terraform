### Task

The Nautilus DevOps team has been creating a couple of services on AWS cloud. They have been breaking down the migration into smaller tasks, allowing for better control, risk mitigation, and optimization of resources throughout the migration process. Recently they came up with requirements mentioned below.

There is an instance named `xfusion-ec2` and an elastic-ip named `xfusion-ec2-eip` in `us-east-1` region. Attach the `xfusion-ec2-eip` elastic-ip to the `xfusion-ec2` instance using Terraform only. The Terraform working directory is `/home/bob/terraform`. Update the `main.tf` file (do not create a separate `.tf` file) to attach the specified Elastic IP to the instance.

### Solution

#### main.tf

```
# Provision EC2 instance
resource "aws_instance" "ec2" {
  ami           = "ami-0c101f26f147fa7fd"
  instance_type = "t2.micro"
  subnet_id     = "subnet-d6f0bd3dfb35024e0"
  vpc_security_group_ids = [
    "sg-5681df153b7b5aca8"
  ]

  tags = {
    Name = "xfusion-ec2"
  }
}

# Provision Elastic IP
resource "aws_eip" "ec2_eip" {
  instance = aws_instance.ec2.id

  tags = {
    Name = "xfusion-ec2-eip"
  }
}
```

```bash
terraform apply
```
