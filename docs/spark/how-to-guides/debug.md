---
title: Ladění rozhraní .NET pro aplikaci Apache Spark v systému Windows
description: Přečtěte si, jak ladit rozhraní .NET pro aplikaci Apache Spark ve Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dac6aed1f7faba7f07b722a6dac0da930ab9ec66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185812"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Ladění rozhraní .NET pro aplikaci Apache Spark

Tento návod poskytuje postup ladění aplikace .NET pro Apache Spark v systému Windows.

## <a name="debug-your-application"></a>Ladění aplikace

Otevřete nové okno příkazového řádku a spusťte následující příkaz:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Při spuštění příkazu se zobrazí následující výstup:

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

V režimu ladění DotnetRunner nespustí aplikaci .NET, ale místo toho čeká na spuštění aplikace .NET. Ponechejte toto okno příkazového řádku otevřené a spusťte aplikaci .NET prostřednictvím ladicího programu jazyka C#, chcete-li ladit aplikaci. Spusťte aplikaci .NET s ladicím programem Jazyka C#[(Ladicí program visual studia pro Windows/macOS](https://visualstudio.microsoft.com/vs/) nebo [Rozšíření debuggeru jazyka C# v kódu sady Visual Studio)](https://code.visualstudio.com/Docs/editor/debugging)pro ladění aplikace.

## <a name="debug-a-user-defined-function-udf"></a>Ladění uživatelem definované funkce (UDF)

> [!NOTE]
> Uživatelem definované funkce jsou podporovány pouze v systému Windows s ladicím programem sady Visual Studio.

Před `spark-submit`spuštěním nastavte následující proměnnou prostředí:

```bat
set DOTNET_WORKER_DEBUG=1
```

Když spustíte aplikaci `Choose Just-In-Time Debugger` Spark, objeví se okno. Zvolte ladicí program sady Visual Studio.

Ladicí program se přeruší na následujícím místě v [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Přejděte do souboru *CS* obsahujícího formát UDF, který chcete ladit, a [nastavte zarážku](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). Zarážka `The breakpoint will not currently be hit` bude uvedeno, protože pracovník ještě nenačetl sestavení, které obsahuje UDF.

Hit `F5` pokračovat ve vaší aplikaci a zarážka bude nakonec přístupů.

> [!NOTE]
> Pro každý úkol se zobrazí okno Zvolit debugger v čase. Chcete-li se vyhnout nadměrnému vyskakovacím líacím, nastavte počet vykonavatelů na nízké číslo. Můžete například použít volbu **--master local[1]** pro spark-submit a nastavit počet úkolů na 1, který spustí jednu instanci ladicího programu.

## <a name="debug-scala-code"></a>Ladění kódu Scala

Pokud potřebujete ladit kód na straně Scala (`DotnetRunner`, `DotnetBackendHandler`, atd.), můžete použít následující příkaz a připojit ladicí program ke spuštěnému procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Po spuštění příkazu připojte ladicí program ke spuštěnému procesu pomocí [programu Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Další kroky

* [Začínáme s rozhraním .NET pro Apache Spark](../tutorials/get-started.md)
* [Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks](../tutorials/databricks-deployment.md)
* [Nasazení rozhraní .NET pro aplikaci Apache Spark do amazonského EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
