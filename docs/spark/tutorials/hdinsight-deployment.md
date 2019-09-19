---
title: Nasazení aplikace .NET pro Apache Spark do Azure HDInsight
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2e8da5497035a83fde75bf91a7d21437d510b480
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117982"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="97551-103">Nasazení aplikace .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="97551-103">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="97551-104">V tomto kurzu se naučíte nasadit rozhraní .NET pro Apache Spark aplikaci do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="97551-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Azure HDInsight.</span></span>

<span data-ttu-id="97551-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="97551-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="97551-106">Příprava Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="97551-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="97551-107">Publikování aplikace Spark .NET</span><span class="sxs-lookup"><span data-stu-id="97551-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="97551-108">Nasazení aplikace do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="97551-108">Deploy your app to Azure HDInsight</span></span>
> * <span data-ttu-id="97551-109">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="97551-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="97551-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97551-110">Prerequisites</span></span>

<span data-ttu-id="97551-111">Než začnete, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="97551-111">Before you start, do the following:</span></span>

* <span data-ttu-id="97551-112">Stáhněte si [Průzkumník služby Azure Storage](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="97551-112">Download [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span>
* <span data-ttu-id="97551-113">Stáhněte si [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do svého místního počítače.</span><span class="sxs-lookup"><span data-stu-id="97551-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="97551-114">Toto je pomocný skript, který později použijete ke kopírování rozhraní .NET pro Apache Spark závislé soubory do pracovních uzlů clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="97551-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="97551-115">Příprava závislostí pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="97551-115">Prepare worker dependencies</span></span>

<span data-ttu-id="97551-116">**Microsoft. spark. Worker** je komponenta back-end, která je umístěná na jednotlivých pracovních uzlech clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="97551-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="97551-117">Pokud chcete spustit systém C# souborů UDF (uživatelsky definovaná funkce), musí Spark pochopit, jak spustit modul CLR .NET pro spouštění systému souborů UDF.</span><span class="sxs-lookup"><span data-stu-id="97551-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="97551-118">**Microsoft. spark. Worker** poskytuje kolekci tříd pro Spark, které tuto funkci povolují.</span><span class="sxs-lookup"><span data-stu-id="97551-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="97551-119">Vyberte verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, která se má nasadit na váš cluster.</span><span class="sxs-lookup"><span data-stu-id="97551-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="97551-120">Pokud například chcete `.NET for Apache Spark v0.1.0` použít `netcoreapp2.1`, Stáhněte si soubor [Microsoft. spark. work. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="97551-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="97551-121">Nahrajte `Microsoft.Spark.Worker.<release>.tar.gz` a [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do distribuovaného systému souborů (např. HDFS, WASB, adls), ke kterému má váš cluster přístup.</span><span class="sxs-lookup"><span data-stu-id="97551-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="97551-122">Příprava rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="97551-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="97551-123">Při sestavování aplikace postupujte podle kurzu [Začínáme](get-started.md) .</span><span class="sxs-lookup"><span data-stu-id="97551-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="97551-124">Publikujte aplikaci Spark .NET jako samostatnou.</span><span class="sxs-lookup"><span data-stu-id="97551-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="97551-125">V systému Linux můžete spustit následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="97551-125">You can run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="97551-126">Vytvořte `<your app>.zip` pro publikované soubory.</span><span class="sxs-lookup"><span data-stu-id="97551-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="97551-127">Následující příkaz můžete spustit na platformě Linux pomocí nástroje `zip`.</span><span class="sxs-lookup"><span data-stu-id="97551-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="97551-128">Následujícím způsobem nahrajte distribuovaný systém souborů (např. HDFS, WASB, ADLS), ke kterému má váš cluster přístup:</span><span class="sxs-lookup"><span data-stu-id="97551-128">Upload the following to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to:</span></span>

   * <span data-ttu-id="97551-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tento JAR je součástí balíčku NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) a je umístěný ve výstupním adresáři sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="97551-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="97551-130">Soubory (jako jsou soubory závislostí nebo společná data dostupná pro každého pracovního procesu) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo `app` knihovny, na kterých závisí), budou umístěny do pracovního adresáře každého prováděcího modulu.</span><span class="sxs-lookup"><span data-stu-id="97551-130">Files (like dependency files or common data accessible to every worker) or Assemblies (like DLLs that contain your user-defined functions or libraries that your `app` depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-azure-hdinsight-spark"></a><span data-ttu-id="97551-131">Nasadit do Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="97551-131">Deploy to Azure HDInsight Spark</span></span>

<span data-ttu-id="97551-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) je implementace Apache Spark v cloudu od Microsoftu, která umožňuje uživatelům spouštět a konfigurovat clustery Spark v Azure.</span><span class="sxs-lookup"><span data-stu-id="97551-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) is the Microsoft implementation of Apache Spark in the cloud that allows users to launch and configure Spark clusters in Azure.</span></span> <span data-ttu-id="97551-133">Clustery HDInsight Spark můžete použít ke zpracování dat uložených v [Azure Storage](https://azure.microsoft.com/services/storage/) nebo [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span><span class="sxs-lookup"><span data-stu-id="97551-133">You can use HDInsight Spark clusters to process your data stored in [Azure Storage](https://azure.microsoft.com/services/storage/) or [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span></span>

> [!NOTE]
> <span data-ttu-id="97551-134">Azure HDInsight Spark je založen na systému Linux.</span><span class="sxs-lookup"><span data-stu-id="97551-134">Azure HDInsight Spark is Linux-based.</span></span> <span data-ttu-id="97551-135">Pokud vás zajímá nasazení aplikace pro Azure HDInsight Spark, ujistěte se, že je vaše aplikace .NET Standard kompatibilní a že ke kompilaci vaší aplikace používáte [kompilátor .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="97551-135">If you are interested in deploying your app to Azure HDInsight Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="97551-136">Nasazení Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="97551-136">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="97551-137">Tento krok se vyžaduje jenom jednou pro váš cluster.</span><span class="sxs-lookup"><span data-stu-id="97551-137">This step is only required once for your cluster.</span></span>

<span data-ttu-id="97551-138">Spusťte `install-worker.sh` v clusteru pomocí [akcí skriptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="97551-138">Run `install-worker.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

|<span data-ttu-id="97551-139">Nastavení</span><span class="sxs-lookup"><span data-stu-id="97551-139">Setting</span></span>|<span data-ttu-id="97551-140">Value</span><span class="sxs-lookup"><span data-stu-id="97551-140">Value</span></span>|
|-------|-----|
|<span data-ttu-id="97551-141">Typ skriptu</span><span class="sxs-lookup"><span data-stu-id="97551-141">Script type</span></span>|<span data-ttu-id="97551-142">Vlastní</span><span class="sxs-lookup"><span data-stu-id="97551-142">Custom</span></span>|
|<span data-ttu-id="97551-143">Name</span><span class="sxs-lookup"><span data-stu-id="97551-143">Name</span></span>|<span data-ttu-id="97551-144">Nainstalovat Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="97551-144">Install Microsoft.Spark.Worker</span></span>|
|<span data-ttu-id="97551-145">Identifikátor URI skriptu bash</span><span class="sxs-lookup"><span data-stu-id="97551-145">Bash script URI</span></span>|<span data-ttu-id="97551-146">Identifikátor URI, na který jste `install-worker.sh`nahráli.</span><span class="sxs-lookup"><span data-stu-id="97551-146">The URI to which you uploaded `install-worker.sh`.</span></span> <span data-ttu-id="97551-147">Třeba `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="97551-147">For example, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span></span>|
|<span data-ttu-id="97551-148">Typ (typy) uzlů</span><span class="sxs-lookup"><span data-stu-id="97551-148">Node type(s)</span></span>|<span data-ttu-id="97551-149">Zaměstnanec</span><span class="sxs-lookup"><span data-stu-id="97551-149">Worker</span></span>|
|<span data-ttu-id="97551-150">Parametry</span><span class="sxs-lookup"><span data-stu-id="97551-150">Parameters</span></span>|<span data-ttu-id="97551-151">Parametry do `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="97551-151">Parameters to `install-worker.sh`.</span></span> <span data-ttu-id="97551-152">Pokud jste například nahráli `install-worker.sh` Azure Data Lake Gen 2, bude to. `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`</span><span class="sxs-lookup"><span data-stu-id="97551-152">For example, if you uploaded `install-worker.sh` to Azure Data Lake Gen 2 then it would be `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span></span>|

![Obrázek akce skriptu](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a><span data-ttu-id="97551-154">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="97551-154">Run your app</span></span>

<span data-ttu-id="97551-155">Svoji úlohu můžete odeslat do Azure HDInsight pomocí `spark-submit` aplikace nebo Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="97551-155">You can submit your job to Azure HDInsight using `spark-submit` or Apache Livy.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="97551-156">Použití Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="97551-156">Use spark-submit</span></span>

<span data-ttu-id="97551-157">K odeslání .NET pro úlohy Apache Spark do Azure HDInsight můžete použít příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) .</span><span class="sxs-lookup"><span data-stu-id="97551-157">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="97551-158">`ssh`do jednoho z hlavních uzlů v clusteru.</span><span class="sxs-lookup"><span data-stu-id="97551-158">`ssh` into one of the head nodes in your cluster.</span></span>

1. <span data-ttu-id="97551-159">Spusťte `spark-submit`:</span><span class="sxs-lookup"><span data-stu-id="97551-159">Run `spark-submit`:</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a><span data-ttu-id="97551-160">Použití Apache Livy</span><span class="sxs-lookup"><span data-stu-id="97551-160">Use Apache Livy</span></span>

<span data-ttu-id="97551-161">K odeslání rozhraní .NET pro Apache Spark úlohy do clusteru Azure HDInsight Spark můžete použít [Apache Livy](https://livy.incubator.apache.org/)Apache Spark REST API.</span><span class="sxs-lookup"><span data-stu-id="97551-161">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="97551-162">Další informace najdete v tématu [vzdálené úlohy s Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="97551-162">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="97551-163">Následující příkaz můžete na platformě Linux spustit pomocí `curl`:</span><span class="sxs-lookup"><span data-stu-id="97551-163">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="97551-164">Další postup</span><span class="sxs-lookup"><span data-stu-id="97551-164">Next steps</span></span>

<span data-ttu-id="97551-165">V tomto kurzu jste nasadili aplikaci .NET pro Apache Spark do služby Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="97551-165">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="97551-166">Pokud se chcete dozvědět víc o službě HDInsight, přejděte k dokumentaci k Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="97551-166">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="97551-167">Dokumentace ke službě Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="97551-167">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
