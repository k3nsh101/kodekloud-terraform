### Task

The Nautilus DevOps team is currently engaged in a cleanup process, focusing on removing unnecessary data and services from their AWS account. As part of the migration process, several resources were created for one-time use only, necessitating a cleanup effort to optimize their AWS environment.

Delete an IAM group named `iamgroup_ammar` using terraform. Make sure to keep the provisioning code, as we might need to provision this instance again later.

### Solution

```bash
cd /home/bob/terraform/
terraform destroy -target=aws_iam_group.this
```

Verify using the following command and making sure the group is not existing

```bash
aws iam list-groups
```
