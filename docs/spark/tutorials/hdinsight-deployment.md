---
title: Nasazení aplikace .NET pro Apache Spark do Azure HDInsight
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3604aff5d1f138071c941ea85546af03185d722d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460716"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="c36f1-103">Kurz: nasazení aplikace .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="c36f1-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="c36f1-104">V tomto kurzu se naučíte, jak nasadit aplikaci .NET pro Apache Spark do cloudu prostřednictvím clusteru Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="c36f1-105">HDInsight usnadňuje vytvoření a konfiguraci clusteru Spark v Azure, protože Clustery Spark v HDInsight jsou kompatibilní s Azure Storage a Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="c36f1-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="c36f1-106">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="c36f1-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="c36f1-107">Přístup k účtům úložiště pomocí Průzkumník služby Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="c36f1-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="c36f1-108">Vytvořte cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="c36f1-109">Publikování aplikace .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="c36f1-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="c36f1-110">Vytvořte a spusťte akci skriptu HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="c36f1-111">Spusťte rozhraní .NET pro Apache Spark aplikaci v clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c36f1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c36f1-112">Prerequisites</span></span>

<span data-ttu-id="c36f1-113">Než začnete, proveďte následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c36f1-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="c36f1-114">Pokud nemáte předplatné Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="c36f1-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="c36f1-115">Přihlaste se k [Azure Portal](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="c36f1-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="c36f1-116">Nainstalujte Průzkumník služby Azure Storage na počítač se [systémem Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)nebo [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .</span><span class="sxs-lookup"><span data-stu-id="c36f1-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="c36f1-117">Dokončete kurz [k rozhraní .NET pro Apache Spark – Začínáme během 10 minut](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="c36f1-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="c36f1-118">Přístup k účtům úložiště</span><span class="sxs-lookup"><span data-stu-id="c36f1-118">Access your storage accounts</span></span>

1. <span data-ttu-id="c36f1-119">Otevřete Průzkumník služby Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="c36f1-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="c36f1-120">V nabídce vlevo vyberte **Přidat účet** a přihlaste se ke svému účtu Azure.</span><span class="sxs-lookup"><span data-stu-id="c36f1-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Přihlaste se k účtu Azure z Průzkumník služby Storage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="c36f1-122">Po přihlášení byste měli vidět všechny účty úložiště, které máte, a všechny prostředky, které jste nahráli do účtů úložiště.</span><span class="sxs-lookup"><span data-stu-id="c36f1-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="c36f1-123">Vytvoření clusteru HDInsight</span><span class="sxs-lookup"><span data-stu-id="c36f1-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c36f1-124">Fakturace za clustery HDInsight se účtuje poměrně po minutách, a to i v případě, že je nepoužíváte.</span><span class="sxs-lookup"><span data-stu-id="c36f1-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="c36f1-125">Po dokončení používání clusteru nezapomeňte tento cluster odstranit.</span><span class="sxs-lookup"><span data-stu-id="c36f1-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="c36f1-126">Další informace najdete v části [vyčištění prostředků](#clean-up-resources) v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="c36f1-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="c36f1-127">Navštivte [Azure Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c36f1-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="c36f1-128">Vyberte **+ vytvořit prostředek**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="c36f1-129">Pak z kategorie **Analytics** vyberte **HDInsight** .</span><span class="sxs-lookup"><span data-stu-id="c36f1-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Vytvořit prostředek HDInsight z Azure Portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="c36f1-131">V části **základy**zadejte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c36f1-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="c36f1-132">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c36f1-132">Property</span></span>  |<span data-ttu-id="c36f1-133">Popis</span><span class="sxs-lookup"><span data-stu-id="c36f1-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="c36f1-134">Formě</span><span class="sxs-lookup"><span data-stu-id="c36f1-134">Subscription</span></span>  | <span data-ttu-id="c36f1-135">V rozevíracím seznamu vyberte jedno z aktivních předplatných Azure.</span><span class="sxs-lookup"><span data-stu-id="c36f1-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="c36f1-136">Skupina prostředků</span><span class="sxs-lookup"><span data-stu-id="c36f1-136">Resource group</span></span> | <span data-ttu-id="c36f1-137">Určete, zda chcete vytvořit novou skupinu prostředků, nebo použít existující.</span><span class="sxs-lookup"><span data-stu-id="c36f1-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="c36f1-138">Skupina prostředků je kontejner, který obsahuje související prostředky pro řešení Azure.</span><span class="sxs-lookup"><span data-stu-id="c36f1-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="c36f1-139">Název clusteru</span><span class="sxs-lookup"><span data-stu-id="c36f1-139">Cluster name</span></span> | <span data-ttu-id="c36f1-140">Zadejte název clusteru HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="c36f1-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="c36f1-141">Umístění</span><span class="sxs-lookup"><span data-stu-id="c36f1-141">Location</span></span>   | <span data-ttu-id="c36f1-142">Vyberte umístění pro skupinu prostředků.</span><span class="sxs-lookup"><span data-stu-id="c36f1-142">Select a location for the resource group.</span></span> <span data-ttu-id="c36f1-143">Šablona používá toto umístění pro vytvoření clusteru i pro výchozí úložiště clusteru.</span><span class="sxs-lookup"><span data-stu-id="c36f1-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="c36f1-144">Typ clusteru</span><span class="sxs-lookup"><span data-stu-id="c36f1-144">Cluster type</span></span>| <span data-ttu-id="c36f1-145">Jako typ clusteru vyberte **Spark** .</span><span class="sxs-lookup"><span data-stu-id="c36f1-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="c36f1-146">Verze clusteru</span><span class="sxs-lookup"><span data-stu-id="c36f1-146">Cluster version</span></span>|<span data-ttu-id="c36f1-147">Po výběru typu clusteru bude toto pole automaticky vyplněno výchozí verzí.</span><span class="sxs-lookup"><span data-stu-id="c36f1-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="c36f1-148">Vyberte verzi Sparku 2,3 nebo 2,4.</span><span class="sxs-lookup"><span data-stu-id="c36f1-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="c36f1-149">Uživatelské jméno přihlášení clusteru</span><span class="sxs-lookup"><span data-stu-id="c36f1-149">Cluster login username</span></span>| <span data-ttu-id="c36f1-150">Zadejte uživatelské jméno pro přihlášení ke clusteru.</span><span class="sxs-lookup"><span data-stu-id="c36f1-150">Enter the cluster login username.</span></span>  <span data-ttu-id="c36f1-151">Výchozí název je *admin*.</span><span class="sxs-lookup"><span data-stu-id="c36f1-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="c36f1-152">Heslo pro přihlášení ke clusteru</span><span class="sxs-lookup"><span data-stu-id="c36f1-152">Cluster login password</span></span>| <span data-ttu-id="c36f1-153">Zadejte libovolné přihlašovací heslo.</span><span class="sxs-lookup"><span data-stu-id="c36f1-153">Enter any login password.</span></span> |
    |<span data-ttu-id="c36f1-154">Uživatelské jméno Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="c36f1-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="c36f1-155">Zadejte uživatelské jméno SSH.</span><span class="sxs-lookup"><span data-stu-id="c36f1-155">Enter the SSH username.</span></span> <span data-ttu-id="c36f1-156">Ve výchozím nastavení tento účet sdílí stejné heslo jako účet *přihlášení ke clusteru* .</span><span class="sxs-lookup"><span data-stu-id="c36f1-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="c36f1-157">Kliknutím na tlačítko **Další: úložiště > >** pokračujte na stránku **úložiště** .</span><span class="sxs-lookup"><span data-stu-id="c36f1-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="c36f1-158">V části **Storage (úložiště**) zadejte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c36f1-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="c36f1-159">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c36f1-159">Property</span></span>  |<span data-ttu-id="c36f1-160">Popis</span><span class="sxs-lookup"><span data-stu-id="c36f1-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="c36f1-161">Typ primárního úložiště</span><span class="sxs-lookup"><span data-stu-id="c36f1-161">Primary storage type</span></span>|<span data-ttu-id="c36f1-162">Použijte výchozí hodnotu **Azure Storage**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="c36f1-163">Metoda výběru</span><span class="sxs-lookup"><span data-stu-id="c36f1-163">Selection method</span></span>|<span data-ttu-id="c36f1-164">Použijte výchozí hodnotu **vybrat ze seznamu**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="c36f1-165">Primární účet úložiště</span><span class="sxs-lookup"><span data-stu-id="c36f1-165">Primary storage account</span></span>|<span data-ttu-id="c36f1-166">Vyberte své předplatné a jeden z aktivních účtů úložiště v rámci tohoto předplatného.</span><span class="sxs-lookup"><span data-stu-id="c36f1-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="c36f1-167">vnitřního</span><span class="sxs-lookup"><span data-stu-id="c36f1-167">Container</span></span>|<span data-ttu-id="c36f1-168">Tento kontejner je specifickým kontejnerem objektů BLOB ve vašem účtu úložiště, ve kterém váš cluster hledá soubory ke spuštění vaší aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="c36f1-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="c36f1-169">Můžete mu dát libovolný dostupný název.</span><span class="sxs-lookup"><span data-stu-id="c36f1-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="c36f1-170">V nabídce **Revize + vytvořit**vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="c36f1-171">Vytvoření clusteru trvá přibližně 20 minut.</span><span class="sxs-lookup"><span data-stu-id="c36f1-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="c36f1-172">Aby bylo možné pokračovat k dalšímu kroku, musí být cluster vytvořen.</span><span class="sxs-lookup"><span data-stu-id="c36f1-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="c36f1-173">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="c36f1-173">Publish your app</span></span>

<span data-ttu-id="c36f1-174">V dalším kroku publikujete *mySparkApp* vytvořenou v [rozhraní .NET pro Apache Spark – Začínáme během 10 minut](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , což vašemu clusteru Spark poskytne přístup ke všem souborům, které potřebuje ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c36f1-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="c36f1-175">Pro publikování *mySparkApp*spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="c36f1-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="c36f1-176">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="c36f1-176">**On Windows:**</span></span>

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="c36f1-177">**V systému Linux:**</span><span class="sxs-lookup"><span data-stu-id="c36f1-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="c36f1-178">Proveďte následující úlohy pro zip publikovaných souborů aplikace, abyste je mohli snadno nahrát do clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="c36f1-179">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="c36f1-179">**On Windows:**</span></span>

   <span data-ttu-id="c36f1-180">Přejděte na *mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="c36f1-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="c36f1-181">Potom klikněte pravým tlačítkem na složku pro **publikování** a vyberte **Odeslat do > Komprimovaná složka (ZIP)** .</span><span class="sxs-lookup"><span data-stu-id="c36f1-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="c36f1-182">Pojmenujte novou složku **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="c36f1-183">**V systému Linux spusťte následující příkaz:**</span><span class="sxs-lookup"><span data-stu-id="c36f1-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="c36f1-184">Nahrání souborů do Azure</span><span class="sxs-lookup"><span data-stu-id="c36f1-184">Upload files to Azure</span></span>

<span data-ttu-id="c36f1-185">Dále pomocí Průzkumník služby Azure Storage nahrajte do kontejneru objektů blob, který jste zvolili pro úložiště clusteru, následující pět souborů:</span><span class="sxs-lookup"><span data-stu-id="c36f1-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="c36f1-186">Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="c36f1-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="c36f1-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="c36f1-187">install-worker.sh</span></span>
* <span data-ttu-id="c36f1-188">Publish. zip</span><span class="sxs-lookup"><span data-stu-id="c36f1-188">publish.zip</span></span>
* <span data-ttu-id="c36f1-189">Microsoft-Spark-2.3. x-0.3.0. jar</span><span class="sxs-lookup"><span data-stu-id="c36f1-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="c36f1-190">Input. txt.</span><span class="sxs-lookup"><span data-stu-id="c36f1-190">input.txt.</span></span>

1. <span data-ttu-id="c36f1-191">Otevřete Průzkumník služby Azure Storage a v nabídce vlevo přejděte k účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="c36f1-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="c36f1-192">V části **kontejnery objektů BLOB** v účtu úložiště přejděte k podrobnostem o kontejneru objektů BLOB pro váš cluster.</span><span class="sxs-lookup"><span data-stu-id="c36f1-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="c36f1-193">*Microsoft. spark. Worker* pomáhá Apache Spark spustit vaši aplikaci, jako jsou například všechny uživatelsky definované funkce (UDF), které jste mohli napsat.</span><span class="sxs-lookup"><span data-stu-id="c36f1-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="c36f1-194">Stáhněte si [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="c36f1-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="c36f1-195">Pak vyberte **odeslat** Průzkumník služby Azure Storage a odešlete pracovní proces.</span><span class="sxs-lookup"><span data-stu-id="c36f1-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Nahrání souborů do Průzkumník služby Azure Storage](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="c36f1-197">*Install-Worker.sh* je skript, který umožňuje zkopírovat rozhraní .net pro Apache Spark závislé soubory do uzlů clusteru.</span><span class="sxs-lookup"><span data-stu-id="c36f1-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="c36f1-198">Vytvořte nový soubor s názvem **install-Worker.sh** v místním počítači a vložte [obsah Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c36f1-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="c36f1-199">Pak nahrajte *install-Worker.sh* do kontejneru objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="c36f1-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="c36f1-200">Váš cluster potřebuje soubor Publish. zip, který obsahuje publikované soubory vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c36f1-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="c36f1-201">Přejděte do složky Publikováno, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**a vyhledejte soubor **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="c36f1-202">Pak odešlete soubor *Publish. zip* do kontejneru objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="c36f1-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="c36f1-203">Váš cluster potřebuje kód aplikace, který byl zabalen do souboru jar.</span><span class="sxs-lookup"><span data-stu-id="c36f1-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="c36f1-204">Přejděte do složky Publikováno, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**a vyhledejte **Microsoft-Spark-2.3. x-0.3.0. jar**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="c36f1-205">Pak nahrajte soubor JAR do kontejneru objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="c36f1-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="c36f1-206">Může existovat více souborů. jar (pro verze 2.3. x a 2.4. x ze Sparku).</span><span class="sxs-lookup"><span data-stu-id="c36f1-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="c36f1-207">Musíte vybrat soubor. jar, který odpovídá verzi Sparku, kterou jste zvolili při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="c36f1-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="c36f1-208">Zvolte například *Microsoft-Spark-2.3. x-0.3.0. jar* , pokud při vytváření clusteru vyberete možnost Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="c36f1-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="c36f1-209">Váš cluster potřebuje vstup do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c36f1-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="c36f1-210">Přejděte do adresáře **mySparkApp** a najděte **input. txt**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="c36f1-211">Nahrajte vstupní soubor do adresáře **uživatelů nebo sshuser** v kontejneru objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="c36f1-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="c36f1-212">K vašemu clusteru se připojíte přes SSH a tato složka je tam, kde váš cluster hledá svůj vstup.</span><span class="sxs-lookup"><span data-stu-id="c36f1-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="c36f1-213">*Vstupní soubor. txt* je jediný soubor nahraný do konkrétního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c36f1-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="c36f1-214">Spusťte akci skriptu HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-214">Run the HDInsight script action</span></span>

<span data-ttu-id="c36f1-215">Po spuštění clusteru a nahrání souborů do Azure spustíte skript **install-Worker.sh** v clusteru.</span><span class="sxs-lookup"><span data-stu-id="c36f1-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="c36f1-216">V Azure Portal přejděte do clusteru HDInsight Spark a pak vyberte **akce skriptu**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="c36f1-217">Vyberte **+ Odeslat nové** a zadejte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c36f1-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="c36f1-218">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c36f1-218">Property</span></span>  |<span data-ttu-id="c36f1-219">Popis</span><span class="sxs-lookup"><span data-stu-id="c36f1-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="c36f1-220">Typ skriptu</span><span class="sxs-lookup"><span data-stu-id="c36f1-220">Script type</span></span> |<span data-ttu-id="c36f1-221">Uživatelská</span><span class="sxs-lookup"><span data-stu-id="c36f1-221">Custom</span></span>|
   | <span data-ttu-id="c36f1-222">Name</span><span class="sxs-lookup"><span data-stu-id="c36f1-222">Name</span></span> | <span data-ttu-id="c36f1-223">Instalace pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="c36f1-223">Install Worker</span></span>|
   | <span data-ttu-id="c36f1-224">Identifikátor URI skriptu bash</span><span class="sxs-lookup"><span data-stu-id="c36f1-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="c36f1-225">Pokud chcete tento identifikátor URI potvrdit, klikněte pravým tlačítkem na install-worker.sh v Průzkumník služby Azure Storage a vyberte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c36f1-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="c36f1-226">Typ (typy) uzlů</span><span class="sxs-lookup"><span data-stu-id="c36f1-226">Node type(s)</span></span>| <span data-ttu-id="c36f1-227">Zaměstnanec</span><span class="sxs-lookup"><span data-stu-id="c36f1-227">Worker</span></span>|
   | <span data-ttu-id="c36f1-228">Parametry</span><span class="sxs-lookup"><span data-stu-id="c36f1-228">Parameters</span></span> | <span data-ttu-id="c36f1-229">Azure</span><span class="sxs-lookup"><span data-stu-id="c36f1-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="c36f1-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="c36f1-230">/usr/local/bin</span></span>

3. <span data-ttu-id="c36f1-231">Vyberte **vytvořit** a odešlete skript.</span><span class="sxs-lookup"><span data-stu-id="c36f1-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="c36f1-232">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="c36f1-232">Run your app</span></span>

1. <span data-ttu-id="c36f1-233">Přejděte do clusteru HDInsight Spark v Azure Portal a pak vyberte **ssh + přihlášení ke clusteru**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="c36f1-234">Zkopírujte přihlašovací informace SSH a vložte přihlašovací jméno do terminálu.</span><span class="sxs-lookup"><span data-stu-id="c36f1-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="c36f1-235">Přihlaste se ke svému clusteru pomocí hesla, které jste nastavili při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="c36f1-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="c36f1-236">Měli byste vidět zprávy, které vás přivítá vás a Ubuntu a Spark.</span><span class="sxs-lookup"><span data-stu-id="c36f1-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="c36f1-237">Pomocí příkazu **Spark-Submit** spusťte aplikaci v clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="c36f1-238">Nezapomeňte nahradit **myContainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy vašeho kontejneru objektů BLOB a účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="c36f1-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="c36f1-239">Když je vaše aplikace spuštěná, zobrazí se stejná tabulka počtu slov z místního spuštění Začínáme s konzolou.</span><span class="sxs-lookup"><span data-stu-id="c36f1-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="c36f1-240">Gratulujeme, spustili jste první rozhraní .NET pro Apache Spark aplikaci v cloudu!</span><span class="sxs-lookup"><span data-stu-id="c36f1-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="c36f1-241">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="c36f1-241">Clean up resources</span></span>

<span data-ttu-id="c36f1-242">HDInsight ukládá vaše data v Azure Storage, takže můžete cluster bezpečně odstranit, pokud se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="c36f1-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="c36f1-243">Účtují se vám také poplatky za cluster HDInsight, a to i v případě, že se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="c36f1-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="c36f1-244">Vzhledem k tomu, že se poplatky za cluster mnohokrát účtují rychleji než poplatky za úložiště, má ekonomický smysl odstraňovat clustery, když se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="c36f1-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="c36f1-245">Můžete také vybrat název skupiny prostředků a otevřít tak stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**.</span><span class="sxs-lookup"><span data-stu-id="c36f1-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="c36f1-246">Odstraněním skupiny prostředků odstraníte cluster HDInsight Spark i výchozí účet úložiště.</span><span class="sxs-lookup"><span data-stu-id="c36f1-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c36f1-247">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c36f1-247">Next steps</span></span>

<span data-ttu-id="c36f1-248">V tomto kurzu jste nasadili aplikaci .NET pro Apache Spark do služby Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="c36f1-249">Pokud se chcete dozvědět víc o službě HDInsight, přejděte k dokumentaci k Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c36f1-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c36f1-250">Dokumentace ke službě Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="c36f1-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
