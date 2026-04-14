# Set up Crossplane Workshop

## Create local Kind cluster
    kind create cluster --name crossplane

## Set up Crossplane via Helm chart
    helm repo add crossplane-stable https://charts.crossplane.io/stable
    helm repo update

    helm install crossplane --namespace crossplane-system --create-namespace crossplane-stable/crossplane

    kubectl get pods -n crossplane-system


# After Workshop

## Delete resources
    All cloud resources need to be deleted separately

## Clean up Service Principal
    az ad sp delete --id <your-sp-id>
    az ad app delete --id <your-app-id>

## Clean up Cluster
    kind delete cluster --name crossplane


# Links

    Crossplane XRD docs:            https://docs.crossplane.io/latest/composition/
    Crossplane API ref:             https://docs.crossplane.io/latest/api/
    Upbound provider Marketplace:   https://marketplace.upbound.io/providers