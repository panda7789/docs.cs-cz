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
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Přečtěte si, jak vytvořit rozhraní .NET pro aplikaci Apache Spark ve Windows

Tento článek vás naučí, jak vytvořit rozhraní .NET pro aplikace Apache Spark v systému Windows.

## <a name="prerequisites"></a>Požadavky

Pokud již máte všechny následující požadavky, přejděte na kroky [sestavení.](#build)

  1. Stáhněte a nainstalujte **[sadu .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** `dotnet` - instalace sady SDK přidá řetězec nástrojů do vaší cesty. Podporují se jádra .NET 2.1, 2.2 a 3.1.
  2. Nainstalujte **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (verze 16.3 nebo novější). Verze Společenství je zcela zdarma. Při konfiguraci instalace zahrňte minimálně tyto součásti:
     * Vývoj stolních počítačů .NET
       * Všechny požadované součásti
         * Vývojové nástroje rozhraní .NET Framework 4.6.1
     * Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core
       * Všechny požadované součásti
  3. Nainstalujte **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.
     - Vyberte příslušnou verzi operačního systému. Například *jdk-8u201-windows-x64.exe* pro windows x64 počítač.
     - Nainstalujte pomocí instalačního programu a `java` ověřte, zda je možné spustit z příkazového řádku.
  4. Nainstalujte **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.
     - Stažení [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Extrahovat do místního adresáře. Například *C:\bin\apache-maven-3.6.0\*.
     - Přidejte Apache Maven do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml). Například *C:\bin\apache-maven-3.6.0\bin*.
     - Ověřte, zda `mvn` je možné spustit z příkazového řádku.
  5. Nainstalujte **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.
     - Stáhněte si [Apache Spark 2.3+](https://spark.apache.org/downloads.html) a extrahujte ji do místní složky (například *C:\bin\spark-2.3.2-bin-hadoop2.7)\*pomocí [7-zip](https://www.7-zip.org/). (Podporované verze jiskry jsou 2.3.*, 2.4.0, 2.4.1, 2.4.3 a 2.4.4)
     - Přidejte [novou proměnnou](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`prostředí . Například *C:\bin\spark-2.3.2-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - Přidejte Apache Spark do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml). Například *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Ověřte, zda `spark-shell` je možné spustit z příkazového řádku.
        Ukázkový výstup konzoly:

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

  6. Nainstalujte **[program WinUtils](https://github.com/steveloughran/winutils)**.
     - Stáhnout `winutils.exe` binární soubor z [úložiště WinUtils](https://github.com/steveloughran/winutils). Měli byste vybrat verzi Hadoopu, se kterou byla zkompilován distribuce Spark. Pro zkoušku použijte hadoop-2.7.1 pro Spark 2.3.2.
     - Uložte `winutils.exe` binární soubor do adresáře podle vašeho výběru. Například *C:\hadoop\bin*.
     - Nastavte `HADOOP_HOME` tak, aby odrážel adresář s winutils.exe (bez přihrádky). Například pomocí příkazového řádku:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Nastavte proměnnou prostředí `%HADOOP_HOME%\bin`PATH tak, aby zahrnovala . Například pomocí příkazového řádku:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Před přechodem do `dotnet`další `java` `mvn`části `spark-shell` se ujistěte, že je možné spustit příkazový řádek . Cítíš, že existuje lepší způsob? [Otevřete problém](https://github.com/dotnet/spark/issues) a neváhejte přispět.

> [!NOTE]
> Pokud byly aktualizovány všechny proměnné prostředí, může být vyžadována nová instance příkazového řádku.

## <a name="build"></a>Sestavení

Pro zbytek této příručky budete muset mít klonované .NET pro Apache Spark úložiště do počítače. Můžete zvolit libovolné umístění pro klonované úložiště. Například *C:\github\dotnet-spark\*.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Sestavení vrstvy rozšíření .NET pro Apache Spark Scala

Když odešlete .NET aplikaci, .NET pro Apache Spark má potřebnou logiku napsanou v Scala, která informuje Apache Spark, jak zpracovat vaše požadavky (například žádost o vytvoření nové spark session, žádost o přenos dat ze strany .NET na stranu JVM atd.). Tuto logiku naleznete v [rozhraní .NET pro zdrojový kód Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).

Bez ohledu na to, zda používáte rozhraní .NET Framework nebo .NET Core, budete muset vytvořit přípojnou vrstvu .NET pro Apache Spark Scala:

```powershell
cd src\scala
mvn clean package
```

Měli byste vidět JARs vytvořené pro podporované verze Spark:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Vytvoření rozhraní .NET pro ukázkové aplikace Spark

Tato část vysvětluje, jak vytvořit [ukázkové aplikace](https://github.com/dotnet/spark/tree/master/examples) pro rozhraní .NET pro Apache Spark. Tyto kroky vám pomohou pochopit celkový proces vytváření pro všechny .NET pro aplikaci Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Použití sady Visual Studio pro rozhraní .NET Framework

  1. Otevřete `src\csharp\Microsoft.Spark.sln` v sadě `Microsoft.Spark.CSharp.Examples` Visual Studio `examples` a vytvořte projekt pod složkou (to bude zase sestavení projektu vazby .NET také). Pokud chcete, můžete do `Microsoft.Spark.Examples` projektu napsat vlastní kód ("input_file.json" v tomto příkladu je soubor json s daty, která chcete vytvořit datový rámec):
  
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

     Jakmile je sestavení úspěšné, zobrazí se příslušné binární soubory vytvořené ve výstupním adresáři.
     Ukázkový výstup konzoly:

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

#### <a name="using-net-core-cli-for-net-core"></a>Použití rozhraní CLI jádra rozhraní .NET pro jádro rozhraní .NET

> [!NOTE]
> V současné době pracujeme na automatizaci sestavení .NET Core pro Spark .NET. Do té doby oceňujeme vaši trpělivost při provádění některých kroků ručně.

  1. Sestavte pracovníka:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Ukázkový výstup konzoly:

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

  2. Sestavte ukázky:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Ukázkový výstup konzoly:

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

## <a name="run-the-net-for-spark-sample-applications"></a>Spuštění rozhraní .NET pro ukázkové aplikace Spark

Po sestavení ukázky, jejich spuštění `spark-submit` bude prostřednictvím bez ohledu na to, zda se zaměřujete na rozhraní .NET Framework nebo .NET Core. Ujistěte se, že jste postupovali [podle požadavků](#prerequisites) a nainstalovali Apache Spark.

  1. Nastavte `DOTNET_WORKER_DIR` proměnnou prostředí `PATH` or tak, `Microsoft.Spark.Worker` aby zahrnovala cestu, kde byl binární soubor vygenerován (například *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Otevřete Powershell a přejděte do adresáře, kde byla vygenerována vaše binární sada aplikace (například *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. Spuštění aplikace se řídí základní strukturou:

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Zde je několik příkladů, které můžete spustit:

     - **[Microsoft.Spark.Examples.sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven přístupné)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (sklenice k dispozici)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
