---
title: Ladění kurzu nevracení paměti
description: Zjistěte, jak ladit nevracení paměti v .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737732"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="32567-103">Kurz: Ladění nevracení paměti v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="32567-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="32567-104">**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="32567-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="32567-105">Tento kurz ukazuje nástroje pro analýzu nevracení paměti .NET Core.</span><span class="sxs-lookup"><span data-stu-id="32567-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="32567-106">Tento kurz používá ukázkovou aplikaci, která je určena k úmyslnému úniku paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="32567-107">Vzorek je poskytován jako cvičení.</span><span class="sxs-lookup"><span data-stu-id="32567-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="32567-108">Můžete analyzovat aplikaci, která je neúmyslně nevracení paměti příliš.</span><span class="sxs-lookup"><span data-stu-id="32567-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="32567-109">V tomto kurzu provedete následující:</span><span class="sxs-lookup"><span data-stu-id="32567-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="32567-110">Zkontrolujte využití spravované paměti pomocí [čítačů dotnet](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="32567-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="32567-111">Vygenerujte soubor s výpisem stavu paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-111">Generate a dump file.</span></span>
> - <span data-ttu-id="32567-112">Analyzujte využití paměti pomocí souboru s výpisem stavu paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32567-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32567-113">Prerequisites</span></span>

<span data-ttu-id="32567-114">Kurz používá:</span><span class="sxs-lookup"><span data-stu-id="32567-114">The tutorial uses:</span></span>

- <span data-ttu-id="32567-115">[Sada .NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="32567-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="32567-116">[dotnet-trace](dotnet-trace.md) do seznamu procesů.</span><span class="sxs-lookup"><span data-stu-id="32567-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="32567-117">[dotnet-čítače](dotnet-counters.md) pro kontrolu využití spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="32567-118">[dotnet-dump](dotnet-dump.md) shromažďovat a analyzovat soubor s výpisem stavu paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="32567-119">[Ukázka ladění cílové](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) aplikace diagnostikovat.</span><span class="sxs-lookup"><span data-stu-id="32567-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="32567-120">Kurz předpokládá, že ukázka a nástroje jsou nainstalovány a připraveny k použití.</span><span class="sxs-lookup"><span data-stu-id="32567-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="32567-121">Zkontrolujte využití spravované paměti</span><span class="sxs-lookup"><span data-stu-id="32567-121">Examine managed memory usage</span></span>

<span data-ttu-id="32567-122">Než začnete shromažďovat diagnostická data, která nám pomáhají způsobit tento scénář, musíte se ujistit, že skutečně vidíte nevracení paměti (růst paměti).</span><span class="sxs-lookup"><span data-stu-id="32567-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="32567-123">Můžete použít [nástroj dotnet-čítače](dotnet-counters.md) k potvrzení.</span><span class="sxs-lookup"><span data-stu-id="32567-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="32567-124">Otevřete okno konzoly a přejděte do adresáře, do kterého jste stáhli a rozbalili [ukázkový ladicí cíl](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="32567-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="32567-125">Spusťte cíl:</span><span class="sxs-lookup"><span data-stu-id="32567-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="32567-126">Ze samostatné konzoly vyhledejte ID procesu pomocí nástroje [dotnet-trace:](dotnet-trace.md)</span><span class="sxs-lookup"><span data-stu-id="32567-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="32567-127">Výstup by měl být podobný:</span><span class="sxs-lookup"><span data-stu-id="32567-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="32567-128">Nyní zkontrolujte využití spravované paměti pomocí nástroje [dotnet-counters.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="32567-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="32567-129">Určuje `--refresh-interval` počet sekund mezi aktualizacemi:</span><span class="sxs-lookup"><span data-stu-id="32567-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="32567-130">Živý výstup by měl být podobný:</span><span class="sxs-lookup"><span data-stu-id="32567-130">The live output should be similar to:</span></span>

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

<span data-ttu-id="32567-131">Zaměření na tento řádek:</span><span class="sxs-lookup"><span data-stu-id="32567-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="32567-132">Můžete vidět, že spravované haldy paměti je 4 MB hned po spuštění.</span><span class="sxs-lookup"><span data-stu-id="32567-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="32567-133">Nyní stiskněte adresu `http://localhost:5000/api/diagscenario/memleak/20000`URL .</span><span class="sxs-lookup"><span data-stu-id="32567-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="32567-134">Všimněte si, že využití paměti se rozrostla na 30 MB.</span><span class="sxs-lookup"><span data-stu-id="32567-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="32567-135">Sledováním využití paměti, můžete bezpečně říci, že paměť roste nebo nevracení.</span><span class="sxs-lookup"><span data-stu-id="32567-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="32567-136">Dalším krokem je shromáždit správná data pro analýzu paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="32567-137">Generovat výpis stavu paměti</span><span class="sxs-lookup"><span data-stu-id="32567-137">Generate memory dump</span></span>

<span data-ttu-id="32567-138">Při analýze možných nevracení paměti potřebujete přístup k haldě paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="32567-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="32567-139">Pak můžete analyzovat obsah paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="32567-140">Při pohledu na vztahy mezi objekty vytváříte teorie o tom, proč není paměť uvolněna.</span><span class="sxs-lookup"><span data-stu-id="32567-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="32567-141">Běžný diagnostický zdroj dat je výpis stavu paměti v systému Windows nebo ekvivalentní výpis jádra v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="32567-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="32567-142">Chcete-li generovat výpis aplikace .NET Core, můžete použít nástroj [dotnet-dump).](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="32567-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="32567-143">Pomocí [dříve spuštěného ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) vygenerujte výpis jádra Linuxu následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="32567-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="32567-144">Výsledkem je výpis jádra umístěný ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="32567-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="32567-145">Restartování neúspěšného procesu</span><span class="sxs-lookup"><span data-stu-id="32567-145">Restart the failed process</span></span>

<span data-ttu-id="32567-146">Jakmile je výpis shromážděn, měli byste mít dostatek informací k diagnostice neúspěšného procesu.</span><span class="sxs-lookup"><span data-stu-id="32567-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="32567-147">Pokud je neúspěšný proces spuštěn na produkčním serveru, je nyní ideální čas pro krátkodobou nápravu restartováním procesu.</span><span class="sxs-lookup"><span data-stu-id="32567-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="32567-148">V tomto kurzu jste nyní hotovi s [cíl ladění ukázkové](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) a můžete jej zavřít.</span><span class="sxs-lookup"><span data-stu-id="32567-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="32567-149">Přejděte na terminál, který `Control-C`spustil server, a stiskněte klávesu .</span><span class="sxs-lookup"><span data-stu-id="32567-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="32567-150">Analýza výpisu jádra</span><span class="sxs-lookup"><span data-stu-id="32567-150">Analyze the core dump</span></span>

<span data-ttu-id="32567-151">Nyní, když máte generovaný výpis jádra, použijte nástroj [dotnet-dump)](dotnet-dump.md) k analýze výpisu:</span><span class="sxs-lookup"><span data-stu-id="32567-151">Now that you have a core dump generated, use the [dotnet-dump)](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="32567-152">Kde `core_20190430_185145` je název výpisu jádra, který chcete analyzovat.</span><span class="sxs-lookup"><span data-stu-id="32567-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="32567-153">Pokud se zobrazí chyba, která si stěžuje, že *libdl.so* nebyl a nebyl nalezen, bude pravděpodobně nutné nainstalovat balíček *libc6-dev.*</span><span class="sxs-lookup"><span data-stu-id="32567-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="32567-154">Další informace naleznete [v tématu Požadavky pro .NET Core na Linuxu](../linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="32567-154">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

<span data-ttu-id="32567-155">Zobrazí se výzva, kde můžete zadat příkazy SOS.</span><span class="sxs-lookup"><span data-stu-id="32567-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="32567-156">Obvykle první věc, kterou chcete podívat na je celkový stav spravované haldy:</span><span class="sxs-lookup"><span data-stu-id="32567-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

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

<span data-ttu-id="32567-157">Zde můžete vidět, že `String` většina objektů jsou buď nebo `Customer` objekty.</span><span class="sxs-lookup"><span data-stu-id="32567-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="32567-158">`dumpheap` Příkaz můžete použít znovu s tabulkou metody (MT) `String` k získání seznamu všech instancí:</span><span class="sxs-lookup"><span data-stu-id="32567-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

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

<span data-ttu-id="32567-159">Nyní můžete použít `gcroot` příkaz `System.String` na instanci vidět, jak a proč je objekt zakořeněný.</span><span class="sxs-lookup"><span data-stu-id="32567-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="32567-160">Buďte trpěliví, protože tento příkaz trvá několik minut s haldou 30 MB:</span><span class="sxs-lookup"><span data-stu-id="32567-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

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

<span data-ttu-id="32567-161">Můžete vidět, `String` že je přímo `Customer` držen objektem a `CustomerCache` nepřímo v držení objektu.</span><span class="sxs-lookup"><span data-stu-id="32567-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="32567-162">Můžete pokračovat dumping z objektů `String` vidět, že většina objektů sledovat podobný vzor.</span><span class="sxs-lookup"><span data-stu-id="32567-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="32567-163">V tomto okamžiku šetření za předpokladu, dostatečné informace k identifikaci hlavní příčinu ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="32567-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="32567-164">Tento obecný postup umožňuje identifikovat zdroj hlavní nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="32567-165">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="32567-165">Clean up resources</span></span>

<span data-ttu-id="32567-166">V tomto kurzu jste spustili ukázkový webový server.</span><span class="sxs-lookup"><span data-stu-id="32567-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="32567-167">Tento server měl být vypnut, jak je vysvětleno v části [Restartovat proces, který se nezdařil.](#restart-the-failed-process)</span><span class="sxs-lookup"><span data-stu-id="32567-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="32567-168">Můžete také odstranit soubor s výpisem stavu paměti, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="32567-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="32567-169">Další kroky</span><span class="sxs-lookup"><span data-stu-id="32567-169">Next steps</span></span>

<span data-ttu-id="32567-170">Blahopřejeme k dokončení tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="32567-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="32567-171">Stále zveřejňujeme další diagnostické kurzy.</span><span class="sxs-lookup"><span data-stu-id="32567-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="32567-172">Můžete si přečíst koncept verze v úložišti [dotnet/diagnostics.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)</span><span class="sxs-lookup"><span data-stu-id="32567-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="32567-173">Tento kurz se zabýval základy klíčových diagnostických nástrojů .NET.</span><span class="sxs-lookup"><span data-stu-id="32567-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="32567-174">Informace o pokročilém použití naleznete v následující referenční dokumentaci:</span><span class="sxs-lookup"><span data-stu-id="32567-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="32567-175">[dotnet-trace](dotnet-trace.md) do seznamu procesů.</span><span class="sxs-lookup"><span data-stu-id="32567-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="32567-176">[dotnet-čítače](dotnet-counters.md) pro kontrolu využití spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="32567-177">[dotnet-dump](dotnet-dump.md) shromažďovat a analyzovat soubor s výpisem stavu paměti.</span><span class="sxs-lookup"><span data-stu-id="32567-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
