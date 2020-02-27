---
title: Vytvoření rozhraní .NET pro Apache Spark aplikaci v systému Windows
description: Naučte se, jak sestavit rozhraní .NET pro Apache Spark aplikaci v systému Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: 640459c8c80b6d798718b89d4965802cdacd6c63
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628654"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Informace o tom, jak sestavit rozhraní .NET pro Apache Spark aplikaci v systému Windows

V tomto článku se naučíte, jak sestavit rozhraní .NET pro Apache Spark aplikace ve Windows.

## <a name="prerequisites"></a>Předpoklady

Pokud již máte všechny následující požadavky, přejděte k postupu [sestavení](#build) .

  1. Stažení a instalace **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** – instalace sady SDK přidá do vaší cesty `dotnet` sada nástrojů. Podporují se .NET Core 2,1, 2,2 a 3,1.
  2. Nainstalujte **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (verze 16,3 nebo novější). Verze komunity je zcela zadarmo. Při konfiguraci instalace zahrňte tyto komponenty minimálně:
     * Vývoj desktopových aplikací .NET
       * Všechny požadované součásti
         * Vývojové nástroje .NET Framework 4.6.1
     * Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core
       * Všechny požadované součásti
  3. Nainstalujte **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** . 
     - Vyberte odpovídající verzi pro váš operační systém. Například *JDK-8u201-Windows-x64. exe* pro počítač s Windows x64.
     - Nainstalujte pomocí instalačního programu a ověřte, že je možné spustit `java` z příkazového řádku.
  4. Nainstalujte **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .
     - Stáhněte si [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Extrahuje do místního adresáře. Například * C:\bin\apache-Maven-3.6.0\*.
     - Přidejte Apache Maven do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml). Například *C:\bin\apache-Maven-3.6.0\Bin*.
     - Ověřte, že je možné spustit `mvn` z příkazového řádku.
  5. Nainstalujte **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .
     - Stáhněte si [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) a extrahujte ji do místní složky (například *C:\bin\spark-2.3.2-bin-hadoop2.7\*) pomocí [7-zip](https://www.7-zip.org/). (Podporované verze Sparku jsou 2,3.* , 2.4.0, 2.4.1, 2.4.3 a 2.4.4)
     - Přidejte [novou proměnnou prostředí](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`. Například * C:\bin\spark-2.3.2-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - Přidejte Apache Spark do [proměnné prostředí PATH](https://www.java.com/en/download/help/path.xml). Například *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - Ověřte, že je možné spustit `spark-shell` z příkazového řádku.        
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

  6. Nainstalujte **[WinUtils](https://github.com/steveloughran/winutils)** .
     - Stažení `winutils.exe` binárního souboru z [úložiště WinUtils](https://github.com/steveloughran/winutils) Měli byste vybrat verzi Hadoop, se kterou byla distribuce Sparku zkompilována. Pro exammple použijte Hadoop-2.7.1 pro Spark 2.3.2.
     - Uložte `winutils.exe` binární soubor do adresáře podle vašeho výběru. Například *C:\hadoop\bin*.
     - Nastavte `HADOOP_HOME` tak, aby odrážel adresář pomocí winutils. exe (bez přihrádky). Například při použití příkazového řádku:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Nastavte proměnnou prostředí PATH tak, aby zahrnovala `%HADOOP_HOME%\bin`. Například pomocí příkazového řádku:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Než přejdete k další části, ujistěte se, že máte možnost spustit `dotnet`, `java`, `mvn``spark-shell` z příkazového řádku. Máte lepší možnost? [Otevřete problém](https://github.com/dotnet/spark/issues) a nebojte se přispět.

> [!NOTE]
> Je-li kterákoli z proměnných prostředí aktualizována, může být vyžadována nová instance příkazového řádku.

## <a name="build"></a>Sestavení

Ve zbývající části tohoto průvodce budete muset naklonovat rozhraní .NET pro Apache Spark úložiště do svého počítače. Můžete zvolit libovolné umístění klonovaného úložiště. Například * C:\github\dotnet-Spark\*.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Sestavit vrstvu rozšíření .NET pro Apache Spark Scala

Při odeslání aplikace .NET má rozhraní .NET pro Apache Spark potřebnou logiku napsanou v Scala, která informuje Apache Spark jak zpracovat vaše požadavky (například požádat o vytvoření nové relace Sparku, požádat o přenos dat ze strany .NET na stranu JVM atd.). Tuto logiku najdete ve [zdrojovém kódu .NET pro Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).

Bez ohledu na to, jestli používáte .NET Framework nebo .NET Core, budete muset sestavit vrstvu rozšíření .NET for Apache Spark Scala:

```powershell
cd src\scala
mvn clean package 
```

Měli byste vidět jar vytvořené pro podporované verze Sparku:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Sestavení ukázkových aplikací .NET pro Spark

V této části je vysvětlen postup sestavení [ukázkových aplikací](https://github.com/dotnet/spark/tree/master/examples) pro rozhraní .net pro Apache Spark. Tyto kroky vám pomůžou pochopit celkový proces vytváření jakékoli aplikace .NET pro Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Používání sady Visual Studio pro .NET Framework

  1. Otevřete `src\csharp\Microsoft.Spark.sln` v aplikaci Visual Studio a sestavte projekt `Microsoft.Spark.CSharp.Examples` ve složce `examples` (tím se vytvoří také projekt vazby rozhraní .NET). Pokud chcete, můžete napsat vlastní kód v projektu `Microsoft.Spark.Examples` (' input_file. JSON ' v tomto příkladu je soubor JSON s daty, se kterými chcete vytvořit datový rámec.):
  
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

     Po úspěšném sestavení se zobrazí příslušné binární soubory, které byly vytvořeny ve výstupním adresáři.     
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

#### <a name="using-net-core-cli-for-net-core"></a>Použití .NET Core CLI pro .NET Core

> [!NOTE]
> V současné době pracujeme na automatizaci sestavení .NET Core pro Spark .NET. Dokud pak nebudeme mít v provedení některých kroků k trpělivost.

  1. Sestavte pracovní proces:

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

## <a name="run-the-net-for-spark-sample-applications"></a>Spuštění ukázkových aplikací .NET pro Spark

Po sestavení vzorků se jejich spuštění bude provádět prostřednictvím `spark-submit` bez ohledu na to, jestli cílíte .NET Framework nebo .NET Core. Ujistěte se, že jste postupovali s částí [požadavky](#prerequisites) a nainstalovali Apache Spark.

  1. Nastavte proměnnou prostředí `DOTNET_WORKER_DIR` nebo `PATH` tak, aby zahrnovala cestu, kde byl vygenerován `Microsoft.Spark.Worker` binární (například *C:\github\dotnet\spark\artifacts\bin\Microsoft.spark.Worker\Debug\net461* pro .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* pro .NET Core):

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Otevřete PowerShell a vyhledejte adresář, ve kterém byl vygenerován binární soubor aplikace (například *C:\github\dotnet\spark\artifacts\bin\Microsoft.spark.CSharp.Examples\Debug\net461* pro .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* pro .NET Core):

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

     Tady je několik příkladů, které můžete spustit:

     - **[Microsoft. spark. Examples. SQL. batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft. spark. Examples. SQL. Streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft. spark. Examples. SQL. Streaming. StructuredKafkaWordCount (přístup k Maven)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft. spark. Examples. SQL. Streamed. StructuredKafkaWordCount (poskytnutý jar)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
