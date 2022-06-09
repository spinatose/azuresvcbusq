- Setup some useful vars for BASH
```
myLocation=<myLocation>
myNameSpaceName=az204svcbus$RANDOM
```

- Create resource group
`az group create --name az204-svcbus-rg --location $myLocation`

- Create ServiceBus namespace
```
  az servicebus namespace create \
    --resource-group az204-svcbus-rg \
    --name $myNameSpaceName \
    --location $myLocation
```

- Create ServiceBus queue
```
az servicebus queue create --resource-group az204-svcbus-rg \
    --namespace-name $myNameSpaceName \
    --name az204-queue
```

## Azure Portal
- Go to resource group just created
- Select servicebus resource in that resource group
- Select "Shared access policies" under "Settings"
- Click on "RootManageSharedAccessKey"
- Copy "Primary Connection String"


### Back to Bash
- Delete resource group
`az group delete --name az204-svcbus-rg --no-wait`