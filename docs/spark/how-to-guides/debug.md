---
title: Ladění rozhraní .NET pro Apache Spark aplikaci ve Windows
description: Naučte se ladit rozhraní .NET pro Apache Spark aplikace ve Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 25f5291c47dc1cdf2668cb077fae7439e330cc1c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919929"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Ladění aplikace .NET pro Apache Spark

Tento postup poskytuje kroky pro ladění rozhraní .NET pro Apache Spark aplikaci v systému Windows.

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

V režimu ladění DotnetRunner nespustí aplikaci .NET, ale místo toho čeká na spuštění aplikace .NET. Nechte okno příkazového řádku otevřené a spusťte aplikaci .NET prostřednictvím C# ladicího programu pro ladění aplikace. Spusťte aplikaci .NET pomocí C# ladicího programu ([ladicí program sady Visual Studio pro Windows/MacOS](https://visualstudio.microsoft.com/vs/) nebo [ C# rozšíření ladicího programu v Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) pro ladění aplikace.

## <a name="debug-a-user-defined-function-udf"></a>Ladění uživatelsky definované funkce (UDF)

> [!NOTE]
> Uživatelsky definované funkce jsou podporovány pouze ve Windows pomocí ladicího programu sady Visual Studio.

Před spuštěním `spark-submit`nastavte následující proměnnou prostředí:

```bat
set DOTNET_WORKER_DEBUG=1
```

Při spuštění aplikace Spark se automaticky otevře okno `Choose Just-In-Time Debugger`. Vyberte ladicí program sady Visual Studio.

Ladicí program se přeruší v následujícím umístění v [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Přejděte k souboru *. cs* obsahujícímu systém souborů UDF, který chcete ladit, a [Nastavte zarážku](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). Zarážka znamená `The breakpoint will not currently be hit`, protože pracovní proces ještě nenačítal sestavení, které obsahuje systém souborů UDF.

Stiskněte `F5`, abyste mohli pokračovat v aplikaci a nakonec se zarážka bude opakovat.

> [!NOTE] 
> Pro každý úkol se zobrazí okno zvolit ladicí program za běhu. Aby nedocházelo k nadměrným překryvům, nastavte počet prováděcích modulů na nízké číslo. Například můžete použít **místní možnost--Master [1]** pro Spark-Submit k nastavení počtu úkolů na 1, což spustí jednu instanci ladicího programu.

## <a name="debug-scala-code"></a>Ladění kódu Scala

Pokud potřebujete ladit Scala kód (`DotnetRunner`, `DotnetBackendHandler`atd.), můžete použít následující příkaz a připojit ladicí program k běžícímu procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):

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
