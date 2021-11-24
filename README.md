# Infrastructure as code hands on labs
In these labs we'll cover creating Azure Resources in an automated way using the Azure CLI & Arm Templates or Bicep


---
### Lab 1: Create a web app using Azure CLI
Objective: Create an Azure App Service Plan & Azure Web App using the Azure CLI in your resource group `invo-<yourinitials>`

The name of the app service & web app should be `invo-<yourinitials>-cli`

> Tip: [Installing the CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)

>  Tip 2: [az appservice plandocumentation](https://docs.microsoft.com/en-us/cli/azure/appservice/plan?view=azure-cli-latest)

> Tip 3: [az webapp documentation](https://docs.microsoft.com/en-us/cli/azure/webapp?view=azure-cli-latest)

1. Create an Azure appservice plan (SKU `b1`) & azure web app in your resource group
2. Change the sku of the app service plan from `b1` to `s1`. deploy again. notice what happens with the resources
3. list all available web apps using CLI
4. [optional] create a deployment slot and make it auto swapp

---
### Lab 2: Create a web app using ARM template or Bicep Template
Objective: Create an Azure App service plan and Azure Web App using ARM templates or Bicep templates

The name of the app service & web app should be `invo-<yourinitials>-arm`

> Tip: [Az group deployment create](https://docs.microsoft.com/en-us/cli/azure/group/deployment?view=azure-cli-latest#az_group_deployment_create)

> Tip 2: [Azure quick start templates](https://azure.microsoft.com/en-us/resources/templates/)

> Tip 3: [ARM templates docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/overview)

> Tip 4: [Install Bicep](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/install)

> tip 5: [Bicep decompile from ARM](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/decompile?tabs=azure-cli)

> tip 6: [Bicep playground](https://bicepdemo.z22.web.core.windows.net/)



1. Create an Azure appservice plan (SKU `b1`) & azure web app in your resource group
2. Change the sku of the app service plan from `b1` to `b2` and deploy again. Notice what happens.
3. Set the Name,location & SKU using a parameter file

---


# Deploy a web application to an Azure web app using pipelines

In this lab we'll be learning how to create an automated pipeline using Azure DevOps to create our infrastructure and deploy our code to it

---
### Lab 1:
Create a service connection in Azure DevOps to connect to Azure. Name it `sc-<yourinitials>-dev`

> Tip: [Creating Service Connections](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops&tabs=yaml)

1. Create a service connection in azure devops scoped to your **resource group**

---
### Lab 2: 
Create a repository and store the ARM/Bicep template you created for web apps in this repo in a folder called `infra` and create a pipeline that runs each time a change is made to these files.

> Tip: [ARM templates in Azure Pipelines docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/add-template-to-azure-pipelines)
> tip: [Azure CLI task in Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/azure-cli?view=azure-devops)

1. Create a repository called `webapp-<yourinitials>` Azure Devops
2. Add the ARM/bicep templates you created to this repository
3. Create a yaml pipeline that executes the arm/bicep template at each push to your repository
4. Build & Deploy the [sample api]() after deploying the infrastructure
5. check the website by browsing to `https://<websiteurl>/swagger`

---
### Lab 3:
Create a pipeline that creates a dev + production environment

> Tip: [Azure Pipelines Stages docs](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/stages?view=azure-devops&tabs=yaml)

1. Create a 2nd service connection in Azure DevOps calles `sc-<yourinitials>-prod`
2. Add a stage for Dev & Prod and deploy the arm/bicep template & Code in each
3. Set manual approval on the service connection for production.
4. Deploy the production stage using the service connection
5. [Optional] Add a staging slot to the web app, deploy to it and auto switch after deployment for zero downtime deployments
