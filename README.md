# setup-cd-workspace-all-in-one

A composite action to set up all components you need about CD.

## Inputs

| Action inputs                  | Description                             | Default | Required |
|--------------------------------|-----------------------------------------|---------|----------|
| cloud-provider                 | cloud provider: Azure, AliCloud, TBD.   | /       | true     |
| azure-client-id                | OIDC client id to login Azure           | /       | false    |
| azure-tenant-id                | OIDC tenant id to login Azure           | /       | false    |
| azure-subscription-id          | OIDC subscription id to login Azure     | /       | false    |
| acr-login-registry             | Azure/AliCloud ACR registry to login    | /       | true     |
| acr-username                   | Azure/AliCloud ACR username to login    | /       | true     |
| acr-password                   | Azure/AliCloud ACR password to login    | /       | true     |
| azure-aks-resource-group       | Azure AKS cluster resource group        | /       | false    |
| azure-aks-cluster-name         | Azure AKS cluster name to use           | /       | false    |
| alicloud-ack-cluster-id        | AliCloud ACK cluster id to login        | /       | false    |
| alicloud-ack-access-key-id     | AliCloud access key id to login ACK     | /       | false    |
| alicloud-ack-access-key-secret | AliCloud access key secret to login ACK | /       | fasle    |
| need-cd-tools                  | Whether to install CD tools             | true    | false    |

## Outputs

None

## Example

### Azure

```yaml
# omit others configs

# It's required
permissions:
  id-token: write
  contents: read

jobs:
build-and-deploy:
  runs-on: ubuntu-latest
  environment: github-environment
  steps:
  # omit others steps
  - name: Setup CD workspace all in one
    uses: coscene-io/setup-cd-workspace-all-in-one@latest
    with:
      cloud-provider: Azure
      azure-client-id: ${{ secrets.AZURE_CLIENT_ID }}
      azure-tenant-id: ${{ secrets.AZURE_TENANT_ID }}
      azure-subscription-id: ${{ secrets.AZURE_SUBSCRIPTION_ID }}
      acr-login-registry: ${{ secrets.AZURE_REGISTRY_LOGIN_SERVER }}
      acr-password: ${{ secrets.AZURE_REGISTRY_USERNAME }}
      azure-acr-password: ${{ secrets.AZURE_REGISTRY_PASSWORD }}
      azure-aks-resource-group: 'Dev-EUS'
      azure-aks-cluster-name: 'Dev-EUS'
  # omit others steps
```

>  In your GitHub workflow, Set `permissions:` with `id-token: write` at workflow level or job level based on whether the OIDC token needs to be auto-generated for all Jobs or a specific Job.

[Azure Login](https://github.com/marketplace/actions/azure-login#github-action-for-azure-login) require this.

### AliCloud

```yaml
# omit others configs
jobs:
build-and-deploy:
  runs-on: ubuntu-latest
  environment: github-environment
  steps:
  # omit others steps
  - name: Setup CD workspace all in one
    uses: coscene-io/setup-cd-workspace-all-in-one@latest
    with:
      cloud-provider: AliCloud
      acr-login-registry: registry.cn-hangzhou.aliyuncs.com
      acr-username: ${{ secrets.ACR_USERNAME }}
      acr-password: ${{ secrets.ACR_PASSWORD }}
      alicloud-access-key-id: ${{ secrets.ACK_ACCESS_KEY_ID }}
      alicloud-access-key-secret: ${{ secrets.ACK_ACCESS_KEY_SECRET }}
      alicloud-cluster-id: ${{ secrets.ACK_CLUSTER_ID }}
  # omit others steps
```

## Troubleshooting

None
