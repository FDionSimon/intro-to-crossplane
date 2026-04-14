# XRD Crossplane Workshop

## Create namespace
    kubectl create namespace composite

## Add the Kubernetes provider to the Crossplane instance
    kubectl apply -f ./02-composite/kubernetes-provider.yaml

## Add the Kubernetes provider config
    # Set up correct service account in kubernetes-provider-config.yaml
    kubectl apply -f ./02-composite/kubernetes-provider-config.yaml

## Create Composite Resource Definition
    kubectl apply -f ./02-composite/composite-resource-definition.yaml

## Create Composition
    kubectl apply -f ./02-composite/composition.yaml

## Create Resources
    kubectl apply -f ./02-composite/composition-claim.yaml