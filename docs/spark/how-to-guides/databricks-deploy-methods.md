---
title: Odeslat úlohu .NET pro Apache Spark do Databricks
description: Naučte se, jak odeslat úlohu .NET pro Apache Spark do Databricks pomocí spark-submit a Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187613"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="96816-103">Odeslat úlohu .NET pro Apache Spark do Databricks</span><span class="sxs-lookup"><span data-stu-id="96816-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="96816-104">Existují dva způsoby nasazení úlohy .NET pro Apache `spark-submit` Spark do Databricks: a Set Jar.</span><span class="sxs-lookup"><span data-stu-id="96816-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="96816-105">Nasazení pomocí spark-submit</span><span class="sxs-lookup"><span data-stu-id="96816-105">Deploy using spark-submit</span></span>

<span data-ttu-id="96816-106">Příkaz [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete použít k odeslání úloh .NET pro Apache Spark do Databricks.</span><span class="sxs-lookup"><span data-stu-id="96816-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="96816-107">`spark-submit`umožňuje odesílání pouze do clusteru, který získá vytvořené na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="96816-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="96816-108">Přejděte do pracovního prostoru Databricks a vytvořte úlohu.</span><span class="sxs-lookup"><span data-stu-id="96816-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="96816-109">Vyberte název úlohy a pak vyberte **Konfigurovat spark-submit**.</span><span class="sxs-lookup"><span data-stu-id="96816-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="96816-110">Vložte do konfigurace úlohy následující parametry a vyberte **potvrdit**.</span><span class="sxs-lookup"><span data-stu-id="96816-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="96816-111">Aktualizujte obsah výše uvedeného parametru na základě vašich konkrétních souborů a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="96816-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="96816-112">Například odkazovat na verzi microsoft.spark jar soubor, který jste nahráli do DBFS a použijte příslušný název aplikace a publikované aplikace zip soubor.</span><span class="sxs-lookup"><span data-stu-id="96816-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="96816-113">Přejděte do úlohy a vyberte **Upravit** a nakonfigurujte cluster své úlohy.</span><span class="sxs-lookup"><span data-stu-id="96816-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="96816-114">Nastavte datovou verzi runtime na základě verze Apache Spark, kterou chcete použít ve svém nasazení.</span><span class="sxs-lookup"><span data-stu-id="96816-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="96816-115">Pak vyberte **Upřesnit možnosti > init skripty**a nastavte Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="96816-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="96816-116">Chcete-li potvrdit nastavení clusteru, vyberte potvrdit možnost **Potvrdit.**</span><span class="sxs-lookup"><span data-stu-id="96816-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="96816-117">Přejděte ke své úloze a vyberte **Spustit nyní,** chcete-li spustit úlohu v nově nakonfigurovaném clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="96816-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="96816-118">Vytvoření clusteru úlohy trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="96816-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="96816-119">Jakmile je vytvořen, vaše práce bude odeslána.</span><span class="sxs-lookup"><span data-stu-id="96816-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="96816-120">Výstup můžete zobrazit výběrem **clusterů** z levé nabídky pracovního prostoru Databricks a vyberte **položku Protokoly ovladačů**.</span><span class="sxs-lookup"><span data-stu-id="96816-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="96816-121">Nasazení pomocí sady jar</span><span class="sxs-lookup"><span data-stu-id="96816-121">Deploy using Set Jar</span></span>

<span data-ttu-id="96816-122">Případně můžete použít [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) v pracovním prostoru Databricks k odeslání .NET pro úlohy Apache Spark databricks.</span><span class="sxs-lookup"><span data-stu-id="96816-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="96816-123">*Set Jar* umožňuje odeslání úlohy do existujícího aktivního clusteru.</span><span class="sxs-lookup"><span data-stu-id="96816-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="96816-124">Jednorázové nastavení</span><span class="sxs-lookup"><span data-stu-id="96816-124">One-time setup</span></span>

1. <span data-ttu-id="96816-125">Přejděte do clusteru Databricks a v yberte **Úlohy** z nabídky na levé straně, následované **sadou JAR**.</span><span class="sxs-lookup"><span data-stu-id="96816-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="96816-126">Nahrajte `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`příslušnou .</span><span class="sxs-lookup"><span data-stu-id="96816-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="96816-127">Upravte následující parametry tak, aby obsahovaly správný název spustitelného souboru, který jste publikovali místo `<your-app-name>`:</span><span class="sxs-lookup"><span data-stu-id="96816-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="96816-128">Nakonfigurujte cluster tak, aby ukazoval na existující cluster, pro který jste již nastavili skript init.</span><span class="sxs-lookup"><span data-stu-id="96816-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="96816-129">Publikování a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="96816-129">Publish and run your app</span></span>

1. <span data-ttu-id="96816-130">Ujistěte se, že jste aplikaci publikovali `SparkSession.Stop()`a že kód aplikace nepoužívá .</span><span class="sxs-lookup"><span data-stu-id="96816-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="96816-131">Pomocí zapisování se k odeslání aplikace do clusteru Databricks použijte [zapisovatelská](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) nastavení datových cli datových zoadů.</span><span class="sxs-lookup"><span data-stu-id="96816-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="96816-132">K nahrání publikované aplikace do clusteru například nahrajte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="96816-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="96816-133">Pokud máte ve vaší aplikaci nějaké uživatelem definované funkce, je třeba do pracovního adresáře každého *Microsoft.Spark.Worker*umístit sestavení aplikací, například knihovny DLL, které obsahují uživatelem definované funkce spolu s jejich závislostmi.</span><span class="sxs-lookup"><span data-stu-id="96816-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="96816-134">Nahrajte sestavení aplikací do clusteru Databricks:</span><span class="sxs-lookup"><span data-stu-id="96816-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="96816-135">Odkomentujte a upravte oddíl závislostí aplikací v [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) tak, aby ukazoval na cestu závislosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="96816-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="96816-136">Potom nahrajte aktualizovanou *db-init.sh* do clusteru:</span><span class="sxs-lookup"><span data-stu-id="96816-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="96816-137">Přejděte do **clusteru Databricks > úlohy > [Job-name] > Spustit nyní** spustit úlohu.</span><span class="sxs-lookup"><span data-stu-id="96816-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="96816-138">Další kroky</span><span class="sxs-lookup"><span data-stu-id="96816-138">Next steps</span></span>

* [<span data-ttu-id="96816-139">Začínáme s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="96816-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="96816-140">Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks</span><span class="sxs-lookup"><span data-stu-id="96816-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="96816-141">Dokumentace k Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="96816-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
