---
title: Create a static HTML web app in Azure in five minutes | Microsoft Docs
description: Learn how easy it is to run web apps in App Service by deploying a sample app.
services: app-service\web
documentationcenter: ''
author: cephalin
manager: wpickett
editor: ''

ms.assetid: 60495cc5-6963-4bf0-8174-52786d226c26
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: hero-article
ms.date: 03/08/2017
ms.author: cephalin

---
# Create a static HTML web app in Azure in five minutes
[!INCLUDE [app-service-web-selector-get-started](../../includes/app-service-web-selector-get-started.md)] 

This Quickstart helps you deploy a simple HTML+CSS site to [Azure App Service](../app-service/app-service-value-prop-what-is.md) in just a few minutes.

Before starting this Quickstart, ensure that [the Azure CLI is installed](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) on your machine.

## Create a static HTML site in Azure
2. Log in to Azure by running `az login` and following the on-screen directions.
   
    ```azurecli
    az login
    ```

3. Create a [resource group](../azure-resource-manager/resource-group-overview.md). This is where you put all the Azure resources that you want to manage together, such as 
the web app and its SQL Database back end.

    ```azurecli
    az group create --location "West Europe" --name myResourceGroup
    ```

    To see what possible values you can use for `---location`, use the `az appservice list-locations` Azure CLI command.

3. Create a "FREE" [App Service plan](../app-service/azure-web-sites-web-hosting-plans-in-depth-overview.md). 

    ```azurecli
    az appservice plan create --name my-free-appservice-plan --resource-group myResourceGroup --sku FREE
    ```

4. Create a new web app with a unique name in `<app_name>`.

    ```azurecli
    az appservice web create --name <app_name> --resource-group myResourceGroup --plan my-free-appservice-plan
    ```

4. Deploy a sample HTML site from GitHub.

    ```azurecli
    az appservice web source-control config --name <app_name> --resource-group myResourceGroup \
    --repo-url "https://github.com/Azure-Samples/app-service-web-html-get-started.git" --branch master --manual-integration 
    ```

5. To see your app running live in Azure, run this command.

    ```azurecli
    az appservice web browse --name <app_name> --resource-group myResourceGroup
    ```

Congratulations, your first static HTML site is running live in Azure App Service.

[!INCLUDE [cli-samples-clean-up](../../includes/cli-samples-clean-up.md)]

## Next steps

Explore pre-created [Web apps CLI scripts](app-service-cli-samples.md).
