---
title: Začínáme s rozhraním .NET pro Apache Spark
description: Zjistěte, jak spustit aplikaci .NET pro Apache Spark pomocí .NET Core ve Windows, MacOS a Ubuntu.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187541"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="755b5-103">Kurz: Začínáme s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="755b5-104">Tento výukový program vás naučí, jak spustit aplikaci .NET pro Apache Spark pomocí .NET Core ve Windows, MacOS a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="755b5-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="755b5-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="755b5-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="755b5-106">Příprava prostředí na rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="755b5-107">Napište svou první aplikaci .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="755b5-108">Sestavení a spuštění jednoduché aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="755b5-109">Příprava prostředí</span><span class="sxs-lookup"><span data-stu-id="755b5-109">Prepare your environment</span></span>

<span data-ttu-id="755b5-110">Než začnete psát aplikaci, musíte nastavit některé požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="755b5-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="755b5-111">Pokud můžete `dotnet`spustit `java` `mvn`, `spark-shell` , , z prostředí příkazového řádku, pak je vaše prostředí již připraveno a můžete přeskočit na další část.</span><span class="sxs-lookup"><span data-stu-id="755b5-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="755b5-112">Pokud nelze spustit některý nebo všechny příkazy, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="755b5-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="755b5-113">1. Instalace rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="755b5-113">1. Install .NET</span></span>

<span data-ttu-id="755b5-114">Chcete-li začít vytvářet aplikace .NET, je třeba stáhnout a nainstalovat .NET SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="755b5-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="755b5-115">Stáhněte a nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span><span class="sxs-lookup"><span data-stu-id="755b5-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="755b5-116">Instalace sady SDK `dotnet` přidá nástrojovou řetězka do cesty.</span><span class="sxs-lookup"><span data-stu-id="755b5-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="755b5-117">Po instalaci sady .NET Core SDK otevřete nový příkazový `dotnet`řádek nebo terminál a spusťte program .</span><span class="sxs-lookup"><span data-stu-id="755b5-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="755b5-118">Pokud příkaz spustí a vytiskne informace o tom, jak používat dotnet, můžete přejít k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="755b5-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="755b5-119">Pokud se `'dotnet' is not recognized as an internal or external command` zobrazí chyba, před spuštěním příkazu zkontrolujte, zda jste otevřeli **nový** příkazový řádek nebo terminál.</span><span class="sxs-lookup"><span data-stu-id="755b5-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="755b5-120">2. Instalace Javy</span><span class="sxs-lookup"><span data-stu-id="755b5-120">2. Install Java</span></span>

<span data-ttu-id="755b5-121">Nainstalujte [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) pro Windows a MacOS nebo [OpenJDK 8](https://openjdk.java.net/install/) pro Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="755b5-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="755b5-122">Vyberte příslušnou verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="755b5-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="755b5-123">Vyberte například **jdk-8u201-windows-x64.exe** pro počítač se systémem Windows x64 (jak je znázorněno níže) nebo **jdk-8u231-macosx-x64.dmg** pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="755b5-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="755b5-124">Potom použijte příkaz `java` k ověření instalace.</span><span class="sxs-lookup"><span data-stu-id="755b5-124">Then, use the command `java` to verify the installation.</span></span>

![Java ke stažení](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="755b5-126">3. Instalace kompresního softwaru</span><span class="sxs-lookup"><span data-stu-id="755b5-126">3. Install compression software</span></span>

<span data-ttu-id="755b5-127">Apache Spark je stažen jako komprimovaný soubor .tgz.</span><span class="sxs-lookup"><span data-stu-id="755b5-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="755b5-128">K extrahování souboru použijte extrakční program, například [7-Zip](https://www.7-zip.org/) nebo [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="755b5-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="755b5-129">4. Nainstalujte Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-129">4. Install Apache Spark</span></span>

<span data-ttu-id="755b5-130">[Stáhněte a nainstalujte Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="755b5-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="755b5-131">Budete muset vybrat z verze 2.3.\* nebo 2.4.0, 2.4.1, 2.4.3 nebo 2.4.4 (.NET pro Apache Spark není kompatibilní s jinými verzemi Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="755b5-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="755b5-132">Příkazy použité v následujících krocích předpokládají, že jste [stáhli a nainstalovali Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="755b5-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="755b5-133">Chcete-li použít jinou verzi, nahraďte **verzi 2.4.1** příslušným číslem verze.</span><span class="sxs-lookup"><span data-stu-id="755b5-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="755b5-134">Potom extrahujte soubor **.tar** a soubory Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="755b5-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="755b5-135">Extrahování vnořeného souboru **TAR:**</span><span class="sxs-lookup"><span data-stu-id="755b5-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="755b5-136">Vyhledejte stažený soubor **spark-2.4.1-bin-hadoop2.7.tgz.**</span><span class="sxs-lookup"><span data-stu-id="755b5-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="755b5-137">Klikněte pravým tlačítkem myši na soubor a vyberte **7-Zip -> Extract zde**.</span><span class="sxs-lookup"><span data-stu-id="755b5-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="755b5-138">**spark-2.4.1-bin-hadoop2.7.tar** je vytvořen vedle souboru **.tgz,** který jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="755b5-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="755b5-139">Extrahování souborů Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="755b5-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="755b5-140">Klikněte pravým tlačítkem myši na **jiskru-2.4.1-bin-hadoop2.7.tar** a vyberte **7-Zip -> Extrahovat soubory ...**</span><span class="sxs-lookup"><span data-stu-id="755b5-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="755b5-141">Do pole **Extrahovat do** pole Zadejte **C:\bin.**</span><span class="sxs-lookup"><span data-stu-id="755b5-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="755b5-142">Zaškrtnutí políčka pod polem **Extrahovat do** zaškrtněte.</span><span class="sxs-lookup"><span data-stu-id="755b5-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="755b5-143">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="755b5-143">Select **OK**.</span></span>
* <span data-ttu-id="755b5-144">Soubory Apache Spark jsou extrahovány do C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="755b5-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Instalace Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="755b5-146">Spusťte následující příkazy pro nastavení proměnných prostředí používaných k vyhledání Apache Spark v **systému Windows**:</span><span class="sxs-lookup"><span data-stu-id="755b5-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="755b5-147">Spusťte následující příkazy pro nastavení proměnných prostředí používaných k vyhledání Apache Spark v **Systému MacOS** a **Ubuntu**:</span><span class="sxs-lookup"><span data-stu-id="755b5-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="755b5-148">Po instalaci všeho a nastavení proměnných prostředí otevřete **nový** příkazový řádek nebo terminál a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="755b5-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="755b5-149">Pokud příkaz spustí a vytiskne informace o verzi, můžete přejít k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="755b5-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="755b5-150">Pokud se `'spark-submit' is not recognized as an internal or external command` zobrazí chyba, zkontrolujte, zda jste otevřeli **nový** příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="755b5-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="755b5-151">5. Instalace rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="755b5-152">Stáhněte si verzi [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) z rozhraní .NET pro Apache Spark GitHub.</span><span class="sxs-lookup"><span data-stu-id="755b5-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="755b5-153">Pokud jste například na počítači se systémem Windows a plánujete používat rozhraní .NET Core, [stáhněte si verzi netcoreapp3.1 systému Windows x64](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span><span class="sxs-lookup"><span data-stu-id="755b5-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="755b5-154">Extrahování microsoft.spark.worker:</span><span class="sxs-lookup"><span data-stu-id="755b5-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="755b5-155">Vyhledejte soubor **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip,** který jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="755b5-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="755b5-156">Klikněte pravým tlačítkem myši a vyberte **7-Zip -> Extrahovat soubory ...**.</span><span class="sxs-lookup"><span data-stu-id="755b5-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="755b5-157">Do pole **Extrahovat do** pole Zadejte **C:\bin.**</span><span class="sxs-lookup"><span data-stu-id="755b5-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="755b5-158">Zaškrtnutí políčka pod polem **Extrahovat do** zaškrtněte.</span><span class="sxs-lookup"><span data-stu-id="755b5-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="755b5-159">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="755b5-159">Select **OK**.</span></span>

![Instalace služby .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="755b5-161">6. Instalace WinUtils (pouze windows)</span><span class="sxs-lookup"><span data-stu-id="755b5-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="755b5-162">.NET pro Apache Spark vyžaduje, aby se WinUtils instaloval vedle Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="755b5-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="755b5-163">[Stáhnout winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="755b5-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="755b5-164">Potom zkopírujte winutils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="755b5-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="755b5-165">Pokud používáte jinou verzi Hadoopu, která je anotována na konci názvu instalační složky Spark, [vyberte verzi WinUtils,](https://github.com/steveloughran/winutils) která je kompatibilní s vaší verzí Hadoopu.</span><span class="sxs-lookup"><span data-stu-id="755b5-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="755b5-166">7. Nastavení DOTNET_WORKER_DIR a kontrola závislostí</span><span class="sxs-lookup"><span data-stu-id="755b5-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="755b5-167">Spusťte jeden z následujících `DOTNET_WORKER_DIR` příkazů a nastavte proměnnou prostředí, kterou aplikace .NET používají k vyhledání rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="755b5-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="755b5-168">V **systému Windows**vytvořte [novou proměnnou](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` prostředí a nastavte ji do adresáře, `C:\bin\Microsoft.Spark.Worker\`do kterého jste stáhli a extrahovali microsoft.spark.worker (například ).</span><span class="sxs-lookup"><span data-stu-id="755b5-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="755b5-169">V **systému MacOS**vytvořte `export DOTNET_WORKER_DIR <your_path>` novou proměnnou prostředí pomocí a nastavte ji do adresáře, do kterého jste stáhli a extrahovali microsoft.spark.worker (například *~/bin/Microsoft.Spark.Worker/*).</span><span class="sxs-lookup"><span data-stu-id="755b5-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="755b5-170">Na **Ubuntu**, vytvořte [novou proměnnou](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` prostředí a nastavte ji do adresáře, kde jste stáhli a extrahovali Microsoft.Spark.Worker (například *~/bin/Microsoft.Spark.Worker*).</span><span class="sxs-lookup"><span data-stu-id="755b5-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="755b5-171">Nakonec před přechodem do `dotnet`další `java` `mvn`části `spark-shell` zkontrolujte, zda lze spustit příkazový řádek .</span><span class="sxs-lookup"><span data-stu-id="755b5-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="755b5-172">Napsat rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="755b5-173">1. Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="755b5-173">1. Create a console app</span></span>

<span data-ttu-id="755b5-174">V příkazovém řádku nebo terminálu vytvořte novou konzolovou aplikaci následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="755b5-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="755b5-175">Příkaz `dotnet` vytvoří `new` aplikaci `console` typu pro vás.</span><span class="sxs-lookup"><span data-stu-id="755b5-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="755b5-176">Parametr `-o` vytvoří adresář s názvem *mySparkApp,* kde je vaše aplikace uložena a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="755b5-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="755b5-177">Příkaz `cd mySparkApp` změní adresář na adresář aplikace, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="755b5-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="755b5-178">2. Nainstalujte balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="755b5-178">2. Install NuGet package</span></span>

<span data-ttu-id="755b5-179">Chcete-li v aplikaci použít rozhraní .NET pro Apache Spark, nainstalujte balíček Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="755b5-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="755b5-180">V příkazovém řádku nebo terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="755b5-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="755b5-181">3. Kód aplikace</span><span class="sxs-lookup"><span data-stu-id="755b5-181">3. Code your app</span></span>

<span data-ttu-id="755b5-182">Otevřete *Program.cs* v kódu Visual Studia nebo v libovolném textovém editoru a nahraďte celý kód následujícím:</span><span class="sxs-lookup"><span data-stu-id="755b5-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="755b5-183">4. Vytvoření a přidání datového souboru</span><span class="sxs-lookup"><span data-stu-id="755b5-183">4. Create and add a data file</span></span>

<span data-ttu-id="755b5-184">Otevřete příkazový řádek nebo terminál a přejděte do složky aplikace.</span><span class="sxs-lookup"><span data-stu-id="755b5-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="755b5-185">Aplikace zpracuje soubor obsahující řádky textu.</span><span class="sxs-lookup"><span data-stu-id="755b5-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="755b5-186">Vytvořte soubor *input.txt* v adresáři *mySparkApp,* který obsahuje následující text:</span><span class="sxs-lookup"><span data-stu-id="755b5-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="755b5-187">Spuštění aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="755b5-188">Chcete-li vytvořit aplikaci, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="755b5-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="755b5-189">Spusťte následující příkaz a odešlete svou žádost ke spuštění na Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="755b5-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="755b5-190">Tento příkaz předpokládá, že jste si stáhli Apache Spark a přidali ji do proměnné prostředí PATH, abyste mohli používat `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="755b5-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="755b5-191">V opačném případě byste museli použít úplnou cestu (například *C:\bin\apache-spark\bin\spark-submit* nebo *~/spark/bin/spark-submit).*</span><span class="sxs-lookup"><span data-stu-id="755b5-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="755b5-192">Při spuštění aplikace se do konzoly zapisují data počtu slov souboru *input.txt.*</span><span class="sxs-lookup"><span data-stu-id="755b5-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="755b5-193">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="755b5-193">Congratulations!</span></span> <span data-ttu-id="755b5-194">Úspěšně jste vytvořili a spustili .NET pro aplikaci Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="755b5-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="755b5-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="755b5-195">Next steps</span></span>

<span data-ttu-id="755b5-196">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="755b5-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="755b5-197">Příprava prostředí Windows na rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="755b5-198">Napište svou první aplikaci .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="755b5-199">Sestavení a spuštění jednoduché aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="755b5-200">Chcete-li zobrazit video vysvětlující výše uvedené kroky, podívejte se na [video sérii .NET pro Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="755b5-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="755b5-201">Další informace najdete na stránce zdrojů.</span><span class="sxs-lookup"><span data-stu-id="755b5-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="755b5-202">.NET pro prostředky Apache Spark</span><span class="sxs-lookup"><span data-stu-id="755b5-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
