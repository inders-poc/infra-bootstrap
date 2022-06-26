# Infrastructure Bootstrap


## Components

The folder structure of this repo is split as follows:

├── templates                         <===  📖 helm templates to create ArgoCD Applications and Projects

├── infra-setup                       <===  📖 helm values files containing applications we wish to deploy

├── Chart.yaml                         <===  📖 we deploy infra using a helm chart

└── values.yaml                        <===  📖 infra application's helm chart values


There are two main components to this repository:

1. `infra-setup` - Contains all the tools and their helm dependencies to be deployed on new K8s cluster . This includes tools like istio, monitoring/observability and tools to support security.
2. `templates` - Contains template of argocd application and project.


### 🤠 Deploying the Infra applications

A handy one liner to deploy all the default infra applications in this project using their default values.

```bash
helm upgrade --install infra --namespace argocd .
```

you should see lots of things spinning up


You can set `enabled: true` on all of the application definitions in the `values-*.yaml` files if you want to deploy everything


### Cleanup

Uninstall and delete all resources in the various projects
```bash
# This may take a while:
helm delete infra --namespace argocd

```

### Debugging

Run the following command to debug one of the UJ values files to see which values are being passed:

```bash
# example debugging the ArgoCD `Application` manifests from the example deployment
helm install debug --dry-run  .
```
