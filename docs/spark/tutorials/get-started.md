---
title: Začínáme s .NET pro Apache Spark
description: Zjistěte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 679ee7660e96504768a781e1e384acab80362736
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743212"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="4ec0c-103">Kurz: Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="4ec0c-104">V tomto kurzu se naučíte, jak spustit rozhraní .NET pro Apache Spark aplikaci pomocí .NET Core ve Windows.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="4ec0c-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4ec0c-106">Příprava prostředí Windows pro rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="4ec0c-107">Zápis prvního rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="4ec0c-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="4ec0c-108">Sestavování a spouštění jednoduchého rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="4ec0c-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="4ec0c-109">Příprava prostředí</span><span class="sxs-lookup"><span data-stu-id="4ec0c-109">Prepare your environment</span></span>

<span data-ttu-id="4ec0c-110">Než začnete psát aplikaci, musíte nastavit některé závislosti požadavků.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="4ec0c-111">Pokud v prostředí příkazového řádku můžete spustit `dotnet`, `java`, `mvn``spark-shell`, je vaše prostředí už připravené a můžete přejít k další části.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="4ec0c-112">Pokud nemůžete spustit žádný z příkazů nebo všechny, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="4ec0c-113">1. instalace .NET</span><span class="sxs-lookup"><span data-stu-id="4ec0c-113">1. Install .NET</span></span>

<span data-ttu-id="4ec0c-114">Chcete-li začít sestavovat aplikace .NET, je nutné stáhnout a nainstalovat sadu .NET SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="4ec0c-115">Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span> <span data-ttu-id="4ec0c-116">Instalace sady SDK přidá do vaší cesty `dotnet` sada nástrojů.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="4ec0c-117">Po instalaci .NET Core SDK otevřete nový příkazový řádek a spusťte `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-117">Once you've installed the .NET Core SDK, open a new command prompt and run `dotnet`.</span></span>

<span data-ttu-id="4ec0c-118">Pokud se příkaz spustí a vytiskne informace o použití dotnet, může přejít k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="4ec0c-119">Pokud se zobrazí chyba `'dotnet' is not recognized as an internal or external command`, před spuštěním příkazu se ujistěte, že jste otevřeli **Nový** příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="4ec0c-120">2. instalace Java</span><span class="sxs-lookup"><span data-stu-id="4ec0c-120">2. Install Java</span></span>

<span data-ttu-id="4ec0c-121">Nainstalujte [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

<span data-ttu-id="4ec0c-122">Vyberte odpovídající verzi pro váš operační systém.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="4ec0c-123">Vyberte například **JDK-8u201-Windows-x64. exe** pro počítač se systémem Windows x64.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span> <span data-ttu-id="4ec0c-124">Pak pomocí příkazového `java` Ověřte instalaci.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-124">Then, use the command `java` to verify the installation.</span></span>

![Stažení Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a><span data-ttu-id="4ec0c-126">3. instalace 7 – zip</span><span class="sxs-lookup"><span data-stu-id="4ec0c-126">3. Install 7-zip</span></span>

<span data-ttu-id="4ec0c-127">Apache Spark se stáhl jako komprimovaný soubor. tgz.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="4ec0c-128">K extrakci souboru použijte program pro extrakci, například 7 – zip.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-128">Use an extraction program, like 7-zip, to extract the file.</span></span>

* <span data-ttu-id="4ec0c-129">Navštivte [soubory ke stažení pro 7 – zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-129">Visit [7-Zip downloads](https://www.7-zip.org/).</span></span>
* <span data-ttu-id="4ec0c-130">V první tabulce na stránce vyberte 32 stažení x86 nebo 64-bit x64, v závislosti na vašem operačním systému.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-130">In the first table on the page, select the 32-bit x86 or 64-bit x64 download, depending on your operating system.</span></span>
* <span data-ttu-id="4ec0c-131">Po dokončení stahování spusťte instalační program.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-131">When the download completes, run the installer.</span></span>

![Stažení 7Zip](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a><span data-ttu-id="4ec0c-133">4. instalace Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-133">4. Install Apache Spark</span></span>

<span data-ttu-id="4ec0c-134">[Stáhněte a nainstalujte Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-134">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="4ec0c-135">Bude nutné vybrat z verze 2,3. \* nebo 2.4.0, 2.4.1, 2.4.3 nebo 2.4.4 (rozhraní .NET pro Apache Spark není kompatibilní s jinými verzemi Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-135">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="4ec0c-136">Příkazy použité v následujících krocích předpokládají, že jste [stáhli a nainstalovali Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-136">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="4ec0c-137">Pokud chcete použít jinou verzi, nahraďte hodnotu **2.4.1** příslušným číslem verze.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-137">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="4ec0c-138">Pak extrahujte soubor **. tar** a Apache Spark soubory.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-138">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="4ec0c-139">Extrahování vnořeného souboru **. tar** :</span><span class="sxs-lookup"><span data-stu-id="4ec0c-139">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="4ec0c-140">Vyhledejte soubor **Spark-2.4.1-bin-Hadoop 2.7. tgz** , který jste si stáhli.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-140">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="4ec0c-141">Klikněte pravým tlačítkem na soubor a vyberte **7-zip-> extrakci**.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-141">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="4ec0c-142">**Spark-2.4.1-bin-Hadoop 2.7. tar** se vytvoří společně s souborem **. tgz** , který jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-142">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="4ec0c-143">Extrahování Apache Spark souborů:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-143">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="4ec0c-144">Klikněte pravým tlačítkem na **Spark-2.4.1-bin-Hadoop 2.7. tar** a vyberte **7-zip-> extrahování souborů...**</span><span class="sxs-lookup"><span data-stu-id="4ec0c-144">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="4ec0c-145">Do pole **extrahovat do** zadejte **C:\Bin** .</span><span class="sxs-lookup"><span data-stu-id="4ec0c-145">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="4ec0c-146">Zrušte zaškrtnutí políčka pod polem **extrahovat do** .</span><span class="sxs-lookup"><span data-stu-id="4ec0c-146">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="4ec0c-147">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-147">Select **OK**.</span></span>
* <span data-ttu-id="4ec0c-148">Soubory Apache Spark jsou extrahovány do C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="4ec0c-148">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Instalace Sparku](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="4ec0c-150">Spuštěním následujících příkazů nastavte proměnné prostředí používané k vyhledání Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-150">Run the following commands to set the environment variables used to locate Apache Spark:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="4ec0c-151">Jakmile nainstalujete vše a nastavíte proměnné prostředí, otevřete **Nový** příkazový řádek a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-151">Once you've installed everything and set your environment variables, open a **new** command prompt and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="4ec0c-152">Pokud se příkaz spustí a zobrazí informace o verzi, můžete přejít k dalšímu kroku.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-152">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="4ec0c-153">Pokud se zobrazí chyba `'spark-submit' is not recognized as an internal or external command`, ujistěte se, že jste otevřeli **Nový** příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-153">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="4ec0c-154">5. Nainstalujte rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-154">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="4ec0c-155">Stáhněte si verzi [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) z rozhraní .net pro Apache Spark GitHub.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-155">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="4ec0c-156">Například pokud jste na počítači s Windows a plánujete použít .NET Core, [Stáhněte si verzi Windows x64 netcoreapp 2.1](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-156">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp2.1 release](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span></span>

<span data-ttu-id="4ec0c-157">Extrakce Microsoft. spark. Worker:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-157">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="4ec0c-158">Vyhledejte soubor **Microsoft. spark. work. netcoreapp 2.1. Win-x64-0.6.0. zip** , který jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-158">Locate the **Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="4ec0c-159">Klikněte pravým tlačítkem a vyberte **7-zip-> extrahování souborů...** .</span><span class="sxs-lookup"><span data-stu-id="4ec0c-159">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="4ec0c-160">Do pole **extrahovat do** zadejte **C:\Bin** .</span><span class="sxs-lookup"><span data-stu-id="4ec0c-160">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="4ec0c-161">Zrušte zaškrtnutí políčka pod polem **extrahovat do** .</span><span class="sxs-lookup"><span data-stu-id="4ec0c-161">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="4ec0c-162">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-162">Select **OK**.</span></span>

![Instalace .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a><span data-ttu-id="4ec0c-164">6. instalace WinUtils</span><span class="sxs-lookup"><span data-stu-id="4ec0c-164">6. Install WinUtils</span></span>

<span data-ttu-id="4ec0c-165">Rozhraní .NET pro Apache Spark vyžaduje, aby se WinUtils nainstalovaly společně s Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-165">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="4ec0c-166">[Stáhněte si winutils. exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-166">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="4ec0c-167">Pak zkopírujte WinUtils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-167">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="4ec0c-168">Pokud používáte jinou verzi systému Hadoop, která je Poznáma na konci názvu instalační složky Sparku, [Vyberte verzi WinUtils](https://github.com/steveloughran/winutils) , která je kompatibilní s vaší verzí Hadoop.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-168">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="4ec0c-169">7. Nastavte DOTNET_WORKER_DIR a ověřte závislosti.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-169">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="4ec0c-170">Spuštěním následujícího příkazu nastavte proměnnou prostředí `DOTNET_WORKER_DIR`, kterou aplikace .NET používá k vyhledání rozhraní .NET pro Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-170">Run the following command to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark:</span></span>

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

<span data-ttu-id="4ec0c-171">Nakonec před přechodem na další oddíl dvakrát ověřte, že je možné spustit `dotnet`, `java`, `mvn``spark-shell` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="4ec0c-172">Zápis rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="4ec0c-173">1. vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="4ec0c-173">1. Create a console app</span></span>

<span data-ttu-id="4ec0c-174">Na příkazovém řádku spusťte následující příkazy k vytvoření nové konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-174">In your command prompt, run the following commands to create a new console application:</span></span>

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="4ec0c-175">Příkaz `dotnet` vytvoří pro vás `new`ou aplikaci typu `console`.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="4ec0c-176">Parametr `-o` vytvoří adresář s názvem *mySparkApp* , kde je vaše aplikace uložená, a naplní ji požadovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="4ec0c-177">Příkaz `cd mySparkApp` změní adresář na adresář aplikace, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="4ec0c-178">2. instalace balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="4ec0c-178">2. Install NuGet package</span></span>

<span data-ttu-id="4ec0c-179">Pokud chcete použít .NET pro Apache Spark v aplikaci, nainstalujte balíček Microsoft. spark.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="4ec0c-180">Na příkazovém řádku spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-180">In your command prompt, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a><span data-ttu-id="4ec0c-181">3. kódování aplikace</span><span class="sxs-lookup"><span data-stu-id="4ec0c-181">3. Code your app</span></span>

<span data-ttu-id="4ec0c-182">Otevřete *program.cs* v Visual Studio Code nebo libovolný textový editor a nahraďte celý kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
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

### <a name="4-add-data-file"></a><span data-ttu-id="4ec0c-183">4. Přidejte datový soubor.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-183">4. Add data file</span></span>

<span data-ttu-id="4ec0c-184">Vaše aplikace zpracovává soubor obsahující řádky textu.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-184">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="4ec0c-185">Vytvořte ve svém adresáři *mySparkApp* soubor *input. txt* s následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-185">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="4ec0c-186">Spuštění aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-186">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="4ec0c-187">Spuštěním následujícího příkazu sestavte aplikaci:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-187">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="4ec0c-188">Spuštěním následujícího příkazu odešlete aplikaci, která se má spustit na Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-188">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. <span data-ttu-id="4ec0c-189">Po spuštění aplikace se do konzoly zapíše data počtu slov ve *vstupním souboru. txt* .</span><span class="sxs-lookup"><span data-stu-id="4ec0c-189">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="4ec0c-190">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="4ec0c-190">Congratulations!</span></span> <span data-ttu-id="4ec0c-191">Úspěšně jste vytvořili a spustili rozhraní .NET pro Apache Spark aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-191">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4ec0c-192">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4ec0c-192">Next steps</span></span>

<span data-ttu-id="4ec0c-193">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="4ec0c-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4ec0c-194">Příprava prostředí Windows pro rozhraní .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-194">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="4ec0c-195">Zápis prvního rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="4ec0c-195">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="4ec0c-196">Sestavování a spouštění jednoduchého rozhraní .NET pro Apache Spark aplikaci</span><span class="sxs-lookup"><span data-stu-id="4ec0c-196">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="4ec0c-197">Pokud se chcete podívat na video s vysvětlením výše uvedených kroků, Zarezervujte si [řadu videí .NET pro Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="4ec0c-197">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="4ec0c-198">Další informace najdete na stránce prostředky.</span><span class="sxs-lookup"><span data-stu-id="4ec0c-198">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4ec0c-199">.NET pro prostředky Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4ec0c-199">.NET for Apache Spark Resources</span></span>](../resources/index.md)
