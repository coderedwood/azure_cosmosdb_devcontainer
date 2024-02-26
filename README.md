###Azure CosmosDB DevContainer Project

##.Net DevContainer Project to create reasource group for Azure CosmosDB using the .Net 6 SDK

#Login with Azure using 
az login OR az login --use-device-code

Create resources in Azure
Create a resource group for the resources needed for this exercise. Replace <myLocation> with a region near you.


Copy
az group create --location <myLocation> --name <resourceGroupName>
Create the Azure Cosmos DB account. Replace <myCosmosDBacct> with a unique name to identify your Azure Cosmos DB account. The name can only contain lowercase letters, numbers, and the hyphen (-) character. It must be between 3-31 characters in length. This command takes a few minutes to complete.


Copy
az cosmosdb create --name <myCosmosDBacct> --resource-group <resourceGroupName>
Record the documentEndpoint shown in the JSON response, it's used later in the exercise.

Retrieve the primary key for the account by using the following command. Record the primaryMasterKey from the command results it will be used in the code.


# Retrieve the primary key
az cosmosdb keys list --name <myCosmosDBacct> --resource-group <resourceGroupName>


# Create a folder for the project and change in to the folder.


mkdir az204-cosmos
cd az204-cosmos

# Create the .NET console app.

dotnet new console
code . -r

# Build the console app
It's time to start adding the packages and code to the project.

# Add packages and using statements
Open the terminal in Visual Studio Code and use the following command to add the Microsoft.Azure.Cosmos package to the project.

dotnet add package Microsoft.Azure.Cosmos

# After package is installed look through the code ans update the keys you saved earlier then save, build and run the application
dotnet build
dotnet run

# After running you should see the output below if successful
Beginning operations...

Created Database: <<databasename>>

Created Container: <<containername>>

End of program, press any key to exit.

# Clean up Azure resources
You can now safely delete the <<resourceGroupName>> resource group from your account by running the following command in the azure cli

az group delete --name <<resourceGroupName>> --no-wait