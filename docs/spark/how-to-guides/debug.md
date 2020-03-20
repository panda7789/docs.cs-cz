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
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="f570f-103">Ladění rozhraní .NET pro aplikaci Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f570f-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="f570f-104">Tento návod poskytuje postup ladění aplikace .NET pro Apache Spark v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f570f-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="f570f-105">Ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="f570f-105">Debug your application</span></span>

<span data-ttu-id="f570f-106">Otevřete nové okno příkazového řádku a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f570f-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="f570f-107">Při spuštění příkazu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f570f-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="f570f-108">V režimu ladění DotnetRunner nespustí aplikaci .NET, ale místo toho čeká na spuštění aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="f570f-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="f570f-109">Ponechejte toto okno příkazového řádku otevřené a spusťte aplikaci .NET prostřednictvím ladicího programu jazyka C#, chcete-li ladit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f570f-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="f570f-110">Spusťte aplikaci .NET s ladicím programem Jazyka C#[(Ladicí program visual studia pro Windows/macOS](https://visualstudio.microsoft.com/vs/) nebo [Rozšíření debuggeru jazyka C# v kódu sady Visual Studio)](https://code.visualstudio.com/Docs/editor/debugging)pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f570f-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="f570f-111">Ladění uživatelem definované funkce (UDF)</span><span class="sxs-lookup"><span data-stu-id="f570f-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="f570f-112">Uživatelem definované funkce jsou podporovány pouze v systému Windows s ladicím programem sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f570f-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="f570f-113">Před `spark-submit`spuštěním nastavte následující proměnnou prostředí:</span><span class="sxs-lookup"><span data-stu-id="f570f-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="f570f-114">Když spustíte aplikaci `Choose Just-In-Time Debugger` Spark, objeví se okno.</span><span class="sxs-lookup"><span data-stu-id="f570f-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="f570f-115">Zvolte ladicí program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f570f-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="f570f-116">Ladicí program se přeruší na následujícím místě v [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span><span class="sxs-lookup"><span data-stu-id="f570f-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="f570f-117">Přejděte do souboru *CS* obsahujícího formát UDF, který chcete ladit, a [nastavte zarážku](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="f570f-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="f570f-118">Zarážka `The breakpoint will not currently be hit` bude uvedeno, protože pracovník ještě nenačetl sestavení, které obsahuje UDF.</span><span class="sxs-lookup"><span data-stu-id="f570f-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="f570f-119">Hit `F5` pokračovat ve vaší aplikaci a zarážka bude nakonec přístupů.</span><span class="sxs-lookup"><span data-stu-id="f570f-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="f570f-120">Pro každý úkol se zobrazí okno Zvolit debugger v čase.</span><span class="sxs-lookup"><span data-stu-id="f570f-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="f570f-121">Chcete-li se vyhnout nadměrnému vyskakovacím líacím, nastavte počet vykonavatelů na nízké číslo.</span><span class="sxs-lookup"><span data-stu-id="f570f-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="f570f-122">Můžete například použít volbu **--master local[1]** pro spark-submit a nastavit počet úkolů na 1, který spustí jednu instanci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f570f-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="f570f-123">Ladění kódu Scala</span><span class="sxs-lookup"><span data-stu-id="f570f-123">Debug Scala code</span></span>

<span data-ttu-id="f570f-124">Pokud potřebujete ladit kód na straně Scala (`DotnetRunner`, `DotnetBackendHandler`, atd.), můžete použít následující příkaz a připojit ladicí program ke spuštěnému procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span><span class="sxs-lookup"><span data-stu-id="f570f-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="f570f-125">Po spuštění příkazu připojte ladicí program ke spuštěnému procesu pomocí [programu Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="f570f-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f570f-126">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f570f-126">Next steps</span></span>

* [<span data-ttu-id="f570f-127">Začínáme s rozhraním .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f570f-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="f570f-128">Nasazení rozhraní .NET pro aplikaci Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="f570f-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="f570f-129">Nasazení rozhraní .NET pro aplikaci Apache Spark do databricks</span><span class="sxs-lookup"><span data-stu-id="f570f-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="f570f-130">Nasazení rozhraní .NET pro aplikaci Apache Spark do amazonského EMR Spark</span><span class="sxs-lookup"><span data-stu-id="f570f-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
