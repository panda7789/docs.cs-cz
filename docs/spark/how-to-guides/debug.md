---
title: Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows
description: Naučte se ladit rozhraní .NET pro Apache Spark aplikace ve Windows.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 9209d5bdec6dd85f6d21a502fb07204effef1934
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617753"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Ladění aplikace .NET pro Apache Spark

Tento postup poskytuje kroky pro ladění rozhraní .NET pro Apache Spark aplikaci v systému Windows.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a>Ladění aplikace

Otevřete nové okno příkazového řádku a spusťte následující příkaz:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Po spuštění příkazu se zobrazí následující výstup:

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

V režimu ladění DotnetRunner nespustí aplikaci .NET, ale místo toho čeká na spuštění aplikace .NET. Nechte okno příkazového řádku otevřené a spusťte aplikaci .NET prostřednictvím ladicího programu C# k ladění aplikace. Spusťte aplikaci .NET pomocí ladicího programu jazyka C# (ladicí program sady[Visual Studio pro Windows/MacOS](https://visualstudio.microsoft.com/vs/) nebo [C# Debugger v Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)), chcete-li ladit aplikaci.

## <a name="debug-a-user-defined-function-udf"></a>Ladění uživatelsky definované funkce (UDF)

> [!NOTE]
> Uživatelsky definované funkce jsou podporovány pouze ve Windows pomocí ladicího programu sady Visual Studio.

Před spuštěním `spark-submit` nastavte následující proměnnou prostředí:

```bat
set DOTNET_WORKER_DEBUG=1
```

Když spouštíte aplikaci Spark, `Choose Just-In-Time Debugger` okno se automaticky otevře. Vyberte ladicí program sady Visual Studio.

Ladicí program se přeruší v následujícím umístění v [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Přejděte k souboru *. cs* obsahujícímu systém souborů UDF, který chcete ladit, a [Nastavte zarážku](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). Zarážka znamená, že `The breakpoint will not currently be hit` pracovní proces ještě nenačte sestavení, které obsahuje UDF.

`F5`Přivedete se k pokračování aplikace a nakonec zarážka bude k dispozice.

> [!NOTE]
> Pro každý úkol se zobrazí okno zvolit ladicí program za běhu. Aby nedocházelo k nadměrným překryvům, nastavte počet prováděcích modulů na nízké číslo. Například můžete použít **místní možnost--Master [1]** pro Spark-Submit k nastavení počtu úkolů na 1, což spustí jednu instanci ladicího programu.

## <a name="debug-scala-code"></a>Ladění kódu Scala

Pokud potřebujete ladit Scala kód ( `DotnetRunner` , `DotnetBackendHandler` atd.), můžete použít následující příkaz a připojit ladicí program k běžícímu procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Po spuštění příkazu připojte ladicí program k běžícímu procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Další kroky

* [Začínáme s .NET pro Apache Spark](../tutorials/get-started.md)
* [Nasazení aplikace .NET pro Apache Spark do Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů](../tutorials/databricks-deployment.md)
* [Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
