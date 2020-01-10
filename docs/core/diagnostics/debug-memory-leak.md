---
title: Ladění kurzu nevracení paměti
description: Naučte se ladit nevracení paměti v .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: cb137503cbc81f5ab9438dadcf1dc1c6750a1ca8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715595"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="3f3bf-103">Kurz: ladění nevracení paměti v .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f3bf-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="3f3bf-104">**Tento článek se týká: ✓** .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="3f3bf-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="3f3bf-105">Tento kurz demonstruje nástroje pro analýzu nevracení paměti .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="3f3bf-106">V tomto kurzu se používá ukázková aplikace, která je navržená pro úmyslně nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="3f3bf-107">Ukázka je poskytována jako cvičení.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="3f3bf-108">Můžete analyzovat aplikaci, která neúmyslně nevrací paměť.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="3f3bf-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3f3bf-110">Projděte si využití spravované paměti pomocí [čítače dotnet-Counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="3f3bf-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="3f3bf-111">Vygenerujte soubor s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-111">Generate a dump file.</span></span>
> - <span data-ttu-id="3f3bf-112">Analyzujte využití paměti pomocí souboru s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f3bf-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f3bf-113">Prerequisites</span></span>

<span data-ttu-id="3f3bf-114">V tomto kurzu se používá:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-114">The tutorial uses:</span></span>

- <span data-ttu-id="3f3bf-115">[.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="3f3bf-116">[dotnet – trasování](dotnet-trace.md) pro výpis procesů</span><span class="sxs-lookup"><span data-stu-id="3f3bf-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="3f3bf-117">[dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti</span><span class="sxs-lookup"><span data-stu-id="3f3bf-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="3f3bf-118">[dotnet – vypíše stav](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="3f3bf-119">[Ukázková cílová aplikace ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) , která se má diagnostikovat</span><span class="sxs-lookup"><span data-stu-id="3f3bf-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="3f3bf-120">V tomto kurzu se předpokládá, že je nainstalovaná ukázka a nástroje, které jsou připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="3f3bf-121">Prověření využití spravované paměti</span><span class="sxs-lookup"><span data-stu-id="3f3bf-121">Examine managed memory usage</span></span>

<span data-ttu-id="3f3bf-122">Než začnete shromažďovat diagnostická data, která nám pomůžou hlavní příčinu tohoto scénáře, musíte se ujistit, že se skutečně zobrazuje nevracení paměti (nárůst paměti).</span><span class="sxs-lookup"><span data-stu-id="3f3bf-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="3f3bf-123">K potvrzení můžete použít nástroj [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="3f3bf-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="3f3bf-124">Otevřete okno konzoly a přejděte do adresáře, do kterého jste stáhli, a vraťte se do [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="3f3bf-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="3f3bf-125">Spusťte cíl:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="3f3bf-126">V samostatné konzole Najděte ID procesu pomocí nástroje [dotnet-Trace](dotnet-trace.md) Tool:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="3f3bf-127">Výstup by měl vypadat přibližně:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="3f3bf-128">Teď pomocí nástroje [dotnet-Counters](dotnet-counters.md) ověřte využití spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="3f3bf-129">`--refresh-interval` určuje počet sekund mezi aktualizacemi:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="3f3bf-130">Živý výstup by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="3f3bf-131">Zaměřit se na tento řádek:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="3f3bf-132">Můžete zjistit, že paměť spravované haldy je 4 MB, a to hned po spuštění.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="3f3bf-133">Nyní stiskněte `http://localhost:5000/api/diagscenario/memleak/20000`adresu URL.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="3f3bf-134">Pozor, aby využití paměti bylo nárůst na 30 MB.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="3f3bf-135">Sledováním využití paměti můžete bezpečně vyslovit, že se paměť zvětšuje nebo nevrací.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="3f3bf-136">Dalším krokem je shromáždění správných dat pro analýzu paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="3f3bf-137">Generovat výpis paměti</span><span class="sxs-lookup"><span data-stu-id="3f3bf-137">Generate memory dump</span></span>

<span data-ttu-id="3f3bf-138">Při analýze možné nevracení paměti potřebujete přístup k haldě paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="3f3bf-139">Pak můžete analyzovat obsah paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="3f3bf-140">Při prohlížení vztahů mezi objekty vytvoříte teorie, proč se paměť neuvolňuje.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="3f3bf-141">Běžný zdroj dat diagnostiky je výpis paměti ve Windows nebo ekvivalentní základní Výpis stavu systému Linux.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="3f3bf-142">Chcete-li vygenerovat výpis paměti aplikace .NET Core, můžete použít nástroj [dotnet-dump)](dotnet-dump.md) .</span><span class="sxs-lookup"><span data-stu-id="3f3bf-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="3f3bf-143">Pomocí dříve spuštěného [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) spusťte následující příkaz, který vygeneruje výpis jádra pro Linux:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="3f3bf-144">Výsledkem je základní Výpis paměti umístěný ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="3f3bf-145">Restartování neúspěšného procesu</span><span class="sxs-lookup"><span data-stu-id="3f3bf-145">Restart the failed process</span></span>

<span data-ttu-id="3f3bf-146">Po shromáždění výpisu paměti by měly být k dispozici dostatečné informace pro diagnostiku neúspěšného procesu.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="3f3bf-147">Pokud se neúspěšný proces na provozním serveru běží, je teď to ideální čas pro krátkodobou nápravu, protože proces se restartuje.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="3f3bf-148">V tomto kurzu jste teď hotovi s [ukázkovým cílem ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) a můžete ho zavřít.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="3f3bf-149">Přejděte do terminálu, na kterém je spuštěný Server, a stiskněte `Control-C`.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="3f3bf-150">Analyzovat základní Výpis paměti</span><span class="sxs-lookup"><span data-stu-id="3f3bf-150">Analyze the core dump</span></span>

<span data-ttu-id="3f3bf-151">Teď, když máte vygenerovaný základní Výpis, použijte nástroj [dotnet-dump)](dotnet-dump.md) k analýze výpisu:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-151">Now that you have a core dump generated, use the [dotnet-dump)](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="3f3bf-152">Kde `core_20190430_185145` je název základního výpisu, který chcete analyzovat.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="3f3bf-153">Pokud se zobrazí chyba s stížností, že se *libdl.so* nedá najít, možná budete muset nainstalovat balíček *libc6-dev* .</span><span class="sxs-lookup"><span data-stu-id="3f3bf-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="3f3bf-154">Další informace najdete v tématu [předpoklady pro .NET Core v systému Linux](../linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="3f3bf-154">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

<span data-ttu-id="3f3bf-155">Zobrazí se výzva, kde můžete zadat SOS příkazy.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="3f3bf-156">Obvykle první věc, kterou chcete sledovat, je celkový stav spravované haldy:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="3f3bf-157">Tady vidíte, že většina objektů je buď `String`, nebo `Customer` objektů.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="3f3bf-158">K získání seznamu všech instancí `String` můžete použít příkaz `dumpheap` znovu s tabulkou Method (MT):</span><span class="sxs-lookup"><span data-stu-id="3f3bf-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="3f3bf-159">Nyní můžete použít příkaz `gcroot` na instanci `System.String` a zjistit, jak a proč je objekt rootem.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="3f3bf-160">Být pacient, protože tento příkaz trvá několik minut s haldou 30 MB:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="3f3bf-161">Můžete vidět, že `String` přímo drží objekt `Customer` a nepřímo ho drží objekt `CustomerCache`.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="3f3bf-162">Můžete pokračovat v oddálení objektů, abyste viděli, že většina objektů `String` sleduje podobný vzor.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="3f3bf-163">V tomto okamžiku šetření poskytlo dostatečné informace pro identifikaci hlavní příčiny ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="3f3bf-164">Tento obecný postup vám umožní identifikovat zdroj nevracení velkých pamětí.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="3f3bf-165">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="3f3bf-165">Clean up resources</span></span>

<span data-ttu-id="3f3bf-166">V tomto kurzu jste spustili ukázkový webový server.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="3f3bf-167">Tento server by měl být vypnutý, jak je vysvětleno v části [restartování procesu selhání](#restart-the-failed-process) .</span><span class="sxs-lookup"><span data-stu-id="3f3bf-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="3f3bf-168">Můžete také odstranit soubor s výpisem paměti, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f3bf-169">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3f3bf-169">Next steps</span></span>

<span data-ttu-id="3f3bf-170">Blahopřejeme k dokončení tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="3f3bf-171">Pořád ještě probíhá publikování dalších diagnostických kurzů.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="3f3bf-172">Můžete si přečíst koncepty verze v úložišti [dotnet/Diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) .</span><span class="sxs-lookup"><span data-stu-id="3f3bf-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="3f3bf-173">Tento kurz se věnuje základům klíčových diagnostických nástrojů .NET.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="3f3bf-174">Rozšířené použití najdete v následující referenční dokumentaci:</span><span class="sxs-lookup"><span data-stu-id="3f3bf-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="3f3bf-175">[dotnet – trasování](dotnet-trace.md) pro výpis procesů</span><span class="sxs-lookup"><span data-stu-id="3f3bf-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="3f3bf-176">[dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti</span><span class="sxs-lookup"><span data-stu-id="3f3bf-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="3f3bf-177">[dotnet – vypíše stav](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="3f3bf-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
