### Task

Data protection and recovery are fundamental aspects of data management. It's essential to have systems in place to ensure that data can be recovered in case of accidental deletion or corruption. The DevOps team has received a requirement for implementing such measures for one of the S3 buckets they are managing.

The S3 bucket name is `nautilus-s3-3471`, enable versioning for this bucket using `Terraform`.

The Terraform working directory is `/home/bob/terraform`. Update the `main.tf` file (do not create a different `.tf` file) to accomplish this task.

### Solution

#### main.tf

```terraform
resource "aws_s3_bucket" "s3_ran_bucket" {
  bucket = "nautilus-s3-3471"
  acl    = "private"

  tags = {
    Name        = "nautilus-s3-3471"
  }
}

resource "aws_s3_bucket_versioning" "s3_ran_bucket_versioning" {
  bucket = aws_s3_bucket.s3_ran_bucket.id
  versioning_configuration {
    status = "Enabled"
  }
}
```

```bash
terraform apply
```
