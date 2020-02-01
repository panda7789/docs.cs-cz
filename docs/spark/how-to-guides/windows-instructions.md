---
title: Vytvoření rozhraní .NET pro Apache Spark aplikaci v systému Windows
description: Naučte se, jak sestavit rozhraní .NET pro Apache Spark aplikaci v systému Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: e6dec09f7d3e8d478cdcccf9df1c3e72d5f884eb
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76928034"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="503ea-103">Informace o tom, jak sestavit rozhraní .NET pro Apache Spark aplikaci v systému Windows</span><span class="sxs-lookup"><span data-stu-id="503ea-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="503ea-104">V tomto článku se naučíte, jak sestavit rozhraní .NET pro Apache Spark aplikace ve Windows.</span><span class="sxs-lookup"><span data-stu-id="503ea-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="503ea-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="503ea-105">Prerequisites</span></span>

<span data-ttu-id="503ea-106">Pokud již máte všechny následující požadavky, přejděte k postupu [sestavení](#build) .</span><span class="sxs-lookup"><span data-stu-id="503ea-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="503ea-107">Stažení a instalace **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** – instalace sady SDK přidá do vaší cesty `dotnet` sada nástrojů.</span><span class="sxs-lookup"><span data-stu-id="503ea-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="503ea-108">Podporují se .NET Core 2,1, 2,2 a 3,1.</span><span class="sxs-lookup"><span data-stu-id="503ea-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="503ea-109">Nainstalujte **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (verze 16,3 nebo novější).</span><span class="sxs-lookup"><span data-stu-id="503ea-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="503ea-110">Verze komunity je zcela zadarmo.</span><span class="sxs-lookup"><span data-stu-id="503ea-110">The Community version is completely free.</span></span> <span data-ttu-id="503ea-111">Při konfiguraci instalace zahrňte tyto komponenty minimálně:</span><span class="sxs-lookup"><span data-stu-id="503ea-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="503ea-112">Vývoj desktopových aplikací pomocí .NET</span><span class="sxs-lookup"><span data-stu-id="503ea-112">.NET desktop development</span></span>
       * <span data-ttu-id="503ea-113">Všechny požadované součásti</span><span class="sxs-lookup"><span data-stu-id="503ea-113">All Required Components</span></span>
         * <span data-ttu-id="503ea-114">Vývojové nástroje .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="503ea-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="503ea-115">Vývoj multiplatformních aplikací pomocí rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="503ea-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="503ea-116">Všechny požadované součásti</span><span class="sxs-lookup"><span data-stu-id="503ea-116">All Required Components</span></span>
  3. <span data-ttu-id="503ea-117">Nainstalujte **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** .</span><span class="sxs-lookup"><span data-stu-id="503ea-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span> 
     - <span data-ttu-id="503ea-118">Vyberte příslušnou verzi operačního systému, třeba JDK-8u201-Windows-x64. exe pro počítač se systémem Win x64.</span><span class="sxs-lookup"><span data-stu-id="503ea-118">Select the appropriate version for your operating system e.g., jdk-8u201-windows-x64.exe for Win x64 machine.</span></span>
     - <span data-ttu-id="503ea-119">Nainstalujte pomocí instalačního programu a ověřte, že je možné spustit `java` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="503ea-119">Install using the installer and verify you are able to run `java` from your command-line.</span></span>
  4. <span data-ttu-id="503ea-120">Nainstalujte **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .</span><span class="sxs-lookup"><span data-stu-id="503ea-120">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="503ea-121">Stáhněte si [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="503ea-121">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
     - <span data-ttu-id="503ea-122">Extrahujte do místního adresáře, například `C:\bin\apache-maven-3.6.0\`.</span><span class="sxs-lookup"><span data-stu-id="503ea-122">Extract to a local directory e.g., `C:\bin\apache-maven-3.6.0\`.</span></span>
     - <span data-ttu-id="503ea-123">Přidejte Apache Maven do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml) , např. `C:\bin\apache-maven-3.6.0\bin`.</span><span class="sxs-lookup"><span data-stu-id="503ea-123">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\apache-maven-3.6.0\bin`.</span></span>
     - <span data-ttu-id="503ea-124">Ověřte, že je možné spustit `mvn` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="503ea-124">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="503ea-125">Nainstalujte **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .</span><span class="sxs-lookup"><span data-stu-id="503ea-125">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="503ea-126">Stáhněte si [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) a extrahujte ji do místní složky (např. `C:\bin\spark-2.3.2-bin-hadoop2.7\`) pomocí [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="503ea-126">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`) using [7-zip](https://www.7-zip.org/).</span></span> <span data-ttu-id="503ea-127">(Podporované verze Sparku jsou 2,3. \*, 2.4.0, 2.4.1, 2.4.3 a 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="503ea-127">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="503ea-128">Přidejte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` například `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="503ea-128">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - <span data-ttu-id="503ea-129">Přidejte Apache Spark do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml) , např. `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span><span class="sxs-lookup"><span data-stu-id="503ea-129">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span></span>

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - <span data-ttu-id="503ea-130">Ověřte, že je možné spustit `spark-shell` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="503ea-130">Verify you are able to run `spark-shell` from your command-line.</span></span>        
        <span data-ttu-id="503ea-131">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="503ea-131">Sample console output:</span></span>

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

  6. <span data-ttu-id="503ea-132">Nainstalujte **[WinUtils](https://github.com/steveloughran/winutils)** .</span><span class="sxs-lookup"><span data-stu-id="503ea-132">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="503ea-133">Stažení `winutils.exe` binárního souboru z [úložiště WinUtils](https://github.com/steveloughran/winutils)</span><span class="sxs-lookup"><span data-stu-id="503ea-133">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="503ea-134">Měli byste vybrat verzi Hadoop, se kterou byla zkompilována distribuce Spark, např. použijte Hadoop-2.7.1 pro Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="503ea-134">You should select the version of Hadoop the Spark distribution was compiled with, e.g. use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="503ea-135">`winutils.exe` binární soubor uložte do zvoleného adresáře, například `C:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="503ea-135">Save `winutils.exe` binary to a directory of your choice e.g., `C:\hadoop\bin`.</span></span>
     - <span data-ttu-id="503ea-136">Nastavte `HADOOP_HOME` tak, aby odrážel adresář pomocí winutils. exe (bez přihrádky).</span><span class="sxs-lookup"><span data-stu-id="503ea-136">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="503ea-137">Například při použití příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="503ea-137">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="503ea-138">Nastavte proměnnou prostředí PATH tak, aby zahrnovala `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="503ea-138">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="503ea-139">Například při použití příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="503ea-139">For instance, using command-line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="503ea-140">Než přejdete k další části, ujistěte se, že máte možnost spustit `dotnet`, `java`, `mvn``spark-shell` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="503ea-140">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="503ea-141">Máte lepší možnost?</span><span class="sxs-lookup"><span data-stu-id="503ea-141">Feel there is a better way?</span></span> <span data-ttu-id="503ea-142">[Otevřete prosím problém](https://github.com/dotnet/spark/issues) a nebojte se přispívat.</span><span class="sxs-lookup"><span data-stu-id="503ea-142">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="503ea-143">Pokud byly aktualizovány jakékoli proměnné prostředí, může být nutné zadat novou instanci příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="503ea-143">A new instance of the command-line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="503ea-144">Sestavit</span><span class="sxs-lookup"><span data-stu-id="503ea-144">Build</span></span>

<span data-ttu-id="503ea-145">Ve zbývající části tohoto průvodce budete muset naklonovat rozhraní .NET pro Apache Spark úložiště do svého počítače.</span><span class="sxs-lookup"><span data-stu-id="503ea-145">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="503ea-146">Můžete zvolit libovolné umístění klonovaného úložiště, například `C:\github\dotnet-spark\`.</span><span class="sxs-lookup"><span data-stu-id="503ea-146">You can choose any location for the cloned repository, e.g., `C:\github\dotnet-spark\`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="503ea-147">Sestavit vrstvu rozšíření .NET pro Apache Spark Scala</span><span class="sxs-lookup"><span data-stu-id="503ea-147">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="503ea-148">Při odeslání aplikace .NET má rozhraní .NET pro Apache Spark potřebnou logiku napsanou v Scala, která informuje Apache Spark jak zpracovat vaše požadavky (například požadavek na vytvoření nové relace Sparku, požádat o přenos dat ze strany .NET na stranu JVM atd.).</span><span class="sxs-lookup"><span data-stu-id="503ea-148">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="503ea-149">Tuto logiku najdete ve [zdrojovém kódu .NET pro Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="503ea-149">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="503ea-150">Bez ohledu na to, jestli používáte .NET Framework nebo .NET Core, budete muset sestavit vrstvu rozšíření .NET for Apache Spark Scala:</span><span class="sxs-lookup"><span data-stu-id="503ea-150">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package 
```

<span data-ttu-id="503ea-151">Měli byste vidět jar vytvořené pro podporované verze Sparku:</span><span class="sxs-lookup"><span data-stu-id="503ea-151">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="503ea-152">Sestavení ukázkových aplikací .NET pro Spark</span><span class="sxs-lookup"><span data-stu-id="503ea-152">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="503ea-153">V této části je vysvětlen postup sestavení [ukázkových aplikací](https://github.com/dotnet/spark/tree/master/examples) pro rozhraní .net pro Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="503ea-153">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="503ea-154">Tyto kroky vám pomůžou pochopit celkový proces vytváření jakékoli aplikace .NET pro Spark.</span><span class="sxs-lookup"><span data-stu-id="503ea-154">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="503ea-155">Používání sady Visual Studio pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="503ea-155">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="503ea-156">Otevřete `src\csharp\Microsoft.Spark.sln` v aplikaci Visual Studio a sestavte projekt `Microsoft.Spark.CSharp.Examples` ve složce `examples` (tím se vytvoří také projekt vazby rozhraní .NET).</span><span class="sxs-lookup"><span data-stu-id="503ea-156">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="503ea-157">Pokud chcete, můžete napsat vlastní kód v projektu `Microsoft.Spark.Examples` (' input_file. JSON ' v tomto příkladu je soubor JSON s daty, se kterými chcete vytvořit datový rámec.):</span><span class="sxs-lookup"><span data-stu-id="503ea-157">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
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

     <span data-ttu-id="503ea-158">Po úspěšném sestavení se zobrazí příslušné binární soubory, které byly vytvořeny ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="503ea-158">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>     
     <span data-ttu-id="503ea-159">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="503ea-159">Sample console output:</span></span>
     
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

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="503ea-160">Použití .NET Core CLI pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="503ea-160">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="503ea-161">V současné době pracujeme na automatizaci sestavení .NET Core pro Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="503ea-161">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="503ea-162">Dokud pak nebudeme mít v provedení některých kroků k trpělivost.</span><span class="sxs-lookup"><span data-stu-id="503ea-162">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="503ea-163">Sestavte pracovní proces:</span><span class="sxs-lookup"><span data-stu-id="503ea-163">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
      
      <span data-ttu-id="503ea-164">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="503ea-164">Sample console output:</span></span>

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

  2. <span data-ttu-id="503ea-165">Sestavte ukázky:</span><span class="sxs-lookup"><span data-stu-id="503ea-165">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
   
      <span data-ttu-id="503ea-166">Ukázkový výstup konzoly:</span><span class="sxs-lookup"><span data-stu-id="503ea-166">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="503ea-167">Spuštění ukázkových aplikací .NET pro Spark</span><span class="sxs-lookup"><span data-stu-id="503ea-167">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="503ea-168">Po sestavení vzorků se jejich spuštění bude provádět prostřednictvím `spark-submit` bez ohledu na to, jestli cílíte .NET Framework nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="503ea-168">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="503ea-169">Ujistěte se, že jste postupovali s částí [požadavky](#prerequisites) a nainstalovali Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="503ea-169">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="503ea-170">Nastavte proměnnou prostředí `DOTNET_WORKER_DIR` nebo `PATH` tak, aby zahrnovala cestu, kde byl vygenerován `Microsoft.Spark.Worker` binární (např. `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` pro .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` pro .NET Core):</span><span class="sxs-lookup"><span data-stu-id="503ea-170">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="503ea-171">Otevřete PowerShell a vyhledejte adresář, ve kterém jste vygenerovali binární soubor aplikace (například `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` pro .NET Framework `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` pro .NET Core):</span><span class="sxs-lookup"><span data-stu-id="503ea-171">Open Powershell and go to the directory where your app binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="503ea-172">Spuštění aplikace se řídí základní strukturou:</span><span class="sxs-lookup"><span data-stu-id="503ea-172">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="503ea-173">Tady je několik příkladů, které můžete spustit:</span><span class="sxs-lookup"><span data-stu-id="503ea-173">Here are some examples you can run:</span></span>

     - <span data-ttu-id="503ea-174">**[Microsoft. spark. Examples. SQL. batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="503ea-174">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="503ea-175">**[Microsoft. spark. Examples. SQL. Streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="503ea-175">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="503ea-176">**[Microsoft. spark. Examples. SQL. Streaming. StructuredKafkaWordCount (přístup k Maven)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="503ea-176">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="503ea-177">**[Microsoft. spark. Examples. SQL. Streamed. StructuredKafkaWordCount (poskytnutý jar)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="503ea-177">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
