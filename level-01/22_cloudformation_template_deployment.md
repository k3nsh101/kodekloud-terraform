### Task

The Nautilus DevOps team is working on automating infrastructure deployment using AWS CloudFormation. As part of this effort, they need to create a CloudFormation stack that provisions an S3 bucket with versioning enabled.

Create a CloudFormation stack named `nautilus-stack` using `Terraform`. This stack should contain an S3 bucket named `nautilus-bucket-13706` as a resource, and the bucket must have versioning enabled. The Terraform working directory is `/home/bob/terraform`. Create the `main.tf` file (do not create a different `.tf` file) to accomplish this task.

### Solution

#### main.tf

```terraform
resource "aws_cloudformation_stack" "nautilus" {
  name = "nautilus-stack"

  template_body = jsonencode({
    Resources = {
      nautilusBucket = {
        Type = "AWS::S3::Bucket"
        Properties = {
          BucketName = "nautilus-bucket-13706"

          VersioningConfiguration = {
            Status = "Enabled"
          }
        }
      }
    }
  })
}
```

```bash
terraform init
terraform apply
```
