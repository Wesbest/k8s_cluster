# k8s_cluster
k8s cluster setup with terraform

## Step 1: Create Azure container to store state file
```
# Create Resource Group
az group create -n wesbesttfstates -l westeurope
 
# Create Storage Account
az storage account create -n wesbesttf -g wesbesttfstates -l westeurope --sku Standard_LRS
 
# Create Storage Account Container
az storage container create -n tfstatedevops
```

## Step 2: Create Azure Service Principal
```
# Create Service Principal 
az ad sp create-for-rbac --name wesbesttf2
````

## Step 3: Add secrets to Github
AZURE_AD_CLIENT_ID – Will be the service principal ID from above

AZURE_AD_CLIENT_SECRET – The secret that was created as part of the Azure Service Principal

AZURE_AD_TENANT_ID – The Azure AD tenant ID to where the service principal was created

AZURE_SUBSCRIPTION_ID – Subscription ID of where you want to deploy the Terraform

## Step 4: Run pipeline
On push pipeline will be deployed. 




