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
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="c4eec-103">Ladění aplikace .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c4eec-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="c4eec-104">Tento postup poskytuje kroky pro ladění rozhraní .NET pro Apache Spark aplikaci v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c4eec-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a><span data-ttu-id="c4eec-105">Ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="c4eec-105">Debug your application</span></span>

<span data-ttu-id="c4eec-106">Otevřete nové okno příkazového řádku a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c4eec-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="c4eec-107">Po spuštění příkazu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c4eec-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="c4eec-108">V režimu ladění DotnetRunner nespustí aplikaci .NET, ale místo toho čeká na spuštění aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="c4eec-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="c4eec-109">Nechte okno příkazového řádku otevřené a spusťte aplikaci .NET prostřednictvím ladicího programu C# k ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4eec-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="c4eec-110">Spusťte aplikaci .NET pomocí ladicího programu jazyka C# (ladicí program sady[Visual Studio pro Windows/MacOS](https://visualstudio.microsoft.com/vs/) nebo [C# Debugger v Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)), chcete-li ladit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c4eec-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="c4eec-111">Ladění uživatelsky definované funkce (UDF)</span><span class="sxs-lookup"><span data-stu-id="c4eec-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="c4eec-112">Uživatelsky definované funkce jsou podporovány pouze ve Windows pomocí ladicího programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4eec-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="c4eec-113">Před spuštěním `spark-submit` nastavte následující proměnnou prostředí:</span><span class="sxs-lookup"><span data-stu-id="c4eec-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="c4eec-114">Když spouštíte aplikaci Spark, `Choose Just-In-Time Debugger` okno se automaticky otevře.</span><span class="sxs-lookup"><span data-stu-id="c4eec-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="c4eec-115">Vyberte ladicí program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4eec-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="c4eec-116">Ladicí program se přeruší v následujícím umístění v [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span><span class="sxs-lookup"><span data-stu-id="c4eec-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="c4eec-117">Přejděte k souboru *. cs* obsahujícímu systém souborů UDF, který chcete ladit, a [Nastavte zarážku](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="c4eec-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="c4eec-118">Zarážka znamená, že `The breakpoint will not currently be hit` pracovní proces ještě nenačte sestavení, které obsahuje UDF.</span><span class="sxs-lookup"><span data-stu-id="c4eec-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="c4eec-119">`F5`Přivedete se k pokračování aplikace a nakonec zarážka bude k dispozice.</span><span class="sxs-lookup"><span data-stu-id="c4eec-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="c4eec-120">Pro každý úkol se zobrazí okno zvolit ladicí program za běhu.</span><span class="sxs-lookup"><span data-stu-id="c4eec-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="c4eec-121">Aby nedocházelo k nadměrným překryvům, nastavte počet prováděcích modulů na nízké číslo.</span><span class="sxs-lookup"><span data-stu-id="c4eec-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="c4eec-122">Například můžete použít **místní možnost--Master [1]** pro Spark-Submit k nastavení počtu úkolů na 1, což spustí jednu instanci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="c4eec-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="c4eec-123">Ladění kódu Scala</span><span class="sxs-lookup"><span data-stu-id="c4eec-123">Debug Scala code</span></span>

<span data-ttu-id="c4eec-124">Pokud potřebujete ladit Scala kód ( `DotnetRunner` , `DotnetBackendHandler` atd.), můžete použít následující příkaz a připojit ladicí program k běžícímu procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span><span class="sxs-lookup"><span data-stu-id="c4eec-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="c4eec-125">Po spuštění příkazu připojte ladicí program k běžícímu procesu pomocí [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="c4eec-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c4eec-126">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c4eec-126">Next steps</span></span>

* [<span data-ttu-id="c4eec-127">Začínáme s .NET pro Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c4eec-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="c4eec-128">Nasazení aplikace .NET pro Apache Spark do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="c4eec-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="c4eec-129">Nasazení rozhraní .NET pro Apache Spark aplikaci do datacihlů</span><span class="sxs-lookup"><span data-stu-id="c4eec-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="c4eec-130">Nasazení .NET pro Apache Spark aplikaci do Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="c4eec-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
