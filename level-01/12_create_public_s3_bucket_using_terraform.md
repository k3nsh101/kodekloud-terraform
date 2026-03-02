### Task

As part of the data migration process, the Nautilus DevOps team is actively creating several S3 buckets on AWS. They plan to utilize both private and public S3 buckets to store the relevant data. Given the ongoing migration of other infrastructure to AWS, it is logical to consolidate data storage within the AWS environment as well.

1. Create a `public` S3 bucket named `nautilus-s3-22433` using Terraform.
2. **Ensure the bucket is accessible publicly once created** by setting the proper ACL.

The Terraform working directory is /home/bob/terraform. Create the main.tf file (do not create a different .tf file) to accomplish this task.

### Solution

#### main.tf

```terraform
resource "aws_s3_bucket" "nautilus" {
  bucket = "nautilus-s3-22433"

  tags = {
    Name = "nautilus-s3-22433"
  }
}

# This is used to change the ownership from default BucketOwnerEnforced.
# With BucketOwnerEnforced, ACLs does not affect the permissions to data in the s3
resource "aws_s3_bucket_ownership_controls" "nautilus" {
  bucket = aws_s3_bucket.nautilus.id
  rule {
    object_ownership = "BucketOwnerPreferred"
  }
}

# The attributes are same as the defaults. They all default to false
resource "aws_s3_bucket_public_access_block" "nautilus" {
  bucket = aws_s3_bucket.nautilus.id

  block_public_acls       = false
  block_public_policy     = false
  ignore_public_acls      = false
  restrict_public_buckets = false
}

resource "aws_s3_bucket_acl" "nautilus" {
  depends_on = [
    aws_s3_bucket_ownership_controls.nautilus,
    aws_s3_bucket_public_access_block.nautilus,
  ]

  bucket = aws_s3_bucket.nautilus.id
  acl    = "public-read"
}
```

Note:

- Both `aws_s3_bucket_ownership_controls` and `"aws_s3_bucket_public_access_block` are for security.
- The above way of accessing is not safe and encouraged to disable `ACL` and use `Bucket policies`
