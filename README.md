# setup-cd-workspace-all-in-one

A composite action to set up all components you need about CD.

## Inputs

| Action inputs | Description | Default | Required |
|---------------|-------------|---------|---------------|
|  cloud-provider    | cloud provider: Azure, AliCloud, TBD.| / | true |
| azure-client-id | OIDC client id to login Azure | / | false |
| azure-tenant-id | OIDC tenant id to login Azure | / | false |
| azure-subscription-id | OIDC subscription id to login Azure | / | false |
| azure-acr-login-server | Azure ACR registry to login | / | false |
| azure-acr-username | Azure ACR username to login | / | false |
| azure-acr-password | Azure ACR password to login | / | false |
| azure-aks-resource-group | Azure AKS cluster resource group | / | false |
| azure-aks-cluster-name | Azure AKS cluster name to use | / | false |
| alicloud-acr-registry | AliCloud ACR registry to login | / | false |
| alicloud-ack-cluster-id | AliCloud ACK cluster id to login | / | false |
| alicloud-ack-access-key-id | AliCloud access key id to login ACK | / | false |
| alicloud-ack-access-key-secret | AliCloud access key secret to login ACK | / | fasle |
| need-cd-tools | Whether to install CD tools | true | false |

## Outputs

None

## Example

TBD

## Troubleshooint

None
