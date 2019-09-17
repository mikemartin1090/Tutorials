## Quickstart: Deploy an Azure virtual machine from a template with the Azure SDK for Go
https://docs.microsoft.com/en-us/azure/go/azure-sdk-go-qs-vm

## Create a service principal
What is a service principal?
- Service principals are part of role-based access control (RBAC), which creates a unique user identity.
- Make sure to set the playground subscription or wherever you'll be testing
  - Don't want these service principals getting access to real live stuff...
```
# login if necessary
az login

# get the list of subscriptions you have access to currently
az account list

# set cli default subscription to playground
az account set --subscription "id-in-quotes-"

# create a service principal with a name and store credentials in a file on disk
az ad sp create-for-rbac --name "MikeMartinGoCLI-SP" --sdk-auth > /tmp/MikeMartinGoCLI-SP.auth

# delete when done
# Where you supply the value for CLIENT_ID_VALUE from /tmp/MikeMartinGoCLI-SP.auth
az ad sp delete --id "${CLIENT_ID_VALUE}"
```