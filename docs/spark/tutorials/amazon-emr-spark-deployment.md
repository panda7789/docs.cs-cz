---
title: Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454932"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="9f21d-103">Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="9f21d-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="9f21d-104">V tomto kurzu se naučíte nasadit rozhraní .NET pro Apache Spark aplikaci do Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="9f21d-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="9f21d-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="9f21d-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9f21d-106">Příprava Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="9f21d-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="9f21d-107">Publikování aplikace Spark .NET</span><span class="sxs-lookup"><span data-stu-id="9f21d-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="9f21d-108">Nasazení aplikace do Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="9f21d-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="9f21d-109">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9f21d-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f21d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f21d-110">Prerequisites</span></span>

<span data-ttu-id="9f21d-111">Než začnete, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="9f21d-111">Before you start, do the following:</span></span>

* <span data-ttu-id="9f21d-112">Stáhněte si rozhraní příkazového [řádku AWS](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="9f21d-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="9f21d-113">Stáhněte si [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do svého místního počítače.</span><span class="sxs-lookup"><span data-stu-id="9f21d-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="9f21d-114">Toto je pomocný skript, který později použijete ke kopírování rozhraní .NET pro Apache Spark závislé soubory do pracovních uzlů clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="9f21d-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="9f21d-115">Příprava závislostí pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="9f21d-115">Prepare worker dependencies</span></span>

<span data-ttu-id="9f21d-116">**Microsoft. spark. Worker** je komponenta back-end, která je umístěná na jednotlivých pracovních uzlech clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="9f21d-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="9f21d-117">Pokud chcete spustit systém C# souborů UDF (uživatelsky definovaná funkce), musí Spark pochopit, jak spustit modul CLR .NET pro spouštění systému souborů UDF.</span><span class="sxs-lookup"><span data-stu-id="9f21d-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="9f21d-118">**Microsoft. spark. Worker** poskytuje kolekci tříd pro Spark, které tuto funkci povolují.</span><span class="sxs-lookup"><span data-stu-id="9f21d-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="9f21d-119">Vyberte verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, která se má nasadit na váš cluster.</span><span class="sxs-lookup"><span data-stu-id="9f21d-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="9f21d-120">Pokud například chcete `.NET for Apache Spark v0.1.0` pomocí `netcoreapp2.1`, Stáhněte si soubor [Microsoft. spark. work. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="9f21d-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="9f21d-121">Nahrajte `Microsoft.Spark.Worker.<release>.tar.gz` a [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) se do distribuovaného systému souborů (např. S3), ke kterému má váš cluster přístup.</span><span class="sxs-lookup"><span data-stu-id="9f21d-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="9f21d-122">Příprava rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="9f21d-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="9f21d-123">Při sestavování aplikace postupujte podle kurzu [Začínáme](get-started.md) .</span><span class="sxs-lookup"><span data-stu-id="9f21d-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="9f21d-124">Publikujte aplikaci Spark .NET jako samostatnou.</span><span class="sxs-lookup"><span data-stu-id="9f21d-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="9f21d-125">Spusťte následující příkaz na platformě Linux.</span><span class="sxs-lookup"><span data-stu-id="9f21d-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="9f21d-126">Vyprodukuje pro publikované soubory `<your app>.zip`.</span><span class="sxs-lookup"><span data-stu-id="9f21d-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="9f21d-127">Spusťte následující příkaz na platformě Linux pomocí `zip`.</span><span class="sxs-lookup"><span data-stu-id="9f21d-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="9f21d-128">Nahrajte následující položky do distribuovaného systému souborů (například S3), ke kterému má váš cluster přístup:</span><span class="sxs-lookup"><span data-stu-id="9f21d-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="9f21d-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tento JAR je součástí balíčku NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) a je umístěn v adresáři výstupu sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f21d-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="9f21d-130">Soubory (jako jsou soubory závislosti nebo společná data dostupná pro každého pracovního procesu) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo knihovny, na kterých je vaše aplikace závislá), aby se umístily do pracovního adresáře každého prováděcího modulu.</span><span class="sxs-lookup"><span data-stu-id="9f21d-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="9f21d-131">Nasazení na Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="9f21d-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="9f21d-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) je spravovaná platforma clusteru, která usnadňuje spouštění rozsáhlých datových ARCHITEKTUR na AWS.</span><span class="sxs-lookup"><span data-stu-id="9f21d-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="9f21d-133">Amazon EMR Spark je založený na systému Linux.</span><span class="sxs-lookup"><span data-stu-id="9f21d-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="9f21d-134">Proto pokud vás zajímá nasazení aplikace do Amazon EMR Spark, ujistěte se, že je vaše aplikace .NET Standard kompatibilní a že ke kompilaci vaší aplikace použijete [kompilátor .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="9f21d-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="9f21d-135">Nasazení Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="9f21d-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="9f21d-136">Tento krok se vyžaduje jenom při vytváření clusteru.</span><span class="sxs-lookup"><span data-stu-id="9f21d-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="9f21d-137">Spuštění `install-worker.sh` při vytváření clusteru pomocí [spouštěcích akcí](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="9f21d-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="9f21d-138">Spusťte následující příkaz na platformě Linux pomocí rozhraní příkazového řádku AWS.</span><span class="sxs-lookup"><span data-stu-id="9f21d-138">Run the following command on Linux using AWS CLI.</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="9f21d-139">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9f21d-139">Run your app</span></span>

<span data-ttu-id="9f21d-140">Existují dva způsoby, jak aplikaci spustit v Amazon EMR Spark: Spark-Submit a Amazon EMR kroky.</span><span class="sxs-lookup"><span data-stu-id="9f21d-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="9f21d-141">Použití Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="9f21d-141">Use spark-submit</span></span>

<span data-ttu-id="9f21d-142">Pomocí příkazu [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) můžete odesílat .NET pro úlohy Apache Spark do Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="9f21d-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="9f21d-143">`ssh` do jednoho z uzlů v clusteru.</span><span class="sxs-lookup"><span data-stu-id="9f21d-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="9f21d-144">Spusťte `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="9f21d-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="9f21d-145">Použití kroků Amazon EMR</span><span class="sxs-lookup"><span data-stu-id="9f21d-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="9f21d-146">[Kroky Amazon EMR](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) je možné použít k odesílání úloh do rozhraní Spark instalovaného v clusteru EMR.</span><span class="sxs-lookup"><span data-stu-id="9f21d-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="9f21d-147">Spusťte následující příkaz na platformě Linux pomocí rozhraní příkazového řádku AWS.</span><span class="sxs-lookup"><span data-stu-id="9f21d-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="9f21d-148">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9f21d-148">Next steps</span></span>

<span data-ttu-id="9f21d-149">V tomto kurzu jste nasadili rozhraní .NET pro Apache Spark aplikaci do Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="9f21d-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="9f21d-150">V případě rozhraní .NET for Apache Spark ukázkové projekty pokračujte na GitHub.</span><span class="sxs-lookup"><span data-stu-id="9f21d-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f21d-151">Ukázky pro .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="9f21d-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
