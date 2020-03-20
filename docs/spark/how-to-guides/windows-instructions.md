---
title: Vytvoření aplikace .NET pro Apache Spark ve Windows
description: Přečtěte si, jak vytvořit rozhraní .NET pro aplikaci Apache Spark ve Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185762"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="409c0-103">Přečtěte si, jak vytvořit rozhraní .NET pro aplikaci Apache Spark ve Windows</span><span class="sxs-lookup"><span data-stu-id="409c0-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="409c0-104">Tento článek vás naučí, jak vytvořit rozhraní .NET pro aplikace Apache Spark v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="409c0-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="409c0-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="409c0-105">Prerequisites</span></span>

<span data-ttu-id="409c0-106">Pokud již máte všechny následující požadavky, přejděte na kroky [sestavení.](#build)</span><span class="sxs-lookup"><span data-stu-id="409c0-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="409c0-107">Stáhněte a nainstalujte **[sadu .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** `dotnet` - instalace sady SDK přidá řetězec nástrojů do vaší cesty.</span><span class="sxs-lookup"><span data-stu-id="409c0-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="409c0-108">Podporují se jádra .NET 2.1, 2.2 a 3.1.</span><span class="sxs-lookup"><span data-stu-id="409c0-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="409c0-109">Nainstalujte **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (verze 16.3 nebo novější).</span><span class="sxs-lookup"><span data-stu-id="409c0-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="409c0-110">Verze Společenství je zcela zdarma.</span><span class="sxs-lookup"><span data-stu-id="409c0-110">The Community version is completely free.</span></span> <span data-ttu-id="409c0-111">Při konfiguraci instalace zahrňte minimálně tyto součásti:</span><span class="sxs-lookup"><span data-stu-id="409c0-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="409c0-112">Vývoj stolních počítačů .NET</span><span class="sxs-lookup"><span data-stu-id="409c0-112">.NET desktop development</span></span>
       * <span data-ttu-id="409c0-113">Všechny požadované součásti</span><span class="sxs-lookup"><span data-stu-id="409c0-113">All Required Components</span></span>
         * <span data-ttu-id="409c0-114">Vývojové nástroje rozhraní .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="409c0-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="409c0-115">Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="409c0-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="409c0-116">Všechny požadované součásti</span><span class="sxs-lookup"><span data-stu-id="409c0-116">All Required Components</span></span>
  3. <span data-ttu-id="409c0-117">Nainstalujte **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span><span class="sxs-lookup"><span data-stu-id="409c0-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span>
     - <span data-ttu-id="409c0-118">Vyberte příslušnou verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="409c0-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="409c0-119">Například *jdk-8u201-windows-x64.exe* pro windows x64 počítač.</span><span class="sxs-lookup"><span data-stu-id="409c0-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="409c0-120">Nainstalujte pomocí instalačního programu a `java` ověřte, zda je možné spustit z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="409c0-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="409c0-121">Nainstalujte **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span><span class="sxs-lookup"><span data-stu-id="409c0-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="409c0-122">Stažení [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="409c0-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="409c0-123">Extrahovat do místního adresáře.</span><span class="sxs-lookup"><span data-stu-id="409c0-123">Extract to a local directory.</span></span> <span data-ttu-id="409c0-124">Například \*C:\bin\apache-maven-3.6.0\*.</span><span class="sxs-lookup"><span data-stu-id="409c0-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="409c0-125">Přidejte Apache Maven do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="409c0-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="409c0-126">Například *C:\bin\apache-maven-3.6.0\bin*.</span><span class="sxs-lookup"><span data-stu-id="409c0-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="409c0-127">Ověřte, zda `mvn` je možné spustit z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="409c0-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="409c0-128">Nainstalujte **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span><span class="sxs-lookup"><span data-stu-id="409c0-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="409c0-129">Stáhněte si [Apache Spark 2.3+](https://spark.apache.org/downloads.html) a extrahujte ji do místní složky (například *C:\bin\spark-2.3.2-bin-hadoop2.7)\*pomocí [7-zip](https://www.7-zip.org/). (Podporované verze jiskry jsou 2.3.*, 2.4.0, 2.4.1, 2.4.3 a 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="409c0-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="409c0-130">Přidejte [novou proměnnou](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`prostředí .</span><span class="sxs-lookup"><span data-stu-id="409c0-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="409c0-131">Například \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span><span class="sxs-lookup"><span data-stu-id="409c0-131">For example, \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - <span data-ttu-id="409c0-132">Přidejte Apache Spark do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="409c0-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="409c0-133">Například *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span><span class="sxs-lookup"><span data-stu-id="409c0-133">For example, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span></span>

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - <span data-ttu-id="409c0-134">Ověřte, zda `spark-shell` je možné spustit z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="409c0-134">Verify you are able to run `spark-shell` from your command-line.</span></span>
        <span data-ttu-id="409c0-135">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="409c0-135">Sample console output:</span></span>

        ```
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. <span data-ttu-id="409c0-136">Nainstalujte **[program WinUtils](https://github.com/steveloughran/winutils)**.</span><span class="sxs-lookup"><span data-stu-id="409c0-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="409c0-137">Stáhnout `winutils.exe` binární soubor z [úložiště WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="409c0-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="409c0-138">Měli byste vybrat verzi Hadoopu, se kterou byla zkompilován distribuce Spark.</span><span class="sxs-lookup"><span data-stu-id="409c0-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="409c0-139">Pro zkoušku použijte hadoop-2.7.1 pro Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="409c0-139">For exammple, use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="409c0-140">Uložte `winutils.exe` binární soubor do adresáře podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="409c0-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="409c0-141">Například *C:\hadoop\bin*.</span><span class="sxs-lookup"><span data-stu-id="409c0-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="409c0-142">Nastavte `HADOOP_HOME` tak, aby odrážel adresář s winutils.exe (bez přihrádky).</span><span class="sxs-lookup"><span data-stu-id="409c0-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="409c0-143">Například pomocí příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="409c0-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="409c0-144">Nastavte proměnnou prostředí `%HADOOP_HOME%\bin`PATH tak, aby zahrnovala .</span><span class="sxs-lookup"><span data-stu-id="409c0-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="409c0-145">Například pomocí příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="409c0-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="409c0-146">Před přechodem do `dotnet`další `java` `mvn`části `spark-shell` se ujistěte, že je možné spustit příkazový řádek .</span><span class="sxs-lookup"><span data-stu-id="409c0-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="409c0-147">Cítíš, že existuje lepší způsob?</span><span class="sxs-lookup"><span data-stu-id="409c0-147">Feel there is a better way?</span></span> <span data-ttu-id="409c0-148">[Otevřete problém](https://github.com/dotnet/spark/issues) a neváhejte přispět.</span><span class="sxs-lookup"><span data-stu-id="409c0-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="409c0-149">Pokud byly aktualizovány všechny proměnné prostředí, může být vyžadována nová instance příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="409c0-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="409c0-150">Sestavení</span><span class="sxs-lookup"><span data-stu-id="409c0-150">Build</span></span>

<span data-ttu-id="409c0-151">Pro zbytek této příručky budete muset mít klonované .NET pro Apache Spark úložiště do počítače.</span><span class="sxs-lookup"><span data-stu-id="409c0-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="409c0-152">Můžete zvolit libovolné umístění pro klonované úložiště.</span><span class="sxs-lookup"><span data-stu-id="409c0-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="409c0-153">Například \*C:\github\dotnet-spark\*.</span><span class="sxs-lookup"><span data-stu-id="409c0-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="409c0-154">Sestavení vrstvy rozšíření .NET pro Apache Spark Scala</span><span class="sxs-lookup"><span data-stu-id="409c0-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="409c0-155">Když odešlete .NET aplikaci, .NET pro Apache Spark má potřebnou logiku napsanou v Scala, která informuje Apache Spark, jak zpracovat vaše požadavky (například žádost o vytvoření nové spark session, žádost o přenos dat ze strany .NET na stranu JVM atd.).</span><span class="sxs-lookup"><span data-stu-id="409c0-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="409c0-156">Tuto logiku naleznete v [rozhraní .NET pro zdrojový kód Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="409c0-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="409c0-157">Bez ohledu na to, zda používáte rozhraní .NET Framework nebo .NET Core, budete muset vytvořit přípojnou vrstvu .NET pro Apache Spark Scala:</span><span class="sxs-lookup"><span data-stu-id="409c0-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package
```

<span data-ttu-id="409c0-158">Měli byste vidět JARs vytvořené pro podporované verze Spark:</span><span class="sxs-lookup"><span data-stu-id="409c0-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="409c0-159">Vytvoření rozhraní .NET pro ukázkové aplikace Spark</span><span class="sxs-lookup"><span data-stu-id="409c0-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="409c0-160">Tato část vysvětluje, jak vytvořit [ukázkové aplikace](https://github.com/dotnet/spark/tree/master/examples) pro rozhraní .NET pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="409c0-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="409c0-161">Tyto kroky vám pomohou pochopit celkový proces vytváření pro všechny .NET pro aplikaci Spark.</span><span class="sxs-lookup"><span data-stu-id="409c0-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="409c0-162">Použití sady Visual Studio pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="409c0-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="409c0-163">Otevřete `src\csharp\Microsoft.Spark.sln` v sadě `Microsoft.Spark.CSharp.Examples` Visual Studio `examples` a vytvořte projekt pod složkou (to bude zase sestavení projektu vazby .NET také).</span><span class="sxs-lookup"><span data-stu-id="409c0-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="409c0-164">Pokud chcete, můžete do `Microsoft.Spark.Examples` projektu napsat vlastní kód ("input_file.json" v tomto příkladu je soubor json s daty, která chcete vytvořit datový rámec):</span><span class="sxs-lookup"><span data-stu-id="409c0-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     <span data-ttu-id="409c0-165">Jakmile je sestavení úspěšné, zobrazí se příslušné binární soubory vytvořené ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="409c0-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>
     <span data-ttu-id="409c0-166">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="409c0-166">Sample console output:</span></span>

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="409c0-167">Použití rozhraní CLI jádra rozhraní .NET pro jádro rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="409c0-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="409c0-168">V současné době pracujeme na automatizaci sestavení .NET Core pro Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="409c0-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="409c0-169">Do té doby oceňujeme vaši trpělivost při provádění některých kroků ručně.</span><span class="sxs-lookup"><span data-stu-id="409c0-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="409c0-170">Sestavte pracovníka:</span><span class="sxs-lookup"><span data-stu-id="409c0-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="409c0-171">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="409c0-171">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. <span data-ttu-id="409c0-172">Sestavte ukázky:</span><span class="sxs-lookup"><span data-stu-id="409c0-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="409c0-173">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="409c0-173">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="409c0-174">Spuštění rozhraní .NET pro ukázkové aplikace Spark</span><span class="sxs-lookup"><span data-stu-id="409c0-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="409c0-175">Po sestavení ukázky, jejich spuštění `spark-submit` bude prostřednictvím bez ohledu na to, zda se zaměřujete na rozhraní .NET Framework nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="409c0-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="409c0-176">Ujistěte se, že jste postupovali [podle požadavků](#prerequisites) a nainstalovali Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="409c0-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="409c0-177">Nastavte `DOTNET_WORKER_DIR` proměnnou prostředí `PATH` or tak, `Microsoft.Spark.Worker` aby zahrnovala cestu, kde byl binární soubor vygenerován (například *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span><span class="sxs-lookup"><span data-stu-id="409c0-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="409c0-178">Otevřete Powershell a přejděte do adresáře, kde byla vygenerována vaše binární sada aplikace (například *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span><span class="sxs-lookup"><span data-stu-id="409c0-178">Open Powershell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="409c0-179">Spuštění aplikace se řídí základní strukturou:</span><span class="sxs-lookup"><span data-stu-id="409c0-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="409c0-180">Zde je několik příkladů, které můžete spustit:</span><span class="sxs-lookup"><span data-stu-id="409c0-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="409c0-181">**[Microsoft.Spark.Examples.sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="409c0-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="409c0-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="409c0-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="409c0-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven přístupné)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="409c0-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="409c0-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (sklenice k dispozici)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="409c0-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
