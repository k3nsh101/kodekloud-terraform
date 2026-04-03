### Task

The Nautilus DevOps team is presently immersed in data migrations, transferring data from on-premise storage systems to AWS S3 buckets. They have recently received some data that they intend to copy to one of the S3 buckets.

S3 bucket named `xfusion-cp-1976` already exists. Copy the file `/tmp/xfusion.txt` to s3 bucket `xfusion-cp-1976` using Terraform. The Terraform working directory is `/home/bob/terraform`. Update the `main.tf` file (do not create a separate `.tf` file) to accomplish this task.

### Solution

```terraform
resource "aws_s3_bucket" "my_bucket" {
  bucket = "xfusion-cp-1976"
  acl    = "private"

  tags = {
    Name        = "xfusion-cp-1976"
  }
}

resource "aws_s3_object" "upload_file" {
  key        = "xfusion.txt"
  bucket     = aws_s3_bucket.my_bucket.id
  source     = "/tmp/xfusion.txt"
}
```

```bash
terraform apply
```
