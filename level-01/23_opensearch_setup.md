### Task

The Nautilus DevOps team needs to set up an Amazon OpenSearch Service domain to store and search their application logs. The domain should have the following specification:

1. The domain name should be `nautilus-es`.
2. Use `Terraform` to create the `OpenSearch` domain. The Terraform working directory is `/home/bob/terraform`. Create the `main.tf` file (do not create a different `.tf` file) to accomplish this task.

### Solution

#### main.tf

```terraform
resource "aws_opensearch_domain" "nautilus" {
  domain_name    = "nautilus-es"
}
```

```bash
terraform init
terraform apply
```
