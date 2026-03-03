### Task

As part of the data migration process, the Nautilus DevOps team is actively creating several S3 buckets on AWS using Terraform. They plan to utilize both private and public S3 buckets to store the relevant data. Given the ongoing migration of other infrastructure to AWS, it is logical to consolidate data storage within the AWS environment as well.

Create an S3 bucket using Terraform with the following details:

1. The name of the S3 bucket must be `nautilus-s3-19180`.
2. The S3 bucket must block all `public` access, making it a private bucket.

The Terraform working directory is `/home/bob/terraform`. Create the `main.tf` file (do not create a different .tf file) to accomplish this task.

### Solution

#### main.tf

```terraform
resource "aws_s3_bucket" "nautilus" {
  bucket = "nautilus-s3-19180"

  tags = {
      Name = "nautilus-s3-19180"
  }
}

resource "aws_s3_bucket_public_access_block" "nautilus" {
  bucket = aws_s3_bucket.nautilus.id

  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}
```
