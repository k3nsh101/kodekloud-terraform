### Task

During the migration process, several resources were created under the AWS account. Some of these test resources are no longer needed at the moment, so we need to clean them up temporarily. One such instance is currently unused and should be deleted.

1. Delete the ec2 instance named `datacenter-ec2` present in `us-east-1` region using terraform. Make sure to keep the provisioning code, as we might need to provision this instance again later.

2. Before submitting your task, make sure instance is in `terminated` state.

The Terraform working directory is `/home/bob/terraform`.

### Solution

```bash
cd /home/bob/terraform/
terraform destroy -target=aws_instance.ec2

```

Verify using the following command and making sure the `Status` is `terminated`

```bash
aws ec2 describe-instances --filters "Name=tag:Name,Values=datacenter-ec2"
```
