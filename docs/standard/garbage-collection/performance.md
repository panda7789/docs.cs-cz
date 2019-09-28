---
title: Uvolnění paměti a výkon
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0d21ab8af3669575a451644deb2b3572fdb7651
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71354024"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="fa2db-102">Uvolnění paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="fa2db-102">Garbage Collection and Performance</span></span>

<a name="top"></a><span data-ttu-id="fa2db-103">Toto téma popisuje problémy související s uvolňováním paměti a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="fa2db-104">Řeší problémy, které se týkají spravované haldy, a vysvětluje, jak minimalizovat vliv uvolňování paměti v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="fa2db-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="fa2db-105">Každý problém obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-105">Each issue has links to procedures that you can use to investigate problems.</span></span>

<span data-ttu-id="fa2db-106">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="fa2db-106">This topic contains the following sections:</span></span>

- [<span data-ttu-id="fa2db-107">Nástroje pro analýzu výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-107">Performance Analysis Tools</span></span>](#performance_analysis_tools)

- [<span data-ttu-id="fa2db-108">Řešení potíží s výkonem</span><span class="sxs-lookup"><span data-stu-id="fa2db-108">Troubleshooting Performance Issues</span></span>](#troubleshooting_performance_issues)

- [<span data-ttu-id="fa2db-109">Pokyny pro řešení potíží</span><span class="sxs-lookup"><span data-stu-id="fa2db-109">Troubleshooting Guidelines</span></span>](#troubleshooting_guidelines)

- [<span data-ttu-id="fa2db-110">Postupy kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-110">Performance Check Procedures</span></span>](#performance_check_procedures)

<a name="performance_analysis_tools"></a>

## <a name="performance-analysis-tools"></a><span data-ttu-id="fa2db-111">Nástroje pro analýzu výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-111">Performance Analysis Tools</span></span>

<span data-ttu-id="fa2db-112">V následujících částech jsou popsány nástroje, které jsou k dispozici pro zkoumání potíží s využitím paměti a uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-112">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="fa2db-113">[Postupy](#performance_check_procedures) uvedené dále v tomto tématu se týkají těchto nástrojů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-113">The [procedures](#performance_check_procedures) provided later in this topic refer to these tools.</span></span>

<a name="perf_counters"></a>

### <a name="memory-performance-counters"></a><span data-ttu-id="fa2db-114">Čítače výkonu paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-114">Memory Performance Counters</span></span>

<span data-ttu-id="fa2db-115">K shromažďování údajů o výkonu můžete použít čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-115">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="fa2db-116">Pokyny najdete v tématu [profilace modulu runtime](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="fa2db-116">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="fa2db-117">Kategorie paměti .NET CLR čítače výkonu, jak je popsáno v tématu [čítače výkonu v .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-117">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

<a name="sos"></a>

### <a name="debugging-with-sos"></a><span data-ttu-id="fa2db-118">Ladění pomocí SOS</span><span class="sxs-lookup"><span data-stu-id="fa2db-118">Debugging with SOS</span></span>

<span data-ttu-id="fa2db-119">K prozkoumání objektů na spravované haldě můžete použít [ladicí program systému Windows (WinDbg)](/windows-hardware/drivers/debugger/index) .</span><span class="sxs-lookup"><span data-stu-id="fa2db-119">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="fa2db-120">Chcete-li nainstalovat nástroj WinDbg, nainstalujte ladicí nástroje pro systém Windows ze stránky [Stáhnout ladicí nástroje pro Windows](/windows-hardware/drivers/debugger/debugger-download-tools) .</span><span class="sxs-lookup"><span data-stu-id="fa2db-120">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

<a name="etw"></a>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="fa2db-121">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-121">Garbage Collection ETW Events</span></span>

<span data-ttu-id="fa2db-122">Trasování událostí pro Windows (ETW) je systém trasování, který doplňuje podporu profilování a ladění poskytovanou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa2db-122">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="fa2db-123">Počínaje .NET Framework 4, [události ETW uvolňování paměti](../../../docs/framework/performance/garbage-collection-etw-events.md) zaznamenávají užitečné informace pro analýzu spravované haldy ze statistického bodu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-123">Starting with the .NET Framework 4, [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="fa2db-124">Například `GCStart_V1` událost, která je vyvolána při výskytu uvolňování paměti, poskytuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="fa2db-124">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="fa2db-125">Které generace objektů se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="fa2db-125">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="fa2db-126">Co aktivovalo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-126">What triggered the garbage collection.</span></span>

- <span data-ttu-id="fa2db-127">Typ uvolňování paměti (souběžné nebo nesouběžné).</span><span class="sxs-lookup"><span data-stu-id="fa2db-127">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="fa2db-128">Protokolování událostí ETW je efektivní a nebude maskovat žádné problémy s výkonem spojené s uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-128">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="fa2db-129">Proces může poskytovat vlastní události ve spojení s událostmi ETW.</span><span class="sxs-lookup"><span data-stu-id="fa2db-129">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="fa2db-130">Při protokolu mohou být události aplikace i události uvolňování paměti v souvislosti s určením, jak a kdy dochází k problémům s haldou.</span><span class="sxs-lookup"><span data-stu-id="fa2db-130">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="fa2db-131">Například serverová aplikace může poskytovat události na začátku a konci žádosti klienta.</span><span class="sxs-lookup"><span data-stu-id="fa2db-131">For example, a server application could provide events at the start and end of a client request.</span></span>

<a name="profiling_api"></a>

### <a name="the-profiling-api"></a><span data-ttu-id="fa2db-132">Rozhraní API profilování</span><span class="sxs-lookup"><span data-stu-id="fa2db-132">The Profiling API</span></span>

<span data-ttu-id="fa2db-133">Rozhraní pro profilaci modulu CLR (Common Language Runtime) poskytují podrobné informace o objektech, které byly ovlivněny během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-133">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="fa2db-134">Profiler může být upozorněn při zahájení a ukončení uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-134">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="fa2db-135">Může poskytovat sestavy o objektech na spravované haldě, včetně identifikace objektů v každé generaci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-135">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="fa2db-136">Další informace najdete v tématu [profilace – přehled](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa2db-136">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="fa2db-137">Profilery můžou poskytovat komplexní informace.</span><span class="sxs-lookup"><span data-stu-id="fa2db-137">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="fa2db-138">Složité profilery ale můžou potenciálně upravit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="fa2db-138">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="fa2db-139">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="fa2db-139">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="fa2db-140">Počínaje .NET Framework 4 umožňuje monitorování prostředků domény aplikace (ARM) hostitelům monitorovat využití procesoru a paměti podle aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="fa2db-140">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="fa2db-141">Další informace najdete v tématu [monitorování prostředků domény aplikace](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="fa2db-141">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>

[<span data-ttu-id="fa2db-142">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fa2db-142">Back to top</span></span>](#top)

<a name="troubleshooting_performance_issues"></a>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="fa2db-143">Řešení potíží s výkonem</span><span class="sxs-lookup"><span data-stu-id="fa2db-143">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="fa2db-144">Prvním krokem je [určit, jestli je problém ve skutečnosti uvolňováním paměti](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="fa2db-144">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="fa2db-145">Pokud zjistíte, že je, vyberte z následujícího seznamu, abyste mohli problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="fa2db-145">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="fa2db-146">Je vyvolána výjimka nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-146">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="fa2db-147">Proces využívá příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-147">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="fa2db-148">Systém uvolňování paměti neuvolňuje objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="fa2db-148">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="fa2db-149">Spravovaná halda je příliš fragmentovaná.</span><span class="sxs-lookup"><span data-stu-id="fa2db-149">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="fa2db-150">Pozastavení uvolňování paměti jsou příliš dlouhé.</span><span class="sxs-lookup"><span data-stu-id="fa2db-150">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="fa2db-151">Generace 0 je příliš velká.</span><span class="sxs-lookup"><span data-stu-id="fa2db-151">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="fa2db-152">Využití CPU při uvolňování paměti je příliš vysoké.</span><span class="sxs-lookup"><span data-stu-id="fa2db-152">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="fa2db-153">Problém: Je vyvolána výjimka nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-153">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="fa2db-154">Existují dva legitimní případy, kdy je spravované <xref:System.OutOfMemoryException> vyvoláno:</span><span class="sxs-lookup"><span data-stu-id="fa2db-154">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="fa2db-155">Nedostatek virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-155">Running out of virtual memory.</span></span>

  <span data-ttu-id="fa2db-156">Systém uvolňování paměti přiděluje paměť ze systému v segmentech předem určené velikosti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-156">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="fa2db-157">Pokud přidělení vyžaduje další segment, ale v virtuální paměti procesu není k dispozici žádný souvislý bezplatný blok, přidělení pro spravovanou haldu se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="fa2db-157">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="fa2db-158">Není dostatek fyzické paměti k přidělení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-158">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="fa2db-159">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-159">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="fa2db-160">Určete, zda je spravovaná výjimka nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-160">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="fa2db-161">Určete, kolik virtuální paměti lze rezervovat.</span><span class="sxs-lookup"><span data-stu-id="fa2db-161">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="fa2db-162">Určete, zda je k dispozici dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-162">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="fa2db-163">Pokud zjistíte, že výjimka není legitimní, obraťte se na zákaznickou službu a podporu Microsoftu s následujícími informacemi:</span><span class="sxs-lookup"><span data-stu-id="fa2db-163">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="fa2db-164">Zásobník s nespravovanou výjimkou paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-164">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="fa2db-165">Úplný výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-165">Full memory dump.</span></span>

- <span data-ttu-id="fa2db-166">Data, která ukážou, že se nejedná o legitimní výjimku při nedostatku paměti, včetně dat, která ukazují, že virtuální nebo fyzická paměť není problémem.</span><span class="sxs-lookup"><span data-stu-id="fa2db-166">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="fa2db-167">Problém: Proces využívá příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-167">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="fa2db-168">Běžným předpokladem je, že zobrazení využití paměti na kartě **výkon** ve Správci úloh systému Windows může indikovat, že se používá příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-168">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="fa2db-169">Tento displej se však vztahuje k pracovní sadě; neposkytuje informace o využití virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-169">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="fa2db-170">Pokud zjistíte, že problém je způsoben spravovanou haldou, je nutné změřit spravovanou haldu v čase a určit tak vzory.</span><span class="sxs-lookup"><span data-stu-id="fa2db-170">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="fa2db-171">Pokud zjistíte, že problém není způsoben spravovanou haldou, je nutné použít nativní ladění.</span><span class="sxs-lookup"><span data-stu-id="fa2db-171">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="fa2db-172">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-172">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="fa2db-173">Určete, kolik virtuální paměti lze rezervovat.</span><span class="sxs-lookup"><span data-stu-id="fa2db-173">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="fa2db-174">Určete, kolik paměti se spravovaná halda zavazuje.</span><span class="sxs-lookup"><span data-stu-id="fa2db-174">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="fa2db-175">Určete velikost paměti, kterou spravovaná halda rezervuje.</span><span class="sxs-lookup"><span data-stu-id="fa2db-175">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="fa2db-176">Určení velkých objektů v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="fa2db-176">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="fa2db-177">Určete odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-177">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="fa2db-178">Problém: Systém uvolňování paměti neuvolňuje objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="fa2db-178">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="fa2db-179">Pokud se zobrazí, jako by se objekty neuvolní, jak je očekáváno pro uvolňování paměti, je nutné určit, zda existují silné odkazy na tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-179">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="fa2db-180">K tomuto problému může dojít také v případě, že neexistuje uvolňování paměti pro generaci, která obsahuje nedoručený objekt, což znamená, že finalizační metoda pro mrtvý objekt nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="fa2db-180">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="fa2db-181">To je možné například v případě, že používáte vícevláknovou aplikaci s jedním vláknem (STA) a vlákno, které služba Finalize Queue nemůže volat.</span><span class="sxs-lookup"><span data-stu-id="fa2db-181">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="fa2db-182">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-182">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="fa2db-183">Podívejte se na odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-183">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="fa2db-184">Určete, zda byl spuštěn finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="fa2db-184">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="fa2db-185">Určete, zda objekty čekají na dokončení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-185">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="fa2db-186">Problém: Spravovaná halda je příliš fragmentovaná.</span><span class="sxs-lookup"><span data-stu-id="fa2db-186">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="fa2db-187">Úroveň fragmentace se počítá jako poměr volného místa v celkové přidělené paměti pro generaci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-187">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="fa2db-188">V případě generace 2 není přijatelná úroveň fragmentace více než 20%.</span><span class="sxs-lookup"><span data-stu-id="fa2db-188">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="fa2db-189">Vzhledem k tomu, že generace 2 může dosáhnout hodně velkých, je poměr fragmentace důležitější než absolutní hodnota.</span><span class="sxs-lookup"><span data-stu-id="fa2db-189">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="fa2db-190">Vynulování volného místa v generaci 0 není problém, protože se jedná o generaci, kde jsou přiděleny nové objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-190">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="fa2db-191">K fragmentaci vždy dochází v haldě velkých objektů, protože není komprimována.</span><span class="sxs-lookup"><span data-stu-id="fa2db-191">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="fa2db-192">Bezplatné objekty, které jsou sousedící, jsou přirozeně sbaleny do jednoho prostoru pro splnění požadavků na přidělení velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-192">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="fa2db-193">Fragmentace se může stát problémem v generaci 1 a generaci 2.</span><span class="sxs-lookup"><span data-stu-id="fa2db-193">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="fa2db-194">Pokud tyto generace mají velké množství volného místa po uvolnění paměti, použití objektu aplikace může vyžadovat úpravu a měli byste zvážit přehodnocení životnosti dlouhodobých objektů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-194">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="fa2db-195">Nadměrné Připnutí objektů může zvýšit fragmentaci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-195">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="fa2db-196">Pokud je fragmentace vysoká, je možné připnout příliš mnoho objektů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-196">If fragmentation is high, too many objects could be pinned.</span></span>

<span data-ttu-id="fa2db-197">Pokud fragmentaci virtuální paměti brání v uvolňování paměti při přidávání segmentů, může to být jedna z následujících příčin:</span><span class="sxs-lookup"><span data-stu-id="fa2db-197">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="fa2db-198">Časté načítání a uvolňování mnoha malých sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-198">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="fa2db-199">Při spolupráci s nespravovaným kódem je uchováváno příliš mnoho odkazů na objekty COM.</span><span class="sxs-lookup"><span data-stu-id="fa2db-199">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="fa2db-200">Vytváření velkých přechodných objektů, což způsobí, že halda velkých objektů často přiděluje a uvolňuje segmenty haldy.</span><span class="sxs-lookup"><span data-stu-id="fa2db-200">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="fa2db-201">Při hostování modulu CLR může aplikace požádat, aby systém uvolňování paměti zachoval své segmenty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-201">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="fa2db-202">Tím se snižuje frekvence přidělení segmentů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-202">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="fa2db-203">Toho je možné dosáhnout použitím příznaku STARTUP_HOARD_GC_VM ve [výčtu STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="fa2db-203">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="fa2db-204">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-204">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="fa2db-205">Určete množství volného místa ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="fa2db-205">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="fa2db-206">Určete počet připnutých objektů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-206">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="fa2db-207">Pokud se domníváte, že neexistují žádné oprávněné příčiny pro fragmentaci, obraťte se na zákaznickou službu a podporu Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-207">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="fa2db-208">Problém: Pozastavení uvolňování paměti jsou příliš dlouhé.</span><span class="sxs-lookup"><span data-stu-id="fa2db-208">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="fa2db-209">Uvolňování paměti funguje v tichém reálném čase, takže aplikace musí být schopná tolerovat některá pozastavení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-209">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="fa2db-210">Kritériem pro měkký reálný čas je to, že 95% operací se musí dokončit včas.</span><span class="sxs-lookup"><span data-stu-id="fa2db-210">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="fa2db-211">V případě souběžného uvolňování paměti můžou spravovaná vlákna běžet během shromažďování, což znamená, že pozastavení jsou velmi minimální.</span><span class="sxs-lookup"><span data-stu-id="fa2db-211">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="fa2db-212">Dočasné uvolňování paměti (generace 0 a 1) jsou poslední jenom několik milisekund, takže snížení pauz většinou není proveditelné.</span><span class="sxs-lookup"><span data-stu-id="fa2db-212">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="fa2db-213">Můžete ale snížit počet pozastavení v kolekcích 2. generace změnou vzoru požadavků na přidělení aplikací.</span><span class="sxs-lookup"><span data-stu-id="fa2db-213">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="fa2db-214">Další přesnější metodou je použít [události ETW pro uvolňování paměti](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="fa2db-214">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="fa2db-215">Časování pro kolekce můžete najít přidáním rozdílů časových razítek pro posloupnost událostí.</span><span class="sxs-lookup"><span data-stu-id="fa2db-215">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="fa2db-216">Celá sekvence kolekce zahrnuje pozastavení prováděcího modulu, uvolňování paměti samotného a obnovení spouštěcího modulu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-216">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="fa2db-217">Pomocí oznámení o [uvolňování paměti](../../../docs/standard/garbage-collection/notifications.md) můžete zjistit, jestli se server chystá mít kolekci 2. generace, a jestli žádosti o přesměrování na jiný server můžou způsobit problémy s pozastavením.</span><span class="sxs-lookup"><span data-stu-id="fa2db-217">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="fa2db-218">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-218">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="fa2db-219">Určete dobu v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-219">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="fa2db-220">Určete, co způsobilo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-220">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="fa2db-221">Problém: Generace 0 je příliš velká.</span><span class="sxs-lookup"><span data-stu-id="fa2db-221">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="fa2db-222">Generace 0 pravděpodobně bude mít větší počet objektů v 64 systému, zvlášť když použijete uvolňování paměti serveru místo uvolnění paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="fa2db-222">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="fa2db-223">Důvodem je to, že prahová hodnota pro aktivaci uvolňování paměti generace 0 je v těchto prostředích vyšší, a kolekce generace 0 může být mnohem větší.</span><span class="sxs-lookup"><span data-stu-id="fa2db-223">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="fa2db-224">Zvýšení výkonu je vylepšeno, pokud aplikace přiděluje více paměti před aktivací uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-224">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="fa2db-225">Problém: Využití CPU při uvolňování paměti je příliš vysoké.</span><span class="sxs-lookup"><span data-stu-id="fa2db-225">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="fa2db-226">Využití CPU bude během uvolňování paměti vysoké.</span><span class="sxs-lookup"><span data-stu-id="fa2db-226">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="fa2db-227">Pokud se v uvolňování paměti stráví významné množství času zpracování, počet kolekcí je příliš častý nebo kolekce je trvalá příliš dlouho.</span><span class="sxs-lookup"><span data-stu-id="fa2db-227">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="fa2db-228">Zvýšená míra přidělení objektů na spravované haldě způsobuje, že se uvolňování paměti objevuje častěji.</span><span class="sxs-lookup"><span data-stu-id="fa2db-228">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="fa2db-229">Snížení míry přidělení omezí četnost uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-229">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="fa2db-230">Sazby přidělení můžete sledovat pomocí `Allocated Bytes/second` čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-230">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="fa2db-231">Další informace najdete v tématu [čítače výkonu v .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="fa2db-231">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="fa2db-232">Doba trvání kolekce je primárně faktorem počtu objektů, které jsou po přidělení zachovány.</span><span class="sxs-lookup"><span data-stu-id="fa2db-232">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="fa2db-233">Systém uvolňování paměti musí projít velkým množstvím paměti, pokud je stále shromažďováno mnoho objektů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-233">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="fa2db-234">Práce na komprimaci pozůstalých je časově náročná.</span><span class="sxs-lookup"><span data-stu-id="fa2db-234">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="fa2db-235">Chcete-li určit, kolik objektů bylo zpracováno během kolekce, nastavte zarážku v ladicím programu na konci uvolňování paměti pro zadanou generaci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-235">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="fa2db-236">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-236">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="fa2db-237">Zjistěte, jestli je vysoké využití procesoru způsobeno uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-237">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="fa2db-238">Nastavte zarážku na konci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-238">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

[<span data-ttu-id="fa2db-239">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fa2db-239">Back to top</span></span>](#top)

<a name="troubleshooting_guidelines"></a>

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="fa2db-240">Pokyny pro řešení potíží</span><span class="sxs-lookup"><span data-stu-id="fa2db-240">Troubleshooting Guidelines</span></span>

<span data-ttu-id="fa2db-241">Tato část popisuje pokyny, které byste měli vzít v úvahu při zahájení šetření.</span><span class="sxs-lookup"><span data-stu-id="fa2db-241">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="fa2db-242">Uvolnění paměti pracovní stanice nebo serveru</span><span class="sxs-lookup"><span data-stu-id="fa2db-242">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="fa2db-243">Určete, zda používáte správný typ uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-243">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="fa2db-244">Pokud vaše aplikace používá více vláken a instancí objektů, použijte místo uvolňování paměti pracovních stanic Server uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="fa2db-244">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="fa2db-245">Uvolňování paměti serveru funguje ve více vláknech, zatímco uvolňování paměti pracovní stanice vyžaduje více instancí aplikace, aby spouštěla vlastní vlákna uvolňování paměti a mohla konkurovat času procesoru.</span><span class="sxs-lookup"><span data-stu-id="fa2db-245">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="fa2db-246">Aplikace, která má nízké zatížení a provádí úlohy na pozadí, jako je například služba, může použít uvolňování paměti pracovní stanice se zakázaným souběžným uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-246">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="fa2db-247">Kdy změřit velikost spravované haldy</span><span class="sxs-lookup"><span data-stu-id="fa2db-247">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="fa2db-248">Pokud nepoužíváte Profiler, budete muset vytvořit jednotný měřicí vzor pro efektivní diagnostiku problémů s výkonem.</span><span class="sxs-lookup"><span data-stu-id="fa2db-248">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="fa2db-249">Pro vytvoření plánu Vezměte v úvahu následující body:</span><span class="sxs-lookup"><span data-stu-id="fa2db-249">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="fa2db-250">Pokud měříte po uvolnění paměti 2. generace, celá spravovaná halda bude bez uvolnění paměti (nedoručené objekty).</span><span class="sxs-lookup"><span data-stu-id="fa2db-250">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="fa2db-251">Pokud měříte hned po uvolnění paměti generace 0, objekty v generacích 1 a 2 nebudou dosud shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="fa2db-251">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="fa2db-252">Pokud měříte těsně před uvolňováním paměti, měříte co nejvíce přidělení, než začne uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-252">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="fa2db-253">Měření během uvolňování paměti je problematické, protože datové struktury uvolňování paměti nejsou v platném stavu pro procházení a nemusí být schopné poskytnout kompletní výsledky.</span><span class="sxs-lookup"><span data-stu-id="fa2db-253">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="fa2db-254">Jedná se o účel.</span><span class="sxs-lookup"><span data-stu-id="fa2db-254">This is by design.</span></span>

- <span data-ttu-id="fa2db-255">Pokud používáte uvolňování paměti pracovní stanice s souběžným uvolňováním paměti, uvolněné objekty se nekomprimuje, takže velikost haldy může být stejná nebo větší (fragmentace se může zdát, že je větší).</span><span class="sxs-lookup"><span data-stu-id="fa2db-255">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="fa2db-256">Souběžné uvolňování paměti v generaci 2 je zpožděno, pokud je zatížení fyzické paměti příliš vysoké.</span><span class="sxs-lookup"><span data-stu-id="fa2db-256">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="fa2db-257">Následující postup popisuje, jak nastavit zarážku, abyste mohli změřit spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-257">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="fa2db-258">Nastavení zarážky na konci uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-258">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="fa2db-259">V programu WinDbg s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-259">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="fa2db-260">**knihovny mscorwks BP WKS:: GCHeap:: RestartEE "j (DWO (knihovny Mscorwks! WKS:: GCHeap:: GcCondemnedGeneration) = = 2) ' KB '; ' g ' "**</span><span class="sxs-lookup"><span data-stu-id="fa2db-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="fa2db-261">kde **GcCondemnedGeneration** je nastaveno na požadovanou generaci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-261">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="fa2db-262">Tento příkaz vyžaduje soukromé symboly.</span><span class="sxs-lookup"><span data-stu-id="fa2db-262">This command requires private symbols.</span></span>

  <span data-ttu-id="fa2db-263">Tento příkaz vynutí přerušení, pokud je **RestartEE** provedeno po uvolnění objektů generace 2 pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-263">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="fa2db-264">V uvolňování paměti serveru pouze jedno vlákno volá **RestartEE**, takže během uvolňování paměti 2. generace dojde k zarážce pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="fa2db-264">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

[<span data-ttu-id="fa2db-265">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fa2db-265">Back to top</span></span>](#top)

<a name="performance_check_procedures"></a>

## <a name="performance-check-procedures"></a><span data-ttu-id="fa2db-266">Postupy kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="fa2db-266">Performance Check Procedures</span></span>

<span data-ttu-id="fa2db-267">Tato část popisuje následující postupy k izolaci příčiny problému s výkonem:</span><span class="sxs-lookup"><span data-stu-id="fa2db-267">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="fa2db-268">Určete, zda je problém způsoben uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-268">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="fa2db-269">Určete, zda je spravovaná výjimka nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-269">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="fa2db-270">Určete, kolik virtuální paměti lze rezervovat.</span><span class="sxs-lookup"><span data-stu-id="fa2db-270">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="fa2db-271">Určete, zda je k dispozici dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-271">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="fa2db-272">Určete, kolik paměti se spravovaná halda zavazuje.</span><span class="sxs-lookup"><span data-stu-id="fa2db-272">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="fa2db-273">Určete velikost paměti, kterou spravovaná halda rezervuje.</span><span class="sxs-lookup"><span data-stu-id="fa2db-273">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="fa2db-274">Určení velkých objektů v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="fa2db-274">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="fa2db-275">Určete odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-275">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="fa2db-276">Určete, zda byl spuštěn finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="fa2db-276">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="fa2db-277">Určete, zda objekty čekají na dokončení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-277">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="fa2db-278">Určete množství volného místa ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="fa2db-278">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="fa2db-279">Určete počet připnutých objektů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-279">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="fa2db-280">Určete dobu v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-280">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="fa2db-281">Určete, co aktivovalo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-281">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="fa2db-282">Určete, zda je vysoké využití procesoru způsobeno uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-282">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="fa2db-283">Zjištění, zda je problém způsoben uvolňováním paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-283">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="fa2db-284">Prověřte následující dvě čítače výkonu paměti:</span><span class="sxs-lookup"><span data-stu-id="fa2db-284">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="fa2db-285">**% Času v GC**.</span><span class="sxs-lookup"><span data-stu-id="fa2db-285">**% Time in GC**.</span></span> <span data-ttu-id="fa2db-286">Zobrazuje procento uplynulého času stráveného prováděním uvolňování paměti po posledním cyklu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-286">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="fa2db-287">Pomocí tohoto čítače určíte, zda je uvolňování paměti příliš mnoho času na zpřístupnění spravovaného prostoru haldy.</span><span class="sxs-lookup"><span data-stu-id="fa2db-287">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="fa2db-288">Pokud je doba strávená uvolňováním paměti poměrně nízká, může to znamenat problém s prostředky mimo spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-288">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="fa2db-289">Tento čítač nemusí být přesný, pokud je zapojeno souběžné a uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="fa2db-289">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="fa2db-290">**# Celkový počet potvrzených bajtů**</span><span class="sxs-lookup"><span data-stu-id="fa2db-290">**# Total committed Bytes**.</span></span> <span data-ttu-id="fa2db-291">Zobrazuje velikost virtuální paměti, která je aktuálně potvrzena systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-291">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="fa2db-292">Pomocí tohoto čítače určíte, zda paměť využívaná systémem uvolňování paměti je nadměrná část paměti, kterou vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="fa2db-292">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="fa2db-293">Většina čítačů výkonu paměti se aktualizuje na konci každého uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-293">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="fa2db-294">Proto nemusí odrážet aktuální podmínky, o kterých chcete získat informace.</span><span class="sxs-lookup"><span data-stu-id="fa2db-294">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="fa2db-295">Chcete-li určit, zda je výjimka nedostatek paměti spravovaná</span><span class="sxs-lookup"><span data-stu-id="fa2db-295">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="fa2db-296">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte příkaz pro výjimku tisku (**PE**):</span><span class="sxs-lookup"><span data-stu-id="fa2db-296">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="fa2db-297">**! PE**</span><span class="sxs-lookup"><span data-stu-id="fa2db-297">**!pe**</span></span>

    <span data-ttu-id="fa2db-298">Pokud je výjimka spravovaná, <xref:System.OutOfMemoryException> je zobrazena jako typ výjimky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-298">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="fa2db-299">Pokud výstup neurčuje výjimku, je nutné určit, ze kterého vlákna je výjimka nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-299">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="fa2db-300">Zadejte následující příkaz v ladicím programu pro zobrazení všech vláken s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="fa2db-300">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="fa2db-301">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="fa2db-301">**~\*kb**</span></span>

    <span data-ttu-id="fa2db-302">Vlákno se zásobníkem, který obsahuje volání výjimek, je určeno `RaiseTheException` argumentem.</span><span class="sxs-lookup"><span data-stu-id="fa2db-302">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="fa2db-303">Toto je spravovaný objekt výjimky.</span><span class="sxs-lookup"><span data-stu-id="fa2db-303">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="fa2db-304">Pomocí následujícího příkazu můžete vypsat vnořené výjimky.</span><span class="sxs-lookup"><span data-stu-id="fa2db-304">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="fa2db-305">**! PE – vnořené**</span><span class="sxs-lookup"><span data-stu-id="fa2db-305">**!pe -nested**</span></span>

    <span data-ttu-id="fa2db-306">Pokud nenajdete žádné výjimky, výjimka nedostatek paměti pochází z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-306">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="fa2db-307">Určení velikosti virtuální paměti, která může být vyhrazena</span><span class="sxs-lookup"><span data-stu-id="fa2db-307">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="fa2db-308">V programu WinDbg s načtením rozšíření ladicí program SOS zadejte následující příkaz, který získá největší volnou oblast:</span><span class="sxs-lookup"><span data-stu-id="fa2db-308">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="fa2db-309">**! Adresa – souhrn**</span><span class="sxs-lookup"><span data-stu-id="fa2db-309">**!address -summary**</span></span>

  <span data-ttu-id="fa2db-310">Zobrazí se největší volná oblast, jak je znázorněno v následujícím výstupu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-310">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="fa2db-311">V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové soustavě).</span><span class="sxs-lookup"><span data-stu-id="fa2db-311">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="fa2db-312">Tato oblast je mnohem menší, než systém uvolňování paměti potřebuje pro segment.</span><span class="sxs-lookup"><span data-stu-id="fa2db-312">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="fa2db-313">-nebo-</span><span class="sxs-lookup"><span data-stu-id="fa2db-313">-or-</span></span>

- <span data-ttu-id="fa2db-314">Použijte příkaz **vmstat** :</span><span class="sxs-lookup"><span data-stu-id="fa2db-314">Use the **vmstat** command:</span></span>

  <span data-ttu-id="fa2db-315">**! vmstat**</span><span class="sxs-lookup"><span data-stu-id="fa2db-315">**!vmstat**</span></span>

  <span data-ttu-id="fa2db-316">Největší volná oblast je největší hodnota ve sloupci MAXIMUM, jak je znázorněno v následujícím výstupu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-316">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

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

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="fa2db-317">Určení, zda je k dispozici dostatek fyzické paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-317">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="fa2db-318">Spusťte Správce úloh systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fa2db-318">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="fa2db-319">Na kartě **výkon** se podívejte na potvrzenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-319">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="fa2db-320">(Ve Windows 7 se podívejte na **potvrzení změn (KB)** ve **skupině systém**.)</span><span class="sxs-lookup"><span data-stu-id="fa2db-320">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="fa2db-321">Pokud je **Celkový součet** blízko **limitu**, dochází k nedostatku fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-321">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="fa2db-322">Určení množství paměti, kterou spravovaná halda potvrzování</span><span class="sxs-lookup"><span data-stu-id="fa2db-322">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="fa2db-323">Pomocí čítače výkonu paměti získáte počet bajtů, které spravovaná halda potvrzování. `# Total committed bytes`</span><span class="sxs-lookup"><span data-stu-id="fa2db-323">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="fa2db-324">Systém uvolňování paměti potvrdí bloky dat v segmentu podle potřeby, nikoli ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-324">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="fa2db-325">Nepoužívejte `# Bytes in all Heaps` čítač výkonu, protože nepředstavuje skutečné využití paměti spravovanou haldou.</span><span class="sxs-lookup"><span data-stu-id="fa2db-325">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="fa2db-326">Velikost generování je zahrnuta v této hodnotě a je to skutečná velikost prahové hodnoty, což je velikost, která vychází z uvolňování paměti, pokud je generování vyplněno objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-326">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="fa2db-327">Proto je tato hodnota obvykle nula.</span><span class="sxs-lookup"><span data-stu-id="fa2db-327">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="fa2db-328">Určení velikosti paměti, kterou spravovaná halda vyhradí</span><span class="sxs-lookup"><span data-stu-id="fa2db-328">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="fa2db-329">Použijte čítač výkonu paměti. `# Total reserved bytes`</span><span class="sxs-lookup"><span data-stu-id="fa2db-329">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="fa2db-330">Systém uvolňování paměti rezervuje paměť v segmentech a můžete určit, kde se bude segment spouštět, pomocí příkazu **eeheap** .</span><span class="sxs-lookup"><span data-stu-id="fa2db-330">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="fa2db-331">I když můžete určit velikost paměti, kterou systém uvolňování paměti přiděluje pro každý segment, velikost segmentu je specifická pro konkrétní implementaci a může se kdykoli změnit, a to i v pravidelných aktualizacích.</span><span class="sxs-lookup"><span data-stu-id="fa2db-331">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="fa2db-332">Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-332">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="fa2db-333">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-333">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="fa2db-334">**! eeheap – GC**</span><span class="sxs-lookup"><span data-stu-id="fa2db-334">**!eeheap -gc**</span></span>

  <span data-ttu-id="fa2db-335">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="fa2db-335">The result is as follows.</span></span>

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

  <span data-ttu-id="fa2db-336">Adresy označené "segment" představují počáteční adresy segmentů.</span><span class="sxs-lookup"><span data-stu-id="fa2db-336">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="fa2db-337">Určení velkých objektů v generaci 2</span><span class="sxs-lookup"><span data-stu-id="fa2db-337">To determine large objects in generation 2</span></span>

- <span data-ttu-id="fa2db-338">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-338">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="fa2db-339">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="fa2db-339">**!dumpheap –stat**</span></span>

  <span data-ttu-id="fa2db-340">Pokud je spravovaná halda velká, může dokončení **dumpheap** chvíli trvat.</span><span class="sxs-lookup"><span data-stu-id="fa2db-340">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="fa2db-341">Můžete zahájit analýzu z posledních několika řádků výstupu, protože obsahují seznam objektů, které používají nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="fa2db-341">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="fa2db-342">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fa2db-342">For example:</span></span>

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

  <span data-ttu-id="fa2db-343">Poslední uvedený objekt je řetězec a zabírá nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="fa2db-343">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="fa2db-344">Můžete kontrolovat svoji aplikaci, abyste viděli, jak lze optimalizovat objekty řetězců.</span><span class="sxs-lookup"><span data-stu-id="fa2db-344">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="fa2db-345">Chcete-li zobrazit řetězce, které jsou v rozmezí 150 až 200 bajtů, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-345">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="fa2db-346">**! dumpheap-Type System. String-min 150-max 200**</span><span class="sxs-lookup"><span data-stu-id="fa2db-346">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="fa2db-347">Příkladem výsledků je následující.</span><span class="sxs-lookup"><span data-stu-id="fa2db-347">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="fa2db-348">Použití celého čísla namísto řetězce pro ID může být efektivnější.</span><span class="sxs-lookup"><span data-stu-id="fa2db-348">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="fa2db-349">Pokud se stejný řetězec opakuje v tisících, zvažte, že se bude považovat za interning.</span><span class="sxs-lookup"><span data-stu-id="fa2db-349">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="fa2db-350">Další informace o použití řetězců naleznete v tématu Reference k <xref:System.String.Intern%2A?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="fa2db-350">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="fa2db-351">Určení odkazů na objekty</span><span class="sxs-lookup"><span data-stu-id="fa2db-351">To determine references to objects</span></span>

- <span data-ttu-id="fa2db-352">V programu WinDbg s načtením rozšíření ladicí program SOS zadejte následující příkaz pro výpis odkazů na objekty:</span><span class="sxs-lookup"><span data-stu-id="fa2db-352">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="fa2db-353">**! gcroot**</span><span class="sxs-lookup"><span data-stu-id="fa2db-353">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="fa2db-354">Chcete-li určit odkazy na konkrétní objekt, zadejte adresu:</span><span class="sxs-lookup"><span data-stu-id="fa2db-354">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="fa2db-355">**! gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="fa2db-355">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="fa2db-356">Kořeny nalezené v zásobnících můžou být falešně pozitivní.</span><span class="sxs-lookup"><span data-stu-id="fa2db-356">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="fa2db-357">Další informace získáte pomocí příkazu `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="fa2db-357">For more information, use the command `!help gcroot`.</span></span>

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

  <span data-ttu-id="fa2db-358">Dokončení příkazu **gcroot** může trvat dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-358">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="fa2db-359">Libovolný objekt, který není uvolněn uvolňováním paměti, je živý objekt.</span><span class="sxs-lookup"><span data-stu-id="fa2db-359">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="fa2db-360">To znamená, že některé kořenové složky jsou přímo nebo nepřímo uchovávány na objekt, takže **gcroot** by měl vrátit informace o cestě k objektu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-360">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="fa2db-361">Měli byste prošetřit vrácené grafy a zjistit, proč se na tyto objekty stále odkazuje.</span><span class="sxs-lookup"><span data-stu-id="fa2db-361">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="fa2db-362">Určení, zda byl spuštěn finalizační metoda</span><span class="sxs-lookup"><span data-stu-id="fa2db-362">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="fa2db-363">Spusťte testovací program, který obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="fa2db-363">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="fa2db-364">Pokud test problém vyřeší, znamená to, že systém uvolňování paměti neuvolňuje objekty, protože byly pozastaveny finalizační metody pro tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-364">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="fa2db-365"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metoda umožňuje, aby finalizační metody dokončily své úkoly a vyřešily problém.</span><span class="sxs-lookup"><span data-stu-id="fa2db-365">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="fa2db-366">Určení, zda objekty čekají na dokončení</span><span class="sxs-lookup"><span data-stu-id="fa2db-366">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="fa2db-367">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-367">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="fa2db-368">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="fa2db-368">**!finalizequeue**</span></span>

    <span data-ttu-id="fa2db-369">Podívejte se na počet objektů, které jsou připravené k dokončení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-369">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="fa2db-370">Pokud je číslo vysoké, je nutné prostudovat, proč tyto finalizační metody nemůžou průběžně postupovat, nebo nemůže rychle probíhat.</span><span class="sxs-lookup"><span data-stu-id="fa2db-370">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="fa2db-371">Výstup vláken získáte tak, že zadáte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-371">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="fa2db-372">**vlákna – speciální**</span><span class="sxs-lookup"><span data-stu-id="fa2db-372">**threads -special**</span></span>

    <span data-ttu-id="fa2db-373">Tento příkaz poskytuje výstup jako následující.</span><span class="sxs-lookup"><span data-stu-id="fa2db-373">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="fa2db-374">Finalizační vlákno indikuje, který finalizační metodu (pokud existuje) se právě spouští.</span><span class="sxs-lookup"><span data-stu-id="fa2db-374">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="fa2db-375">Když finalizační vlákno nespouští žádné finalizační metody, čeká na událost, aby ji informovala o své práci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-375">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="fa2db-376">Ve většině případů se v tomto stavu zobrazí finalizační vlákno, protože běží na THREAD_HIGHEST_PRIORITY a má za následek, že se mají dokončit spuštěné finalizační metody, pokud jsou nějaké velmi rychlé.</span><span class="sxs-lookup"><span data-stu-id="fa2db-376">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="fa2db-377">Určení množství volného místa ve spravované haldě</span><span class="sxs-lookup"><span data-stu-id="fa2db-377">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="fa2db-378">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-378">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="fa2db-379">**! dumpheap – typ Free – stat**</span><span class="sxs-lookup"><span data-stu-id="fa2db-379">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="fa2db-380">Tento příkaz zobrazí celkovou velikost všech bezplatných objektů na spravované haldě, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-380">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="fa2db-381">Chcete-li zjistit volné místo v generaci 0, zadejte následující příkaz pro informace o spotřebě paměti podle generace:</span><span class="sxs-lookup"><span data-stu-id="fa2db-381">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="fa2db-382">**! eeheap – GC**</span><span class="sxs-lookup"><span data-stu-id="fa2db-382">**!eeheap -gc**</span></span>

  <span data-ttu-id="fa2db-383">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-383">This command displays output similar to the following.</span></span> <span data-ttu-id="fa2db-384">Poslední řádek zobrazuje dočasný segment.</span><span class="sxs-lookup"><span data-stu-id="fa2db-384">The last line shows the ephemeral segment.</span></span>

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

- <span data-ttu-id="fa2db-385">Vypočítat místo využívané v generaci 0:</span><span class="sxs-lookup"><span data-stu-id="fa2db-385">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="fa2db-386">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="fa2db-386">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="fa2db-387">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="fa2db-387">The result is as follows.</span></span> <span data-ttu-id="fa2db-388">Generace 0 je přibližně 9 MB.</span><span class="sxs-lookup"><span data-stu-id="fa2db-388">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="fa2db-389">Následující příkaz vypíše volné místo v rámci rozsahu generace 0:</span><span class="sxs-lookup"><span data-stu-id="fa2db-389">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="fa2db-390">**! dumpheap-typ Free-stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="fa2db-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="fa2db-391">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="fa2db-391">The result is as follows.</span></span>

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

  <span data-ttu-id="fa2db-392">Tento výstup ukazuje, že část haldy generace 0 používá 9 MB prostoru pro objekty a má 7 MB volného místa.</span><span class="sxs-lookup"><span data-stu-id="fa2db-392">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="fa2db-393">Tato analýza zobrazuje rozsah, ke kterému generace 0 přispívá ke fragmentaci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-393">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="fa2db-394">Tato velikost využití haldy by měla být zlevněná od celkové částky jako příčina fragmentace dlouhodobými objekty.</span><span class="sxs-lookup"><span data-stu-id="fa2db-394">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="fa2db-395">Určení počtu připnutých objektů</span><span class="sxs-lookup"><span data-stu-id="fa2db-395">To determine the number of pinned objects</span></span>

- <span data-ttu-id="fa2db-396">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa2db-396">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="fa2db-397">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="fa2db-397">**!gchandles**</span></span>

  <span data-ttu-id="fa2db-398">Zobrazené statistiky obsahují počet připnutých popisovačů, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fa2db-398">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="fa2db-399">Určení doby v uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-399">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="fa2db-400">Prověřte čítač výkonu paměti. `% Time in GC`</span><span class="sxs-lookup"><span data-stu-id="fa2db-400">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="fa2db-401">Hodnota se vypočítává pomocí časového intervalu vzorkování.</span><span class="sxs-lookup"><span data-stu-id="fa2db-401">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="fa2db-402">Vzhledem k tomu, že počítadla jsou aktualizována na konci každého uvolňování paměti, aktuální vzorek bude mít stejnou hodnotu jako předchozí vzorek, pokud během intervalu nedošlo k žádným kolekcím.</span><span class="sxs-lookup"><span data-stu-id="fa2db-402">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="fa2db-403">Čas shromažďování dat je získán vynásobením času intervalu vzorkování s procentuální hodnotou.</span><span class="sxs-lookup"><span data-stu-id="fa2db-403">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="fa2db-404">Následující data znázorňují čtyři intervaly vzorkování dvou sekund pro studii 8 sekund.</span><span class="sxs-lookup"><span data-stu-id="fa2db-404">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="fa2db-405">Sloupce `Gen0`, `Gen1` a`Gen2` zobrazují počet uvolňování paměti, ke kterým došlo během daného intervalu pro danou generaci.</span><span class="sxs-lookup"><span data-stu-id="fa2db-405">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="fa2db-406">Tyto informace se nezobrazují, když dojde k uvolnění paměti, ale můžete určit počet uvolňování paměti, ke kterým došlo v časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-406">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="fa2db-407">V případě nejhoršího případu bylo dokončeno uvolňování paměti desáté generace 0 na začátku druhého intervalu a jedenácté uvolňování paměti 0 na konci pátého intervalu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-407">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="fa2db-408">Doba mezi koncem desátého a koncem jedenáctého uvolňování paměti je přibližně 2 sekundy a čítač výkonu zobrazuje 3%, takže doba trvání jedenáctého uvolňování paměti 0 (2 sekundy \* 3% = 60ms).</span><span class="sxs-lookup"><span data-stu-id="fa2db-408">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="fa2db-409">V tomto příkladu je 5 teček.</span><span class="sxs-lookup"><span data-stu-id="fa2db-409">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="fa2db-410">Druhá kolekce paměti 2. generace začala během třetího intervalu a skončila v pátém intervalu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-410">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="fa2db-411">Za nejhorší případ byl poslední uvolňování paměti pro kolekci generace 0, která skončila na začátku druhého intervalu, a uvolnění paměti 2. generace bylo dokončeno na konci pátého intervalu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-411">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="fa2db-412">Proto je čas mezi koncem uvolňování paměti generace 0 a koncem uvolňování paměti 2. generace 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="fa2db-412">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="fa2db-413">Vzhledem k tomu, že počítadlo `% Time in GC` je 20%, pak maximální doba, po kterou by bylo možné považovat uvolňování paměti 2. generace, je (4 sekundy \* 20% = 800ms).</span><span class="sxs-lookup"><span data-stu-id="fa2db-413">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="fa2db-414">Alternativně můžete určit délku uvolňování paměti pomocí [událostí ETW pro uvolňování paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace a určit dobu trvání uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-414">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="fa2db-415">Například následující data ukazují sekvenci události, ke které došlo během nesouběžného uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-415">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

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

  <span data-ttu-id="fa2db-416">Pozastavení spravovaného vlákna trvalo 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="fa2db-416">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="fa2db-417">Skutečné uvolňování paměti trvalo 4,8 ms (`GCEnd_V1` – `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="fa2db-417">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="fa2db-418">Obnovení spravovaných vláken trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="fa2db-418">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="fa2db-419">Následující výstup poskytuje příklad pro uvolňování paměti na pozadí a obsahuje pole proces, vlákno a událost.</span><span class="sxs-lookup"><span data-stu-id="fa2db-419">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="fa2db-420">(Ne všechna data jsou zobrazena.)</span><span class="sxs-lookup"><span data-stu-id="fa2db-420">(Not all data is shown.)</span></span>

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

  <span data-ttu-id="fa2db-421">Událost v 42504816 označuje, že se jedná o uvolňování paměti na pozadí, protože poslední pole `1`je. `GCStart_V1`</span><span class="sxs-lookup"><span data-stu-id="fa2db-421">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="fa2db-422">To se v tomto případě stalo uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-422">This becomes garbage collection No.</span></span> <span data-ttu-id="fa2db-423">102019.</span><span class="sxs-lookup"><span data-stu-id="fa2db-423">102019.</span></span>

  <span data-ttu-id="fa2db-424">K `GCStart` události dochází, protože před spuštěním uvolňování paměti na pozadí je zapotřebí dočasné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-424">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="fa2db-425">To se v tomto případě stalo uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-425">This becomes garbage collection No.</span></span> <span data-ttu-id="fa2db-426">102020.</span><span class="sxs-lookup"><span data-stu-id="fa2db-426">102020.</span></span>

  <span data-ttu-id="fa2db-427">V 42514170, č. uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-427">At 42514170, garbage collection No.</span></span> <span data-ttu-id="fa2db-428">102020 dokončí.</span><span class="sxs-lookup"><span data-stu-id="fa2db-428">102020 finishes.</span></span> <span data-ttu-id="fa2db-429">Spravovaná vlákna jsou v tuto chvíli restartována.</span><span class="sxs-lookup"><span data-stu-id="fa2db-429">The managed threads are restarted at this point.</span></span> <span data-ttu-id="fa2db-430">Tato operace je dokončena ve vláknu 4372, které aktivovalo tuto kolekci paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="fa2db-430">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="fa2db-431">Na vlákně 4744 dojde k pozastavení.</span><span class="sxs-lookup"><span data-stu-id="fa2db-431">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="fa2db-432">Toto je jediná doba, s jakou má uvolňování paměti na pozadí pozastavit spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="fa2db-432">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="fa2db-433">Toto trvání je přibližně 99ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="fa2db-433">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="fa2db-434">`GCEnd` Událost pro uvolňování paměti na pozadí je 89931423.</span><span class="sxs-lookup"><span data-stu-id="fa2db-434">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="fa2db-435">To znamená, že uvolňování paměti na pozadí uplynulo pro přibližně 47seconds ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="fa2db-435">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="fa2db-436">I když jsou spuštěná spravovaná vlákna, vidíte libovolný počet dočasných uvolňování paměti, ke kterým dochází.</span><span class="sxs-lookup"><span data-stu-id="fa2db-436">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="fa2db-437">Určení toho, co vyvolalo uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-437">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="fa2db-438">V ladicím programu WinDbg nebo Visual Studio s načteným rozšířením ladicího programu SOS zadejte následující příkaz pro zobrazení všech vláken s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="fa2db-438">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="fa2db-439">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="fa2db-439">**~\*kb**</span></span>

  <span data-ttu-id="fa2db-440">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="fa2db-440">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="fa2db-441">Pokud uvolňování paměti bylo způsobeno oznámením o nedostatku paměti z operačního systému, je zásobník volání podobný, s tím rozdílem, že vlákno je finalizační vlákno.</span><span class="sxs-lookup"><span data-stu-id="fa2db-441">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="fa2db-442">Finalizační vlákno získá oznámení o asynchronní nedostatku paměti a vyřadí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fa2db-442">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="fa2db-443">Pokud uvolňování paměti bylo způsobeno přidělením paměti, zásobník se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="fa2db-443">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

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

  <span data-ttu-id="fa2db-444">Nakonec se volá`JIT_New*` `GCHeap::GarbageCollectGeneration`pomocník za běhu ().</span><span class="sxs-lookup"><span data-stu-id="fa2db-444">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="fa2db-445">Pokud zjistíte, že jsou uvolňovány paměti generace 2 způsobeny přidělením, je nutné určit, které objekty jsou shromažďovány uvolňováním paměti 2. generace a jak se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="fa2db-445">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="fa2db-446">To znamená, že chcete určit rozdíl mezi začátkem a koncem uvolňování paměti 2. generace a objekty, které způsobily kolekci 2. generace.</span><span class="sxs-lookup"><span data-stu-id="fa2db-446">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="fa2db-447">Zadejte například následující příkaz v ladicím programu, který zobrazí začátek kolekce generace 2:</span><span class="sxs-lookup"><span data-stu-id="fa2db-447">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="fa2db-448">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="fa2db-448">**!dumpheap –stat**</span></span>

  <span data-ttu-id="fa2db-449">Příklad výstupu (zkráceně pro zobrazení objektů, které používají nejvíce místa):</span><span class="sxs-lookup"><span data-stu-id="fa2db-449">Example output (abridged to show the objects that use the most space):</span></span>

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

  <span data-ttu-id="fa2db-450">Opakujte tento příkaz na konci generace 2:</span><span class="sxs-lookup"><span data-stu-id="fa2db-450">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="fa2db-451">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="fa2db-451">**!dumpheap –stat**</span></span>

  <span data-ttu-id="fa2db-452">Příklad výstupu (zkráceně pro zobrazení objektů, které používají nejvíce místa):</span><span class="sxs-lookup"><span data-stu-id="fa2db-452">Example output (abridged to show the objects that use the most space):</span></span>

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

  <span data-ttu-id="fa2db-453">`double[]` Objekty zmizely na konci výstupu, což znamená, že byly shromážděny.</span><span class="sxs-lookup"><span data-stu-id="fa2db-453">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="fa2db-454">Tyto objekty jsou přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="fa2db-454">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="fa2db-455">Zbývající objekty se nezměnily mnohem.</span><span class="sxs-lookup"><span data-stu-id="fa2db-455">The remaining objects did not change much.</span></span> <span data-ttu-id="fa2db-456">Proto by tyto `double[]` objekty byly důvodem, proč došlo k této chybě uvolňování paměti 2. generace.</span><span class="sxs-lookup"><span data-stu-id="fa2db-456">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="fa2db-457">V dalším kroku zjistíte, proč `double[]` jsou objekty tam a proč uhynulé.</span><span class="sxs-lookup"><span data-stu-id="fa2db-457">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="fa2db-458">Můžete požádat vývojáře kódu, ze kterého pocházejí tyto objekty, nebo můžete použít příkaz **gcroot** .</span><span class="sxs-lookup"><span data-stu-id="fa2db-458">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="fa2db-459">Určení, zda vysoké využití procesoru je způsobeno uvolňováním paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-459">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="fa2db-460">Proveďte korelaci hodnoty čítače výkonu pamětisčasemprocesu.`% Time in GC`</span><span class="sxs-lookup"><span data-stu-id="fa2db-460">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="fa2db-461">Pokud je `% Time in GC` hodnota špičky ve stejnou dobu jako doba zpracování, uvolňování paměti způsobuje vysoké využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="fa2db-461">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="fa2db-462">V opačném případě profilujte aplikaci, abyste zjistili, kde dochází k vysokému využití.</span><span class="sxs-lookup"><span data-stu-id="fa2db-462">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa2db-463">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa2db-463">See also</span></span>

- [<span data-ttu-id="fa2db-464">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="fa2db-464">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
