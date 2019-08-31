---
title: Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows
description: Naučte se ladit rozhraní .NET pro Apache Spark aplikace ve Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dcaca96f6eb871c15a37adc18190b073c63c8e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206141"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Ladění aplikace .NET pro Apache Spark

Tento postup poskytuje příkazy, které je třeba spustit, chcete-li ladit rozhraní .NET pro Apache Spark Scala a kód aplikace v systému Windows.

## <a name="debug-your-application"></a>Ladění aplikace

Otevřete nové okno příkazového řádku, spusťte následující příkaz:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Po spuštění příkazu se zobrazí následující výstup:

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

V tomto režimu `DotnetRunner` ladění aplikace nespustí aplikaci .NET, ale čeká na připojení. Nechte okno příkazového řádku otevřené.

Nyní můžete spustit aplikaci .NET pomocí libovolného ladicího programu pro ladění aplikace.

## <a name="debug-scala-code"></a>Ladění kódu Scala

Pokud potřebujete ladit kód na straně Scala, například `DotnetRunner` nebo `DotnetBackendHandler`, spusťte následující příkaz:

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Po spuštění příkazu připojte ladicí program k běžícímu procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Další postup

* [Začínáme s .NET pro Apache Spark](../tutorials/get-started.md)
* [Nasazení aplikace .NET pro Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů](../tutorials/databricks-deployment.md)
* [Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
