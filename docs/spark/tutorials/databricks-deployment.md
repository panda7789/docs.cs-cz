---
title: Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.
ms.date: 05/12/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4010f363e8ba606a7294ea32dc34587da6d6c8aa
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202232"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="10b90-103">Kurz: nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů</span><span class="sxs-lookup"><span data-stu-id="10b90-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="10b90-104">V tomto kurzu se naučíte, jak nasadit vaši aplikaci do cloudu prostřednictvím Azure Databricks, analytických platforem založených na Apache Spark s nastavením jedním kliknutím, zjednodušenými pracovními postupy a interaktivním pracovním prostorem, který umožňuje spolupráci.</span><span class="sxs-lookup"><span data-stu-id="10b90-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="10b90-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="10b90-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="10b90-106">Vytvořte pracovní prostor Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="10b90-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="10b90-107">Publikování aplikace .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="10b90-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="10b90-108">Vytvoření úlohy Spark a clusteru Spark</span><span class="sxs-lookup"><span data-stu-id="10b90-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="10b90-109">Spusťte aplikaci v clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="10b90-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10b90-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10b90-110">Prerequisites</span></span>

<span data-ttu-id="10b90-111">Než začnete, proveďte následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="10b90-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="10b90-112">Pokud nemáte účet Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="10b90-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="10b90-113">Přihlaste se k webu [Azure Portal](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="10b90-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="10b90-114">Dokončete kurz [k rozhraní .NET pro Apache Spark – Začínáme během 10 minut](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="10b90-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="10b90-115">Vytvoření pracovního prostoru Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="10b90-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="10b90-116">Tento kurz se nedá provést pomocí **předplatného Azure free zkušební verze**.</span><span class="sxs-lookup"><span data-stu-id="10b90-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="10b90-117">Pokud máte bezplatný účet, přejděte na svůj profil a změňte si předplatné na **průběžné platby**.</span><span class="sxs-lookup"><span data-stu-id="10b90-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="10b90-118">Další informace najdete na stránce [bezplatného účtu Azure](https://azure.microsoft.com/free/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="10b90-118">For more information, see [Azure free account](https://azure.microsoft.com/free/dotnet/).</span></span> <span data-ttu-id="10b90-119">Pak [odeberte limit útraty](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)a [požádejte o zvýšení kvóty](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pro vCPU ve vaší oblasti.</span><span class="sxs-lookup"><span data-stu-id="10b90-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="10b90-120">Když vytváříte pracovní prostor Azure Databricks, můžete vybrat cenovou úroveň **DBU (Premium-14-days)** a poskytnout tak přístup k pracovnímu prostoru zdarma Premium Azure Databricks DBU po dobu 14 dnů.</span><span class="sxs-lookup"><span data-stu-id="10b90-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="10b90-121">V této části vytvoříte pomocí portálu Azure pracovní prostor služby Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="10b90-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="10b90-122">V Azure Portal vyberte vytvořit Azure Databricks **prostředků**  >  **Analytics**  >  **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="10b90-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Vytvoření prostředku Azure Databricks v Azure Portal](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="10b90-124">V části **Služba Azure Databricks** zadejte hodnoty pro vytvoření pracovního prostoru Databricks.</span><span class="sxs-lookup"><span data-stu-id="10b90-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="10b90-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="10b90-125">Property</span></span>  |<span data-ttu-id="10b90-126">Popis</span><span class="sxs-lookup"><span data-stu-id="10b90-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="10b90-127">**Název pracovního prostoru**</span><span class="sxs-lookup"><span data-stu-id="10b90-127">**Workspace name**</span></span>     | <span data-ttu-id="10b90-128">Zadejte název pracovního prostoru Databricks.</span><span class="sxs-lookup"><span data-stu-id="10b90-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="10b90-129">**Předplatné**</span><span class="sxs-lookup"><span data-stu-id="10b90-129">**Subscription**</span></span>     | <span data-ttu-id="10b90-130">Z rozevíracího seznamu vyberte své předplatné Azure.</span><span class="sxs-lookup"><span data-stu-id="10b90-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="10b90-131">**Skupina prostředků**</span><span class="sxs-lookup"><span data-stu-id="10b90-131">**Resource group**</span></span>     | <span data-ttu-id="10b90-132">Určete, jestli chcete vytvořit novou skupinu prostředků, nebo použít existující.</span><span class="sxs-lookup"><span data-stu-id="10b90-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="10b90-133">Skupina prostředků je kontejner, který uchovává související prostředky pro řešení Azure.</span><span class="sxs-lookup"><span data-stu-id="10b90-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="10b90-134">Další informace naleznete v tématu [Přehled skupin prostředků v Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="10b90-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="10b90-135">**Umístění**</span><span class="sxs-lookup"><span data-stu-id="10b90-135">**Location**</span></span>     | <span data-ttu-id="10b90-136">Vyberte preferovanou oblast.</span><span class="sxs-lookup"><span data-stu-id="10b90-136">Select your preferred region.</span></span> <span data-ttu-id="10b90-137">Informace o dostupných oblastech najdete v tématu [služby Azure dostupné v jednotlivých oblastech](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="10b90-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="10b90-138">**Cenová úroveň**</span><span class="sxs-lookup"><span data-stu-id="10b90-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="10b90-139">Vyberte si mezi **standardem**, **Premium**nebo **zkušební verzí**.</span><span class="sxs-lookup"><span data-stu-id="10b90-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="10b90-140">Další informace o těchto úrovních najdete na [stránce s cenami za Databricks](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="10b90-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="10b90-141">**Virtual Network**</span><span class="sxs-lookup"><span data-stu-id="10b90-141">**Virtual Network**</span></span>     |   <span data-ttu-id="10b90-142">No</span><span class="sxs-lookup"><span data-stu-id="10b90-142">No</span></span>       |

3. <span data-ttu-id="10b90-143">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="10b90-143">Select **Create**.</span></span> <span data-ttu-id="10b90-144">Vytvoření pracovního prostoru trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="10b90-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="10b90-145">Při vytváření pracovního prostoru můžete zobrazit stav nasazení v části **oznámení**.</span><span class="sxs-lookup"><span data-stu-id="10b90-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="10b90-146">Nainstalovat Azure Databricks nástroje</span><span class="sxs-lookup"><span data-stu-id="10b90-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="10b90-147">Pomocí rozhraní příkazového **řádku datacihly** se můžete připojit k Azure Databricks clusterům a odesílat do nich soubory z místního počítače.</span><span class="sxs-lookup"><span data-stu-id="10b90-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="10b90-148">Clustery datacihly přistupují k souborům prostřednictvím DBFS (systém souborů datacihly).</span><span class="sxs-lookup"><span data-stu-id="10b90-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="10b90-149">Rozhraní příkazového řádku datacihly vyžaduje Python 3,6 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="10b90-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="10b90-150">Pokud už máte nainstalovaný Python, můžete tento krok přeskočit.</span><span class="sxs-lookup"><span data-stu-id="10b90-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="10b90-151">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="10b90-151">**For Windows:**</span></span>

   [<span data-ttu-id="10b90-152">Stažení Pythonu pro Windows</span><span class="sxs-lookup"><span data-stu-id="10b90-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="10b90-153">**Pro Linux:** Python přichází do předinstalovaných distribucí pro Linux.</span><span class="sxs-lookup"><span data-stu-id="10b90-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="10b90-154">Spuštěním následujícího příkazu zobrazíte verzi, kterou jste nainstalovali:</span><span class="sxs-lookup"><span data-stu-id="10b90-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="10b90-155">Pomocí PIP nainstalujte rozhraní příkazového řádku datacihly.</span><span class="sxs-lookup"><span data-stu-id="10b90-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="10b90-156">Python 3,4 a novější standardně zahrnují PIP.</span><span class="sxs-lookup"><span data-stu-id="10b90-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="10b90-157">Použijte PIP3 pro Python 3.</span><span class="sxs-lookup"><span data-stu-id="10b90-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="10b90-158">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="10b90-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="10b90-159">Po instalaci CLI datacihly otevřete nový příkazový řádek a spusťte příkaz `databricks` .</span><span class="sxs-lookup"><span data-stu-id="10b90-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="10b90-160">Pokud **se zobrazí "datacihly" nejsou rozpoznány jako vnitřní nebo externí Chyba příkazu**, otevřete nový příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="10b90-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="10b90-161">Nastavit Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="10b90-161">Set up Azure Databricks</span></span>

<span data-ttu-id="10b90-162">Teď, když máte nainstalované rozhraní příkazového řádku datacihly, je potřeba nastavit podrobnosti ověřování.</span><span class="sxs-lookup"><span data-stu-id="10b90-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="10b90-163">Spusťte příkaz rozhraní příkazového řádku datacihly `databricks configure --token` .</span><span class="sxs-lookup"><span data-stu-id="10b90-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="10b90-164">Po spuštění příkazu konfigurace se zobrazí výzva k zadání hostitele.</span><span class="sxs-lookup"><span data-stu-id="10b90-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="10b90-165">Adresa URL hostitele používá formát: `https://<Location>.azuredatabricks.net` .</span><span class="sxs-lookup"><span data-stu-id="10b90-165">Your host URL uses the format: `https://<Location>.azuredatabricks.net`.</span></span> <span data-ttu-id="10b90-166">Pokud jste například vybrali **eastus2** při vytváření služby Azure Databricks, hostitel by byl `https://eastus2.azuredatabricks.net` .</span><span class="sxs-lookup"><span data-stu-id="10b90-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be `https://eastus2.azuredatabricks.net`.</span></span>

3. <span data-ttu-id="10b90-167">Po zadání hostitele se zobrazí výzva k zadání tokenu.</span><span class="sxs-lookup"><span data-stu-id="10b90-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="10b90-168">V Azure Portal vyberte **Spustit pracovní prostor** a spusťte Azure Databricks pracovní prostor.</span><span class="sxs-lookup"><span data-stu-id="10b90-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Spustit Azure Databricks pracovní prostor](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="10b90-170">Na domovské stránce pracovního prostoru vyberte **nastavení uživatele**.</span><span class="sxs-lookup"><span data-stu-id="10b90-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Nastavení uživatele v pracovním prostoru Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="10b90-172">Na stránce nastavení uživatele můžete vygenerovat nový token.</span><span class="sxs-lookup"><span data-stu-id="10b90-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="10b90-173">Zkopírujte vygenerovaný token a vložte ho zpátky do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="10b90-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Vygenerování nového přístupového tokenu v pracovním prostoru Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="10b90-175">Nyní byste měli mít přístup k jakýmkoli Azure Databricks clusterům, které vytvoříte a nahrajete soubory do DBFS.</span><span class="sxs-lookup"><span data-stu-id="10b90-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="10b90-176">Stáhnout závislosti pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="10b90-176">Download worker dependencies</span></span>

1. <span data-ttu-id="10b90-177">Microsoft. spark. Worker pomáhá Apache Spark spustit vaši aplikaci, jako jsou například všechny uživatelsky definované funkce (UDF), které jste mohli napsat.</span><span class="sxs-lookup"><span data-stu-id="10b90-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="10b90-178">Stáhněte si [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="10b90-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="10b90-179">*Install-Worker.sh* je skript, který umožňuje zkopírovat rozhraní .net pro Apache Spark závislé soubory do uzlů clusteru.</span><span class="sxs-lookup"><span data-stu-id="10b90-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="10b90-180">V místním počítači vytvořte nový soubor s názvem **install-Worker.sh** a vložte [obsah Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="10b90-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="10b90-181">*DB-init.sh* je skript, který nainstaluje závislosti do vašeho clusteru datacihly Spark.</span><span class="sxs-lookup"><span data-stu-id="10b90-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="10b90-182">V místním počítači vytvořte nový soubor s názvem **DB-init.sh** a vložte [obsah DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="10b90-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="10b90-183">V souboru, který jste právě vytvořili, nastavte `DOTNET_SPARK_RELEASE` proměnnou na `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz` .</span><span class="sxs-lookup"><span data-stu-id="10b90-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="10b90-184">Zbývající část souboru *DB-init.sh* ponechte beze změny.</span><span class="sxs-lookup"><span data-stu-id="10b90-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="10b90-185">Pokud používáte systém Windows, ověřte, že zakončení řádků ve skriptech *install-Worker.sh* a *DB-init.sh* mají formát UNIX (LF).</span><span class="sxs-lookup"><span data-stu-id="10b90-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="10b90-186">Konce řádků můžete změnit pomocí textových editorů, jako je Poznámkový blok + + a Atom.</span><span class="sxs-lookup"><span data-stu-id="10b90-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="10b90-187">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="10b90-187">Publish your app</span></span>

<span data-ttu-id="10b90-188">V dalším kroku publikujete *mySparkApp* vytvořenou v [rozhraní .NET pro Apache Spark – Začínáme s 10 minutami](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , abyste zajistili, že cluster Spark bude mít přístup ke všem souborům, které potřebuje ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="10b90-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="10b90-189">Pro publikování *mySparkApp*spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="10b90-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="10b90-190">Proveďte následující úlohy pro zip publikovaných souborů aplikace, abyste je mohli snadno nahrát do vašeho clusteru datacihly Spark.</span><span class="sxs-lookup"><span data-stu-id="10b90-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="10b90-191">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="10b90-191">**On Windows:**</span></span>

   <span data-ttu-id="10b90-192">Přejděte na mySparkApp/bin/Release/netcoreapp 3.1/Ubuntu. 16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="10b90-192">Navigate to mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64.</span></span> <span data-ttu-id="10b90-193">Potom klikněte pravým tlačítkem na složku pro **publikování** a vyberte **Odeslat do > Komprimovaná složka (ZIP)**.</span><span class="sxs-lookup"><span data-stu-id="10b90-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="10b90-194">Pojmenujte novou složku **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="10b90-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="10b90-195">**V systému Linux spusťte následující příkaz:**</span><span class="sxs-lookup"><span data-stu-id="10b90-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="10b90-196">Nahrání souborů</span><span class="sxs-lookup"><span data-stu-id="10b90-196">Upload files</span></span>

<span data-ttu-id="10b90-197">V této části nahrajete několik souborů do DBFS, aby měl váš cluster vše, co potřebuje ke spuštění vaší aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="10b90-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="10b90-198">Pokaždé, když nahrajete soubor do DBFS, ujistěte se, že jste v adresáři, ve kterém je tento soubor umístěný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="10b90-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="10b90-199">Spusťte následující příkazy, abyste nahráli *DB-init.sh*, *install-Worker.sh*a *Microsoft. spark. Worker* do DBFS:</span><span class="sxs-lookup"><span data-stu-id="10b90-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="10b90-200">Spuštěním následujících příkazů nahrajte zbývající soubory, které cluster bude potřebovat ke spuštění vaší aplikace: složku pro stažení zip, *input. txt*a *Microsoft-Spark-2.4. x-0.3.1. jar*.</span><span class="sxs-lookup"><span data-stu-id="10b90-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.1.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.1\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="10b90-201">Vytvoření úlohy</span><span class="sxs-lookup"><span data-stu-id="10b90-201">Create a job</span></span>

<span data-ttu-id="10b90-202">Vaše aplikace se spouští na Azure Databricks prostřednictvím úlohy, která spouští **Spark-Submit**, což je příkaz, který použijete ke spuštění .NET pro úlohy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="10b90-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="10b90-203">V pracovním prostoru Azure Databricks vyberte ikonu **úlohy** a potom **+ vytvořit úlohu**.</span><span class="sxs-lookup"><span data-stu-id="10b90-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Vytvoření úlohy Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="10b90-205">Zvolte název úlohy a pak vyberte **Konfigurovat Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="10b90-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Konfigurace úlohy Spark-submit pro datacihly](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="10b90-207">Do konfigurace úlohy vložte následující parametry.</span><span class="sxs-lookup"><span data-stu-id="10b90-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="10b90-208">Pak vyberte **Potvrdit**.</span><span class="sxs-lookup"><span data-stu-id="10b90-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="10b90-209">Vytvoření clusteru</span><span class="sxs-lookup"><span data-stu-id="10b90-209">Create a cluster</span></span>

1. <span data-ttu-id="10b90-210">Přejděte do úlohy a výběrem **Upravit** Nakonfigurujte cluster vaší úlohy.</span><span class="sxs-lookup"><span data-stu-id="10b90-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="10b90-211">Nastavte cluster na **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="10b90-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="10b90-212">Pak vyberte **Upřesnit možnosti**  >  **skripty init**.</span><span class="sxs-lookup"><span data-stu-id="10b90-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="10b90-213">Nastavte cestu skriptu init jako `dbfs:/spark-dotnet/db-init.sh` .</span><span class="sxs-lookup"><span data-stu-id="10b90-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Konfigurace clusteru Spark v Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="10b90-215">Vyberte **Potvrdit** a potvrďte nastavení clusteru.</span><span class="sxs-lookup"><span data-stu-id="10b90-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="10b90-216">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="10b90-216">Run your app</span></span>

1. <span data-ttu-id="10b90-217">Přejděte do úlohy a výběrem **Spustit nyní** spusťte úlohu na nově nakonfigurovaném clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="10b90-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="10b90-218">Vytvoření clusteru úlohy trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="10b90-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="10b90-219">Po vytvoření bude vaše úloha odeslána a můžete zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="10b90-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="10b90-220">V nabídce vlevo vyberte **clustery** a potom název a spuštění úlohy.</span><span class="sxs-lookup"><span data-stu-id="10b90-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="10b90-221">Vyberte **protokoly ovladačů** a zobrazte výstup vaší úlohy.</span><span class="sxs-lookup"><span data-stu-id="10b90-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="10b90-222">Až se vaše aplikace dokončí, zobrazí se stejná tabulka počtu slov z místního spouštěného příkazu Začínáme do standardní výstupní konzoly.</span><span class="sxs-lookup"><span data-stu-id="10b90-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Výstupní tabulka úlohy Azure Databricks](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="10b90-224">Gratulujeme, spustili jste první rozhraní .NET pro Apache Spark aplikaci v cloudu!</span><span class="sxs-lookup"><span data-stu-id="10b90-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="10b90-225">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="10b90-225">Clean up resources</span></span>

<span data-ttu-id="10b90-226">Pokud už nepotřebujete pracovní prostor datacihly, můžete prostředek Azure Databricks odstranit v Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="10b90-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="10b90-227">Můžete také výběrem názvu skupiny prostředků otevřít stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**.</span><span class="sxs-lookup"><span data-stu-id="10b90-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="10b90-228">Další kroky</span><span class="sxs-lookup"><span data-stu-id="10b90-228">Next steps</span></span>

<span data-ttu-id="10b90-229">V tomto kurzu jste nasadili rozhraní .NET pro Apache Spark aplikaci na datacihly.</span><span class="sxs-lookup"><span data-stu-id="10b90-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="10b90-230">Pokud se chcete dozvědět víc o datacihlách, přejděte k dokumentaci Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="10b90-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10b90-231">Dokumentace k Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="10b90-231">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
