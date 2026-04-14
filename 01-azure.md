# Crossplane Workshop

## Setup Service Principal
    az login --use-device-code

    az ad sp create-for-rbac --name <yourname>-crossplane-sp --role Contributor \
    --scopes /subscriptions/<sub_id> > ./01-azure/azure-credentials.json

    # Change azure-credentials file keys:
    #   appId       --> clientId
    #   password    --> clientSecret
    #   tenant      --> tenantId
    #   *add*       --> subscriptionId
    #   displayname --> *remove*

## Install providers
    kubectl create namespace azure

    kubectl create secret generic azure-secret -n azure --from-file=creds=./01-azure/azure-credentials.json

    kubectl apply -f ./01-azure/azure-provider.yaml -n azure

    kubectl apply -f ./01-azure/azure-provider-config.yaml -n azure

    # Adjust the resource group name in the azure-resource manifest
    kubectl apply -f ./01-azure/azure-resource.yaml -n azure
