## Project: Deploy Azure SQL Database DACPAC using Entra Service Principal

**Project Description**: This project will deploy a SQL Database data-tier application (DAC) using an Entra Service Principal

## Prerequisites

* Create App registration (Service Principal) in Azure Entra and new client secret.

* Add Service Principal to the SQL Database:

```
CREATE USER [<Service Principal name>] FROM EXTERNAL PROVIDER;
GO
ALTER ROLE db_owner ADD MEMBER [<Service Principal name>];
GO
```
* Create DACPAC:

![App diagram](/screenshots/Extract Data-tier Application.png)  