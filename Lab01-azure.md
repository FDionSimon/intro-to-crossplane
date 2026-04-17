# Crossplane Workshop

## Setup Service Principal
    az login --use-device-code

    az ad sp create-for-rbac --name <name>-crossplane-sp --role Contributor \
    --scopes /subscriptions/<subscriptionId> > ./01-azure/azure-credentials.json

    # Change azure-credentials file keys:
    #   appId       --> clientId
    #   password    --> clientSecret
    #   tenant      --> tenantId
    #   *add*       --> subscriptionId
    #   displayname --> *remove*

## Create Namespace
    kubectl create namespace azure
    kubectl get namespaces

## Set Credentials in K8s Secret
    kubectl create secret generic azure-secret -n azure --from-file=creds=./01-azure/azure-credentials.json
    kubectl get secrets -n azure

## Install Azure providers
    kubectl apply -f ./01-azure/azure-provider.yaml -n azure
    kubectl get providers -n azure

## Setup Provider config
    kubectl apply -f ./01-azure/azure-provider-config.yaml -n azure
    kubectl get providerconfigs -n azure

## Install resources
    # Adjust the resource group name in the azure-resource manifest
    kubectl apply -f ./01-azure/azure-resource.yaml -n azure
    kubectl get virtualnetworks -n azure
    kubectl get subnets -n azure
    # Check the azure portal for the resources

