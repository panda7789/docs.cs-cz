---
title: Nasazení rozhraní .NET pro aplikaci Apache Spark do amazonského EMR Spark
description: Zjistěte, jak nasadit .NET pro aplikaci Apache Spark do Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73454932"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="84823-103">Nasazení rozhraní .NET pro aplikaci Apache Spark do amazonského EMR Spark</span><span class="sxs-lookup"><span data-stu-id="84823-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="84823-104">Tento kurz učí, jak nasadit .NET pro aplikaci Apache Spark do Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="84823-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="84823-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="84823-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="84823-106">Příprava microsoft.spark.worker</span><span class="sxs-lookup"><span data-stu-id="84823-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="84823-107">Publikování aplikace Spark .NET</span><span class="sxs-lookup"><span data-stu-id="84823-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="84823-108">Nasazení aplikace do Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="84823-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="84823-109">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="84823-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84823-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84823-110">Prerequisites</span></span>

<span data-ttu-id="84823-111">Než začnete, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="84823-111">Before you start, do the following:</span></span>

* <span data-ttu-id="84823-112">Stáhněte si [rozhraní se křižovatek AWS](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="84823-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="84823-113">Stáhněte [si install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do místního počítače.</span><span class="sxs-lookup"><span data-stu-id="84823-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="84823-114">Toto je pomocný skript, který později použijete ke kopírování souborů .NET pro závislé soubory Apache Spark do pracovních uzlů clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="84823-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="84823-115">Příprava závislostí pracovníků</span><span class="sxs-lookup"><span data-stu-id="84823-115">Prepare worker dependencies</span></span>

<span data-ttu-id="84823-116">**Microsoft.Spark.Worker** je back-endová součást, která žije na jednotlivých pracovních uzlech vašeho clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="84823-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="84823-117">Pokud chcete spustit C# UDF (uživatelem definovaná funkce), Spark musí pochopit, jak spustit .NET CLR ke spuštění UDF.</span><span class="sxs-lookup"><span data-stu-id="84823-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="84823-118">**Microsoft.Spark.Worker** poskytuje kolekci tříd pro Spark, které umožňují tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="84823-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="84823-119">Vyberte verzi [netcoreapp microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux, která se má nasadit ve vašem clusteru.</span><span class="sxs-lookup"><span data-stu-id="84823-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="84823-120">Chcete-li například `.NET for Apache Spark v0.1.0` `netcoreapp2.1`použít program , stáhněte si soubor [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="84823-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="84823-121">Nahrávání `Microsoft.Spark.Worker.<release>.tar.gz` a [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do distribuovaného systému souborů (např. s3), ke kterému má cluster přístup.</span><span class="sxs-lookup"><span data-stu-id="84823-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="84823-122">Příprava aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="84823-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="84823-123">Podle kurzu [Začínáme](get-started.md) vytvořte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="84823-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="84823-124">Publikujte aplikaci Spark .NET jako samostatnou.</span><span class="sxs-lookup"><span data-stu-id="84823-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="84823-125">Spusťte následující příkaz na Linuxu.</span><span class="sxs-lookup"><span data-stu-id="84823-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="84823-126">Vytvořit `<your app>.zip` pro publikované soubory.</span><span class="sxs-lookup"><span data-stu-id="84823-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="84823-127">Spusťte následující příkaz `zip`na Linuxu pomocí .</span><span class="sxs-lookup"><span data-stu-id="84823-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="84823-128">Nahrajte do distribuovaného systému souborů (např. s3) následující položky, ke kterému má cluster přístup:</span><span class="sxs-lookup"><span data-stu-id="84823-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="84823-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tato nádoba je součástí balíčku [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet a je umístěna společně ve výstupním adresáři sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="84823-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="84823-130">Soubory (jako jsou soubory závislostí nebo společná data přístupná každému pracovníkovi) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo knihovny, na kterých závisí vaše aplikace), které mají být umístěny do pracovního adresáře každého vykonavatele.</span><span class="sxs-lookup"><span data-stu-id="84823-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="84823-131">Nasazení na Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="84823-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="84823-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) je spravovaná clusterová platforma, která zjednodušuje provoz rámců pro velké objemy dat na AWS.</span><span class="sxs-lookup"><span data-stu-id="84823-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="84823-133">Amazon EMR Spark je založen na Linuxu.</span><span class="sxs-lookup"><span data-stu-id="84823-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="84823-134">Pokud tedy máte zájem o nasazení aplikace do Amazon EMR Spark, ujistěte se, že vaše aplikace je kompatibilní se standardem .NET standard a že k kompilaci aplikace používáte [kompilátor .NET Core.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="84823-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="84823-135">Nasazení microsoft.spark.worker</span><span class="sxs-lookup"><span data-stu-id="84823-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="84823-136">Tento krok je vyžadován pouze při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="84823-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="84823-137">Spustit `install-worker.sh` během vytváření clusteru pomocí [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="84823-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="84823-138">Spusťte následující příkaz na Linuxu pomocí příkazového příkazu AWS.</span><span class="sxs-lookup"><span data-stu-id="84823-138">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="84823-139">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="84823-139">Run your app</span></span>

<span data-ttu-id="84823-140">Existují dva způsoby, jak spustit aplikaci v Amazon EMR Spark: spark-submit a Amazon EMR Steps.</span><span class="sxs-lookup"><span data-stu-id="84823-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="84823-141">Použití spark-submit</span><span class="sxs-lookup"><span data-stu-id="84823-141">Use spark-submit</span></span>

<span data-ttu-id="84823-142">Příkaz [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete použít k odeslání .NET pro úlohy Apache Spark do Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="84823-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="84823-143">`ssh`do jednoho z uzlů v clusteru.</span><span class="sxs-lookup"><span data-stu-id="84823-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="84823-144">Spusťte `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="84823-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="84823-145">Použití Amazon EMR kroky</span><span class="sxs-lookup"><span data-stu-id="84823-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="84823-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) lze použít k odeslání úloh do rámce Spark nainstalovaného v clusteru EMR.</span><span class="sxs-lookup"><span data-stu-id="84823-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="84823-147">Spusťte následující příkaz na Linuxu pomocí příkazového příkazu AWS.</span><span class="sxs-lookup"><span data-stu-id="84823-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="84823-148">Další kroky</span><span class="sxs-lookup"><span data-stu-id="84823-148">Next steps</span></span>

<span data-ttu-id="84823-149">V tomto kurzu jste nasadili .NET pro aplikaci Apache Spark do Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="84823-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="84823-150">Pro .NET pro projekty příklad Apache Spark pokračujte na GitHub.</span><span class="sxs-lookup"><span data-stu-id="84823-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84823-151">.NET pro ukázky Apache Spark</span><span class="sxs-lookup"><span data-stu-id="84823-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
