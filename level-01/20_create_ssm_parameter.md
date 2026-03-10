### Task

The Nautilus DevOps team needs to create an SSM parameter in AWS with the following requirements:

1. The name of the parameter should be `datacenter-ssm-parameter`.
2. Set the parameter type to `String`.
3. Set the parameter value to `datacenter-value`.
4. The parameter should be created in the `us-east-1` region.
5. Ensure the parameter is successfully created using `terraform` and can be retrieved when the task is completed.

### Solution

#### main.tf

```terraform
resource "aws_ssm_parameter" "nautilus" {
  name  = "datacenter-ssm-parameter"
  type  = "String"
  value = "datacenter-value"
}
```

```bash
terraform init
terraform apply
```
