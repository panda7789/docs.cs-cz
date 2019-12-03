---
title: Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e79b4c5bf38416cf45776488559bd0b2d5582361
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716468"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="e480c-103">Kurz: nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů</span><span class="sxs-lookup"><span data-stu-id="e480c-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="e480c-104">V tomto kurzu se naučíte, jak nasadit vaši aplikaci do cloudu prostřednictvím Azure Databricks, analytických platforem založených na Apache Spark s nastavením jedním kliknutím, zjednodušenými pracovními postupy a interaktivním pracovním prostorem, který umožňuje spolupráci.</span><span class="sxs-lookup"><span data-stu-id="e480c-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="e480c-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="e480c-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e480c-106">Vytvořte pracovní prostor Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="e480c-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="e480c-107">Publikování aplikace .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e480c-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="e480c-108">Vytvoření úlohy Spark a clusteru Spark</span><span class="sxs-lookup"><span data-stu-id="e480c-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="e480c-109">Spusťte aplikaci v clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="e480c-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e480c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e480c-110">Prerequisites</span></span>

<span data-ttu-id="e480c-111">Než začnete, proveďte následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="e480c-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="e480c-112">Pokud nemáte účet Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="e480c-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="e480c-113">Přihlaste se k [Azure Portal](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="e480c-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="e480c-114">Dokončete kurz [k rozhraní .NET pro Apache Spark – Začínáme během 10 minut](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="e480c-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="e480c-115">Vytvoření pracovního prostoru Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e480c-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="e480c-116">Tento kurz se nedá provést pomocí **předplatného Azure free zkušební verze**.</span><span class="sxs-lookup"><span data-stu-id="e480c-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="e480c-117">Pokud máte bezplatný účet, přejděte na svůj profil a změňte si předplatné na **průběžné platby**.</span><span class="sxs-lookup"><span data-stu-id="e480c-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="e480c-118">Další informace najdete v tématu [bezplatný účet Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="e480c-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="e480c-119">Pak [odeberte limit útraty](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)a [požádejte o zvýšení kvóty](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pro vCPU ve vaší oblasti.</span><span class="sxs-lookup"><span data-stu-id="e480c-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="e480c-120">Když vytváříte pracovní prostor Azure Databricks, můžete vybrat cenovou úroveň **DBU (Premium-14-days)** a poskytnout tak přístup k pracovnímu prostoru zdarma Premium Azure Databricks DBU po dobu 14 dnů.</span><span class="sxs-lookup"><span data-stu-id="e480c-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="e480c-121">V této části vytvoříte Azure Databricks pracovní prostor pomocí Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="e480c-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="e480c-122">V Azure Portal vyberte **vytvořit prostředek** > **Analytics** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="e480c-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Vytvoření prostředku Azure Databricks v Azure Portal](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="e480c-124">V části **služba Azure Databricks**zadejte hodnoty pro vytvoření pracovního prostoru datacihly.</span><span class="sxs-lookup"><span data-stu-id="e480c-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="e480c-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e480c-125">Property</span></span>  |<span data-ttu-id="e480c-126">Popis</span><span class="sxs-lookup"><span data-stu-id="e480c-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="e480c-127">**Název pracovního prostoru**</span><span class="sxs-lookup"><span data-stu-id="e480c-127">**Workspace name**</span></span>     | <span data-ttu-id="e480c-128">Zadejte název pracovního prostoru datacihly.</span><span class="sxs-lookup"><span data-stu-id="e480c-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="e480c-129">**Formě**</span><span class="sxs-lookup"><span data-stu-id="e480c-129">**Subscription**</span></span>     | <span data-ttu-id="e480c-130">V rozevíracím seznamu vyberte své předplatné Azure.</span><span class="sxs-lookup"><span data-stu-id="e480c-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="e480c-131">**Skupina prostředků**</span><span class="sxs-lookup"><span data-stu-id="e480c-131">**Resource group**</span></span>     | <span data-ttu-id="e480c-132">Určete, zda chcete vytvořit novou skupinu prostředků, nebo použít existující.</span><span class="sxs-lookup"><span data-stu-id="e480c-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="e480c-133">Skupina prostředků je kontejner, který uchovává související prostředky pro řešení Azure.</span><span class="sxs-lookup"><span data-stu-id="e480c-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="e480c-134">Další informace najdete v tématu [Přehled skupiny prostředků Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="e480c-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="e480c-135">**Poloha**</span><span class="sxs-lookup"><span data-stu-id="e480c-135">**Location**</span></span>     | <span data-ttu-id="e480c-136">Vyberte upřednostňovanou oblast.</span><span class="sxs-lookup"><span data-stu-id="e480c-136">Select your preferred region.</span></span> <span data-ttu-id="e480c-137">Informace o dostupných oblastech najdete v tématu [služby Azure dostupné v jednotlivých oblastech](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="e480c-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="e480c-138">**Cenová úroveň**</span><span class="sxs-lookup"><span data-stu-id="e480c-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="e480c-139">Vyberte si mezi **standardem**, **Premium**nebo **zkušební verzí**.</span><span class="sxs-lookup"><span data-stu-id="e480c-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="e480c-140">Další informace o těchto úrovních najdete na stránce s [cenami pro datacihly](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="e480c-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="e480c-141">**Virtual Network**</span><span class="sxs-lookup"><span data-stu-id="e480c-141">**Virtual Network**</span></span>     |   <span data-ttu-id="e480c-142">Ne</span><span class="sxs-lookup"><span data-stu-id="e480c-142">No</span></span>       |

3. <span data-ttu-id="e480c-143">Vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e480c-143">Select **Create**.</span></span> <span data-ttu-id="e480c-144">Vytváření pracovního prostoru trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="e480c-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="e480c-145">Při vytváření pracovního prostoru můžete zobrazit stav nasazení v části **oznámení**.</span><span class="sxs-lookup"><span data-stu-id="e480c-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="e480c-146">Nainstalovat Azure Databricks nástroje</span><span class="sxs-lookup"><span data-stu-id="e480c-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="e480c-147">Pomocí rozhraní příkazového **řádku datacihly** se můžete připojit k Azure Databricks clusterům a odesílat do nich soubory z místního počítače.</span><span class="sxs-lookup"><span data-stu-id="e480c-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="e480c-148">Clustery datacihly přistupují k souborům prostřednictvím DBFS (systém souborů datacihly).</span><span class="sxs-lookup"><span data-stu-id="e480c-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="e480c-149">Rozhraní příkazového řádku datacihly vyžaduje Python 3,6 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="e480c-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="e480c-150">Pokud už máte nainstalovaný Python, můžete tento krok přeskočit.</span><span class="sxs-lookup"><span data-stu-id="e480c-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="e480c-151">**Pro Windows:**</span><span class="sxs-lookup"><span data-stu-id="e480c-151">**For Windows:**</span></span>

   [<span data-ttu-id="e480c-152">Stažení Pythonu pro Windows</span><span class="sxs-lookup"><span data-stu-id="e480c-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="e480c-153">**Pro Linux:** Python přichází do předinstalovaných distribucí pro Linux.</span><span class="sxs-lookup"><span data-stu-id="e480c-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="e480c-154">Spuštěním následujícího příkazu zobrazíte verzi, kterou jste nainstalovali:</span><span class="sxs-lookup"><span data-stu-id="e480c-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="e480c-155">Pomocí PIP nainstalujte rozhraní příkazového řádku datacihly.</span><span class="sxs-lookup"><span data-stu-id="e480c-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="e480c-156">Python 3,4 a novější standardně zahrnují PIP.</span><span class="sxs-lookup"><span data-stu-id="e480c-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="e480c-157">Použijte PIP3 pro Python 3.</span><span class="sxs-lookup"><span data-stu-id="e480c-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="e480c-158">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="e480c-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="e480c-159">Po instalaci CLI datacihly otevřete nový příkazový řádek a spusťte příkaz `databricks`.</span><span class="sxs-lookup"><span data-stu-id="e480c-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="e480c-160">Pokud **se zobrazí "datacihly" nejsou rozpoznány jako vnitřní nebo externí Chyba příkazu**, otevřete nový příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="e480c-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="e480c-161">Nastavit Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e480c-161">Set up Azure Databricks</span></span>

<span data-ttu-id="e480c-162">Teď, když máte nainstalované rozhraní příkazového řádku datacihly, je potřeba nastavit podrobnosti ověřování.</span><span class="sxs-lookup"><span data-stu-id="e480c-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="e480c-163">Spusťte příkaz rozhraní příkazového řádku datacihly `databricks configure --token`.</span><span class="sxs-lookup"><span data-stu-id="e480c-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="e480c-164">Po spuštění příkazu konfigurace se zobrazí výzva k zadání hostitele.</span><span class="sxs-lookup"><span data-stu-id="e480c-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="e480c-165">Adresa URL hostitele používá formát: **https://< \Location >. NET**.</span><span class="sxs-lookup"><span data-stu-id="e480c-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="e480c-166">Pokud jste například během vytváření Azure Databricks služby vybrali možnost **eastus2** , bude hostitel **https://eastus2.azuredatabricks.net** .</span><span class="sxs-lookup"><span data-stu-id="e480c-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="e480c-167">Po zadání hostitele se zobrazí výzva k zadání tokenu.</span><span class="sxs-lookup"><span data-stu-id="e480c-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="e480c-168">V Azure Portal vyberte **Spustit pracovní prostor** a spusťte Azure Databricks pracovní prostor.</span><span class="sxs-lookup"><span data-stu-id="e480c-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Spustit Azure Databricks pracovní prostor](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="e480c-170">Na domovské stránce pracovního prostoru vyberte **nastavení uživatele**.</span><span class="sxs-lookup"><span data-stu-id="e480c-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Nastavení uživatele v pracovním prostoru Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="e480c-172">Na stránce nastavení uživatele můžete vygenerovat nový token.</span><span class="sxs-lookup"><span data-stu-id="e480c-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="e480c-173">Zkopírujte vygenerovaný token a vložte ho zpátky do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e480c-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Vygenerování nového přístupového tokenu v pracovním prostoru Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="e480c-175">Nyní byste měli mít přístup k jakýmkoli Azure Databricks clusterům, které vytvoříte a nahrajete soubory do DBFS.</span><span class="sxs-lookup"><span data-stu-id="e480c-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="e480c-176">Stáhnout závislosti pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="e480c-176">Download worker dependencies</span></span>

1. <span data-ttu-id="e480c-177">Microsoft. spark. Worker pomáhá Apache Spark spustit vaši aplikaci, jako jsou například všechny uživatelsky definované funkce (UDF), které jste mohli napsat.</span><span class="sxs-lookup"><span data-stu-id="e480c-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="e480c-178">Stáhněte si [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="e480c-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="e480c-179">*Install-Worker.sh* je skript, který umožňuje zkopírovat rozhraní .net pro Apache Spark závislé soubory do uzlů clusteru.</span><span class="sxs-lookup"><span data-stu-id="e480c-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="e480c-180">V místním počítači vytvořte nový soubor s názvem **install-Worker.sh** a vložte [obsah Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="e480c-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="e480c-181">*DB-init.sh* je skript, který nainstaluje závislosti do vašeho clusteru datacihly Spark.</span><span class="sxs-lookup"><span data-stu-id="e480c-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="e480c-182">V místním počítači vytvořte nový soubor s názvem **DB-init.sh** a vložte [obsah DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="e480c-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="e480c-183">V souboru, který jste právě vytvořili, nastavte proměnnou `DOTNET_SPARK_RELEASE` na `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="e480c-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="e480c-184">Zbývající část souboru *DB-init.sh* ponechte beze změny.</span><span class="sxs-lookup"><span data-stu-id="e480c-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="e480c-185">Pokud používáte systém Windows, ověřte, že zakončení řádků ve skriptech *install-Worker.sh* a *DB-init.sh* mají formát UNIX (LF).</span><span class="sxs-lookup"><span data-stu-id="e480c-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="e480c-186">Konce řádků můžete změnit pomocí textových editorů, jako je Poznámkový blok + + a Atom.</span><span class="sxs-lookup"><span data-stu-id="e480c-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="e480c-187">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="e480c-187">Publish your app</span></span>

<span data-ttu-id="e480c-188">V dalším kroku publikujete *mySparkApp* vytvořenou v [rozhraní .NET pro Apache Spark – Začínáme s 10 minutami](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , abyste zajistili, že cluster Spark bude mít přístup ke všem souborům, které potřebuje ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e480c-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="e480c-189">Pro publikování *mySparkApp*spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="e480c-189">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="e480c-190">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="e480c-190">**On Windows:**</span></span>

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x6
   ```

   <span data-ttu-id="e480c-191">**V systému Linux:**</span><span class="sxs-lookup"><span data-stu-id="e480c-191">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="e480c-192">Proveďte následující úlohy pro zip publikovaných souborů aplikace, abyste je mohli snadno nahrát do vašeho clusteru datacihly Spark.</span><span class="sxs-lookup"><span data-stu-id="e480c-192">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="e480c-193">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="e480c-193">**On Windows:**</span></span>

   <span data-ttu-id="e480c-194">Přejděte na mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="e480c-194">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="e480c-195">Potom klikněte pravým tlačítkem na složku pro **publikování** a vyberte **Odeslat do > Komprimovaná složka (ZIP)** .</span><span class="sxs-lookup"><span data-stu-id="e480c-195">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="e480c-196">Pojmenujte novou složku **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="e480c-196">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="e480c-197">**V systému Linux spusťte následující příkaz:**</span><span class="sxs-lookup"><span data-stu-id="e480c-197">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="e480c-198">Nahrání souborů</span><span class="sxs-lookup"><span data-stu-id="e480c-198">Upload files</span></span>

<span data-ttu-id="e480c-199">V této části nahrajete několik souborů do DBFS, aby měl váš cluster vše, co potřebuje ke spuštění vaší aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="e480c-199">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="e480c-200">Pokaždé, když nahrajete soubor do DBFS, ujistěte se, že jste v adresáři, ve kterém je tento soubor umístěný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="e480c-200">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="e480c-201">Spusťte následující příkazy, abyste nahráli *DB-init.sh*, *install-Worker.sh*a *Microsoft. spark. Worker* do DBFS:</span><span class="sxs-lookup"><span data-stu-id="e480c-201">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="e480c-202">Spuštěním následujících příkazů nahrajte zbývající soubory, které cluster bude potřebovat ke spuštění vaší aplikace: složku pro stažení zip, *input. txt*a *Microsoft-Spark-2.4. x-0.3.0. jar*.</span><span class="sxs-lookup"><span data-stu-id="e480c-202">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="e480c-203">Vytvoření úlohy</span><span class="sxs-lookup"><span data-stu-id="e480c-203">Create a job</span></span>

<span data-ttu-id="e480c-204">Vaše aplikace se spouští na Azure Databricks prostřednictvím úlohy, která spouští **Spark-Submit**, což je příkaz, který použijete ke spuštění .NET pro úlohy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e480c-204">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="e480c-205">V pracovním prostoru Azure Databricks vyberte ikonu **úlohy** a potom **+ vytvořit úlohu**.</span><span class="sxs-lookup"><span data-stu-id="e480c-205">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Vytvoření úlohy Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="e480c-207">Zvolte název úlohy a pak vyberte **Konfigurovat Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="e480c-207">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Konfigurace úlohy Spark-submit pro datacihly](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="e480c-209">Do konfigurace úlohy vložte následující parametry.</span><span class="sxs-lookup"><span data-stu-id="e480c-209">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="e480c-210">Pak vyberte **Potvrdit**.</span><span class="sxs-lookup"><span data-stu-id="e480c-210">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="e480c-211">Vytvoření clusteru</span><span class="sxs-lookup"><span data-stu-id="e480c-211">Create a cluster</span></span>

1. <span data-ttu-id="e480c-212">Přejděte do úlohy a výběrem **Upravit** Nakonfigurujte cluster vaší úlohy.</span><span class="sxs-lookup"><span data-stu-id="e480c-212">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="e480c-213">Nastavte cluster na **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="e480c-213">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="e480c-214">Pak vyberte **Upřesnit možnosti** > **skripty init**.</span><span class="sxs-lookup"><span data-stu-id="e480c-214">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="e480c-215">Nastavte cestu ke skriptu init jako `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="e480c-215">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Konfigurace clusteru Spark v Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="e480c-217">Vyberte **Potvrdit** a potvrďte nastavení clusteru.</span><span class="sxs-lookup"><span data-stu-id="e480c-217">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="e480c-218">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e480c-218">Run your app</span></span>

1. <span data-ttu-id="e480c-219">Přejděte do úlohy a výběrem **Spustit nyní** spusťte úlohu na nově nakonfigurovaném clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="e480c-219">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="e480c-220">Vytvoření clusteru úlohy trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="e480c-220">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="e480c-221">Po vytvoření bude vaše úloha odeslána a můžete zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="e480c-221">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="e480c-222">V nabídce vlevo vyberte **clustery** a potom název a spuštění úlohy.</span><span class="sxs-lookup"><span data-stu-id="e480c-222">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="e480c-223">Vyberte **protokoly ovladačů** a zobrazte výstup vaší úlohy.</span><span class="sxs-lookup"><span data-stu-id="e480c-223">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="e480c-224">Až se vaše aplikace dokončí, zobrazí se stejná tabulka počtu slov z místního spouštěného příkazu Začínáme do standardní výstupní konzoly.</span><span class="sxs-lookup"><span data-stu-id="e480c-224">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Výstupní tabulka úlohy Azure Databricks](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="e480c-226">Gratulujeme, spustili jste první rozhraní .NET pro Apache Spark aplikaci v cloudu!</span><span class="sxs-lookup"><span data-stu-id="e480c-226">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="e480c-227">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="e480c-227">Clean up resources</span></span>

<span data-ttu-id="e480c-228">Pokud už nepotřebujete pracovní prostor datacihly, můžete prostředek Azure Databricks odstranit v Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="e480c-228">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="e480c-229">Můžete také vybrat název skupiny prostředků a otevřít tak stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**.</span><span class="sxs-lookup"><span data-stu-id="e480c-229">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e480c-230">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e480c-230">Next steps</span></span>

<span data-ttu-id="e480c-231">V tomto kurzu jste nasadili rozhraní .NET pro Apache Spark aplikaci na datacihly.</span><span class="sxs-lookup"><span data-stu-id="e480c-231">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="e480c-232">Pokud se chcete dozvědět víc o datacihlách, přejděte k dokumentaci Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="e480c-232">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e480c-233">Dokumentace k Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e480c-233">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
