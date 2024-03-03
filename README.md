## Project: Deploy Azure SQL Database DACPAC using Entra Service Principal

**Project Description**: This project will deploy a SQL Database data-tier application (DAC) using an Microsoft Entra Service Principal

## Prerequisites

* Create App registration (Service Principal) in Azure Entra and new client secret.

* Add Service Principal to the SQL Database:

```
-- in master database
CREATE LOGIN [<Service Principal name>] FROM EXTERNAL PROVIDER;
GO
CREATE USER [<Service Principal name>] FROM LOGIN [<Service Principal name>];
GO
ALTER SERVER ROLE ##MS_DatabaseManager##
    ADD MEMBER [<Service Principal name>];
GO
-- in user database
CREATE USER [<Service Principal name>] FROM LOGIN [<Service Principal name>];
GO
ALTER ROLE db_owner ADD MEMBER [<Service Principal name>];
GO
```

* Create DACPAC and upload to repo.

![Create DACPAC](/screenshots/ExtractData-tierApplication.png)


## Create pipeline

* Create new project in Azure DevOps.

* Create pipeline then connect to existing repo in GitHub and select YAML file.

* In the Project Settings, create service connection to your Azure Subscription called AzureSubscriptionConnector.

* Create the variables in the pipeline:

![Pipeline variables](/screenshots/pipeline_variables.png)

## Run the pipeline

![run the pipeline](/screenshots/dacpacdeployment.png)