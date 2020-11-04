## Terraform and cloud-init
### Bootstrapping Ubuntu 20.04 with a Minecraft Server

#### Quick How-to commands

```shell script
# to bootstrap the instance
terraform init
terraform apply
# to destroy
terraform destroy
```

```shell script
# get the instance public ip
terraform show -json | jq -r '.values[].child_modules[].resources[]
| select(.address == "module.ec2.aws_instance.this[0]") |
.values.public_ip'
```

```shell script
# get the private ssh key
terraform show -json | jq -r '.values[].resources[] | select(.address == "tls_private_key.example") | .values.private_key_pem'
```
