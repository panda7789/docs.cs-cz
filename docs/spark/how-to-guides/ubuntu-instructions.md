---
title: Sestavení aplikace .NET pro Apache Spark na Ubuntu
description: Naučte se, jak vytvořit aplikaci .NET pro Apache Spark na Ubuntu
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 6dd6f60bb89a51c47fe17182fc47de818cd00b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187575"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>Naučte se, jak vytvořit aplikaci .NET pro Apache Spark na Ubuntu

Tento článek vás naučí, jak vytvořit .NET pro aplikace Apache Spark na Ubuntu.

## <a name="prerequisites"></a>Požadavky

Pokud již máte všechny následující požadavky, přejděte na kroky [sestavení.](#build)

1. Stáhněte a nainstalujte **[sadu .NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** nebo **[sadu .NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** – instalace sady SDK přidá sadu `dotnet` nástrojů do vaší cesty.  Podporují se jádra .NET 2.1, 2.2 a 3.1.

2. Nainstalujte **[OpenJDK 8](https://openjdk.java.net/install/)**.

   - Můžete použít následující příkaz:

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * Ověřte, zda `java` je možné spustit z příkazového řádku.

      Ukázkový výstup java -version:

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * Pokud už máte nainstalované více verzí OpenJDK a chcete vybrat OpenJDK 8, použijte následující příkaz:

      ```bash
      sudo update-alternatives --config java
      ```

3. Nainstalujte **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.

   * Spusťte následující příkaz:

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       Všimněte si, že tyto proměnné prostředí budou ztraceny při zavření terminálu. Pokud chcete, aby změny byly `export` trvalé, `~/.bashrc` přidejte řádky do souboru.

   * Ověřte, zda `mvn` je možné spustit z příkazového řádku

       Ukázkový výstup mvn -version:

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. Nainstalujte **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.
Stáhněte si [Apache Spark 2.3+](https://spark.apache.org/downloads.html) a extrahujte `~/bin/spark-2.3.2-bin-hadoop2.7`ji do místní složky (např. ). (Podporované verze jiskry jsou 2.3.*, 2.4.0, 2.4.1, 2.4.3 a 2.4.4)

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * Přidejte potřebné [proměnné](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` prostředí (např. `~/bin/spark-2.3.2-bin-hadoop2.7/`) `PATH` a (např. `$SPARK_HOME/bin:$PATH`)

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      Všimněte si, že tyto proměnné prostředí budou ztraceny při zavření terminálu. Pokud chcete, aby změny byly `export` trvalé, `~/.bashrc` přidejte řádky do souboru.

   * Ověřte, zda `spark-shell` je možné spustit z příkazového řádku.

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

Před přechodem do `dotnet`další `java` `mvn`části `spark-shell` se ujistěte, že je možné spustit příkazový řádek . Cítíš, že existuje lepší způsob? Prosím, [otevřete problém](https://github.com/dotnet/spark/issues) a neváhejte přispět.

## <a name="build"></a>Sestavení

Pro zbytek této příručky budete muset naklonovat úložiště .NET pro Apache Spark do `~/dotnet.spark/`vašeho počítače např.

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>Sestavení rozhraní .NET pro vrstvu rozšíření Spark Scala

Když odešlete .NET aplikaci, .NET pro Apache Spark má potřebnou logiku napsanou v Scale, která informuje Apache Spark, jak zpracovat vaše požadavky (např. žádost o vytvoření nové Spark Session, žádost o přenos dat ze strany .NET na stranu JVM atd.). Tuto logiku lze nalézt v [.NET pro Apache Spark Scala zdrojový kód](https://github.com/dotnet/spark/tree/master/src/scala).

Dalším krokem je vytvoření přípojné vrstvy .NET pro Apache Spark Scala:

```bash
cd src/scala
mvn clean package
```

Měli byste vidět JARs vytvořené pro podporované verze Spark:

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>Vytváření ukázkových aplikací rozhraní .NET pomocí rozhraní CLI jádra .NET

Tato část vysvětluje, jak vytvořit [ukázkové aplikace](https://github.com/dotnet/spark/tree/master/examples) pro rozhraní .NET pro Apache Spark. Tyto kroky vám pomohou pochopit celkový proces vytváření pro všechny .NET pro aplikaci Spark.

1. Sestavte pracovníka:

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Ukázkový výstup konzoly:

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```

2. Sestavte ukázky:

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Ukázkový výstup konzoly:

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a>Spuštění rozhraní .NET pro ukázkové aplikace Spark

Po sestavení ukázky, můžete `spark-submit` použít k odeslání aplikace .NET Core. Ujistěte se, že jste postupovali [podle požadavků](#prerequisites) a nainstalovali Apache Spark.

1. Nastavte `DOTNET_WORKER_DIR` proměnnou prostředí nebo `PATH` tak, `Microsoft.Spark.Worker` aby zahrnovala cestu, kde `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`byl binární soubor vygenerován (např. ).

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. Otevřete terminál a přejděte do adresáře, kde byl vygenerován binární soubor aplikace (např. `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. Spuštění aplikace se řídí základní strukturou:

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   Zde je několik příkladů, které můžete spustit:

   * **[Microsoft.Spark.Examples.sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven přístupné)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (sklenice k dispozici)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
