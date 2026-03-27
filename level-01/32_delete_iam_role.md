### Task

The Nautilus DevOps team is currently engaged in a cleanup process, focusing on removing unnecessary data and services from their AWS account. As part of the migration process, several resources were created for one-time use only, necessitating a cleanup effort to optimize their AWS environment.

Delete the IAM role named `iamrole_jim` using `Terraform`. Make sure to keep the provisioning code, as we might need to provision this instance again later.

The Terraform working directory is `/home/bob/terraform`.

### Solution

```bash
cd /home/bob/terraform/
terraform destroy -target=aws_iam_role.role
```

Verify using the following command and making sure the role is deleted

```bash
aws iam list-roles
```
