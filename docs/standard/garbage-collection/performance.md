---
title: Uvolnění paměti a výkon
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 72cf742aae26f9441229b355dc6e70da7a5fc9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75900585"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="7ed8a-102">Uvolnění paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="7ed8a-102">Garbage Collection and Performance</span></span>

<span data-ttu-id="7ed8a-103">Toto téma popisuje problémy související s uvolňovánípaměti a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="7ed8a-104">Řeší problémy, které se týká spravované haldy a vysvětluje, jak minimalizovat vliv uvolňování paměti na vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="7ed8a-105">Každý problém obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-105">Each issue has links to procedures that you can use to investigate problems.</span></span>

## <a name="performance-analysis-tools"></a><span data-ttu-id="7ed8a-106">Nástroje pro analýzu výkonu</span><span class="sxs-lookup"><span data-stu-id="7ed8a-106">Performance Analysis Tools</span></span>

<span data-ttu-id="7ed8a-107">Následující části popisují nástroje, které jsou k dispozici pro zkoumání využití paměti a uvolňování paměti problémy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-107">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="7ed8a-108">[Postupy](#performance-check-procedures) uvedené dále v tomto tématu odkazují na tyto nástroje.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-108">The [procedures](#performance-check-procedures) provided later in this topic refer to these tools.</span></span>

### <a name="memory-performance-counters"></a><span data-ttu-id="7ed8a-109">Čítače výkonu paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-109">Memory Performance Counters</span></span>

<span data-ttu-id="7ed8a-110">Čítače výkonu můžete použít ke shromažďování dat o výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-110">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="7ed8a-111">Pokyny naleznete v [tématu Runtime Profilování](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-111">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="7ed8a-112">Kategorie výkonu .NET CLR memory, jak je popsáno v [čítačích výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-112">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

### <a name="debugging-with-sos"></a><span data-ttu-id="7ed8a-113">Ladění pomocí SOS</span><span class="sxs-lookup"><span data-stu-id="7ed8a-113">Debugging with SOS</span></span>

<span data-ttu-id="7ed8a-114">Ladicí [program systému Windows (WinDbg)](/windows-hardware/drivers/debugger/index) můžete použít ke kontrole objektů na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-114">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="7ed8a-115">Chcete-li nainstalovat aplikaci WinDbg, nainstalujte nástroje pro ladění pro systém Windows na stránce [Nástroje pro stažení ladění pro systém Windows.](/windows-hardware/drivers/debugger/debugger-download-tools)</span><span class="sxs-lookup"><span data-stu-id="7ed8a-115">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="7ed8a-116">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-116">Garbage Collection ETW Events</span></span>

<span data-ttu-id="7ed8a-117">Trasování událostí pro Windows (ETW) je systém trasování, který doplňuje podporu profilování a ladění poskytovanou rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-117">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="7ed8a-118">Počínaje rozhraním .NET Framework 4, [události uvolňování paměti ETW](../../../docs/framework/performance/garbage-collection-etw-events.md) zachycují užitečné informace pro analýzu spravované haldy ze statistického hlediska.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-118">Starting with the .NET Framework 4, [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="7ed8a-119">Například `GCStart_V1` událost, která je vyvolána, když dojde k uvolnění paměti, poskytuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-119">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="7ed8a-120">Generování objektů jsou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-120">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="7ed8a-121">Co spustilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-121">What triggered the garbage collection.</span></span>

- <span data-ttu-id="7ed8a-122">Typ uvolňování paměti (souběžné nebo ne souběžné).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-122">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="7ed8a-123">Protokolování událostí ETW je efektivní a nebude maskovat žádné problémy s výkonem spojené s uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-123">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="7ed8a-124">Proces může poskytnout své vlastní události ve spojení s událostmi ETW.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-124">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="7ed8a-125">Při protokolování události aplikace a události uvolňování paměti může být korelován k určení, jak a kdy dochází k problémům haldy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-125">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="7ed8a-126">Serverová aplikace může například poskytnout události na začátku a na konci požadavku klienta.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-126">For example, a server application could provide events at the start and end of a client request.</span></span>

### <a name="the-profiling-api"></a><span data-ttu-id="7ed8a-127">Rozhraní API profilování</span><span class="sxs-lookup"><span data-stu-id="7ed8a-127">The Profiling API</span></span>

<span data-ttu-id="7ed8a-128">Rozhraní profilování clr (COMMON Language runtime) poskytují podrobné informace o objektech, které byly ovlivněny během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-128">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="7ed8a-129">Profiler může být upozorněni při uvolnění paměti začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-129">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="7ed8a-130">Může poskytovat sestavy o objektech na spravované haldě, včetně identifikace objektů v každé generaci.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-130">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="7ed8a-131">Další informace naleznete [v tématu Přehled profilování](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-131">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="7ed8a-132">Profilovací programy mohou poskytovat komplexní informace.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-132">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="7ed8a-133">Komplexní profilovací programy však mohou potenciálně upravit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-133">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="7ed8a-134">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="7ed8a-134">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="7ed8a-135">Počínaje rozhraním .NET Framework 4 umožňuje monitorování prostředků domény aplikace (ARM) hostitelům monitorovat využití procesoru a paměti podle domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-135">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="7ed8a-136">Další informace naleznete v [tématu Application Domain Resource Resource .](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)</span><span class="sxs-lookup"><span data-stu-id="7ed8a-136">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="7ed8a-137">Poradce při potížích s výkonem</span><span class="sxs-lookup"><span data-stu-id="7ed8a-137">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="7ed8a-138">Prvním krokem je [zjistit, zda je problém skutečně uvolňování paměti](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-138">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="7ed8a-139">Pokud zjistíte, že tomu tak je, vyberte z následujícího seznamu k řešení problému.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-139">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="7ed8a-140">Je vyvolána výjimka z nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-140">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="7ed8a-141">Tento proces používá příliš mnoho paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-141">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="7ed8a-142">Systém uvolňování paměti neuvolněny objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="7ed8a-142">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="7ed8a-143">Spravovaná halda je příliš fragmentovaná.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-143">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="7ed8a-144">Pozastavení uvolňování paměti jsou příliš dlouhé</span><span class="sxs-lookup"><span data-stu-id="7ed8a-144">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="7ed8a-145">Generace 0 je příliš velká</span><span class="sxs-lookup"><span data-stu-id="7ed8a-145">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="7ed8a-146">Využití procesoru během uvolňování paměti je příliš vysoká</span><span class="sxs-lookup"><span data-stu-id="7ed8a-146">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="7ed8a-147">Problém: Je vyvolána výjimka z nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-147">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="7ed8a-148">Existují dva legitimní případy <xref:System.OutOfMemoryException> pro podařilo být hozen:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-148">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="7ed8a-149">Dochází virtuální paměť.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-149">Running out of virtual memory.</span></span>

  <span data-ttu-id="7ed8a-150">Systém uvolňování paměti přiděluje paměť ze systému v segmentech předem určené velikosti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-150">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="7ed8a-151">Pokud přidělení vyžaduje další segment, ale v prostoru virtuální paměti procesu nezbývá žádný souvislý volný blok, přidělení spravované haldy se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-151">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="7ed8a-152">Nemají dostatek fyzické paměti k přidělení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-152">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="7ed8a-153">Kontroly výkonnosti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-153">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="7ed8a-154">Určete, zda je spravována výjimka z nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-154">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="7ed8a-155">Určete, kolik virtuální paměti lze rezervovat.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-155">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="7ed8a-156">Zjistěte, zda je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-156">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="7ed8a-157">Pokud zjistíte, že výjimka není legitimní, obraťte se na oddělení služeb zákazníkům a podpory společnosti Microsoft s následujícími informacemi:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-157">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="7ed8a-158">Zásobník se spravovanou výjimkou z nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-158">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="7ed8a-159">Úplný výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-159">Full memory dump.</span></span>

- <span data-ttu-id="7ed8a-160">Data, která dokazují, že se nejedná o legitimní výjimku z nedostatku paměti, včetně dat, která ukazují, že virtuální nebo fyzická paměť není problém.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-160">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="7ed8a-161">Problém: Proces používá příliš mnoho paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-161">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="7ed8a-162">Běžným předpokladem je, že zobrazení využití paměti na kartě **Výkon** správce úloh systému Windows může indikovat, kdy je používáno příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-162">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="7ed8a-163">Toto zobrazení se však toto zobrazení netožuje s pracovní sadou; neposkytuje informace o využití virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-163">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="7ed8a-164">Pokud zjistíte, že problém je způsoben spravované haldy, je nutné měřit spravované haldy v průběhu času k určení všechny vzory.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-164">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="7ed8a-165">Pokud zjistíte, že problém není způsoben spravované haldy, je nutné použít nativní ladění.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-165">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="7ed8a-166">Kontroly výkonnosti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-166">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="7ed8a-167">Určete, kolik virtuální paměti lze rezervovat.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-167">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="7ed8a-168">Určete, kolik paměti spravované haldy je potvrzení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-168">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="7ed8a-169">Určete, kolik paměti spravované haldy rezervy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-169">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="7ed8a-170">Určete velké objekty v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-170">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="7ed8a-171">Určete odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-171">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="7ed8a-172">Problém: Uvolňování nezíská objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="7ed8a-172">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="7ed8a-173">Když se zobrazí, jako kdyby objekty nejsou uvolněny podle očekávání pro uvolňování paměti, je nutné určit, zda existují nějaké silné odkazy na tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-173">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="7ed8a-174">K tomuto problému může dojít také v případě, že pro generování, které obsahuje mrtvý objekt, nedošlo k žádnému uvolnění paměti, což znamená, že finalizační metoda pro mrtvý objekt nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-174">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="7ed8a-175">Například je to možné, když spouštěte aplikaci s jedním vláknem (STA) a podproces, který služby finalizační fronty nemůže volat do něj.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-175">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="7ed8a-176">Kontroly výkonnosti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-176">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="7ed8a-177">Zkontrolujte odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-177">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="7ed8a-178">Určete, zda byla spuštěna finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-178">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="7ed8a-179">Zjistěte, zda existují objekty, které čekají na dokončení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-179">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="7ed8a-180">Problém: Spravované haldy je příliš fragmentované</span><span class="sxs-lookup"><span data-stu-id="7ed8a-180">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="7ed8a-181">Úroveň fragmentace se vypočítá jako poměr volného místa k celkové přidělené paměti pro generování.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-181">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="7ed8a-182">Pro generaci 2 není přijatelná úroveň fragmentace větší než 20%.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-182">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="7ed8a-183">Vzhledem k tomu, generace 2 může získat velmi velký, poměr fragmentace je důležitější než absolutní hodnota.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-183">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="7ed8a-184">S velké množství volného místa v generaci 0 není problém, protože se jedná o generování, kde jsou přiděleny nové objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-184">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="7ed8a-185">Fragmentace vždy dochází v haldě velkého objektu, protože není komprimován.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-185">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="7ed8a-186">Volné objekty, které jsou přilehlé jsou přirozeně sbaleny do jednoho prostoru pro splnění požadavků na přidělení velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-186">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="7ed8a-187">Fragmentace se může stát problémem v generaci 1 a generaci 2.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-187">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="7ed8a-188">Pokud tyto generace mají velké množství volného místa po uvolnění paměti, použití objektu aplikace může vyžadovat změny a měli byste zvážit přehodnocení životnosti dlouhodobé objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-188">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="7ed8a-189">Nadměrné připnutí objektů může zvýšit fragmentaci.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-189">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="7ed8a-190">Pokud je fragmentace vysoká, mohlo být připnuto příliš mnoho objektů.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-190">If fragmentation is high, too many objects could have been pinned.</span></span>

<span data-ttu-id="7ed8a-191">Pokud fragmentace virtuální paměti brání uvolňování v přidání segmentů, příčinou může být jedna z následujících příčin:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-191">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="7ed8a-192">Časté nakládání a vykládání mnoha malých sestav.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-192">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="7ed8a-193">Při spolupráci s nespravovaným kódem je při držení příliš mnoho odkazů na objekty MODELU COM.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-193">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="7ed8a-194">Vytvoření velkých přechodných objektů, což způsobuje, že haldy velkých objektů často přidělují a volí segmenty haldy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-194">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="7ed8a-195">Při hostování CLR, aplikace může požádat, aby systém uvolňování paměti zachovat své segmenty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-195">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="7ed8a-196">Tím se snižuje četnost přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-196">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="7ed8a-197">Toho lze dosáhnout pomocí příznaku STARTUP_HOARD_GC_VM ve [výčtu STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-197">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="7ed8a-198">Kontroly výkonnosti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-198">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="7ed8a-199">Určete velikost volného místa ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-199">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="7ed8a-200">Určete počet připnutých objektů.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-200">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="7ed8a-201">Pokud se domníváte, že neexistuje žádný legitimní důvod pro fragmentaci, obraťte se na oddělení služeb zákazníkům společnosti Microsoft a podpory.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-201">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="7ed8a-202">Problém: Pozastavení uvolňování paměti jsou příliš dlouhé</span><span class="sxs-lookup"><span data-stu-id="7ed8a-202">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="7ed8a-203">Uvolňování paměti pracuje v měkké reálném čase, takže aplikace musí být schopen tolerovat některé pauzy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-203">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="7ed8a-204">Kritériem pro měkký reálný čas je, že 95% operací musí být dokončeno včas.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-204">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="7ed8a-205">V souběžné uvolňování paměti spravovaných podprocesů je povoleno spustit během kolekce, což znamená, že pauzy jsou velmi minimální.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-205">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="7ed8a-206">Dočasné uvolňování paměti (generace 0 a 1) trvat pouze několik milisekund, takže snížení pauzy obvykle není možné.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-206">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="7ed8a-207">Můžete však snížit pauzy v kolekcích generace 2 změnou vzoru požadavků na přidělení aplikací.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-207">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="7ed8a-208">Další, přesnější, metoda je použití [uvolnění paměti ETW události](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-208">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="7ed8a-209">Časování kolekcí můžete najít přidáním rozdílů časového razítka pro posloupnost událostí.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-209">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="7ed8a-210">Celá sekvence kolekce zahrnuje pozastavení spuštění motoru, uvolnění paměti sám a obnovení spuštění motoru.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-210">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="7ed8a-211">[Oznámení uvolňování paměti](../../../docs/standard/garbage-collection/notifications.md) můžete použít k určení, zda server má mít kolekci generace 2 a zda přesměrování požadavků na jiný server může zmírnit problémy s pozastavení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-211">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="7ed8a-212">Kontroly výkonnosti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-212">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="7ed8a-213">Určete dobu v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-213">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="7ed8a-214">Zjistěte, co způsobilo uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-214">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="7ed8a-215">Problém: Generace 0 je příliš velká</span><span class="sxs-lookup"><span data-stu-id="7ed8a-215">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="7ed8a-216">Generace 0 je pravděpodobně mít větší počet objektů v 64bitovém systému, zejména při použití uvolňování paměti serveru namísto uvolňování paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-216">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="7ed8a-217">Důvodem je, že prahová hodnota pro aktivaci uvolnění paměti generace 0 je vyšší v těchto prostředích a kolekce generace 0 může získat mnohem větší.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-217">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="7ed8a-218">Výkon je lepší, když aplikace přiděluje více paměti před uvolnění paměti se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-218">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="7ed8a-219">Problém: Využití procesoru během uvolňování paměti je příliš vysoká</span><span class="sxs-lookup"><span data-stu-id="7ed8a-219">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="7ed8a-220">Využití procesoru bude vysoká během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-220">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="7ed8a-221">Pokud značné množství času procesu je vynaloženo v uvolňování paměti, počet kolekcí je příliš časté nebo kolekce trvá příliš dlouho.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-221">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="7ed8a-222">Zvýšená míra přidělení objektů na spravované haldě způsobí, že uvolňování paměti dochází častěji.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-222">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="7ed8a-223">Snížení míry přidělení snižuje četnost uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-223">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="7ed8a-224">Sazby přidělení můžete sledovat `Allocated Bytes/second` pomocí čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-224">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="7ed8a-225">Další informace naleznete [v tématu Čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-225">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="7ed8a-226">Doba trvání kolekce je především faktor počtu objektů, které přežívají po přidělení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-226">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="7ed8a-227">Systém uvolňování paměti musí projít velké množství paměti, pokud mnoho objektů zůstávají shromažďovat.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-227">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="7ed8a-228">Práce na zhutnění přeživších je časově náročná.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-228">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="7ed8a-229">Chcete-li zjistit, kolik objektů bylo zpracováno během kolekce, nastavte zarážku v ladicím programu na konci uvolňování paměti pro zadanou generaci.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-229">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="7ed8a-230">Kontroly výkonnosti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-230">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="7ed8a-231">Zjistěte, zda je vysoké využití procesoru způsobeno uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-231">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="7ed8a-232">Nastavte zarážku na konci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-232">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="7ed8a-233">Pokyny pro řešení potíží</span><span class="sxs-lookup"><span data-stu-id="7ed8a-233">Troubleshooting Guidelines</span></span>

<span data-ttu-id="7ed8a-234">Tato část popisuje pokyny, které byste měli zvážit při zahájení vyšetřování.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-234">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="7ed8a-235">Uvolňování paměti pracovní stanice nebo serveru</span><span class="sxs-lookup"><span data-stu-id="7ed8a-235">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="7ed8a-236">Zjistěte, zda používáte správný typ uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-236">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="7ed8a-237">Pokud vaše aplikace používá více vláken a instancí objektů, použijte místo uvolňování paměti pracovní stanice uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-237">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="7ed8a-238">Uvolňování paměti serveru pracuje na více vláknech, zatímco uvolňování paměti pracovní stanice vyžaduje více instancí aplikace ke spuštění vlastních vláken uvolňování paměti a soutěžit o čas procesoru.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-238">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="7ed8a-239">Aplikace, která má nízké zatížení a která provádí úkoly zřídka na pozadí, jako je například služba, může použít uvolňování paměti pracovní stanice s souběžným uvolňováním paměti zakázáno.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-239">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="7ed8a-240">Kdy měřit velikost spravované haldy</span><span class="sxs-lookup"><span data-stu-id="7ed8a-240">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="7ed8a-241">Pokud používáte profiler, budete muset vytvořit konzistentní vzor měření efektivně diagnostikovat problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-241">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="7ed8a-242">Zvažte následující body pro vytvoření plánu:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-242">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="7ed8a-243">Pokud měříte po uvolnění paměti generace 2, celá spravovaná halda bude bez odpadků (mrtvé objekty).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-243">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="7ed8a-244">Pokud měříte ihned po uvolnění paměti generace 0, objekty v generacích 1 a 2 ještě nebudou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-244">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="7ed8a-245">Pokud měříte bezprostředně před uvolnění paměti, budete měřit co nejvíce přidělení, jak je to možné před spuštěním uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-245">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="7ed8a-246">Měření během uvolňování paměti je problematické, protože datové struktury systému uvolňování paměti nejsou v platném stavu pro průchod a nemusí být schopen poskytnout úplné výsledky.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-246">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="7ed8a-247">Toto chování je úmyslné.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-247">This is by design.</span></span>

- <span data-ttu-id="7ed8a-248">Pokud používáte uvolňování paměti pracovní stanice s souběžným uvolňováním paměti, uvolněné objekty nejsou komprimovány, takže velikost haldy může být stejná nebo větší (fragmentace může způsobit, že se zdá být větší).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-248">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="7ed8a-249">Souběžné uvolňování paměti na generaci 2 je zpožděno, když je zatížení fyzické paměti příliš vysoké.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-249">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="7ed8a-250">Následující postup popisuje, jak nastavit zarážku tak, aby bylo možné měřit spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-250">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="7ed8a-251">Nastavení zarážky na konci uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-251">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="7ed8a-252">Do windbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-252">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="7ed8a-253">**bp mscorwks! WKS::GCHeap::RestartEE "j (dwo(mscorwks! WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';' g'"**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-253">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="7ed8a-254">kde **GcCondemnedGeneration** je nastavena na požadovanou generaci.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-254">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="7ed8a-255">Tento příkaz vyžaduje soukromé symboly.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-255">This command requires private symbols.</span></span>

  <span data-ttu-id="7ed8a-256">Tento příkaz vynutí přerušení, pokud **restartEE** je spuštěn po generace 2 objekty byly uvolněny pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-256">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="7ed8a-257">V uvolňování paměti serveru pouze jedno vlákno volá **RestartEE**, takže zarážka dojde pouze jednou během uvolňování paměti generace 2.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-257">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

## <a name="performance-check-procedures"></a><span data-ttu-id="7ed8a-258">Postupy kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="7ed8a-258">Performance Check Procedures</span></span>

<span data-ttu-id="7ed8a-259">Tato část popisuje následující postupy pro izolaci příčiny problému s výkonem:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-259">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="7ed8a-260">Zjistěte, zda je problém způsoben uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-260">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="7ed8a-261">Určete, zda je spravována výjimka z nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-261">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="7ed8a-262">Určete, kolik virtuální paměti lze rezervovat.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-262">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="7ed8a-263">Zjistěte, zda je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-263">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="7ed8a-264">Určete, kolik paměti spravované haldy je potvrzení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-264">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="7ed8a-265">Určete, kolik paměti spravované haldy rezervy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-265">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="7ed8a-266">Určete velké objekty v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-266">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="7ed8a-267">Určete odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-267">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="7ed8a-268">Určete, zda byla spuštěna finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-268">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="7ed8a-269">Zjistěte, zda existují objekty, které čekají na dokončení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-269">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="7ed8a-270">Určete velikost volného místa ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-270">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="7ed8a-271">Určete počet připnutých objektů.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-271">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="7ed8a-272">Určete dobu v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-272">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="7ed8a-273">Zjistěte, co vyvolalo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-273">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="7ed8a-274">Zjistěte, zda je vysoké využití procesoru způsobeno uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-274">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="7ed8a-275">Chcete-li zjistit, zda je problém způsoben uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-275">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="7ed8a-276">Prozkoumejte následující dva čítače výkonu paměti:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-276">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="7ed8a-277">**% času v GC**.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-277">**% Time in GC**.</span></span> <span data-ttu-id="7ed8a-278">Zobrazí procento uplynulého času stráveného prováděním uvolňování paměti po posledním cyklu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-278">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="7ed8a-279">Tento čítač slouží k určení, zda uvolňování systému tráví příliš mnoho času, aby spravované haldy místo k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-279">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="7ed8a-280">Pokud je čas strávený v uvolňování paměti relativně nízký, může to znamenat problém s prostředky mimo spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-280">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="7ed8a-281">Tento čítač nemusí být přesné, pokud se jedná o souběžné nebo pozadí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-281">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="7ed8a-282">**# Celkem potvrzené bajty**.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-282">**# Total committed Bytes**.</span></span> <span data-ttu-id="7ed8a-283">Zobrazuje množství virtuální paměti aktuálně potvrzené systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-283">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="7ed8a-284">Tento čítač slouží k určení, zda paměť spotřebované systémem uvolňování paměti je nadměrná část paměti, která používá vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-284">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="7ed8a-285">Většina čítačů výkonu paměti jsou aktualizovány na konci každé uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-285">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="7ed8a-286">Proto nemusí odrážet aktuální podmínky, o kterých chcete získat informace.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-286">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="7ed8a-287">Chcete-li zjistit, zda je spravována výjimka z nedostatku paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-287">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="7ed8a-288">Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte příkaz výjimka tisku (**pe):**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-288">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="7ed8a-289">**!pe**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-289">**!pe**</span></span>

    <span data-ttu-id="7ed8a-290">Pokud je výjimka <xref:System.OutOfMemoryException> spravována, zobrazí se jako typ výjimky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-290">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="7ed8a-291">Pokud výstup neurčuje výjimku, budete muset určit, které vlákno výjimka z paměti je z.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-291">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="7ed8a-292">Do ladicího programu zadejte následující příkaz, který zobrazí všechna vlákna s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-292">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="7ed8a-293">**~\*Kb**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-293">**~\*kb**</span></span>

    <span data-ttu-id="7ed8a-294">Podproces s zásobníku, který má volání `RaiseTheException` výjimek je označen argumentem.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-294">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="7ed8a-295">Toto je objekt spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-295">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="7ed8a-296">Následující příkaz můžete použít k vysuševných výjimek.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-296">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="7ed8a-297">**!pe -vnořené**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-297">**!pe -nested**</span></span>

    <span data-ttu-id="7ed8a-298">Pokud nenajdete žádné výjimky, výjimka z paměti pochází z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-298">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="7ed8a-299">Chcete-li zjistit, kolik virtuální paměti lze rezervovat</span><span class="sxs-lookup"><span data-stu-id="7ed8a-299">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="7ed8a-300">Do windbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz, abyste získali největší volnou oblast:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-300">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="7ed8a-301">**!adresa -souhrn**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-301">**!address -summary**</span></span>

  <span data-ttu-id="7ed8a-302">Největší volná oblast je zobrazena tak, jak je znázorněno na následujícím výstupu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-302">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="7ed8a-303">V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-303">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="7ed8a-304">Tato oblast je mnohem menší než co systém uvolňování paměti potřebuje pro segment.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-304">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="7ed8a-305">-nebo-</span><span class="sxs-lookup"><span data-stu-id="7ed8a-305">-or-</span></span>

- <span data-ttu-id="7ed8a-306">Použijte příkaz **vmstat:**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-306">Use the **vmstat** command:</span></span>

  <span data-ttu-id="7ed8a-307">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-307">**!vmstat**</span></span>

  <span data-ttu-id="7ed8a-308">Největší volná oblast je největší hodnota ve sloupci MAXIMUM, jak je znázorněno na následujícím výstupu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-308">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="7ed8a-309">Chcete-li zjistit, zda je dostatek fyzické paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-309">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="7ed8a-310">Spusťte Správce úloh systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-310">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="7ed8a-311">Na kartě **Výkon** se podívejte na potvrzenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-311">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="7ed8a-312">(V systému Windows 7, podívejte se na **potvrzení (KB)** ve **skupině System**.)</span><span class="sxs-lookup"><span data-stu-id="7ed8a-312">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="7ed8a-313">Pokud **součet** je blízko **limit**, dochází fyzická paměť.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-313">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="7ed8a-314">Chcete-li zjistit, kolik paměti spravované haldy je potvrzení</span><span class="sxs-lookup"><span data-stu-id="7ed8a-314">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="7ed8a-315">Pomocí `# Total committed bytes` čítače výkonu paměti získat počet bajtů, které spravované haldy je potvrzení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-315">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="7ed8a-316">Systém uvolňování paměti odevzdvá bloky v segmentu podle potřeby, ne všechny současně.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-316">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="7ed8a-317">Nepoužívejte čítač `# Bytes in all Heaps` výkonu, protože nepředstavuje skutečné využití paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-317">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="7ed8a-318">Velikost generace je zahrnuta v této hodnotě a je ve skutečnosti jeho prahová velikost, to znamená velikost, která indukuje uvolnění paměti, pokud je generace vyplněna objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-318">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="7ed8a-319">Proto je tato hodnota obvykle nula.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-319">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="7ed8a-320">Chcete-li zjistit, kolik paměti spravované haldy rezervy</span><span class="sxs-lookup"><span data-stu-id="7ed8a-320">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="7ed8a-321">Použijte `# Total reserved bytes` čítač výkonu paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-321">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="7ed8a-322">Systém uvolňování paměti rezervuje paměť v segmentech a můžete určit, kde segment začíná pomocí příkazu **eeheap.**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-322">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="7ed8a-323">I když můžete určit velikost paměti, kterou systém uvolňování paměti přiděluje pro každý segment, velikost segmentu je specifická pro implementaci a může se kdykoli změnit, včetně pravidelných aktualizací.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-323">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="7ed8a-324">Vaše aplikace by nikdy neměla dělat předpoklady o konkrétní velikosti segmentu nebo na ní záviset, ani by se neměla pokoušet nakonfigurovat množství paměti, která je k dispozici pro přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-324">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="7ed8a-325">Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-325">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="7ed8a-326">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-326">**!eeheap -gc**</span></span>

  <span data-ttu-id="7ed8a-327">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-327">The result is as follows.</span></span>

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  <span data-ttu-id="7ed8a-328">Adresy označené "segmentem" jsou počáteční adresy segmentů.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-328">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="7ed8a-329">Určení velkých objektů v generaci 2</span><span class="sxs-lookup"><span data-stu-id="7ed8a-329">To determine large objects in generation 2</span></span>

- <span data-ttu-id="7ed8a-330">Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-330">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="7ed8a-331">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-331">**!dumpheap –stat**</span></span>

  <span data-ttu-id="7ed8a-332">Pokud spravované haldy je velký, **dumpheap** může chvíli trvat až do konce.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-332">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="7ed8a-333">Můžete začít analyzovat z několika posledních řádků výstupu, protože seznam objektů, které používají nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-333">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="7ed8a-334">Například:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-334">For example:</span></span>

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  <span data-ttu-id="7ed8a-335">Poslední uvedený objekt je řetězec a zabírá nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-335">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="7ed8a-336">Můžete prozkoumat aplikace a zjistit, jak lze optimalizovat objekty řetězce.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-336">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="7ed8a-337">Chcete-li zobrazit řetězce, které jsou mezi 150 a 200 bajtů, zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-337">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="7ed8a-338">**!dumpheap -typ System.String -min 150 -max 200**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-338">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="7ed8a-339">Příklad výsledků je následující.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-339">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="7ed8a-340">Použití celého čísla namísto řetězce pro ID může být efektivnější.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-340">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="7ed8a-341">Pokud stejný řetězec se opakuje tisíckrát, zvažte řetězec interning.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-341">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="7ed8a-342">Další informace o interning řetězce, naleznete <xref:System.String.Intern%2A?displayProperty=nameWithType> v referenční téma pro metodu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-342">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="7ed8a-343">Určení odkazů na objekty</span><span class="sxs-lookup"><span data-stu-id="7ed8a-343">To determine references to objects</span></span>

- <span data-ttu-id="7ed8a-344">Do windbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz pro seznam odkazů na objekty:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-344">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="7ed8a-345">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-345">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="7ed8a-346">Chcete-li určit odkazy na konkrétní objekt, uveďte adresu:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-346">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="7ed8a-347">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-347">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="7ed8a-348">Kořeny nalezené na hromádkách mohou být falešně pozitivní.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-348">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="7ed8a-349">Další informace získáte pomocí `!help gcroot`příkazu .</span><span class="sxs-lookup"><span data-stu-id="7ed8a-349">For more information, use the command `!help gcroot`.</span></span>

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  <span data-ttu-id="7ed8a-350">Dokončení příkazu **gcroot** může trvat dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-350">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="7ed8a-351">Jakýkoli objekt, který není uvolněn a uvolnění paměti je živý objekt.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-351">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="7ed8a-352">To znamená, že některé root je přímo nebo nepřímo drží na objektu, takže **gcroot** by měl vrátit informace o cestě k objektu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-352">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="7ed8a-353">Měli byste prozkoumat vrácené grafy a zjistit, proč jsou tyto objekty stále odkazovány.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-353">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="7ed8a-354">Chcete-li zjistit, zda byla spuštěna finalizační metoda</span><span class="sxs-lookup"><span data-stu-id="7ed8a-354">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="7ed8a-355">Spusťte testovací program, který obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-355">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="7ed8a-356">Pokud test problém vyřeší, to znamená, že uvolňování paměti nebyl akultivace objektů, protože finalizační metody pro tyto objekty byla pozastavena.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-356">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="7ed8a-357">Metoda <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> umožňuje finalizační metody k dokončení svých úkolů a řeší problém.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-357">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="7ed8a-358">Chcete-li zjistit, zda existují objekty, které čekají na dokončení</span><span class="sxs-lookup"><span data-stu-id="7ed8a-358">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="7ed8a-359">Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-359">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="7ed8a-360">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-360">**!finalizequeue**</span></span>

    <span data-ttu-id="7ed8a-361">Podívejte se na počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-361">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="7ed8a-362">Pokud je číslo vysoké, je nutné prozkoumat, proč tyto finalizační metody nelze postupovat vůbec nebo nemůže postupovat dostatečně rychle.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-362">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="7ed8a-363">Chcete-li získat výstup vláken, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-363">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="7ed8a-364">**závity -speciální**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-364">**threads -special**</span></span>

    <span data-ttu-id="7ed8a-365">Tento příkaz poskytuje výstup, například následující.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-365">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="7ed8a-366">Vlákno finalizační metody označuje, která finalizační metoda, pokud existuje, je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-366">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="7ed8a-367">Pokud vlákno finalizační metody nespouštějí žádné finalizační metody, čeká na událost, která mu řekne, aby dělala svou práci.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-367">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="7ed8a-368">Většinu času se zobrazí finalizační vlákno v tomto stavu, protože běží na THREAD_HIGHEST_PRIORITY a má dokončit spuštění finalizačních metod, pokud existuje, velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-368">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="7ed8a-369">Určení množství volného místa ve spravované haldě</span><span class="sxs-lookup"><span data-stu-id="7ed8a-369">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="7ed8a-370">Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-370">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="7ed8a-371">**!dumpheap -typ Free -stat**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-371">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="7ed8a-372">Tento příkaz zobrazí celkovou velikost všech volných objektů na spravované haldě, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-372">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="7ed8a-373">Chcete-li určit volné místo v generaci 0, zadejte následující příkaz pro informace o spotřebě paměti podle generování:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-373">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="7ed8a-374">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-374">**!eeheap -gc**</span></span>

  <span data-ttu-id="7ed8a-375">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-375">This command displays output similar to the following.</span></span> <span data-ttu-id="7ed8a-376">Poslední řádek zobrazuje dočasný segment.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-376">The last line shows the ephemeral segment.</span></span>

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- <span data-ttu-id="7ed8a-377">Vypočítejte místo využité generací 0:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-377">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="7ed8a-378">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-378">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="7ed8a-379">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-379">The result is as follows.</span></span> <span data-ttu-id="7ed8a-380">Generace 0 je přibližně 9 MB.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-380">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="7ed8a-381">Následující příkaz vypíše volné místo v rozsahu generace 0:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-381">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="7ed8a-382">**!dumpheap -typ Volný -stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-382">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="7ed8a-383">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-383">The result is as follows.</span></span>

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  <span data-ttu-id="7ed8a-384">Tento výstup ukazuje, že generace 0 část haldy používá 9 MB místa pro objekty a má 7 MB zdarma.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-384">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="7ed8a-385">Tato analýza ukazuje, do jaké míry generace 0 přispívá k fragmentaci.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-385">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="7ed8a-386">Toto množství využití haldy by měla být diskontována z celkové částky jako příčina fragmentace dlouhodobými objekty.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-386">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="7ed8a-387">Určení počtu připnutých objektů</span><span class="sxs-lookup"><span data-stu-id="7ed8a-387">To determine the number of pinned objects</span></span>

- <span data-ttu-id="7ed8a-388">Do ladicího programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-388">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="7ed8a-389">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-389">**!gchandles**</span></span>

  <span data-ttu-id="7ed8a-390">Zobrazené statistiky zahrnují počet připnutých popisovačů, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-390">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="7ed8a-391">Chcete-li zjistit dobu v uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-391">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="7ed8a-392">Zkontrolujte `% Time in GC` čítač výkonu paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-392">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="7ed8a-393">Hodnota se vypočítá pomocí intervalu vzorku.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-393">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="7ed8a-394">Vzhledem k tomu, že čítače jsou aktualizovány na konci každé uvolnění paměti, aktuální vzorek bude mít stejnou hodnotu jako předchozí ukázka, pokud došlo k žádné kolekce během intervalu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-394">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="7ed8a-395">Čas sběru se získá vynásobením intervalového času vzorku procentuální hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-395">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="7ed8a-396">Následující údaje ukazují čtyři intervaly odběru vzorků po dvou sekundách pro 8sekundovou studii.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-396">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="7ed8a-397">V `Gen0` `Gen1`, `Gen2` a sloupce zobrazit počet uvolnění paměti, ke kterým došlo během tohoto intervalu pro tuto generaci.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-397">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="7ed8a-398">Tyto informace nezobrazuje, kdy došlo k uvolnění paměti, ale můžete určit počet uvolnění paměti, ke kterým došlo v časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-398">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="7ed8a-399">Za předpokladu, že nejhorší případ desáté generace 0 uvolňování paměti dokončena na začátku druhého intervalu a jedenácté generace 0 uvolňování paměti dokončena na konci pátého intervalu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-399">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="7ed8a-400">Doba mezi koncem desátéa konce a koncem jedenáctého uvolňování paměti je přibližně 2 sekundy a čítač výkonu zobrazuje 3 %, takže doba trvání jedenácté generace 0 uvolňování paměti byla (2 sekundy \* 3 % = 60 ms).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-400">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="7ed8a-401">V tomto příkladu je 5 období.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-401">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="7ed8a-402">Druhá generace 2 uvolňování paměti zahájena během třetího intervalu a dokončena v pátém intervalu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-402">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="7ed8a-403">Za předpokladu, že nejhorší případ, poslední uvolnění paměti byla pro kolekci generace 0, která byla dokončena na začátku druhého intervalu a uvolnění paměti generace 2 dokončena na konci pátého intervalu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-403">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="7ed8a-404">Proto čas mezi koncem generace 0 uvolňování paměti a konec uvolnění paměti generace 2 je 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-404">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="7ed8a-405">Vzhledem `% Time in GC` k tomu, že čítač je 20 %, maximální doba, po kterou může být trvalo uvolnění paměti generace 2 , je (4 sekundy \* 20 % = 800 ms).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-405">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="7ed8a-406">Alternativně můžete určit délku uvolňování paměti pomocí [události uvolňování paměti ETW](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace k určení doby trvání uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-406">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="7ed8a-407">Například následující data zobrazuje posloupnost událostí, ke kterým došlo během nesouběžného uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-407">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="7ed8a-408">Pozastavení spravovaného závitu trvalo`GCSuspendEEEnd` 26us ( – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-408">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="7ed8a-409">Skutečné uvolňování paměti trvalo 4,8`GCEnd_V1` `GCStart_V1`ms ( – ).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-409">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="7ed8a-410">Obnovení spravovaných vláken trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-410">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="7ed8a-411">Následující výstup obsahuje příklad pro uvolňování paměti na pozadí a zahrnuje pole procesu, vlákna a události.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-411">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="7ed8a-412">(Ne všechna data jsou zobrazena.)</span><span class="sxs-lookup"><span data-stu-id="7ed8a-412">(Not all data is shown.)</span></span>

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  <span data-ttu-id="7ed8a-413">Událost `GCStart_V1` na 42504816 označuje, že se jedná o uvolňování `1`paměti na pozadí, protože poslední pole je .</span><span class="sxs-lookup"><span data-stu-id="7ed8a-413">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="7ed8a-414">To se stane uvolnění paměti ne.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-414">This becomes garbage collection No.</span></span> <span data-ttu-id="7ed8a-415">102019.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-415">102019.</span></span>

  <span data-ttu-id="7ed8a-416">K `GCStart` události dochází, protože je potřeba dočasné uvolnění paměti před spuštěním uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-416">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="7ed8a-417">To se stane uvolnění paměti ne.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-417">This becomes garbage collection No.</span></span> <span data-ttu-id="7ed8a-418">102020.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-418">102020.</span></span>

  <span data-ttu-id="7ed8a-419">Na 42514170, uvolňování paměti č.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-419">At 42514170, garbage collection No.</span></span> <span data-ttu-id="7ed8a-420">102020 povrchových úprav.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-420">102020 finishes.</span></span> <span data-ttu-id="7ed8a-421">Spravovaná vlákna jsou v tomto okamžiku restartována.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-421">The managed threads are restarted at this point.</span></span> <span data-ttu-id="7ed8a-422">To je dokončeno ve vlákně 4372, který spustil toto uvolnění paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-422">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="7ed8a-423">Na závitu 4744 dochází k pozastavení.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-423">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="7ed8a-424">Toto je jediný čas, kdy pozadí uvolňování paměti má pozastavit spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-424">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="7ed8a-425">Tato doba trvání je přibližně 99ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-425">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="7ed8a-426">Událost `GCEnd` pro uvolňování paměti na pozadí je na 89931423.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-426">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="7ed8a-427">To znamená, že uvolňování paměti na pozadí trvalo asi 47 sekund ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="7ed8a-427">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="7ed8a-428">Zatímco jsou spuštěna spravovaná vlákna, můžete zobrazit libovolný počet dočasných uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-428">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="7ed8a-429">Chcete-li zjistit, co vyvolalo uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-429">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="7ed8a-430">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz, který zobrazí všechna vlákna s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-430">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="7ed8a-431">**~\*Kb**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-431">**~\*kb**</span></span>

  <span data-ttu-id="7ed8a-432">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-432">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="7ed8a-433">Pokud uvolňování paměti byla způsobena oznámení nedostatku paměti z operačního systému, zásobník volání je podobný, s tím rozdílem, že vlákno je finalizační podproces.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-433">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="7ed8a-434">Finalizační podproces získá asynchronní oznámení nedostatku paměti a vyvolá uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-434">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="7ed8a-435">Pokud uvolňování paměti bylo způsobeno přidělení paměti, zásobníku se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-435">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  <span data-ttu-id="7ed8a-436">Pomocník just-in-time (`JIT_New*`) nakonec `GCHeap::GarbageCollectGeneration`zavolá .</span><span class="sxs-lookup"><span data-stu-id="7ed8a-436">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="7ed8a-437">Pokud zjistíte, že uvolnění paměti generace 2 jsou způsobeny přidělení, je nutné určit, které objekty jsou shromažďovány uvolnění paměti generace 2 a jak se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-437">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="7ed8a-438">To znamená, že chcete určit rozdíl mezi počáteční a konec uvolnění paměti generace 2 a objekty, které způsobily kolekci generace 2.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-438">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="7ed8a-439">Zadejte například následující příkaz do ladicího programu, který zobrazí začátek kolekce generace 2:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-439">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="7ed8a-440">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-440">**!dumpheap –stat**</span></span>

  <span data-ttu-id="7ed8a-441">Příklad výstupu (zkrácený pro zobrazení objektů, které využívají nejvíce místa):</span><span class="sxs-lookup"><span data-stu-id="7ed8a-441">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  <span data-ttu-id="7ed8a-442">Opakujte příkaz na konci generace 2:</span><span class="sxs-lookup"><span data-stu-id="7ed8a-442">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="7ed8a-443">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-443">**!dumpheap –stat**</span></span>

  <span data-ttu-id="7ed8a-444">Příklad výstupu (zkrácený pro zobrazení objektů, které využívají nejvíce místa):</span><span class="sxs-lookup"><span data-stu-id="7ed8a-444">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  <span data-ttu-id="7ed8a-445">Objekty `double[]` zmizely z konce výstupu, což znamená, že byly shromážděny.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-445">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="7ed8a-446">Tyto objekty představují přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-446">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="7ed8a-447">Zbývající objekty se příliš nezměnily.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-447">The remaining objects did not change much.</span></span> <span data-ttu-id="7ed8a-448">Proto tyto `double[]` objekty byly důvodem, proč došlo k této generování 2 uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-448">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="7ed8a-449">Dalším krokem je zjistit, `double[]` proč jsou tam objekty a proč zemřely.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-449">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="7ed8a-450">Můžete se zeptat vývojáře kódu, odkud tyto objekty pocházejí, nebo můžete použít příkaz **gcroot.**</span><span class="sxs-lookup"><span data-stu-id="7ed8a-450">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="7ed8a-451">Chcete-li zjistit, zda je vysoké využití procesoru způsobeno uvolňovánípaměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-451">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="7ed8a-452">Korelujte `% Time in GC` hodnotu čítače výkonu paměti s časem procesu.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-452">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="7ed8a-453">Pokud `% Time in GC` hodnota špičky ve stejnou dobu jako čas procesu, uvolňování paměti způsobuje vysoké využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-453">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="7ed8a-454">V opačném případě profil aplikace zjistit, kde dochází k vysoké využití.</span><span class="sxs-lookup"><span data-stu-id="7ed8a-454">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ed8a-455">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ed8a-455">See also</span></span>

- [<span data-ttu-id="7ed8a-456">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="7ed8a-456">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
