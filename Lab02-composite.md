# XRD Crossplane Workshop

## Create namespace
    kubectl create namespace composite
    kubectl get namespaces

## Add the Kubernetes provider to the Crossplane instance
    kubectl apply -f ./02-composite/kubernetes-provider.yaml
    kubectl get providers

## Add the Kubernetes provider config
    kubectl get sa -n crossplane-system
    # Select correct service account in kubernetes-provider-config.yaml
    kubectl apply -f ./02-composite/kubernetes-provider-config.yaml
    kubectl get provideconfigs

## Create Composite Resource Definition
    kubectl apply -f ./02-composite/composite-resource-definition.yaml
    kubectl get xrd -n composite

## Create Composition
    kubectl apply -f ./02-composite/composition.yaml
    kubectl get compositions -n composite

## Create Resources
    kubectl apply -f ./02-composite/composition-claim.yaml
    kubectl get applications -n composite