---
title: Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks
description: Zjistěte, jak nasadit .NET pro aplikaci Apache Spark do Databricks.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503958"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="45885-103">Kurz: Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks</span><span class="sxs-lookup"><span data-stu-id="45885-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="45885-104">Tento kurz vás naučí, jak nasadit aplikaci do cloudu prostřednictvím Azure Databricks, analytické platformy založené na Apache Spark s nastavením jedním kliknutím, zjednodušenými pracovními postupy a interaktivním pracovním prostorem, který umožňuje spolupráci.</span><span class="sxs-lookup"><span data-stu-id="45885-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="45885-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="45885-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="45885-106">Vytvořte pracovní prostor Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="45885-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="45885-107">Publikujte svou aplikaci .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="45885-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="45885-108">Vytvořte úlohu Spark a cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="45885-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="45885-109">Spusťte aplikaci v clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="45885-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45885-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45885-110">Prerequisites</span></span>

<span data-ttu-id="45885-111">Než začnete, proveďte následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="45885-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="45885-112">Pokud nemáte účet Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="45885-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="45885-113">Přihlaste se k [portálu Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="45885-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="45885-114">Dokončete [rozhraní .NET pro Apache Spark – začínáme v kurzu 10 minut.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)</span><span class="sxs-lookup"><span data-stu-id="45885-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="45885-115">Vytvoření pracovního prostoru Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="45885-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="45885-116">Tento kurz nelze provést pomocí **bezplatného zkušebního předplatného Azure**.</span><span class="sxs-lookup"><span data-stu-id="45885-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="45885-117">Pokud máte bezplatný účet, přejděte na svůj profil a změňte předplatné na **průběžně placené**.</span><span class="sxs-lookup"><span data-stu-id="45885-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="45885-118">Další informace najdete na stránce [bezplatného účtu Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="45885-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="45885-119">Potom [odeberte limit útraty](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)a [požádejte o zvýšení kvóty](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pro virtuální procesory ve vaší oblasti.</span><span class="sxs-lookup"><span data-stu-id="45885-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="45885-120">Když vytvoříte pracovní prostor Azure Databricks, můžete vybrat **zkušební (premium - 14denní jednotku DBU)** a poskytnout tak pracovnímu prostoru přístup k bezplatným dbům Azure Databricks Azure na 14 dní.</span><span class="sxs-lookup"><span data-stu-id="45885-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="45885-121">V této části vytvoříte pomocí portálu Azure pracovní prostor služby Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="45885-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="45885-122">Na webu Azure Portal vyberte **Vytvořit zdroj** > **Analytics** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="45885-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Vytvoření prostředku Azure Databricks na webu Azure Portal](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="45885-124">V části **Služba Azure Databricks** zadejte hodnoty pro vytvoření pracovního prostoru Databricks.</span><span class="sxs-lookup"><span data-stu-id="45885-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="45885-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="45885-125">Property</span></span>  |<span data-ttu-id="45885-126">Popis</span><span class="sxs-lookup"><span data-stu-id="45885-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="45885-127">**Název pracovního prostoru**</span><span class="sxs-lookup"><span data-stu-id="45885-127">**Workspace name**</span></span>     | <span data-ttu-id="45885-128">Zadejte název pracovního prostoru Databricks.</span><span class="sxs-lookup"><span data-stu-id="45885-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="45885-129">**Předplatné**</span><span class="sxs-lookup"><span data-stu-id="45885-129">**Subscription**</span></span>     | <span data-ttu-id="45885-130">Z rozevíracího seznamu vyberte své předplatné Azure.</span><span class="sxs-lookup"><span data-stu-id="45885-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="45885-131">**Skupina prostředků**</span><span class="sxs-lookup"><span data-stu-id="45885-131">**Resource group**</span></span>     | <span data-ttu-id="45885-132">Určete, jestli chcete vytvořit novou skupinu prostředků, nebo použít existující.</span><span class="sxs-lookup"><span data-stu-id="45885-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="45885-133">Skupina prostředků je kontejner, který obsahuje související prostředky pro řešení Azure.</span><span class="sxs-lookup"><span data-stu-id="45885-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="45885-134">Další informace naleznete v tématu [Přehled skupin prostředků v Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="45885-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="45885-135">**Umístění**</span><span class="sxs-lookup"><span data-stu-id="45885-135">**Location**</span></span>     | <span data-ttu-id="45885-136">Vyberte preferovanou oblast.</span><span class="sxs-lookup"><span data-stu-id="45885-136">Select your preferred region.</span></span> <span data-ttu-id="45885-137">Informace o dostupných oblastech najdete v [tématu Služby Azure dostupné podle oblastí](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="45885-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="45885-138">**Cenová úroveň**</span><span class="sxs-lookup"><span data-stu-id="45885-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="45885-139">Vyberte si mezi **standardními**, **prémiovými**nebo **zkušebními verzemi**.</span><span class="sxs-lookup"><span data-stu-id="45885-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="45885-140">Další informace o těchto úrovních najdete na [stránce s cenami za Databricks](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="45885-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="45885-141">**Virtuální síť**</span><span class="sxs-lookup"><span data-stu-id="45885-141">**Virtual Network**</span></span>     |   <span data-ttu-id="45885-142">Ne</span><span class="sxs-lookup"><span data-stu-id="45885-142">No</span></span>       |

3. <span data-ttu-id="45885-143">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="45885-143">Select **Create**.</span></span> <span data-ttu-id="45885-144">Vytvoření pracovního prostoru trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="45885-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="45885-145">Během vytváření pracovního prostoru můžete zobrazit stav nasazení v **oznámení .**</span><span class="sxs-lookup"><span data-stu-id="45885-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="45885-146">Instalace nástrojů Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="45885-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="45885-147">**Cli Databricks** můžete použít k připojení ke clusterům Azure Databricks a k nahrání souborů z místního počítače.</span><span class="sxs-lookup"><span data-stu-id="45885-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="45885-148">Clustery Databricks přistupují k souborům prostřednictvím DBFS (Databricks File System).</span><span class="sxs-lookup"><span data-stu-id="45885-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="45885-149">Nařízení o cli Databricks vyžaduje Python 3.6 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="45885-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="45885-150">Pokud již máte nainstalovaný Python, můžete tento krok přeskočit.</span><span class="sxs-lookup"><span data-stu-id="45885-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="45885-151">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="45885-151">**For Windows:**</span></span>

   [<span data-ttu-id="45885-152">Stažení Pythonu pro Windows</span><span class="sxs-lookup"><span data-stu-id="45885-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="45885-153">**Pro Linux:** Python je předinstalován na většině linuxových distribucí.</span><span class="sxs-lookup"><span data-stu-id="45885-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="45885-154">Spuštěním následujícího příkazu zobrazíte, kterou verzi jste nainstalovali:</span><span class="sxs-lookup"><span data-stu-id="45885-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="45885-155">Použijte pip k instalaci Databricks CLI.</span><span class="sxs-lookup"><span data-stu-id="45885-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="45885-156">Python 3.4 a novější ve výchozím nastavení obsahují pip.</span><span class="sxs-lookup"><span data-stu-id="45885-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="45885-157">Použijte pip3 pro Python 3.</span><span class="sxs-lookup"><span data-stu-id="45885-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="45885-158">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="45885-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="45885-159">Po instalaci příkazového řádku Databricks otevřete nový příkazový `databricks`řádek a spusťte příkaz .</span><span class="sxs-lookup"><span data-stu-id="45885-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="45885-160">Pokud se zobrazí **'databricks' není rozpoznán jako vnitřní nebo externí chyba příkazu**, ujistěte se, že jste otevřeli nový příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="45885-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="45885-161">Nastavení Datových cihel Azure</span><span class="sxs-lookup"><span data-stu-id="45885-161">Set up Azure Databricks</span></span>

<span data-ttu-id="45885-162">Nyní, když máte nainstalováno nařízení cli Databricks, je třeba nastavit podrobnosti ověřování.</span><span class="sxs-lookup"><span data-stu-id="45885-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="45885-163">Spusťte příkaz `databricks configure --token`příkazu příkazu příkazu příkazu Příkaz příkazu Databricks .</span><span class="sxs-lookup"><span data-stu-id="45885-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="45885-164">Po spuštění příkazu configure budete vyzváni k zadání hostitele.</span><span class="sxs-lookup"><span data-stu-id="45885-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="45885-165">Adresa URL hostitele používá formát: **https://<\Location>.azuredatabricks.net**.</span><span class="sxs-lookup"><span data-stu-id="45885-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="45885-166">Například pokud jste vybrali **eastus2** během vytváření služby Azure **https://eastus2.azuredatabricks.net**Databricks, hostitel by .</span><span class="sxs-lookup"><span data-stu-id="45885-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="45885-167">Po zadání hostitele budete vyzváni k zadání tokenu.</span><span class="sxs-lookup"><span data-stu-id="45885-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="45885-168">Na webu Azure Portal vyberte **Spustit pracovní prostor** a spusťte pracovní prostor Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="45885-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Spuštění pracovního prostoru Azure Databricks](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="45885-170">Na domovské stránce pracovního prostoru vyberte **Uživatelská nastavení**.</span><span class="sxs-lookup"><span data-stu-id="45885-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Uživatelská nastavení v pracovním prostoru Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="45885-172">Na stránce Nastavení uživatele můžete vygenerovat nový token.</span><span class="sxs-lookup"><span data-stu-id="45885-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="45885-173">Zkopírujte vygenerovaný token a vložte jej zpět do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="45885-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Generování nového přístupového tokenu v pracovním prostoru Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="45885-175">Teď byste měli mít přístup ke všem clusterům Azure Databricks, které vytvoříte a nahrajete soubory do DBFS.</span><span class="sxs-lookup"><span data-stu-id="45885-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="45885-176">Stáhnout závislosti pracovníků</span><span class="sxs-lookup"><span data-stu-id="45885-176">Download worker dependencies</span></span>

1. <span data-ttu-id="45885-177">Microsoft.Spark.Worker pomáhá Apache Spark spouštět vaši aplikaci, jako jsou všechny uživatelem definované funkce (UDFs), které jste napsali.</span><span class="sxs-lookup"><span data-stu-id="45885-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="45885-178">Stáhnout [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="45885-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="45885-179">*install-worker.sh* je skript, který umožňuje kopírovat .NET pro apache spark závislé soubory do uzlů clusteru.</span><span class="sxs-lookup"><span data-stu-id="45885-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="45885-180">Vytvořte nový soubor s názvem **install-worker.sh** v místním počítači a vložte [obsah install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="45885-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="45885-181">Db-init.sh *db-init.sh* je skript, který instaluje závislosti do clusteru Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="45885-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="45885-182">Vytvořte nový soubor s názvem **db-init.sh** v místním počítači a vložte [obsah db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="45885-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="45885-183">V souboru, který jste `DOTNET_SPARK_RELEASE` právě `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`vytvořili, nastavte proměnnou na .</span><span class="sxs-lookup"><span data-stu-id="45885-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="45885-184">Zbytek *souboru db-init.sh* ponechejte tak, jak je.</span><span class="sxs-lookup"><span data-stu-id="45885-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="45885-185">Pokud používáte systém Windows, ověřte, zda koncovky řádků ve *skriptech install-worker.sh* a *db-init.sh* jsou ve stylu Unixu (LF).</span><span class="sxs-lookup"><span data-stu-id="45885-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="45885-186">Konce řádků můžete měnit prostřednictvím textových editorů, jako je Notepad++ a Atom.</span><span class="sxs-lookup"><span data-stu-id="45885-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="45885-187">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="45885-187">Publish your app</span></span>

<span data-ttu-id="45885-188">Dále publikujete *mySparkApp* vytvořený v [rozhraní .NET pro Apache Spark – Začínáme v kurzu 10 minut,](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) abyste zajistili, že váš cluster Spark bude mít přístup ke všem souborům, které potřebuje ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="45885-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="45885-189">Chcete-li publikovat *mySparkApp,* spusťte následující příkazy :</span><span class="sxs-lookup"><span data-stu-id="45885-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="45885-190">Proveďte následující úkoly, abyste mohli publikované soubory aplikací zipovat, abyste je mohli snadno nahrát do clusteru Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="45885-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="45885-191">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="45885-191">**On Windows:**</span></span>

   <span data-ttu-id="45885-192">Přejděte na mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="45885-192">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="45885-193">Potom klikněte pravým tlačítkem myši na složku **Publikovat** a vyberte **příkaz Odeslat do > komprimovované (zip) složky**.</span><span class="sxs-lookup"><span data-stu-id="45885-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="45885-194">Pojmenujte novou složku **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="45885-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="45885-195">**Na Linuxu spusťte následující příkaz:**</span><span class="sxs-lookup"><span data-stu-id="45885-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="45885-196">Nahrání souborů</span><span class="sxs-lookup"><span data-stu-id="45885-196">Upload files</span></span>

<span data-ttu-id="45885-197">V této části nahrajete několik souborů do DBFS, aby váš cluster měl vše, co potřebuje ke spuštění aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="45885-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="45885-198">Při každém nahrání souboru do dbfs, ujistěte se, že jste v adresáři, kde je tento soubor umístěn v počítači.</span><span class="sxs-lookup"><span data-stu-id="45885-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="45885-199">Spusťte následující příkazy pro nahrání *db-init.sh*, *install-worker.sh*a *Microsoft.Spark.Worker* do DBFS:</span><span class="sxs-lookup"><span data-stu-id="45885-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="45885-200">Spusťte následující příkazy k nahrání zbývajících souborů, které bude váš cluster potřebovat ke spuštění aplikace: složka publikování na zip, *input.txt*a *microsoft-spark-2.4.x-0.3.0.jar*.</span><span class="sxs-lookup"><span data-stu-id="45885-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="45885-201">Vytvoření úlohy</span><span class="sxs-lookup"><span data-stu-id="45885-201">Create a job</span></span>

<span data-ttu-id="45885-202">Vaše aplikace běží na Azure Databricks prostřednictvím úlohy, která spouští **spark-submit**, což je příkaz, který používáte ke spuštění .NET pro úlohy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="45885-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="45885-203">V pracovním prostoru Azure Databricks vyberte ikonu **Úlohy** a potom **+ Vytvořit úlohu**.</span><span class="sxs-lookup"><span data-stu-id="45885-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Vytvoření úlohy Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="45885-205">Vyberte název úlohy a pak vyberte **Konfigurovat spark-submit**.</span><span class="sxs-lookup"><span data-stu-id="45885-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Konfigurace úlohy spark-submit pro Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="45885-207">Vložte do konfigurace úlohy následující parametry.</span><span class="sxs-lookup"><span data-stu-id="45885-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="45885-208">Potom vyberte **Potvrdit**.</span><span class="sxs-lookup"><span data-stu-id="45885-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="45885-209">Vytvoření clusteru</span><span class="sxs-lookup"><span data-stu-id="45885-209">Create a cluster</span></span>

1. <span data-ttu-id="45885-210">Přejděte do úlohy a vyberte **Upravit** a nakonfigurujte cluster své úlohy.</span><span class="sxs-lookup"><span data-stu-id="45885-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="45885-211">Nastavte cluster na **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="45885-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="45885-212">Potom vyberte **Možnosti upřesnit** > **init skripty**.</span><span class="sxs-lookup"><span data-stu-id="45885-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="45885-213">Nastavte cestu skriptu `dbfs:/spark-dotnet/db-init.sh`Init jako .</span><span class="sxs-lookup"><span data-stu-id="45885-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Konfigurace clusteru spark v Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="45885-215">Chcete-li potvrdit nastavení clusteru, vyberte potvrdit možnost **Potvrdit.**</span><span class="sxs-lookup"><span data-stu-id="45885-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="45885-216">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="45885-216">Run your app</span></span>

1. <span data-ttu-id="45885-217">Přejděte ke své úloze a vyberte **Spustit nyní,** chcete-li spustit úlohu v nově nakonfigurovaném clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="45885-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="45885-218">Vytvoření clusteru úlohy trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="45885-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="45885-219">Jakmile je vytvořena, bude vaše úloha odeslána a můžete zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="45885-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="45885-220">V levé nabídce vyberte **Clustery** a potom název a spuštění úlohy.</span><span class="sxs-lookup"><span data-stu-id="45885-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="45885-221">Chcete-li zobrazit výstup úlohy, vyberte **protokoly ovladačů.**</span><span class="sxs-lookup"><span data-stu-id="45885-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="45885-222">Po dokončení provádění aplikace se zobrazí stejná tabulka počtu slov z místního spuštění Začínáme zapsaného do standardní výstupní konzoly.</span><span class="sxs-lookup"><span data-stu-id="45885-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Výstupní tabulka úloh Azure Databricks](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="45885-224">Gratulujeme, jste spustit svůj první .NET pro Apache Spark aplikace v cloudu!</span><span class="sxs-lookup"><span data-stu-id="45885-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="45885-225">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="45885-225">Clean up resources</span></span>

<span data-ttu-id="45885-226">Pokud už nepotřebujete pracovní prostor Databricks, můžete odstranit prostředek Azure Databricks na webu Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="45885-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="45885-227">Můžete také výběrem názvu skupiny prostředků otevřít stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**.</span><span class="sxs-lookup"><span data-stu-id="45885-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="45885-228">Další kroky</span><span class="sxs-lookup"><span data-stu-id="45885-228">Next steps</span></span>

<span data-ttu-id="45885-229">V tomto kurzu jste nasadili .NET pro aplikaci Apache Spark do Databricks.</span><span class="sxs-lookup"><span data-stu-id="45885-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="45885-230">Další informace o Databricks, pokračujte v dokumentaci Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="45885-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="45885-231">Dokumentace k Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="45885-231">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
