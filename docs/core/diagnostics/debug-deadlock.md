---
title: Ladění zablokování – .NET Core
description: Kurz, který vás provede laděním problému se zámkem v .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 6f060e1ae801eb4eacbbd1fb67110f827c37f597
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557877"
---
# <a name="debug-a-deadlock-in-net-core"></a><span data-ttu-id="02e42-103">Ladění zablokování v .NET Core</span><span class="sxs-lookup"><span data-stu-id="02e42-103">Debug a deadlock in .NET Core</span></span>

<span data-ttu-id="02e42-104">**Tento článek se týká: ✔️** .net Core 3,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="02e42-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="02e42-105">V tomto kurzu se naučíte ladit scénář vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="02e42-105">In this tutorial, you'll learn how to debug a deadlock scenario.</span></span> <span data-ttu-id="02e42-106">Pomocí poskytnutého příkladu ASP.NET Core úložiště zdrojového kódu [webové aplikace](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) můžete způsobit úmyslné zablokování.</span><span class="sxs-lookup"><span data-stu-id="02e42-106">Using the provided example [ASP.NET Core web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="02e42-107">Koncový bod se bude nacházet v zablokování a akumulaci vláken.</span><span class="sxs-lookup"><span data-stu-id="02e42-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="02e42-108">Naučíte se, jak můžete pomocí různých nástrojů analyzovat problém, jako jsou základní výpisy paměti, analýza výpisu jádra a trasování procesů.</span><span class="sxs-lookup"><span data-stu-id="02e42-108">You'll learn how you can use various tools to analyze the problem, such as core dumps, core dump analysis, and process tracing.</span></span>

<span data-ttu-id="02e42-109">V tomto kurzu provedete následující:</span><span class="sxs-lookup"><span data-stu-id="02e42-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="02e42-110">Prozkoumat zablokování aplikace</span><span class="sxs-lookup"><span data-stu-id="02e42-110">Investigate an app hang</span></span>
> - <span data-ttu-id="02e42-111">Vygenerovat základní soubor výpisu</span><span class="sxs-lookup"><span data-stu-id="02e42-111">Generate a core dump file</span></span>
> - <span data-ttu-id="02e42-112">Analyzovat vlákna procesů v souboru s výpisem paměti</span><span class="sxs-lookup"><span data-stu-id="02e42-112">Analyze process threads in the dump file</span></span>
> - <span data-ttu-id="02e42-113">Analýza zásobníky volání a synchronizačních bloků</span><span class="sxs-lookup"><span data-stu-id="02e42-113">Analyze callstacks and sync blocks</span></span>
> - <span data-ttu-id="02e42-114">Diagnostika a řešení zablokování</span><span class="sxs-lookup"><span data-stu-id="02e42-114">Diagnose and solve a deadlock</span></span>

## <a name="prerequisites"></a><span data-ttu-id="02e42-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02e42-115">Prerequisites</span></span>

<span data-ttu-id="02e42-116">V tomto kurzu se používá:</span><span class="sxs-lookup"><span data-stu-id="02e42-116">The tutorial uses:</span></span>

- <span data-ttu-id="02e42-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="02e42-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version</span></span>
- <span data-ttu-id="02e42-118">[Ukázka cíle ladění – webová aplikace](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pro aktivaci scénáře</span><span class="sxs-lookup"><span data-stu-id="02e42-118">[Sample debug target - web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario</span></span>
- <span data-ttu-id="02e42-119">[dotnet – trasování](dotnet-trace.md) pro výpis procesů</span><span class="sxs-lookup"><span data-stu-id="02e42-119">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="02e42-120">[dotnet – výpis](dotnet-dump.md) pro shromažďování a analýzu souboru s výpisem paměti</span><span class="sxs-lookup"><span data-stu-id="02e42-120">[dotnet-dump](dotnet-dump.md) to collect, and analyze a dump file</span></span>

## <a name="core-dump-generation"></a><span data-ttu-id="02e42-121">Generování základního výpisu paměti</span><span class="sxs-lookup"><span data-stu-id="02e42-121">Core dump generation</span></span>

<span data-ttu-id="02e42-122">Chcete-li prozkoumat neodezvu aplikace, základní Výpis paměti nebo výpis paměti vám umožní zkontrolovat stav svých vláken a všechny možné zámky, které mohou mít problémy s kolizí.</span><span class="sxs-lookup"><span data-stu-id="02e42-122">To investigate application unresponsiveness, a core dump or memory dump allows you to inspect the state of its threads and any possible locks that may have contention issues.</span></span> <span data-ttu-id="02e42-123">Spusťte [ukázkovou aplikaci ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pomocí následujícího příkazu z ukázkového kořenového adresáře:</span><span class="sxs-lookup"><span data-stu-id="02e42-123">Run the [sample debug](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) application using the following command from the sample root directory:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="02e42-124">ID procesu zjistíte pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="02e42-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="02e42-125">Poznamenejte si ID procesu z výstupu příkazu.</span><span class="sxs-lookup"><span data-stu-id="02e42-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="02e42-126">Naše ID procesu bylo `4807` , ale bude se lišit.</span><span class="sxs-lookup"><span data-stu-id="02e42-126">Our process ID was `4807`, but yours will be different.</span></span> <span data-ttu-id="02e42-127">Přejděte na následující adresu URL, která je koncovým bodem rozhraní API na ukázkovém webu:</span><span class="sxs-lookup"><span data-stu-id="02e42-127">Navigate to the following URL, which is an API endpoint on the sample site:</span></span>

`https://localhost:5001/api/diagscenario/deadlock`

<span data-ttu-id="02e42-128">Požadavek rozhraní API na web přestane reagovat a nebude reagovat.</span><span class="sxs-lookup"><span data-stu-id="02e42-128">The API request to the site will hang and not respond.</span></span> <span data-ttu-id="02e42-129">Nechte žádost běžet asi 10-15 sekund.</span><span class="sxs-lookup"><span data-stu-id="02e42-129">Let the request run for about 10-15 seconds.</span></span> <span data-ttu-id="02e42-130">Pak vytvořte základní Výpis pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="02e42-130">Then create the core dump using the following command:</span></span>

### <a name="linux"></a>[<span data-ttu-id="02e42-131">Linux</span><span class="sxs-lookup"><span data-stu-id="02e42-131">Linux</span></span>](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[<span data-ttu-id="02e42-132">Windows</span><span class="sxs-lookup"><span data-stu-id="02e42-132">Windows</span></span>](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a><span data-ttu-id="02e42-133">Analyzovat základní Výpis paměti</span><span class="sxs-lookup"><span data-stu-id="02e42-133">Analyze the core dump</span></span>

<span data-ttu-id="02e42-134">Pokud chcete spustit základní analýzu výpisu paměti, otevřete základní Výpis pomocí následujícího `dotnet-dump analyze` příkazu.</span><span class="sxs-lookup"><span data-stu-id="02e42-134">To start the core dump analysis, open the core dump using the following `dotnet-dump analyze` command.</span></span> <span data-ttu-id="02e42-135">Argument je cesta k základnímu souboru výpisu, který byl shromážděn dříve.</span><span class="sxs-lookup"><span data-stu-id="02e42-135">The argument is the path to the core dump file that was collected earlier.</span></span>

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

<span data-ttu-id="02e42-136">Vzhledem k tomu, že se vám podíváte na možné zablokování, budete chtít, aby aktivita vlákna byla v procesu celkově nedodržena.</span><span class="sxs-lookup"><span data-stu-id="02e42-136">Since you're looking at a potential hang, you want an overall feel for the thread activity in the process.</span></span> <span data-ttu-id="02e42-137">Můžete použít `threads` příkaz, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="02e42-137">You can use the `threads` command as shown below:</span></span>

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

<span data-ttu-id="02e42-138">Výstup zobrazuje všechna vlákna aktuálně spuštěná v procesu s jejich přidruženým ID vlákna ladicího programu a ID vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="02e42-138">The output shows all the threads currently running in the process with their associated debugger thread ID and operating system thread ID.</span></span> <span data-ttu-id="02e42-139">Na základě výstupu existuje více než 300 vláken.</span><span class="sxs-lookup"><span data-stu-id="02e42-139">Based on the output, there are over 300 threads.</span></span>

<span data-ttu-id="02e42-140">Dalším krokem je získat lepší informace o tom, co vlákna právě dělají, díky tomu, že se zásobník volání každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="02e42-140">The next step is to get a better understanding of what the threads are currently doing by getting each thread's callstack.</span></span> <span data-ttu-id="02e42-141">`clrstack`Příkaz lze použít k výstupu zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="02e42-141">The `clrstack` command can be used to output callstacks.</span></span> <span data-ttu-id="02e42-142">Může to být buď výstup jednoho zásobník volání, nebo všechny zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="02e42-142">It can either output a single callstack or all the callstacks.</span></span> <span data-ttu-id="02e42-143">Použijte následující příkaz pro výstup všech zásobníky volání pro všechna vlákna v procesu:</span><span class="sxs-lookup"><span data-stu-id="02e42-143">Use the following command to output all the callstacks for all the threads in the process:</span></span>

```console
clrstack -all
```

<span data-ttu-id="02e42-144">Reprezentativní část výstupu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="02e42-144">A representative portion of the output looks like:</span></span>

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

<span data-ttu-id="02e42-145">Pozorování zásobníky volání pro všechna 300 a vlákna ukazují vzor, ve kterém většina vláken sdílí společný zásobník volání:</span><span class="sxs-lookup"><span data-stu-id="02e42-145">Observing the callstacks for all 300+ threads shows a pattern where a majority of the threads share a common callstack:</span></span>

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

<span data-ttu-id="02e42-146">Zásobník volání se zdá, že žádost byla doručena do naší metody zablokování, která zase provádí volání `Monitor.ReliableEnter` .</span><span class="sxs-lookup"><span data-stu-id="02e42-146">The callstack seems to show that the request arrived in our deadlock method that in turn makes a call to `Monitor.ReliableEnter`.</span></span> <span data-ttu-id="02e42-147">Tato metoda označuje, že se vlákna pokoušejí zadat zámek monitoru.</span><span class="sxs-lookup"><span data-stu-id="02e42-147">This method indicates that the threads are trying to enter a monitor lock.</span></span> <span data-ttu-id="02e42-148">Čekají na dostupnost zámku.</span><span class="sxs-lookup"><span data-stu-id="02e42-148">They're waiting on the availability of the lock.</span></span> <span data-ttu-id="02e42-149">Je nejspíš uzamčeno jiným vláknem.</span><span class="sxs-lookup"><span data-stu-id="02e42-149">It's likely locked by a different thread.</span></span>

<span data-ttu-id="02e42-150">V dalším kroku se dozvíte, které vlákno ve skutečnosti udržuje zámek monitorování.</span><span class="sxs-lookup"><span data-stu-id="02e42-150">The next step then is to find out which thread is actually holding the monitor lock.</span></span> <span data-ttu-id="02e42-151">Vzhledem k tomu, že monitory obvykle ukládají informace o uzamčení v tabulce blokování synchronizace, můžeme pomocí `syncblk` příkazu získat další informace:</span><span class="sxs-lookup"><span data-stu-id="02e42-151">Since monitors typically store lock information in the sync block table, we can use the `syncblk` command to get more information:</span></span>

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

<span data-ttu-id="02e42-152">Dva zajímavé sloupce jsou **MonitorHeld** a **vlastnící informace o vláknech**.</span><span class="sxs-lookup"><span data-stu-id="02e42-152">The two interesting columns are **MonitorHeld** and **Owning Thread Info**.</span></span> <span data-ttu-id="02e42-153">Sloupec **MonitorHeld** ukazuje, zda je v rámci vlákna získán zámek monitoru a počet čekajících vláken.</span><span class="sxs-lookup"><span data-stu-id="02e42-153">The **MonitorHeld** column shows whether a monitor lock is acquired by a thread and the number of waiting threads.</span></span> <span data-ttu-id="02e42-154">Sloupec **informace o vlastnícím vlákně** zobrazuje, které vlákno aktuálně vlastní zámek monitoru.</span><span class="sxs-lookup"><span data-stu-id="02e42-154">The **Owning Thread Info** column shows which thread currently owns the monitor lock.</span></span> <span data-ttu-id="02e42-155">Informace o vlákně mají tři různé podsloupce.</span><span class="sxs-lookup"><span data-stu-id="02e42-155">The thread info has three different subcolumns.</span></span> <span data-ttu-id="02e42-156">Druhý Podsloupec zobrazuje ID vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="02e42-156">The second subcolumn shows operating system thread ID.</span></span>

<span data-ttu-id="02e42-157">V tuto chvíli ví, že dvě různá vlákna (0x5634 a 0x51d4) obsahují zámek monitoru.</span><span class="sxs-lookup"><span data-stu-id="02e42-157">At this point, we know two different threads (0x5634 and 0x51d4) hold a monitor lock.</span></span> <span data-ttu-id="02e42-158">V dalším kroku se podíváme na to, co dělají vlákna.</span><span class="sxs-lookup"><span data-stu-id="02e42-158">The next step is to take a look at what those threads are doing.</span></span> <span data-ttu-id="02e42-159">Musíme ověřit, jestli jsou zablokované bez omezení, aby se zámky držely.</span><span class="sxs-lookup"><span data-stu-id="02e42-159">We need to check if they're stuck indefinitely holding the lock.</span></span> <span data-ttu-id="02e42-160">Pojďme použít `setthread` `clrstack` příkazy a k přepnutí na každé vlákno a zobrazení zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="02e42-160">Let's use the `setthread` and `clrstack` commands to switch to each of the threads and display the callstacks.</span></span>

<span data-ttu-id="02e42-161">Chcete-li se podívat na první vlákno, spusťte `setthread` příkaz a vyhledejte index vlákna 0x5634 (náš index byl 28).</span><span class="sxs-lookup"><span data-stu-id="02e42-161">To look at the first thread, run the `setthread` command, and find the index of the 0x5634 thread (our index was 28).</span></span> <span data-ttu-id="02e42-162">Funkce zablokování čeká na získání zámku, ale zámek již vlastní.</span><span class="sxs-lookup"><span data-stu-id="02e42-162">The deadlock function is waiting to acquire a lock, but it already owns the lock.</span></span> <span data-ttu-id="02e42-163">Je v zablokování čeká na zámek, který už drží.</span><span class="sxs-lookup"><span data-stu-id="02e42-163">It's in deadlock waiting for the lock it already holds.</span></span>

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

<span data-ttu-id="02e42-164">Druhý podproces je podobný.</span><span class="sxs-lookup"><span data-stu-id="02e42-164">The second thread is similar.</span></span> <span data-ttu-id="02e42-165">Také se pokouší získat zámek, který již vlastní.</span><span class="sxs-lookup"><span data-stu-id="02e42-165">It's also trying to acquire a lock that it already owns.</span></span> <span data-ttu-id="02e42-166">Zbývající 300 a vlákna, které jsou všechny, čekají pravděpodobně na jeden z zámků, které způsobily zablokování.</span><span class="sxs-lookup"><span data-stu-id="02e42-166">The remaining 300+ threads that are all waiting are most likely also waiting on one of the locks that caused the deadlock.</span></span>

## <a name="see-also"></a><span data-ttu-id="02e42-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="02e42-167">See also</span></span>

- <span data-ttu-id="02e42-168">[dotnet – trasování](dotnet-trace.md) pro výpis procesů</span><span class="sxs-lookup"><span data-stu-id="02e42-168">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="02e42-169">[dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti</span><span class="sxs-lookup"><span data-stu-id="02e42-169">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="02e42-170">[dotnet – vystavení](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti</span><span class="sxs-lookup"><span data-stu-id="02e42-170">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="02e42-171">dotnet/Diagnostika</span><span class="sxs-lookup"><span data-stu-id="02e42-171">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="02e42-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="02e42-172">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02e42-173">Jaké diagnostické nástroje jsou k dispozici v .NET Core</span><span class="sxs-lookup"><span data-stu-id="02e42-173">What diagnostic tools are available in .NET Core</span></span>](index.md)
