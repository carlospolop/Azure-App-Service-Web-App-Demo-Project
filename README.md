# Azure App Service Web App Demo Project

This tutorial azure cloud project demonstrates how to create and deploy a basic web app using azure. We will use our azure account to creature a resource group, app service plan, and a web app. Then we will configure a CI/CD pipeline (continuous integration/continuous deployment) that integregates with our GitHub code repository. Our demo web app is a flask template and python web application.
 
Watch the video tutorials and follow step-by-step instructions to learn how to create your own starter web app running on azure cloud using the azure portal. A second bonus video and instructions are shown that demonstrate quick start creation of a web-app using the CLI (command line interface).  

## Create an Azure Web App with the Azure Portal

### Create Azure Resource Group

Login into your Azure account and create a resource group for this project. In this tutorial we will be using the resource group name `resource-group-web-app-demo` .

### Create Web App Resource

Navigate to the resource group that was just created and add a new resource.
Search for "web app" in the azure marketplace and select the web app template.

A wizard process will guide you through the next steps.

#### Create an App Service Web App with the following configuration:

```
Resource-Group: resource-group-web-app-demo
Web App Name: unique name (example: my-web-app-demo)
Publish: Code
Runtime stack: Python 3.7 or Latest
Operating System: Linux
Region: Closest region to you
App Service Plan: Default name or Create new with a name of your choice
SKU and size: F1 (Free)
```
Note: Azure free account only allows one Linux App Service of size F1. You may need to delete the App Service along with the App Service Plan after this demo if you will create other Linux App Services.

### Verify Default Web App

After clicking on Create to create the web app resource, it may take a few minutes for azure to create and deploy the resource. Azure will deploy a default template for the python web app. Navigate to the Overview page for your web app and click on the URL to see the default deployed web app. A blank or white web page may appear for a few minutes as Azure completes the deployment of the web app. Be patient :)  

### Setup Azure Pipeline

In the Azure portal, navigate to the web app Deployment Center page. 
Select the source as GitHub.
If you have not done so already, clone or fork this web app repository to your own GitHub account.
Select your GitHub account, repository, and branch. You may need to authenticate.
Click on the Save button to save your deployment setup.

### Monitor Deployment Process

After you click save, click on Logs (on the Deployment center page) and navigate to the most recent record.
See the build and deploy activity logs on your GitHub project repository
Verify there are no build or deploy errors
Verify the deployment is complete

### View the Web App

The url to your web app is published in the Complete section of your azure pipeline log. Also, it is available on the Overview page of your web app in the azure portal. Click on the url to view your web app. You may need to do a "hard refresh" so that the browser will load the latest content. 

Voila! You have successfully created a Flask web application running on an azure web app. 

Congratulations!

## Create an Azure Web App with the CLI (Command Line Interface)

Open a BASH terminal window in the root directory of your project. 
Login to azure `az login`
Create a web app specifying the resource group name, web app name, and sku
```
az webapp up \
 --resource-group resource-group-web-app-demo \
 --name my-web-app-demo \
 --sku F1 \
 --verbose
```
This process may take a few minutes to validate your resource names, create, and then deploy your web app. But in the body of the json response you will see a url to access your web app

## Cleanup

Don't forget to stop your azure web app after you are done playing with your project and to delete your resource group. 

You can do this either using the azure portal or cli with this command

`az group delete -n resource-group-web-app-demo`
