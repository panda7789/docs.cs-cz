---
title: Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů
description: Zjistěte, jak nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 035a3c36337413153ee0370aec154d48b84a4711
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957253"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="b0d7a-103">Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů</span><span class="sxs-lookup"><span data-stu-id="b0d7a-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="b0d7a-104">V tomto kurzu se naučíte nasadit rozhraní .NET pro Apache Spark aplikaci do datacihlů.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="b0d7a-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="b0d7a-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="b0d7a-106">Příprava Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="b0d7a-106">Prepare Microsoft.Spark.Worker</span></span>
> - <span data-ttu-id="b0d7a-107">Publikování aplikace Spark .NET</span><span class="sxs-lookup"><span data-stu-id="b0d7a-107">Publish your Spark .NET app</span></span>
> - <span data-ttu-id="b0d7a-108">Nasazení aplikace do datacihlů</span><span class="sxs-lookup"><span data-stu-id="b0d7a-108">Deploy your app to Databricks</span></span>
> - <span data-ttu-id="b0d7a-109">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="b0d7a-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0d7a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0d7a-110">Prerequisites</span></span>

<span data-ttu-id="b0d7a-111">Než začnete, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="b0d7a-111">Before you start, do the following:</span></span>

- <span data-ttu-id="b0d7a-112">Stáhněte si rozhraní příkazového [řádku datacihly](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
- <span data-ttu-id="b0d7a-113">Stáhněte si [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do svého místního počítače.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="b0d7a-114">Toto je pomocný skript, který později použijete ke kopírování rozhraní .NET pro Apache Spark závislé soubory do pracovních uzlů clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="b0d7a-115">Příprava závislostí pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="b0d7a-115">Prepare worker dependencies</span></span>

<span data-ttu-id="b0d7a-116">**Microsoft. spark. Worker** je back-endové komponenta, která je umístěná na jednotlivých pracovních uzlech clusteru Spark.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="b0d7a-117">Pokud chcete spustit systém C# souborů UDF (uživatelsky definovaná funkce), musí Spark pochopit, jak spustit modul CLR .NET pro spouštění systému souborů UDF.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="b0d7a-118">**Microsoft. spark. Worker** poskytuje kolekci tříd pro Spark, které tuto funkci povolují.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="b0d7a-119">Vyberte verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, která se má nasadit na váš cluster.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="b0d7a-120">Pokud například chcete `.NET for Apache Spark v0.1.0` pomocí `netcoreapp2.1`, Stáhněte si soubor [Microsoft. spark. work. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="b0d7a-121">Nahrajte `Microsoft.Spark.Worker.<release>.tar.gz` a [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do distribuovaného systému souborů (například DBFS), ke kterému má váš cluster přístup.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="b0d7a-122">Příprava rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b0d7a-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="b0d7a-123">Při sestavování aplikace postupujte podle kurzu [Začínáme](get-started.md) .</span><span class="sxs-lookup"><span data-stu-id="b0d7a-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="b0d7a-124">Publikujte aplikaci Spark .NET jako samostatnou.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="b0d7a-125">V systému Linux můžete spustit následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-125">You can run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="b0d7a-126">Vyprodukuje pro publikované soubory `<your app>.zip`.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="b0d7a-127">Následující příkaz můžete na platformě Linux spustit pomocí `zip`.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="b0d7a-128">Nahrajte do distribuovaného systému souborů (například DBFS), ke kterému má cluster přístup, následující:</span><span class="sxs-lookup"><span data-stu-id="b0d7a-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   - <span data-ttu-id="b0d7a-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Tento JAR je součástí balíčku NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) a je umístěn ve výstupním adresáři sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   - `<your app>.zip`
   - <span data-ttu-id="b0d7a-130">Soubory (jako jsou soubory závislosti nebo společná data dostupná pro každého pracovního procesu) nebo sestavení (například knihovny DLL, které obsahují uživatelem definované funkce nebo knihovny, na kterých je vaše aplikace závislá), aby se umístily do pracovního adresáře každého prováděcího modulu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="b0d7a-131">Nasazení do Databricks</span><span class="sxs-lookup"><span data-stu-id="b0d7a-131">Deploy to Databricks</span></span>

<span data-ttu-id="b0d7a-132">[Datacihly](https://databricks.com) představují platformu, která poskytuje cloudové zpracování velkých objemů dat pomocí Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="b0d7a-133">[Datacihly](https://databricks.com/aws) [Azure Databricks](https://azure.microsoft.com/services/databricks/) a AWS jsou založené na systému Linux.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="b0d7a-134">Proto pokud vás zajímá nasazení vaší aplikace do datacihly, ujistěte se, že je vaše aplikace .NET Standard kompatibilní a že ke kompilaci vaší aplikace použijete [kompilátor .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="b0d7a-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="b0d7a-135">Datacihly umožňují odesílat rozhraní .NET pro aplikace Apache Spark do existujícího aktivního clusteru nebo vytvořit nový cluster při každém spuštění úlohy.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="b0d7a-136">K tomu je potřeba, aby byl **Microsoft. spark. Worker** nainstalovaný předtím, než odešlete rozhraní .NET pro aplikaci Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="b0d7a-137">Nasazení Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="b0d7a-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="b0d7a-138">Tento krok se vyžaduje jenom jednou pro cluster.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="b0d7a-139">Stáhněte si do svého místního počítače [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) a [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) .</span><span class="sxs-lookup"><span data-stu-id="b0d7a-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="b0d7a-140">Upravte **DB-init.sh** tak, aby odkazoval na verzi **Microsoft. spark. Worker** , kterou chcete stáhnout a nainstalovat do clusteru.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="b0d7a-141">Nainstalujte rozhraní příkazového [řádku datacihly](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="b0d7a-142">[Nastavte podrobnosti ověření](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) pro rozhraní PŘÍKAZového řádku datacihly.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="b0d7a-143">Nahrajte soubory do clusteru datacihly pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="b0d7a-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="b0d7a-144">Přejdete do pracovního prostoru datacihly.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="b0d7a-145">V nabídce na levé straně vyberte **clustery** a pak vyberte **vytvořit cluster**.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="b0d7a-146">Po správné konfiguraci clusteru nastavte **skript init** a vytvořte cluster.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Obrázek akce skriptu](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="b0d7a-148">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="b0d7a-148">Run your app</span></span> 

<span data-ttu-id="b0d7a-149">K odeslání vaší úlohy do datacihlů můžete použít `set JAR` nebo `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="b0d7a-150">Použít nastavení JAR</span><span class="sxs-lookup"><span data-stu-id="b0d7a-150">Use Set JAR</span></span>

<span data-ttu-id="b0d7a-151">[Nastavení jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) umožňuje odeslat úlohu do existujícího aktivního clusteru.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="b0d7a-152">Nastavení jednorázového času</span><span class="sxs-lookup"><span data-stu-id="b0d7a-152">One-time setup</span></span>

1. <span data-ttu-id="b0d7a-153">Přejděte do svého clusteru datacihly a v nabídce vlevo vyberte **úlohy** .</span><span class="sxs-lookup"><span data-stu-id="b0d7a-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="b0d7a-154">Pak vyberte **nastavit jar**.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="b0d7a-155">Nahrajte příslušný soubor `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="b0d7a-156">Nastavte parametry odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-156">Set the parameters appropriately.</span></span>

   | <span data-ttu-id="b0d7a-157">Parametr</span><span class="sxs-lookup"><span data-stu-id="b0d7a-157">Parameter</span></span>   | <span data-ttu-id="b0d7a-158">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0d7a-158">Value</span></span>                                                |
   |-------------|------------------------------------------------------|
   | <span data-ttu-id="b0d7a-159">Main – třída</span><span class="sxs-lookup"><span data-stu-id="b0d7a-159">Main Class</span></span>  | <span data-ttu-id="b0d7a-160">org. Apache. spark. deploy. dotnet. DotnetRunner</span><span class="sxs-lookup"><span data-stu-id="b0d7a-160">org.apache.spark.deploy.dotnet.DotnetRunner</span></span>          |
   | <span data-ttu-id="b0d7a-161">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0d7a-161">Arguments</span></span>   | <span data-ttu-id="b0d7a-162">/dBFS/Apps/< název vaší aplikace >. zip < vaše aplikace – hlavní třída ></span><span class="sxs-lookup"><span data-stu-id="b0d7a-162">/dbfs/apps/<your-app-name>.zip <your-app-main-class></span></span> |

4. <span data-ttu-id="b0d7a-163">Nakonfigurujte **cluster** tak, aby odkazoval na existující **cluster, který** jste vytvořili v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-163">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="b0d7a-164">Publikování a spuštění vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="b0d7a-164">Publish and run your app</span></span>

1. <span data-ttu-id="b0d7a-165">Použijte rozhraní příkazového [řádku datacihly](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) k nahrání vaší aplikace do vašeho clusteru datacihly.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-165">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="b0d7a-166">Tento krok je vyžadován pouze v případě, že vaše sestavení vaší aplikace (například knihovny DLL, které obsahují uživatelsky definované funkce společně s jejich závislostmi) je nutné umístit do pracovního adresáře každého z **Microsoft. spark. Worker**.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-166">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="b0d7a-167">Nahrání sestavení vaší aplikace do clusteru datacihly</span><span class="sxs-lookup"><span data-stu-id="b0d7a-167">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="b0d7a-168">Odkomentujte a upravte část závislosti aplikací v [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) tak, aby odkazovala na cestu k závislostem vaší aplikace a nahráli do vašeho clusteru datacihly.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-168">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="b0d7a-169">Restartujte cluster.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-169">Restart your cluster.</span></span>

3. <span data-ttu-id="b0d7a-170">V pracovním prostoru datacihly přejdete do svého clusteru datacihly.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="b0d7a-171">V části **úlohy**vyberte požadovanou úlohu a spusťte úlohu kliknutím na **Spustit nyní** .</span><span class="sxs-lookup"><span data-stu-id="b0d7a-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="b0d7a-172">Použití Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="b0d7a-172">Use spark-submit</span></span>

<span data-ttu-id="b0d7a-173">Příkaz [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) umožňuje odeslat úlohu do nového clusteru.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-173">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="b0d7a-174">[Vytvořte úlohu](https://docs.databricks.com/user-guide/jobs.html) a vyberte **Konfigurovat Spark-odeslat**.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-174">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="b0d7a-175">Nakonfigurujte `spark-submit` s následujícími parametry:</span><span class="sxs-lookup"><span data-stu-id="b0d7a-175">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="b0d7a-176">V pracovním prostoru datacihly přejdete do svého clusteru datacihly.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-176">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="b0d7a-177">V části **úlohy**vyberte požadovanou úlohu a spusťte úlohu kliknutím na **Spustit nyní** .</span><span class="sxs-lookup"><span data-stu-id="b0d7a-177">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b0d7a-178">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b0d7a-178">Next steps</span></span>

<span data-ttu-id="b0d7a-179">V tomto kurzu jste nasadili rozhraní .NET pro Apache Spark aplikaci na datacihly.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-179">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="b0d7a-180">Pokud se chcete dozvědět víc o datacihlách, přejděte k dokumentaci Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-180">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0d7a-181">Dokumentace k Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="b0d7a-181">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
