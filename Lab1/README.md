Enter the git repository through the commandline and go into the Lab1 directory.

### Prerequisites

The azure CLI must be installed.

### Authentication

This guide depends on a valid azure subscribtion! This azure account must also be authenticated in the azure CLI. 

### Resource Group

Then we need to create a resource group:

```
az group create --name myResourceGroup --location "West Europe"
```

### Deployment

Then we can deploy the stack with this command. Use the appropriate resourcegroupname from the command above. You may change any of the parameters in the parameter file (storageSKU is limited to some options).

```
az deployment group create --name deployment --resource-group {resourcegroupname} --template-file azuredeploy.json --parameters .\azuredeploy.parameters.json
```

### Testing

Once the stack is deployed the output contains the outputs-object where the hostname of the webapp is defined. This is necessary as the name of the webapp is (partially) randomly generated. You can now enter the host name in the browser and see the NODE-Developer azure starting page (It may take a while to fully load the application).