---
title: Odeslání úlohy .NET for Apache Spark do datacihlů
description: Naučte se, jak odeslat úlohu .NET pro Apache Spark do datacihly pomocí Spark – odeslání a nastavení jar.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: bebd170a689d8ae56aa6c55486d70354da2437ea
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617766"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="c5c86-103">Odeslání úlohy .NET for Apache Spark do datacihlů</span><span class="sxs-lookup"><span data-stu-id="c5c86-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="c5c86-104">Můžete spustit rozhraní .NET pro Apache Spark úlohy u clusterů datacihly, ale není dostupné předem.</span><span class="sxs-lookup"><span data-stu-id="c5c86-104">You can run your .NET for Apache Spark jobs on Databricks clusters, but it is not available out-of-the-box.</span></span> <span data-ttu-id="c5c86-105">Existují dva způsoby, jak nasadit rozhraní .NET pro Apache Spark úlohy do datacihly: `spark-submit` a nastavit jar.</span><span class="sxs-lookup"><span data-stu-id="c5c86-105">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="c5c86-106">Nasazení pomocí Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="c5c86-106">Deploy using spark-submit</span></span>

<span data-ttu-id="c5c86-107">K odeslání .NET pro úlohy Apache Spark do datacihly můžete použít příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) .</span><span class="sxs-lookup"><span data-stu-id="c5c86-107">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="c5c86-108">`spark-submit`povolí odeslání pouze do clusteru, který se vytvoří na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="c5c86-108">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="c5c86-109">Přejděte do pracovního prostoru datacihly a vytvořte úlohu.</span><span class="sxs-lookup"><span data-stu-id="c5c86-109">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="c5c86-110">Zvolte název úlohy a pak vyberte **Konfigurovat Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-110">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="c5c86-111">Do konfigurace úlohy vložte následující parametry a pak vyberte **Potvrdit**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-111">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="c5c86-112">Aktualizujte obsah výše uvedeného parametru na základě konkrétních souborů a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c5c86-112">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="c5c86-113">Například odkaz na verzi souboru Microsoft. Spark jar, který jste nahráli do DBFS, a použijte odpovídající název vaší aplikace a publikovaného souboru zip aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5c86-113">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="c5c86-114">Přejděte do úlohy a výběrem **Upravit** Nakonfigurujte cluster vaší úlohy.</span><span class="sxs-lookup"><span data-stu-id="c5c86-114">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="c5c86-115">Nastavte Databricks Runtime verzi na základě verze Apache Spark, kterou chcete ve svém nasazení použít.</span><span class="sxs-lookup"><span data-stu-id="c5c86-115">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="c5c86-116">Pak vyberte **Upřesnit možnosti > inicializační skripty**a jako hodnotu nastavte cestu inicializačního skriptu `dbfs:/spark-dotnet/db-init.sh` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-116">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="c5c86-117">Vyberte **Potvrdit** a potvrďte nastavení clusteru.</span><span class="sxs-lookup"><span data-stu-id="c5c86-117">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="c5c86-118">Přejděte do úlohy a výběrem **Spustit nyní** spusťte úlohu na nově nakonfigurovaném clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="c5c86-118">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="c5c86-119">Vytvoření clusteru úlohy trvá několik minut.</span><span class="sxs-lookup"><span data-stu-id="c5c86-119">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="c5c86-120">Po vytvoření se vaše úloha odešle.</span><span class="sxs-lookup"><span data-stu-id="c5c86-120">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="c5c86-121">Výstup můžete zobrazit tak, že v levé nabídce pracovního prostoru datacihly vyberete **clustery** a pak vyberete **protokoly ovladačů**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-121">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="c5c86-122">Nasazení pomocí Set jar</span><span class="sxs-lookup"><span data-stu-id="c5c86-122">Deploy using Set Jar</span></span>

<span data-ttu-id="c5c86-123">Alternativně můžete použít [Nastavení jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) v pracovním prostoru datacihly k odeslání .net pro Apache Spark úlohy do datacihlů.</span><span class="sxs-lookup"><span data-stu-id="c5c86-123">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="c5c86-124">*Nastavení jar* povolí odeslání úlohy do existujícího aktivního clusteru.</span><span class="sxs-lookup"><span data-stu-id="c5c86-124">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="c5c86-125">Nastavení jednorázového času</span><span class="sxs-lookup"><span data-stu-id="c5c86-125">One-time setup</span></span>

1. <span data-ttu-id="c5c86-126">Přejděte do svého clusteru datacihly a v nabídce na levé straně vyberte **úlohy** a potom **nastavte jar**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-126">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="c5c86-127">Nahrajte příslušné `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-127">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="c5c86-128">Upravte následující parametry tak, aby obsahovaly správný název spustitelného souboru, který jste publikovali místo `<your-app-name>` :</span><span class="sxs-lookup"><span data-stu-id="c5c86-128">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="c5c86-129">Nakonfigurujte cluster tak, aby odkazoval na existující cluster, pro který jste již nastavili inicializační skript.</span><span class="sxs-lookup"><span data-stu-id="c5c86-129">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="c5c86-130">Publikování a spuštění vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="c5c86-130">Publish and run your app</span></span>

1. <span data-ttu-id="c5c86-131">Ujistěte se, že jste publikovali aplikaci a že váš kód aplikace nepoužívá `SparkSession.Stop()` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-131">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="c5c86-132">K nahrání vaší aplikace do clusteru datacihly použijte rozhraní příkazového [řádku datacihly](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) .</span><span class="sxs-lookup"><span data-stu-id="c5c86-132">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="c5c86-133">Například pomocí následujícího příkazu nahrajte publikovanou aplikaci do svého clusteru:</span><span class="sxs-lookup"><span data-stu-id="c5c86-133">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="c5c86-134">Pokud máte ve své aplikaci nějaké uživatelsky definované funkce, sestavení aplikace, jako jsou knihovny DLL, které obsahují uživatelsky definované funkce společně s jejich závislostmi, musí být umístěné v pracovním adresáři každého z *Microsoft. spark. Worker*.</span><span class="sxs-lookup"><span data-stu-id="c5c86-134">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="c5c86-135">Nahrajte sestavení vaší aplikace do vašeho clusteru datacihly:</span><span class="sxs-lookup"><span data-stu-id="c5c86-135">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="c5c86-136">Odkomentujte a upravte část závislosti aplikací v [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) tak, aby odkazovala na cestu k závislostem vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5c86-136">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="c5c86-137">Pak do svého clusteru nahrajte aktualizované *DB-init.sh* :</span><span class="sxs-lookup"><span data-stu-id="c5c86-137">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="c5c86-138">Chcete-li spustit úlohu, přejděte do **clusteru datacihly > úlohy > [název úlohy] > spustit nyní** .</span><span class="sxs-lookup"><span data-stu-id="c5c86-138">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c5c86-139">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c5c86-139">Next steps</span></span>

* [<span data-ttu-id="c5c86-140">Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c5c86-140">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="c5c86-141">Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů</span><span class="sxs-lookup"><span data-stu-id="c5c86-141">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="c5c86-142">Dokumentace k Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="c5c86-142">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
