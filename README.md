# Docker and Github Action for Kubernetes CLI

This action provides `kubectl` for Github Actions.

## Secrets

`KUBE_CONFIG_DATA` – **required**: A base64-encoded kubeconfig file with credentials for Kubernetes to access the cluster. You can get it by running the following command:

## Configurable Variables

`KUBECTL_VERSION` - **optional**: By default, this action pulls the latest version of kubectl. To prevent potential dependency issue, you have the option to only use specific version.

```yaml
      - name: deploy to cluster
        uses: kodermax/kubectl-aws-eks@master
        env:
          KUBE_CONFIG_DATA: ${{ secrets.KUBE_CONFIG_DATA_STAGING }}
          ECR_REGISTRY: ${{ steps.login-ecr.outputs.registry }}
          ECR_REPOSITORY: my-app
          IMAGE_TAG: ${{ github.sha }
          KUBECTL_VERSION: "v1.22.0"
        with:
          args: set image deployment/$ECR_REPOSITORY $ECR_REPOSITORY=$ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG
```

`IAM_VERSION` - **optional**: By default, this action pulls the latest version of aws-iam-authenticator. To prevent potential dependency issue, you have the option to only use specific version.

```yaml
      - name: deploy to cluster
        uses: kodermax/kubectl-aws-eks@master
        env:
          KUBE_CONFIG_DATA: ${{ secrets.KUBE_CONFIG_DATA_STAGING }}
          ECR_REGISTRY: ${{ steps.login-ecr.outputs.registry }}
          ECR_REPOSITORY: my-app
          IMAGE_TAG: ${{ github.sha }
          KUBECTL_VERSION: "v1.22.0"
          IAM_VERSION: "0.5.6"
        with:
          args: set image deployment/$ECR_REPOSITORY $ECR_REPOSITORY=$ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG
```
