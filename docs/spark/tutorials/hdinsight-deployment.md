---
title: Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight
description: Zjistěte, jak nasadit .NET pro aplikaci Apache Spark do HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504165"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="b5c5f-103">Kurz: Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="b5c5f-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="b5c5f-104">Tento kurz vás naučí, jak nasadit vaši .NET pro aplikaci Apache Spark do cloudu prostřednictvím clusteru Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="b5c5f-105">HDInsight usnadňuje vytváření a konfiguraci clusteru Spark v Azure, protože clustery Spark ve HDInsightu jsou kompatibilní s Azure Storage a Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="b5c5f-106">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="b5c5f-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="b5c5f-107">Přístup k účtům úložiště pomocí Azure Storage Explorer.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="b5c5f-108">Vytvořte cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="b5c5f-109">Publikujte svou aplikaci .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="b5c5f-110">Vytvořte a spusťte akci skriptu HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="b5c5f-111">Spusťte aplikaci .NET pro Apache Spark v clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5c5f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5c5f-112">Prerequisites</span></span>

<span data-ttu-id="b5c5f-113">Než začnete, proveďte následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="b5c5f-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="b5c5f-114">Pokud nemáte předplatné Azure, vytvořte si [bezplatný účet](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="b5c5f-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="b5c5f-115">Přihlaste se k [portálu Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="b5c5f-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="b5c5f-116">Nainstalujte Azure Storage Explorer do počítače [s Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linuxem](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)nebo [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="b5c5f-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="b5c5f-117">Dokončete [rozhraní .NET pro Apache Spark – začínáme v kurzu 10 minut.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)</span><span class="sxs-lookup"><span data-stu-id="b5c5f-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="b5c5f-118">Přístup k účtům úložiště</span><span class="sxs-lookup"><span data-stu-id="b5c5f-118">Access your storage accounts</span></span>

1. <span data-ttu-id="b5c5f-119">Otevřete Průzkumníka úložišť Azure.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="b5c5f-120">V levé nabídce vyberte **Přidat účet** a přihlaste se ke svému účtu Azure.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Přihlášení k účtu Azure z Průzkumníka úložiště](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="b5c5f-122">Po přihlášení byste měli vidět všechny účty úložiště, které máte, a všechny prostředky, které jste nahráli do svých účtů úložiště.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="b5c5f-123">Vytvoření clusteru HDInsight</span><span class="sxs-lookup"><span data-stu-id="b5c5f-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5c5f-124">Fakturace pro clustery HDInsight se poměrně účtuje za minutu, i když je nepoužíváte.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="b5c5f-125">Až přestanete cluster používat, nezapomeňte ho odstranit.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="b5c5f-126">Další informace naleznete v části [Vyčištění prostředků](#clean-up-resources) v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="b5c5f-127">Navštivte [portál Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b5c5f-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="b5c5f-128">Vyberte **+ Vytvořit prostředek**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="b5c5f-129">Potom vyberte **HDInsight** z kategorie **Analytics.**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Vytvoření prostředků HDInsight z webu Azure Portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="b5c5f-131">V části **Základy** zadejte tyto hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b5c5f-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="b5c5f-132">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5c5f-132">Property</span></span>  |<span data-ttu-id="b5c5f-133">Popis</span><span class="sxs-lookup"><span data-stu-id="b5c5f-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="b5c5f-134">Předplatné</span><span class="sxs-lookup"><span data-stu-id="b5c5f-134">Subscription</span></span>  | <span data-ttu-id="b5c5f-135">V rozevíracím programu vyberte jedno z aktivních předplatných Azure.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="b5c5f-136">Skupina prostředků</span><span class="sxs-lookup"><span data-stu-id="b5c5f-136">Resource group</span></span> | <span data-ttu-id="b5c5f-137">Určete, jestli chcete vytvořit novou skupinu prostředků, nebo použít existující.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="b5c5f-138">Skupina prostředků je kontejner, který obsahuje související prostředky pro řešení Azure.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="b5c5f-139">Název clusteru</span><span class="sxs-lookup"><span data-stu-id="b5c5f-139">Cluster name</span></span> | <span data-ttu-id="b5c5f-140">Pojmenujte svůj cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="b5c5f-141">Umístění</span><span class="sxs-lookup"><span data-stu-id="b5c5f-141">Location</span></span>   | <span data-ttu-id="b5c5f-142">Vyberte umístění skupiny prostředků.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-142">Select a location for the resource group.</span></span> <span data-ttu-id="b5c5f-143">Šablona toto umístění používá k vytvoření clusteru i jako výchozí úložiště clusteru.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="b5c5f-144">Typ clusteru</span><span class="sxs-lookup"><span data-stu-id="b5c5f-144">Cluster type</span></span>| <span data-ttu-id="b5c5f-145">Jako typ clusteru vyberte **Spark.**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="b5c5f-146">Verze clusteru</span><span class="sxs-lookup"><span data-stu-id="b5c5f-146">Cluster version</span></span>|<span data-ttu-id="b5c5f-147">Toto pole se automaticky naplní výchozí verzí, jakmile bude vybrán typ clusteru.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="b5c5f-148">Vyberte verzi Spark 2.3 nebo 2.4.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="b5c5f-149">Uživatelské jméno přihlášení clusteru</span><span class="sxs-lookup"><span data-stu-id="b5c5f-149">Cluster login username</span></span>| <span data-ttu-id="b5c5f-150">Zadejte uživatelské jméno přihlášení clusteru.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-150">Enter the cluster login username.</span></span>  <span data-ttu-id="b5c5f-151">Výchozí uživatelské jméno je *admin*.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="b5c5f-152">Heslo přihlášení clusteru</span><span class="sxs-lookup"><span data-stu-id="b5c5f-152">Cluster login password</span></span>| <span data-ttu-id="b5c5f-153">Zadejte libovolné přihlašovací heslo.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-153">Enter any login password.</span></span> |
    |<span data-ttu-id="b5c5f-154">Uživatelské jméno Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="b5c5f-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="b5c5f-155">Zadejte uživatelské jméno SSH.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-155">Enter the SSH username.</span></span> <span data-ttu-id="b5c5f-156">Ve výchozím nastavení má tento účet stejné heslo jako účet *Uživatelské jméno přihlášení clusteru*.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="b5c5f-157">Vyberte **Další: Úložiště >>** a pokračujte na stránku **Úložiště.**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="b5c5f-158">V části **Úložiště** zadejte tyto hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b5c5f-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="b5c5f-159">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5c5f-159">Property</span></span>  |<span data-ttu-id="b5c5f-160">Popis</span><span class="sxs-lookup"><span data-stu-id="b5c5f-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="b5c5f-161">Typ primárního úložiště</span><span class="sxs-lookup"><span data-stu-id="b5c5f-161">Primary storage type</span></span>|<span data-ttu-id="b5c5f-162">Použijte výchozí hodnotu **Azure Storage**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="b5c5f-163">Metoda výběru</span><span class="sxs-lookup"><span data-stu-id="b5c5f-163">Selection method</span></span>|<span data-ttu-id="b5c5f-164">Použijte výchozí hodnotu **Vybrat ze seznamu**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="b5c5f-165">Účet primárního úložiště</span><span class="sxs-lookup"><span data-stu-id="b5c5f-165">Primary storage account</span></span>|<span data-ttu-id="b5c5f-166">Vyberte si předplatné a jeden z vašich aktivních účtů úložiště v rámci tohoto předplatného.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="b5c5f-167">Kontejner</span><span class="sxs-lookup"><span data-stu-id="b5c5f-167">Container</span></span>|<span data-ttu-id="b5c5f-168">Tento kontejner je konkrétní kontejner objektů blob v účtu úložiště, kde váš cluster hledá soubory pro spuštění aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="b5c5f-169">Můžete mu dát libovolné dostupné jméno.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="b5c5f-170">V části **Revize + vytvoření**vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="b5c5f-171">Vytvoření clusteru trvá přibližně 20 minut.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="b5c5f-172">Před pokračováním k dalšímu kroku je nutné vytvořit cluster.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="b5c5f-173">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="b5c5f-173">Publish your app</span></span>

<span data-ttu-id="b5c5f-174">Dále publikujete *mySparkApp* vytvořený v [rozhraní .NET pro Apache Spark – Začínáme v kurzu 10 minut,](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) který vašemu clusteru Spark poskytuje přístup ke všem souborům, které potřebuje ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="b5c5f-175">Chcete-li publikovat *mySparkApp,* spusťte následující příkazy :</span><span class="sxs-lookup"><span data-stu-id="b5c5f-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="b5c5f-176">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="b5c5f-177">**Na Linuxu:**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="b5c5f-178">Chcete-li publikované soubory aplikací rozbalit, proveďte následující úkoly, abyste je mohli snadno nahrát do clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="b5c5f-179">**Ve Windows:**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-179">**On Windows:**</span></span>

   <span data-ttu-id="b5c5f-180">Přejděte na *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="b5c5f-181">Potom klikněte pravým tlačítkem myši na složku **Publikovat** a vyberte **příkaz Odeslat do > komprimovované (zip) složky**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="b5c5f-182">Pojmenujte novou složku **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="b5c5f-183">**Na Linuxu spusťte následující příkaz:**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="b5c5f-184">Nahrání souborů do Azure</span><span class="sxs-lookup"><span data-stu-id="b5c5f-184">Upload files to Azure</span></span>

<span data-ttu-id="b5c5f-185">Dále použijete Průzkumníka úložiště Azure k nahrání následujících pěti souborů do kontejneru objektů blob, který jste zvolili pro úložiště clusteru:</span><span class="sxs-lookup"><span data-stu-id="b5c5f-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="b5c5f-186">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="b5c5f-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="b5c5f-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="b5c5f-187">install-worker.sh</span></span>
* <span data-ttu-id="b5c5f-188">publikovat.zip</span><span class="sxs-lookup"><span data-stu-id="b5c5f-188">publish.zip</span></span>
* <span data-ttu-id="b5c5f-189">Microsoft-spark-2.3.x-0.3.0.jar</span><span class="sxs-lookup"><span data-stu-id="b5c5f-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="b5c5f-190">input.txt.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-190">input.txt.</span></span>

1. <span data-ttu-id="b5c5f-191">Otevřete Azure Storage Explorer a přejděte na svůj účet úložiště z levé nabídky.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="b5c5f-192">Přejděte k kontejneru objektů blob pro váš cluster v části **kontejnery objektů blob** ve vašem účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="b5c5f-193">*Microsoft.Spark.Worker* pomáhá Apache Spark spouštět vaši aplikaci, jako jsou všechny uživatelem definované funkce (UDFs), které jste napsali.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="b5c5f-194">Stáhnout [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="b5c5f-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="b5c5f-195">Pak vyberte **Nahrát** v Průzkumníku úložiště Azure a nahrajte pracovníka.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Nahrání souborů do Průzkumníka úložiště Azure](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="b5c5f-197">*install-worker.sh* je skript, který umožňuje kopírovat .NET pro apache spark závislé soubory do uzlů clusteru.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="b5c5f-198">Vytvořte nový soubor s názvem **install-worker.sh** místním počítači a vložte [obsah install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) umístěný na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="b5c5f-199">Potom nahrajte *install-worker.sh* do kontejneru objektů blob.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="b5c5f-200">Cluster potřebuje soubor publish.zip, který obsahuje publikované soubory vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="b5c5f-201">Přejděte do publikované složky **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**a vyhledejte **soubor publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="b5c5f-202">Pak nahrajte *publish.zip* do kontejneru objektů blob.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="b5c5f-203">Cluster potřebuje kód aplikace, který byl zabalen do souboru jar.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="b5c5f-204">Přejděte do publikované složky **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**a vyhledejte **microsoft-spark-2.3.x-0.3.0.jar**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="b5c5f-205">Potom nahrajte soubor jar do kontejneru objektů blob.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="b5c5f-206">Může existovat více souborů .jar (pro verze 2.3.x a 2.4.x Spark).</span><span class="sxs-lookup"><span data-stu-id="b5c5f-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="b5c5f-207">Musíte zvolit soubor .jar, který odpovídá verzi Spark, kterou jste zvolili při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="b5c5f-208">Pokud jste například při vytváření clusteru zvolili Spark 2.3.0.3.0.jar, zvolte například *microsoft-spark-2.3.x-0.3.0.jar.*</span><span class="sxs-lookup"><span data-stu-id="b5c5f-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="b5c5f-209">Váš cluster potřebuje vstup do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="b5c5f-210">Přejděte do adresáře **mySparkApp** a vyhledejte **soubor input.txt**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="b5c5f-211">Nahrajte vstupní soubor do **adresáře uživatele/sshuseru** v kontejneru objektů blob.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="b5c5f-212">Budete se připojovat ke clusteru prostřednictvím ssh a tato složka je místo, kde váš cluster hledá svůj vstup.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="b5c5f-213">Soubor *input.txt* je jediný soubor odeslaný do určitého adresáře.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="b5c5f-214">Spuštění akce skriptu HDInsight</span><span class="sxs-lookup"><span data-stu-id="b5c5f-214">Run the HDInsight script action</span></span>

<span data-ttu-id="b5c5f-215">Jakmile váš cluster běží a nahrajete soubory do Azure, spustíte **install-worker.sh** skript v clusteru.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="b5c5f-216">Přejděte do clusteru HDInsight Spark na webu Azure Portal a pak vyberte **Akce skriptu**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="b5c5f-217">Vyberte **+ Odeslat nové** a zadejte následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b5c5f-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="b5c5f-218">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b5c5f-218">Property</span></span>  |<span data-ttu-id="b5c5f-219">Popis</span><span class="sxs-lookup"><span data-stu-id="b5c5f-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="b5c5f-220">Typ skriptu</span><span class="sxs-lookup"><span data-stu-id="b5c5f-220">Script type</span></span> |<span data-ttu-id="b5c5f-221">Vlastní</span><span class="sxs-lookup"><span data-stu-id="b5c5f-221">Custom</span></span>|
   | <span data-ttu-id="b5c5f-222">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="b5c5f-222">Name</span></span> | <span data-ttu-id="b5c5f-223">Instalace pracovníka</span><span class="sxs-lookup"><span data-stu-id="b5c5f-223">Install Worker</span></span>|
   | <span data-ttu-id="b5c5f-224">Bash skript URI</span><span class="sxs-lookup"><span data-stu-id="b5c5f-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="b5c5f-225">Chcete-li tento identifikátor URI potvrdit, klikněte pravým tlačítkem myši na install-worker.sh v Průzkumníku úložiště Azure a vyberte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="b5c5f-226">Typ uzlu</span><span class="sxs-lookup"><span data-stu-id="b5c5f-226">Node type(s)</span></span>| <span data-ttu-id="b5c5f-227">Pracovník</span><span class="sxs-lookup"><span data-stu-id="b5c5f-227">Worker</span></span>|
   | <span data-ttu-id="b5c5f-228">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5c5f-228">Parameters</span></span> | <span data-ttu-id="b5c5f-229">azure</span><span class="sxs-lookup"><span data-stu-id="b5c5f-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="b5c5f-230">/usr/místní/přihrádka</span><span class="sxs-lookup"><span data-stu-id="b5c5f-230">/usr/local/bin</span></span>

3. <span data-ttu-id="b5c5f-231">Chcete-li skript odeslat, vyberte **vytvořit.**</span><span class="sxs-lookup"><span data-stu-id="b5c5f-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="b5c5f-232">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="b5c5f-232">Run your app</span></span>

1. <span data-ttu-id="b5c5f-233">Přejděte do clusteru HDInsight Spark na webu Azure Portal a pak vyberte **Přihlášení SSH + Cluster**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="b5c5f-234">Zkopírujte přihlašovací údaje ssh a vložte přihlášení do terminálu.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="b5c5f-235">Přihlaste se ke clusteru pomocí hesla, které nastavíte při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="b5c5f-236">Měli byste vidět zprávy, které vás vítají na Ubuntu a Spark.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="b5c5f-237">Pomocí příkazu **spark-submit** můžete aplikaci spouštět v clusteru HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="b5c5f-238">Nezapomeňte nahradit **mycontainer** a **mystorageaccount** v ukázkovém skriptu skutečnými názvy kontejneru objektů blob a účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="b5c5f-239">Při spuštění aplikace se zobrazí stejná tabulka počtu slov z místního spuštění Začínáme zapsaného do konzoly.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="b5c5f-240">Gratulujeme, jste spustit svůj první .NET pro Apache Spark aplikace v cloudu!</span><span class="sxs-lookup"><span data-stu-id="b5c5f-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="b5c5f-241">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="b5c5f-241">Clean up resources</span></span>

<span data-ttu-id="b5c5f-242">HDInsight ukládá vaše data ve službě Azure Storage, takže můžete bezpečně odstranit cluster, když se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="b5c5f-243">Za cluster služby HDInsight se účtují poplatky, i když se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="b5c5f-244">Vzhledem k tomu, že poplatky za cluster představují několikanásobek poplatků za úložiště, dává ekonomický smysl odstraňovat clustery, které nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="b5c5f-245">Můžete také výběrem názvu skupiny prostředků otevřít stránku skupiny prostředků a pak vybrat **Odstranit skupinu prostředků**.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="b5c5f-246">Odstraněním skupiny prostředků odstraníte cluster HDInsight Spark i výchozí účet úložiště.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5c5f-247">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b5c5f-247">Next steps</span></span>

<span data-ttu-id="b5c5f-248">V tomto kurzu jste nasadili .NET pro aplikaci Apache Spark do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="b5c5f-249">Další informace o HDInsightu najdete v dokumentaci k Azure HDInsightu.</span><span class="sxs-lookup"><span data-stu-id="b5c5f-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5c5f-250">Dokumentace ke službě HDInsight</span><span class="sxs-lookup"><span data-stu-id="b5c5f-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
