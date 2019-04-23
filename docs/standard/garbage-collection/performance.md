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
ms.openlocfilehash: 9aa04051a8aad56c653eaee1a79fb48a849cf377
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310561"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="8b865-102">Uvolnění paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="8b865-102">Garbage Collection and Performance</span></span>
<a name="top"></a> <span data-ttu-id="8b865-103">Toto téma popisuje problémy spojené s uvolňování paměti kolekce a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="8b865-104">Řeší problémy, které se vztahují na spravované haldě a vysvětluje, jak minimalizovat dopad uvolňování paměti u svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="8b865-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="8b865-105">Všechny problémy obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.</span><span class="sxs-lookup"><span data-stu-id="8b865-105">Each issue has links to procedures that you can use to investigate problems.</span></span>  
  
 <span data-ttu-id="8b865-106">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="8b865-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="8b865-107">Nástroje pro analýzu výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-107">Performance Analysis Tools</span></span>](#performance_analysis_tools)  
  
-   [<span data-ttu-id="8b865-108">Řešení potíží s problémy s výkonem</span><span class="sxs-lookup"><span data-stu-id="8b865-108">Troubleshooting Performance Issues</span></span>](#troubleshooting_performance_issues)  
  
-   [<span data-ttu-id="8b865-109">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="8b865-109">Troubleshooting Guidelines</span></span>](#troubleshooting_guidelines)  
  
-   [<span data-ttu-id="8b865-110">Výkon zaškrtněte procedury</span><span class="sxs-lookup"><span data-stu-id="8b865-110">Performance Check Procedures</span></span>](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a><span data-ttu-id="8b865-111">Nástroje pro analýzu výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-111">Performance Analysis Tools</span></span>  
 <span data-ttu-id="8b865-112">Následující části popisují nástroje, které jsou k dispozici pro zkoumání problémů paměti využití a uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="8b865-112">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="8b865-113">[Postupy](#performance_check_procedures) najdete dál v tomto tématu najdete v těchto nástrojů.</span><span class="sxs-lookup"><span data-stu-id="8b865-113">The [procedures](#performance_check_procedures) provided later in this topic refer to these tools.</span></span>  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a><span data-ttu-id="8b865-114">Čítače výkonu paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-114">Memory Performance Counters</span></span>  
 <span data-ttu-id="8b865-115">Pomocí čítačů výkonu pro shromažďování dat výkonu.</span><span class="sxs-lookup"><span data-stu-id="8b865-115">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="8b865-116">Pokyny najdete v tématu [běhová profilace](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="8b865-116">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="8b865-117">Paměť .NET CLR kategorie čítačů výkonu, jak je popsáno v [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-117">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a><span data-ttu-id="8b865-118">Ladění pomocí SOS</span><span class="sxs-lookup"><span data-stu-id="8b865-118">Debugging with SOS</span></span>  
 <span data-ttu-id="8b865-119">Můžete použít [ladicí program Windows (WinDbg)](/windows-hardware/drivers/debugger/index) pro kontrolu objektů na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-119">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>
 
 <span data-ttu-id="8b865-120">Chcete-li program WinDbg nainstalovat, nainstalujte ladění nástroje pro Windows z [stáhnout ladění nástroje pro Windows](/windows-hardware/drivers/debugger/debugger-download-tools) stránky.</span><span class="sxs-lookup"><span data-stu-id="8b865-120">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a><span data-ttu-id="8b865-121">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-121">Garbage Collection ETW Events</span></span>  
 <span data-ttu-id="8b865-122">Trasování událostí pro Windows (ETW) je systém trasování, které doplňují profilování a ladění v rozhraní .NET Framework poskytuje podporu.</span><span class="sxs-lookup"><span data-stu-id="8b865-122">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="8b865-123">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md) zachycení užitečné informace pro spravované haldy z hlediska statistickou analýzu.</span><span class="sxs-lookup"><span data-stu-id="8b865-123">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="8b865-124">Například `GCStart_V1` událost, která se vyvolá, když uvolňování paměti se použije, obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="8b865-124">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>  
  
-   <span data-ttu-id="8b865-125">Které generování objektů se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="8b865-125">Which generation of objects is being collected.</span></span>  
  
-   <span data-ttu-id="8b865-126">Co spustí uvolnění.</span><span class="sxs-lookup"><span data-stu-id="8b865-126">What triggered the garbage collection.</span></span>  
  
-   <span data-ttu-id="8b865-127">Typ uvolňování paměti (souběžné nebo není souběžných).</span><span class="sxs-lookup"><span data-stu-id="8b865-127">Type of garbage collection (concurrent or not concurrent).</span></span>  
  
 <span data-ttu-id="8b865-128">Protokolování událostí trasování událostí pro Windows je efektivní a nebude maskují všechny problémy s výkonem, který je přidružený k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-128">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="8b865-129">Proces může poskytnout vlastní události ve spojení s událostmi trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="8b865-129">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="8b865-130">Při přihlášení, můžete určit, jak a kdy dojít k problémům haldy korelaci událostí v aplikaci a události kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-130">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="8b865-131">Serverová aplikace může například poskytovat události na začátku a konci požadavku klienta.</span><span class="sxs-lookup"><span data-stu-id="8b865-131">For example, a server application could provide events at the start and end of a client request.</span></span>  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a><span data-ttu-id="8b865-132">Rozhraní API pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8b865-132">The Profiling API</span></span>  
 <span data-ttu-id="8b865-133">Common language runtime (CLR) rozhraní profilování poskytují podrobné informace o objektech, které byly ovlivněny během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-133">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="8b865-134">Profiler můžete být upozorněni, když uvolňování paměti začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="8b865-134">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="8b865-135">To může poskytovat sestavy o objekty na spravované haldě, včetně identifikaci objektů v každé generaci.</span><span class="sxs-lookup"><span data-stu-id="8b865-135">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="8b865-136">Další informace najdete v tématu [přehled profilace](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8b865-136">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>  
  
 <span data-ttu-id="8b865-137">Profilovací programy mohou poskytnout komplexní informace.</span><span class="sxs-lookup"><span data-stu-id="8b865-137">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="8b865-138">Komplexní profilovací programy však můžete případně upravit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b865-138">However, complex profilers can potentially modify an application's behavior.</span></span>  
  
### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="8b865-139">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8b865-139">Application Domain Resource Monitoring</span></span>  
 <span data-ttu-id="8b865-140">Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], (ARM) sledování prostředků domény aplikace umožňuje hostitelům k monitorování využití procesoru a paměti doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b865-140">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="8b865-141">Další informace najdete v tématu [sledování prostředků aplikační domény](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="8b865-141">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>  
  
 [<span data-ttu-id="8b865-142">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="8b865-142">Back to top</span></span>](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="8b865-143">Řešení potíží s problémy s výkonem</span><span class="sxs-lookup"><span data-stu-id="8b865-143">Troubleshooting Performance Issues</span></span>  
 <span data-ttu-id="8b865-144">Prvním krokem je [zjistit, jestli tento problém je ve skutečnosti uvolňování](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="8b865-144">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="8b865-145">Pokud zjistíte, že se jedná, vyberte z následujícího seznamu k vyřešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="8b865-145">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>  
  
-   [<span data-ttu-id="8b865-146">Dojde k výjimce na více instancí z důvodu nedostatku paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-146">An out-of-memory exception is thrown</span></span>](#Issue_OOM)  
  
-   [<span data-ttu-id="8b865-147">Proces využívá příliš mnoho paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-147">The process uses too much memory</span></span>](#Issue_TooMuchMemory)  
  
-   [<span data-ttu-id="8b865-148">Uvolňování nezíská objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="8b865-148">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)  
  
-   [<span data-ttu-id="8b865-149">Spravovaná halda je příliš fragmentovaná.</span><span class="sxs-lookup"><span data-stu-id="8b865-149">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)  
  
-   [<span data-ttu-id="8b865-150">Pozastaví kolekce uvolnění paměti jsou příliš dlouhé</span><span class="sxs-lookup"><span data-stu-id="8b865-150">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)  
  
-   [<span data-ttu-id="8b865-151">Generace 0 je moc velká.</span><span class="sxs-lookup"><span data-stu-id="8b865-151">Generation 0 is too big</span></span>](#Issue_Gen0)  
  
-   [<span data-ttu-id="8b865-152">Využití procesoru během uvolňování paměti je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="8b865-152">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="8b865-153">Problém: Dojde k výjimce na více instancí z důvodu nedostatku paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-153">Issue: An Out-of-Memory Exception Is Thrown</span></span>  
 <span data-ttu-id="8b865-154">Existují dva případy legitimní pro spravované <xref:System.OutOfMemoryException> vyvolání:</span><span class="sxs-lookup"><span data-stu-id="8b865-154">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>  
  
-   <span data-ttu-id="8b865-155">Nedostatek virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-155">Running out of virtual memory.</span></span>  
  
     <span data-ttu-id="8b865-156">Uvolňování paměti přidělí paměť ze systému v příslušných segmentech v předem určeným rozsahu.</span><span class="sxs-lookup"><span data-stu-id="8b865-156">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="8b865-157">Pokud přidělení vyžaduje další segment, ale neexistuje žádná souvislých volný blok ve virtuální paměti prostoru procesu, se nezdaří přidělení pro spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-157">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>  
  
-   <span data-ttu-id="8b865-158">Nemají dostatek fyzické paměti k přidělení.</span><span class="sxs-lookup"><span data-stu-id="8b865-158">Not having enough physical memory to allocate.</span></span>  
  
|<span data-ttu-id="8b865-159">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-159">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="8b865-160">Určete, jestli je spravované výjimky na více instancí z důvodu nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-160">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="8b865-161">Určete, kolik virtuální paměti je možné vyhradit.</span><span class="sxs-lookup"><span data-stu-id="8b865-161">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="8b865-162">Určení, zda je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-162">Determine whether there is enough physical memory.</span></span>](#Physical)|  
  
 <span data-ttu-id="8b865-163">Pokud zjistíte, že výjimka není oprávněné, obraťte se na Microsoft zákaznický servis a podporu s následujícími informacemi:</span><span class="sxs-lookup"><span data-stu-id="8b865-163">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>  
  
-   <span data-ttu-id="8b865-164">Do zásobníku s spravované výjimky na více instancí z důvodu nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-164">The stack with the managed out-of-memory exception.</span></span>  
  
-   <span data-ttu-id="8b865-165">Úplný výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-165">Full memory dump.</span></span>  
  
-   <span data-ttu-id="8b865-166">Data, která prokáže vaše oprávnění, že se nejedná o legitimní-paměti výjimky, včetně dat, která ukazuje, že virtuální nebo fyzická paměť není problém.</span><span class="sxs-lookup"><span data-stu-id="8b865-166">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="8b865-167">Problém: Proces využívá příliš mnoho paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-167">Issue: The Process Uses Too Much Memory</span></span>  
 <span data-ttu-id="8b865-168">Běžné předpokladem je, že zobrazí využití paměti na **výkonu** karty ve Správci úloh Windows můžete určit, kdy se používá příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-168">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="8b865-169">Nicméně, které zobrazují se vztahují na pracovní sadu; neposkytuje informace o využití virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-169">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>  
  
 <span data-ttu-id="8b865-170">Pokud zjistíte, že problém je způsoben spravované haldě, musí spravované haldě měření průběžným monitorováním určete všechny vzorky.</span><span class="sxs-lookup"><span data-stu-id="8b865-170">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>  
  
 <span data-ttu-id="8b865-171">Pokud zjistíte, jestli problém nezpůsobuje ve spravované haldě, je nutné použít nativní ladění.</span><span class="sxs-lookup"><span data-stu-id="8b865-171">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>  
  
|<span data-ttu-id="8b865-172">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-172">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="8b865-173">Určete, kolik virtuální paměti je možné vyhradit.</span><span class="sxs-lookup"><span data-stu-id="8b865-173">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="8b865-174">Určete, kolik paměti potvrzuje spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-174">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="8b865-175">Určete, kolik paměti rezervuje spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-175">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="8b865-176">Určení velké objekty v 2. generace.</span><span class="sxs-lookup"><span data-stu-id="8b865-176">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="8b865-177">Určete odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-177">Determine references to objects.</span></span>](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="8b865-178">Problém: Uvolňování nezíská objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="8b865-178">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>  
 <span data-ttu-id="8b865-179">Když se objeví jako objekty nejsou jsou uvolněny podle očekávání pro uvolnění paměti, je nutné určit, jestli jsou všechny silné odkazy na tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-179">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>  
  
 <span data-ttu-id="8b865-180">Tento problém se můžete setkat také v případě žádná kolekce uvolnění paměti pro generování, který obsahuje objekt mrtvý, což znamená, že nebyla spuštěna finalizační metodu pro objekt mrtvý.</span><span class="sxs-lookup"><span data-stu-id="8b865-180">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="8b865-181">Například to je možné při spouštění aplikace jednovláknový apartment (STA) a vlákno této služby, které frontě finalizační metodu nejde volat metodu do něj.</span><span class="sxs-lookup"><span data-stu-id="8b865-181">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>  
  
|<span data-ttu-id="8b865-182">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-182">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="8b865-183">Zkontrolujte odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-183">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="8b865-184">Určení, zda byla spuštěna finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="8b865-184">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="8b865-185">Určení, zda jsou objekty čekání na jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="8b865-185">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="8b865-186">Problém: Na spravované haldě je příliš fragmentovaná.</span><span class="sxs-lookup"><span data-stu-id="8b865-186">Issue: The Managed Heap Is Too fragmented</span></span>  
 <span data-ttu-id="8b865-187">Úroveň fragmentace se počítá jako poměr volného místa za Celková přidělená paměť pro generování.</span><span class="sxs-lookup"><span data-stu-id="8b865-187">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="8b865-188">Přijatelnou úroveň fragmentace pro 2. generace, je více než 20 %.</span><span class="sxs-lookup"><span data-stu-id="8b865-188">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="8b865-189">Protože 2. generace můžete získat velmi velký poměr fragmentace je mnohem důležitější než absolutní hodnota.</span><span class="sxs-lookup"><span data-stu-id="8b865-189">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>  
  
 <span data-ttu-id="8b865-190">Máte velké množství volného místa v 0. generace není problém vzhledem k tomu, že to je generace, kde jsou přiděleny nové objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-190">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>  
  
 <span data-ttu-id="8b865-191">Fragmentace vždy dojde v haldy pro velké objekty, protože není setřepána.</span><span class="sxs-lookup"><span data-stu-id="8b865-191">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="8b865-192">Volné objekty, které jsou sousedící jsou přirozeně sbaleny do jednoho místa pro splnění požadavků na přidělení velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="8b865-192">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>  
  
 <span data-ttu-id="8b865-193">Fragmentace stát problémem v 1 a generace 2.</span><span class="sxs-lookup"><span data-stu-id="8b865-193">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="8b865-194">Pokud tyto generace velké množství volného místa po uvolnění, použití objektu aplikace může být nutné změny a měli byste zvážit znovu vyhodnotit životnosti dlouhodobé objektů.</span><span class="sxs-lookup"><span data-stu-id="8b865-194">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>  
  
 <span data-ttu-id="8b865-195">Nadměrné Připnutí objektů můžete zvýšit fragmentace.</span><span class="sxs-lookup"><span data-stu-id="8b865-195">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="8b865-196">Pokud fragmentace je vysoké, může připnout příliš mnoho objektů.</span><span class="sxs-lookup"><span data-stu-id="8b865-196">If fragmentation is high, too many objects could be pinned.</span></span>  
  
 <span data-ttu-id="8b865-197">Pokud fragmentace paměti virtuální brání systému uvolňování paměti daných segmentů, mohou být jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="8b865-197">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>  
  
-   <span data-ttu-id="8b865-198">Časté načítání a uvolňování mnoha malých sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b865-198">Frequent loading and unloading of many small assemblies.</span></span>  
  
-   <span data-ttu-id="8b865-199">Příliš mnoho odkazů na objekty modelu COM drží, když spolupráce s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="8b865-199">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>  
  
-   <span data-ttu-id="8b865-200">Vytvoření velké přechodné objektů, což způsobí, že haldy pro velké objekty na přidělují a uvolňují haldy segmenty často.</span><span class="sxs-lookup"><span data-stu-id="8b865-200">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>  
  
     <span data-ttu-id="8b865-201">Při hostování CLR, může aplikace vyžadovat, že uvolňování zachovat jeho segmentů.</span><span class="sxs-lookup"><span data-stu-id="8b865-201">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="8b865-202">Tím se snižuje frekvence přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="8b865-202">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="8b865-203">To lze provést pomocí příznaku STARTUP_HOARD_GC_VM v [startup_flags – výčet](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8b865-203">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
|<span data-ttu-id="8b865-204">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-204">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="8b865-205">Určení množství volného místa ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-205">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="8b865-206">Určete počet připojených objektů.</span><span class="sxs-lookup"><span data-stu-id="8b865-206">Determine the number of pinned objects.</span></span>](#Pinned)|  
  
 <span data-ttu-id="8b865-207">Pokud se domníváte, že neexistuje žádná legitimní příčinou fragmentaci, obraťte se na Microsoft zákaznický servis a podporu.</span><span class="sxs-lookup"><span data-stu-id="8b865-207">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="8b865-208">Problém: Pozastaví kolekce uvolnění paměti jsou příliš dlouhé</span><span class="sxs-lookup"><span data-stu-id="8b865-208">Issue: Garbage Collection Pauses Are Too Long</span></span>  
 <span data-ttu-id="8b865-209">Uvolňování paměti funguje v obnovitelně v reálném čase, takže aplikace musí být schopné tolerovat některé pozastaví.</span><span class="sxs-lookup"><span data-stu-id="8b865-209">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="8b865-210">Kritéria pro obnovitelné reálném čase je, že 95 % operací musí dokončit včas.</span><span class="sxs-lookup"><span data-stu-id="8b865-210">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>  
  
 <span data-ttu-id="8b865-211">V souběžné uvolňování paměti spravovaná vlákna je možné spustit shromažďování, což znamená, že je možné je minimální.</span><span class="sxs-lookup"><span data-stu-id="8b865-211">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>  
  
 <span data-ttu-id="8b865-212">Pouze několik milisekund, než poslední dočasnému uvolnění (generace 0 a 1), to snižuje pozastaví obvykle není vhodná.</span><span class="sxs-lookup"><span data-stu-id="8b865-212">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="8b865-213">Však může snížit pozastaví v 2. generace kolekce tak, že změníte model požadavků na přidělení aplikací.</span><span class="sxs-lookup"><span data-stu-id="8b865-213">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>  
  
 <span data-ttu-id="8b865-214">Jiný, přesnější, metoda se má používat [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="8b865-214">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="8b865-215">Časování pro kolekce můžete najít tak, že přidáte tyto časové razítko rozdíly pro posloupnost událostí.</span><span class="sxs-lookup"><span data-stu-id="8b865-215">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="8b865-216">Pořadí celé kolekce obsahuje pozastavení prováděcího modulu, uvolňování paměti kolekce a opětovné prováděcího modulu.</span><span class="sxs-lookup"><span data-stu-id="8b865-216">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>  
  
 <span data-ttu-id="8b865-217">Můžete použít [oznámení pro kolekci paměti](../../../docs/standard/garbage-collection/notifications.md) k určení, zda je server ke kolekci generace 2, a určuje, zda přesměrování požadavků na jiný server by mělo odlehčit jakékoliv potíže se pozastaví.</span><span class="sxs-lookup"><span data-stu-id="8b865-217">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>  
  
|<span data-ttu-id="8b865-218">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-218">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="8b865-219">Určuje délku času v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-219">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="8b865-220">Určete, co způsobilo uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-220">Determine what caused a garbage collection.</span></span>](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="8b865-221">Problém: Generace 0 je moc velká.</span><span class="sxs-lookup"><span data-stu-id="8b865-221">Issue: Generation 0 Is Too Big</span></span>  
 <span data-ttu-id="8b865-222">Generace 0 by mohla mít větší počet objektů v 64bitovém systému, zejména v případě, že místo uvolnění paměti pracovní stanice použijete uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="8b865-222">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="8b865-223">Je to proto, že je prahová hodnota pro aktivaci 0 uvolnění paměti generace vyšší v těchto prostředích a kolekcemi generace 0 můžete získat mnohem větší.</span><span class="sxs-lookup"><span data-stu-id="8b865-223">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="8b865-224">Výkon je vyšší, pokud aplikace přiděluje víc paměti než se aktivuje uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-224">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="8b865-225">Problém: Využití procesoru během uvolňování paměti je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="8b865-225">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>  
 <span data-ttu-id="8b865-226">Během uvolňování paměti bude vysoké využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="8b865-226">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="8b865-227">Pokud značné množství času zpracování se stráven v procesu uvolnění paměti, počtu kolekcí je moc často nebo kolekce je trvají příliš dlouho.</span><span class="sxs-lookup"><span data-stu-id="8b865-227">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="8b865-228">Zvýšení přidělení počet objektů na spravované haldě způsobí, že uvolňování paměti dochází častěji.</span><span class="sxs-lookup"><span data-stu-id="8b865-228">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="8b865-229">Snížení frekvence přidělení snižuje frekvence uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-229">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>  
  
 <span data-ttu-id="8b865-230">Přidělení kurzů můžete sledovat pomocí `Allocated Bytes/second` čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="8b865-230">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="8b865-231">Další informace najdete v tématu [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="8b865-231">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
 <span data-ttu-id="8b865-232">Doba trvání kolekce je primárně faktorem počet objektů, které byly zachovány při po přidělení.</span><span class="sxs-lookup"><span data-stu-id="8b865-232">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="8b865-233">Uvolňování paměti musí projít velké množství paměti, pokud zůstanou velký počet objektů, které se mají shromažďovat.</span><span class="sxs-lookup"><span data-stu-id="8b865-233">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="8b865-234">Je časově náročné práce ke komprimaci zachované objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-234">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="8b865-235">Pokud chcete zjistit, kolik objektů zpracovávaly během kolekci, nastavte zarážku v ladicím programu na konci uvolnění pro zadané generace.</span><span class="sxs-lookup"><span data-stu-id="8b865-235">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>  
  
|<span data-ttu-id="8b865-236">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="8b865-236">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="8b865-237">Určete, pokud je způsobena vysoké využití procesoru uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-237">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="8b865-238">Nastavení zarážky na konci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-238">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|  
  
 [<span data-ttu-id="8b865-239">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="8b865-239">Back to top</span></span>](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a><span data-ttu-id="8b865-240">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="8b865-240">Troubleshooting Guidelines</span></span>  
 <span data-ttu-id="8b865-241">Tato část popisuje pokyny, které byste měli zvážit při začnete vaše šetření.</span><span class="sxs-lookup"><span data-stu-id="8b865-241">This section describes guidelines that you should consider as you begin your investigations.</span></span>  
  
### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="8b865-242">Pracovní stanice nebo uvolnění paměti serveru</span><span class="sxs-lookup"><span data-stu-id="8b865-242">Workstation or Server Garbage Collection</span></span>  
 <span data-ttu-id="8b865-243">Určete, pokud používáte správný typ uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-243">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="8b865-244">Pokud vaše aplikace používá více vláken a instance objektů, použijte místo uvolnění paměti pracovní stanice uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="8b865-244">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="8b865-245">Uvolnění paměti serveru funguje ve více vláknech, zatímco uvolňování paměti pracovní stanice vyžaduje více instancí aplikace ke spuštění vlastních vláken pro uvolnění a soutěží o čas procesoru.</span><span class="sxs-lookup"><span data-stu-id="8b865-245">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>  
  
 <span data-ttu-id="8b865-246">Aplikace, který má nízkou zatížení a, který provádí úlohy zřídka na pozadí, třeba služby, může použít uvolnění paměti pracovní stanice se zakázaným souběžným uvolňováním.</span><span class="sxs-lookup"><span data-stu-id="8b865-246">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>  
  
### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="8b865-247">Kdy k měření velikosti spravované haldy</span><span class="sxs-lookup"><span data-stu-id="8b865-247">When to Measure the Managed Heap Size</span></span>  
 <span data-ttu-id="8b865-248">Pokud nepoužíváte profiler, budete muset vytvořit konzistentní měření vzor efektivně diagnostikovat problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="8b865-248">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="8b865-249">Vezměte v úvahu následující body k vytvoření plánu:</span><span class="sxs-lookup"><span data-stu-id="8b865-249">Consider the following points to establish a schedule:</span></span>  
  
-   <span data-ttu-id="8b865-250">Pokud budete vyhodnocovat po uvolnění paměti generace 2, bude celou spravovanou haldu zdarma uvolňování paměti (neživými objekty).</span><span class="sxs-lookup"><span data-stu-id="8b865-250">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>  
  
-   <span data-ttu-id="8b865-251">Pokud budete vyhodnocovat ihned po uvolnění paměti generace 0, nebudou shromažďovat ještě objekty v generace 1 a 2.</span><span class="sxs-lookup"><span data-stu-id="8b865-251">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>  
  
-   <span data-ttu-id="8b865-252">Pokud budete vyhodnocovat bezprostředně před uvolňování paměti, budete měřit tolik přidělení nejvíce předtím, než spustí uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-252">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>  
  
-   <span data-ttu-id="8b865-253">Měření během uvolňování paměti jen těžko, protože datové struktury systému uvolňování paměti nejsou v platném stavu pro procházení a nemusí být schopen poskytnout úplné výsledky.</span><span class="sxs-lookup"><span data-stu-id="8b865-253">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="8b865-254">Jedná se o účel.</span><span class="sxs-lookup"><span data-stu-id="8b865-254">This is by design.</span></span>  
  
-   <span data-ttu-id="8b865-255">Při použití uvolnění paměti pracovní stanice s souběžné uvolňování paměti, nejsou uvolňovaného objekty komprimovat, takže velikost haldy může být stejná nebo větší (fragmentace může vypadat větší).</span><span class="sxs-lookup"><span data-stu-id="8b865-255">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>  
  
-   <span data-ttu-id="8b865-256">Souběžné uvolňování paměti v generaci 2 je zpožděno při fyzické paměti je příliš vysoké.</span><span class="sxs-lookup"><span data-stu-id="8b865-256">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>  
  
 <span data-ttu-id="8b865-257">Následující postup popisuje, jak nastavit zarážku, můžete změřit spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-257">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="8b865-258">Chcete-li nastavit zarážku na konci uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-258">To set a breakpoint at the end of garbage collection</span></span>  
  
-   <span data-ttu-id="8b865-259">V rámci WinDbg s příponou SOS ladicího programu, načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-259">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="8b865-260">**BP mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2) "kb"; " g ""**</span><span class="sxs-lookup"><span data-stu-id="8b865-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>  
  
     <span data-ttu-id="8b865-261">kde **GcCondemnedGeneration** nastavená na požadované generace.</span><span class="sxs-lookup"><span data-stu-id="8b865-261">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="8b865-262">Tento příkaz vyžaduje soukromé symboly.</span><span class="sxs-lookup"><span data-stu-id="8b865-262">This command requires private symbols.</span></span>  
  
     <span data-ttu-id="8b865-263">Tento příkaz vynutí zalomení **RestartEE** se spustí po objektů 2. generace mají byla získána pro uvolnění.</span><span class="sxs-lookup"><span data-stu-id="8b865-263">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>  
  
     <span data-ttu-id="8b865-264">Uvolňování paměti serveru pouze jedno vlákno volá **RestartEE**, takže zarážka dojde pouze jednou během uvolnění paměti generace 2.</span><span class="sxs-lookup"><span data-stu-id="8b865-264">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>  
  
 [<span data-ttu-id="8b865-265">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="8b865-265">Back to top</span></span>](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a><span data-ttu-id="8b865-266">Výkon zaškrtněte procedury</span><span class="sxs-lookup"><span data-stu-id="8b865-266">Performance Check Procedures</span></span>  
 <span data-ttu-id="8b865-267">Tato část popisuje následující postupy k izolaci příčina potíží s výkonem:</span><span class="sxs-lookup"><span data-stu-id="8b865-267">This section describes the following procedures to isolate the cause of your performance issue:</span></span>  
  
-   [<span data-ttu-id="8b865-268">Určí, zda je problém způsoben uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-268">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)  
  
-   [<span data-ttu-id="8b865-269">Určete, jestli je spravované výjimky na více instancí z důvodu nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-269">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)  
  
-   [<span data-ttu-id="8b865-270">Určete, kolik virtuální paměti je možné vyhradit.</span><span class="sxs-lookup"><span data-stu-id="8b865-270">Determine how much virtual memory can be reserved.</span></span>](#GetVM)  
  
-   [<span data-ttu-id="8b865-271">Určení, zda je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-271">Determine whether there is enough physical memory.</span></span>](#Physical)  
  
-   [<span data-ttu-id="8b865-272">Určete, kolik paměti potvrzuje spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-272">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)  
  
-   [<span data-ttu-id="8b865-273">Určete, kolik paměti rezervuje spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-273">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)  
  
-   [<span data-ttu-id="8b865-274">Určení velké objekty v 2. generace.</span><span class="sxs-lookup"><span data-stu-id="8b865-274">Determine large objects in generation 2.</span></span>](#ExamineGen2)  
  
-   [<span data-ttu-id="8b865-275">Určete odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-275">Determine references to objects.</span></span>](#ObjRef)  
  
-   [<span data-ttu-id="8b865-276">Určení, zda byla spuštěna finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="8b865-276">Determine whether a finalizer has been run.</span></span>](#Induce)  
  
-   [<span data-ttu-id="8b865-277">Určení, zda jsou objekty čekání na jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="8b865-277">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)  
  
-   [<span data-ttu-id="8b865-278">Určení množství volného místa ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-278">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)  
  
-   [<span data-ttu-id="8b865-279">Určete počet připojených objektů.</span><span class="sxs-lookup"><span data-stu-id="8b865-279">Determine the number of pinned objects.</span></span>](#Pinned)  
  
-   [<span data-ttu-id="8b865-280">Určuje délku času v uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-280">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)  
  
-   [<span data-ttu-id="8b865-281">Zjistěte, co vyvolalo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-281">Determine what triggered a garbage collection.</span></span>](#Triggered)  
  
-   [<span data-ttu-id="8b865-282">Určete, jestli způsobuje vysoké využití procesoru uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-282">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="8b865-283">Chcete-li zjistit, zda je problém způsoben uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-283">To determine whether the problem is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="8b865-284">Zkontrolujte následující čítače výkonu paměti dvě:</span><span class="sxs-lookup"><span data-stu-id="8b865-284">Examine the following two memory performance counters:</span></span>  
  
    -   <span data-ttu-id="8b865-285">**% Času v uvolňování paměti**.</span><span class="sxs-lookup"><span data-stu-id="8b865-285">**% Time in GC**.</span></span> <span data-ttu-id="8b865-286">Zobrazuje procentuální hodnotu uplynulého času, který byl vynaložen provádění uvolnění posledního cyklu uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="8b865-286">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="8b865-287">Tento čítač použijte k určení, zda systému uvolňování paměti spotřebuje uběhla spousta času uvolněte místo na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-287">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="8b865-288">Pokud doba trvání uvolňování paměti je relativně nízký, to by mohlo znamenat problém prostředků mimo spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-288">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="8b865-289">Tento čítač nemusí být přesné při souběžné nebo je zahrnuta uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8b865-289">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>  
  
    -   <span data-ttu-id="8b865-290">**Celkový počet svěřených bajtů**.</span><span class="sxs-lookup"><span data-stu-id="8b865-290">**# Total committed Bytes**.</span></span> <span data-ttu-id="8b865-291">Zobrazuje velikost virtuální paměti aktuálně potvrzené systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-291">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="8b865-292">Tento čítač použijte k určení, zda je paměť systému uvolňování paměti používané nadměrné část paměti, která vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="8b865-292">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>  
  
     <span data-ttu-id="8b865-293">Většina čítačů výkonu paměti se aktualizují na konci každé uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-293">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="8b865-294">Proto že nemusí odrážet aktuální podmínky, které se mají informace o.</span><span class="sxs-lookup"><span data-stu-id="8b865-294">Therefore, they may not reflect the current conditions that you want information about.</span></span>  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="8b865-295">Chcete-li zjistit, jestli je spravované výjimky na více instancí z důvodu nedostatku paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-295">To determine whether the out-of-memory exception is managed</span></span>  
  
1. <span data-ttu-id="8b865-296">V ladicím programu WinDbg nebo Visual Studio s rozšířením ladicí program SOS načíst, zadejte tisku výjimky (**pe**) příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-296">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>  
  
     <span data-ttu-id="8b865-297">**! pe**</span><span class="sxs-lookup"><span data-stu-id="8b865-297">**!pe**</span></span>  
  
     <span data-ttu-id="8b865-298">Pokud je spravované výjimky, <xref:System.OutOfMemoryException> se zobrazí jako typ výjimky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b865-298">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2. <span data-ttu-id="8b865-299">Pokud výstup neurčuje výjimku, budete muset určit, které vlákno výjimky na více instancí z důvodu nedostatku paměti je z.</span><span class="sxs-lookup"><span data-stu-id="8b865-299">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="8b865-300">Zadejte následující příkaz v ladicím programu, který chcete zobrazit všechna vlákna s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="8b865-300">Type the following command in the debugger to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="8b865-301">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="8b865-301">**~\*kb**</span></span>  
  
     <span data-ttu-id="8b865-302">Vlákno se zásobníkem, který má volání výjimky je indikován `RaiseTheException` argument.</span><span class="sxs-lookup"><span data-stu-id="8b865-302">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="8b865-303">Toto je objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="8b865-303">This is the managed exception object.</span></span>  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3. <span data-ttu-id="8b865-304">Můžete použít následující příkaz pro výpis vnořené výjimky.</span><span class="sxs-lookup"><span data-stu-id="8b865-304">You can use the following command to dump nested exceptions.</span></span>  
  
     <span data-ttu-id="8b865-305">**! pe-vnořené**</span><span class="sxs-lookup"><span data-stu-id="8b865-305">**!pe -nested**</span></span>  
  
     <span data-ttu-id="8b865-306">Pokud nenajdete žádné výjimky, výstup z důvodu nedostatku paměti výjimka pochází z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="8b865-306">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="8b865-307">Chcete-li zjistit, je možné vyhradit velikost virtuální paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-307">To determine how much virtual memory can be reserved</span></span>  
  
-   <span data-ttu-id="8b865-308">V rámci WinDbg s příponou SOS ladicího programu, načíst zadejte následující příkaz získat největší bezplatná oblasti:</span><span class="sxs-lookup"><span data-stu-id="8b865-308">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>  
  
     <span data-ttu-id="8b865-309">**! adres – souhrn**</span><span class="sxs-lookup"><span data-stu-id="8b865-309">**!address -summary**</span></span>  
  
     <span data-ttu-id="8b865-310">Největší bezplatná oblasti se zobrazí, jak je znázorněno v následujícím výstupu.</span><span class="sxs-lookup"><span data-stu-id="8b865-310">The largest free region is displayed as shown in the following output.</span></span>  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     <span data-ttu-id="8b865-311">V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové hodnotě).</span><span class="sxs-lookup"><span data-stu-id="8b865-311">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="8b865-312">Tato oblast je mnohem menší, než které systému uvolňování paměti, musí mít segmentu.</span><span class="sxs-lookup"><span data-stu-id="8b865-312">This region is much smaller than what the garbage collector needs for a segment.</span></span>  
  
     <span data-ttu-id="8b865-313">-nebo-</span><span class="sxs-lookup"><span data-stu-id="8b865-313">-or-</span></span>  
  
-   <span data-ttu-id="8b865-314">Použití **vmstat** příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-314">Use the **vmstat** command:</span></span>  
  
     <span data-ttu-id="8b865-315">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="8b865-315">**!vmstat**</span></span>  
  
     <span data-ttu-id="8b865-316">Největší bezplatná oblasti je největší hodnotu ve sloupci maximální, jak je znázorněno v následujícím výstupu.</span><span class="sxs-lookup"><span data-stu-id="8b865-316">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>  
  
    ```  
    TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL  
    ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~  
    Free:  
    Small       8K        64K         46K       36          1,671K  
    Medium      80K       864K        349K      3           1,047K  
    Large       1,384K    1,278,848K  151,834K  12          1,822,015K  
    Summary     8K        1,278,848K  35,779K   51          1,824,735K  
    ```  
  
<a name="Physical"></a>   
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="8b865-317">Určuje, jestli je dostatečná fyzická paměť</span><span class="sxs-lookup"><span data-stu-id="8b865-317">To determine whether there is enough physical memory</span></span>  
  
1. <span data-ttu-id="8b865-318">Spuštění Správce úloh Windows.</span><span class="sxs-lookup"><span data-stu-id="8b865-318">Start Windows Task Manager.</span></span>  
  
2. <span data-ttu-id="8b865-319">Na **výkonu** kartu, podívejte se na potvrzená hodnota.</span><span class="sxs-lookup"><span data-stu-id="8b865-319">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="8b865-320">(Ve Windows 7, podívejte se na **potvrzení (KB)** v **systémové skupiny**.)</span><span class="sxs-lookup"><span data-stu-id="8b865-320">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>  
  
     <span data-ttu-id="8b865-321">Pokud **celkový** blízko **Limit**, máte málo na fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-321">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="8b865-322">Chcete-li určit, kolik paměti potvrzuje spravované haldy</span><span class="sxs-lookup"><span data-stu-id="8b865-322">To determine how much memory the managed heap is committing</span></span>  
  
-   <span data-ttu-id="8b865-323">Použití `# Total committed bytes` čítače výkonu paměti se získat počet bajtů, které se provádí spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-323">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="8b865-324">Uvolňování potvrzení bloků v segmentu, podle potřeby, nikoli všechny najednou.</span><span class="sxs-lookup"><span data-stu-id="8b865-324">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b865-325">Nepoužívejte `# Bytes in all Heaps` čítače výkonu, protože nepředstavuje skutečné využití paměti ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b865-325">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="8b865-326">Velikost generace je součástí tuto hodnotu a je ve skutečnosti jeho prahová hodnota velikosti, to znamená, velikost, který indukuje uvolňování paměti, pokud generování je vyplněna objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-326">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="8b865-327">Proto se tato hodnota je obvykle nula.</span><span class="sxs-lookup"><span data-stu-id="8b865-327">Therefore, this value is usually zero.</span></span>  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="8b865-328">Chcete-li určit, kolik paměti rezervuje spravované haldy</span><span class="sxs-lookup"><span data-stu-id="8b865-328">To determine how much memory the managed heap reserves</span></span>  
  
-   <span data-ttu-id="8b865-329">Použití `# Total reserved bytes` čítače výkonu paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-329">Use the `# Total reserved bytes` memory performance counter.</span></span>  
  
     <span data-ttu-id="8b865-330">Rezervuje uvolňování paměti v příslušných segmentech a můžete určit, kde segment, který spustí na základě **eeheap** příkazu.</span><span class="sxs-lookup"><span data-stu-id="8b865-330">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8b865-331">I když můžete určit množství paměti, které systému uvolňování paměti přiděluje každého segmentu, velikost segmentu je specifický pro implementaci a může se změnit kdykoli, včetně v pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="8b865-331">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="8b865-332">Vaše aplikace by nikdy vytvořit předpoklady o nebo závisí na velikosti konkrétního segmentu, ani snažit konfigurace množství paměti k přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="8b865-332">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
-   <span data-ttu-id="8b865-333">V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-333">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="8b865-334">**! eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="8b865-334">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="8b865-335">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="8b865-335">The result is as follows.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-336">Adresy indikován "segmentu" jsou počáteční adresy segmentů.</span><span class="sxs-lookup"><span data-stu-id="8b865-336">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="8b865-337">Chcete-li zjistit velké objekty v 2. generace</span><span class="sxs-lookup"><span data-stu-id="8b865-337">To determine large objects in generation 2</span></span>  
  
-   <span data-ttu-id="8b865-338">V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-338">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="8b865-339">**! dumpheap-stat**</span><span class="sxs-lookup"><span data-stu-id="8b865-339">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="8b865-340">Pokud je spravované haldy velkých objemů, **dumpheap** může chvíli trvat dokončení.</span><span class="sxs-lookup"><span data-stu-id="8b865-340">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>  
  
     <span data-ttu-id="8b865-341">Je mohli začít analyzovat během posledních několik řádků výstupu, protože jsou vypsány objekty, které používají nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="8b865-341">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="8b865-342">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8b865-342">For example:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-343">Poslední objekt uvedené je řetězec a zabírá nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="8b865-343">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="8b865-344">Můžete zkontrolovat aplikace, abyste viděli, jak se dá optimalizovat řetězcových objektů.</span><span class="sxs-lookup"><span data-stu-id="8b865-344">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="8b865-345">Zobrazit řetězce, které jsou v rozmezí od 150 až 200 bajtů, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-345">To see strings that are between 150 and 200 bytes, type the following:</span></span>  
  
     <span data-ttu-id="8b865-346">**! dumpheap-zadejte 150 - max -min System.String 200**</span><span class="sxs-lookup"><span data-stu-id="8b865-346">**!dumpheap -type System.String -min 150 -max 200**</span></span>  
  
     <span data-ttu-id="8b865-347">Příklad výsledků je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="8b865-347">An example of the results is as follows.</span></span>  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     <span data-ttu-id="8b865-348">Místo celého čísla na řetězec pro ID může být efektivnější.</span><span class="sxs-lookup"><span data-stu-id="8b865-348">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="8b865-349">Pokud stejný řetězec je opakováno tisíce časy, vezměte v úvahu interning řetězce.</span><span class="sxs-lookup"><span data-stu-id="8b865-349">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="8b865-350">Další informace o interning řetězce, naleznete v referenčním tématu pro <xref:System.String.Intern%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8b865-350">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a><span data-ttu-id="8b865-351">Chcete-li zjistit odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-351">To determine references to objects</span></span>  
  
-   <span data-ttu-id="8b865-352">V rámci WinDbg s příponou SOS ladicího programu, načíst zadejte následující příkaz pro seznam odkazů na objekty:</span><span class="sxs-lookup"><span data-stu-id="8b865-352">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>  
  
     <span data-ttu-id="8b865-353">**! gcroot**</span><span class="sxs-lookup"><span data-stu-id="8b865-353">**!gcroot**</span></span>  
  
     `-or-`  
  
-   <span data-ttu-id="8b865-354">Pokud chcete zjistit odkazy pro konkrétní objekt, patří adresu:</span><span class="sxs-lookup"><span data-stu-id="8b865-354">To determine the references for a specific object, include the address:</span></span>  
  
     <span data-ttu-id="8b865-355">**! gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="8b865-355">**!gcroot 1c37b2ac**</span></span>  
  
     <span data-ttu-id="8b865-356">Kořeny na zásobníky může být falešně pozitivních výsledků.</span><span class="sxs-lookup"><span data-stu-id="8b865-356">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="8b865-357">Další informace získáte pomocí příkazu `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="8b865-357">For more information, use the command `!help gcroot`.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-358">**Gcroot** příkazu může trvat delší dobu.</span><span class="sxs-lookup"><span data-stu-id="8b865-358">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="8b865-359">Libovolný objekt, který není uvolněn systémem uvolňování paměti je objekt za provozu.</span><span class="sxs-lookup"><span data-stu-id="8b865-359">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="8b865-360">To znamená, že některé kořenové je přímo nebo nepřímo držení objektu, takže **gcroot** by měl vrátit informace o cestě k objektu.</span><span class="sxs-lookup"><span data-stu-id="8b865-360">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="8b865-361">By měl prozkoumat grafy vrátil a zobrazit, proč jsou tyto objekty stále odkazuje.</span><span class="sxs-lookup"><span data-stu-id="8b865-361">You should examine the graphs returned and see why these objects are still referenced.</span></span>  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="8b865-362">Chcete-li zjistit, zda byla spuštěna finalizační metodu</span><span class="sxs-lookup"><span data-stu-id="8b865-362">To determine whether a finalizer has been run</span></span>  
  
-   <span data-ttu-id="8b865-363">Spustit testovací program, který obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="8b865-363">Run a test program that contains the following code:</span></span>  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     <span data-ttu-id="8b865-364">Pokud test řeší problém, znamená to, že nebyl systému uvolňování paměti uvolní objektů, protože byla pozastavena finalizační metody týkajících se těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="8b865-364">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="8b865-365"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metoda umožňuje finalizační metody pro dokončení úloh a vyřeší daný problém.</span><span class="sxs-lookup"><span data-stu-id="8b865-365">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="8b865-366">Chcete-li zjistit, zda jsou objekty čekání na jejich dokončení</span><span class="sxs-lookup"><span data-stu-id="8b865-366">To determine whether there are objects waiting to be finalized</span></span>  
  
1. <span data-ttu-id="8b865-367">V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-367">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="8b865-368">**! finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="8b865-368">**!finalizequeue**</span></span>  
  
     <span data-ttu-id="8b865-369">Podívejte se na počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="8b865-369">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="8b865-370">Pokud je vysoké číslo, musíte prozkoumat proč tyto finalizační metody nemůže vůbec průběh nebo nelze průběh rychlé dostatečně.</span><span class="sxs-lookup"><span data-stu-id="8b865-370">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>  
  
2. <span data-ttu-id="8b865-371">Pokud chcete získat výstup vláken, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-371">To get an output of threads, type the following command:</span></span>  
  
     <span data-ttu-id="8b865-372">**vlákna – speciální**</span><span class="sxs-lookup"><span data-stu-id="8b865-372">**threads -special**</span></span>  
  
     <span data-ttu-id="8b865-373">Tento příkaz zjistí výstupu, jako je následující.</span><span class="sxs-lookup"><span data-stu-id="8b865-373">This command provides output such as the following.</span></span>  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     <span data-ttu-id="8b865-374">Vlákno finalizační metody Určuje, které finalizační metodu, pokud existuje, je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="8b865-374">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="8b865-375">Pokud vlákno finalizační metodu neběží žádné finalizační metody, čeká událost určit, ke své práci.</span><span class="sxs-lookup"><span data-stu-id="8b865-375">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="8b865-376">Ve většině případů se zobrazí vlákna finalizační metody v tomto stavu protože běží na THREAD_HIGHEST_PRIORITY a by měl dokončit spuštění finalizační metody, pokud existuje, velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="8b865-376">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="8b865-377">Chcete-li zjistit množství volného místa ve spravované haldě</span><span class="sxs-lookup"><span data-stu-id="8b865-377">To determine the amount of free space in the managed heap</span></span>  
  
-   <span data-ttu-id="8b865-378">V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-378">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="8b865-379">**! dumpheap-zadejte zdarma - stat**</span><span class="sxs-lookup"><span data-stu-id="8b865-379">**!dumpheap -type Free -stat**</span></span>  
  
     <span data-ttu-id="8b865-380">Tento příkaz zobrazí celkovou velikost volné objekty na spravované haldě, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b865-380">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   <span data-ttu-id="8b865-381">Pokud chcete zjistit volné místo v generaci 0, zadejte následující příkaz pro informace o využití paměti podle generace:</span><span class="sxs-lookup"><span data-stu-id="8b865-381">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>  
  
     <span data-ttu-id="8b865-382">**! eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="8b865-382">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="8b865-383">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="8b865-383">This command displays output similar to the following.</span></span> <span data-ttu-id="8b865-384">Poslední řádek zobrazuje dočasný segment.</span><span class="sxs-lookup"><span data-stu-id="8b865-384">The last line shows the ephemeral segment.</span></span>  
  
    ```  
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
  
-   <span data-ttu-id="8b865-385">Vypočítejte místo používané 0. generace:</span><span class="sxs-lookup"><span data-stu-id="8b865-385">Calculate the space used by generation 0:</span></span>  
  
     <span data-ttu-id="8b865-386">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="8b865-386">**? 49e05d04-0x49521f8c**</span></span>  
  
     <span data-ttu-id="8b865-387">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="8b865-387">The result is as follows.</span></span> <span data-ttu-id="8b865-388">Generace 0 je přibližně 9 MB.</span><span class="sxs-lookup"><span data-stu-id="8b865-388">Generation 0 is approximately 9 MB.</span></span>  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   <span data-ttu-id="8b865-389">Následující příkaz vypíše volného místa v rozsahu 0. generace:</span><span class="sxs-lookup"><span data-stu-id="8b865-389">The following command dumps the free space within the generation 0 range:</span></span>  
  
     <span data-ttu-id="8b865-390">**! dumpheap-zadejte zdarma - stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="8b865-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>  
  
     <span data-ttu-id="8b865-391">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="8b865-391">The result is as follows.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-392">Tento výstup ukazuje, že část haldy 0. generace používá 9 MB volného místa pro objekty a je 7 MB volného místa.</span><span class="sxs-lookup"><span data-stu-id="8b865-392">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="8b865-393">Tato analýza ukazuje rozsahu, ke které generace 0 přispívá k fragmentaci.</span><span class="sxs-lookup"><span data-stu-id="8b865-393">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="8b865-394">Toto množství využití haldy by měl odečtena od celkové částky jako Příčina fragmentace dlouhodobé objekty.</span><span class="sxs-lookup"><span data-stu-id="8b865-394">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="8b865-395">Počet nepřesunutelných objektů</span><span class="sxs-lookup"><span data-stu-id="8b865-395">To determine the number of pinned objects</span></span>  
  
-   <span data-ttu-id="8b865-396">V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8b865-396">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="8b865-397">**! GC**</span><span class="sxs-lookup"><span data-stu-id="8b865-397">**!gchandles**</span></span>  
  
     <span data-ttu-id="8b865-398">Statistické údaje zobrazené zahrnuje počet připojených popisovačů, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8b865-398">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="8b865-399">K určení délky času v uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-399">To determine the length of time in a garbage collection</span></span>  
  
-   <span data-ttu-id="8b865-400">Zkontrolujte `% Time in GC` čítače výkonu paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-400">Examine the `% Time in GC` memory performance counter.</span></span>  
  
     <span data-ttu-id="8b865-401">Hodnota se počítá pomocí časový interval vzorku.</span><span class="sxs-lookup"><span data-stu-id="8b865-401">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="8b865-402">Protože čítače se aktualizují na konci každé uvolňování paměti, aktuální ukázky budou mít stejnou hodnotu jako předchozí ukázce, pokud žádné kolekce došlo k chybě během intervalu.</span><span class="sxs-lookup"><span data-stu-id="8b865-402">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>  
  
     <span data-ttu-id="8b865-403">Časem shromáždění vynásobením časový interval vzorku s procentuální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8b865-403">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>  
  
     <span data-ttu-id="8b865-404">Následující data se zobrazí dvě sekund u 8 druhé studie čtyři intervalů vzorkování.</span><span class="sxs-lookup"><span data-stu-id="8b865-404">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="8b865-405">`Gen0`, `Gen1`, A `Gen2` sloupce zobrazují počet uvolnění paměti, ke kterým došlo během tohoto intervalu pro tuto generaci.</span><span class="sxs-lookup"><span data-stu-id="8b865-405">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     <span data-ttu-id="8b865-406">Tyto informace se nezobrazuje, když došlo k uvolnění paměti, ale můžete určit počet uvolnění paměti, ke kterým došlo v časový interval.</span><span class="sxs-lookup"><span data-stu-id="8b865-406">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="8b865-407">Za předpokladu, že nejhorší případ, desátý uvolnění paměti generace 0 dokončeno na začátku druhé interval a dokončení jedenáctý uvolnění paměti generace 0 na konci páté interval.</span><span class="sxs-lookup"><span data-stu-id="8b865-407">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="8b865-408">Doba mezi koncem na desetinu a konec jedenáctý kolekce uvolnění paměti je přibližně 2 sekund a čítač výkonu zobrazuje 3 %, proto byla trvání jedenáctý kolekce uvolnění paměti generace 0 (% 2 sekundy \* 3 = 60ms).</span><span class="sxs-lookup"><span data-stu-id="8b865-408">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>  
  
     <span data-ttu-id="8b865-409">V tomto příkladu jsou 5 období.</span><span class="sxs-lookup"><span data-stu-id="8b865-409">In this example, there are 5 periods.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     <span data-ttu-id="8b865-410">Druhé generace 2 kolekce paměti během intervalu třetí a dokončení v pátém intervalu.</span><span class="sxs-lookup"><span data-stu-id="8b865-410">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="8b865-411">Za předpokladu, že nejhorším případě, byl poslední uvolnění paměti 0. generace kolekce, který skončil na začátku druhý interval a generace 2 uvolňování dokončeno v čase konce páté intervalu.</span><span class="sxs-lookup"><span data-stu-id="8b865-411">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="8b865-412">Doba mezi koncem kolekce uvolnění paměti generace 0 a na konci uvolnění paměti generace 2 je proto 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="8b865-412">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="8b865-413">Vzhledem k tomu, `% Time in GC` čítač je 20 %, maximální množství času se generaci uvolňování paměti 2 mohou trvalo (4 sekundy \* 20 % = 800ms).</span><span class="sxs-lookup"><span data-stu-id="8b865-413">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>  
  
-   <span data-ttu-id="8b865-414">Alternativně můžete zjistit délku kolekce uvolnění paměti pomocí [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace k určení doby trvání uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-414">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>  
  
     <span data-ttu-id="8b865-415">Například následující data zobrazují sekvenci událostí, ke které došlo během nesouběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-415">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>  
  
    ```  
    Timestamp    Event name  
    513052        GCSuspendEEBegin_V1  
    513078        GCSuspendEEEnd  
    513090        GCStart_V1  
    517890        GCEnd_V1  
    517894        GCHeapStats  
    517897        GCRestartEEBegin  
    517918        GCRestartEEEnd  
    ```  
  
     <span data-ttu-id="8b865-416">Pozastavování spravovaná vlákna trvalo 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="8b865-416">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>  
  
     <span data-ttu-id="8b865-417">Skutečné uvolňování trvalo 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="8b865-417">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>  
  
     <span data-ttu-id="8b865-418">Obnovení spravovaných vláken trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="8b865-418">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>  
  
     <span data-ttu-id="8b865-419">Následující výstup představuje příklad, uvolňování paměti na pozadí a obsahuje pole procesu, vlákna a události.</span><span class="sxs-lookup"><span data-stu-id="8b865-419">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="8b865-420">(Zobrazují se všechna data.)</span><span class="sxs-lookup"><span data-stu-id="8b865-420">(Not all data is shown.)</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-421">`GCStart_V1` Událost v 42504816 ukazuje na to, že se jedná uvolňování paměti na pozadí, protože poslední pole má `1`.</span><span class="sxs-lookup"><span data-stu-id="8b865-421">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="8b865-422">Toto číslo změní uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-422">This becomes garbage collection No.</span></span> <span data-ttu-id="8b865-423">102019.</span><span class="sxs-lookup"><span data-stu-id="8b865-423">102019.</span></span>  
  
     <span data-ttu-id="8b865-424">`GCStart` Události dochází, protože je potřeba pro kolekci uvolnění dočasné paměti před zahájením uvolňování na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8b865-424">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="8b865-425">Toto číslo změní uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-425">This becomes garbage collection No.</span></span> <span data-ttu-id="8b865-426">102020.</span><span class="sxs-lookup"><span data-stu-id="8b865-426">102020.</span></span>  
  
     <span data-ttu-id="8b865-427">Při uvolňování paměti 42514170, číslo.</span><span class="sxs-lookup"><span data-stu-id="8b865-427">At 42514170, garbage collection No.</span></span> <span data-ttu-id="8b865-428">102020 dokončí.</span><span class="sxs-lookup"><span data-stu-id="8b865-428">102020 finishes.</span></span> <span data-ttu-id="8b865-429">Spravovaná vlákna jsou v tomto okamžiku restartuje.</span><span class="sxs-lookup"><span data-stu-id="8b865-429">The managed threads are restarted at this point.</span></span> <span data-ttu-id="8b865-430">To je dokončen ve vlákně 4372, která spustí tuto uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8b865-430">This is completed on thread 4372, which triggered this background garbage collection.</span></span>  
  
     <span data-ttu-id="8b865-431">Ve vlákně 4744 dojde k pozastavení.</span><span class="sxs-lookup"><span data-stu-id="8b865-431">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="8b865-432">Toto je pouze doba, jakou má pozastavit spravovaná vlákna uvolňování na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8b865-432">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="8b865-433">Tato doba je přibližně 99ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="8b865-433">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>  
  
     <span data-ttu-id="8b865-434">`GCEnd` Na 89931423 je událost pro uvolňování na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8b865-434">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="8b865-435">To znamená, že uvolňování na pozadí trvalo o 47seconds ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="8b865-435">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>  
  
     <span data-ttu-id="8b865-436">Zatímco spravovaná vlákna jsou spuštěné, zobrazí se libovolný počet kolekcí uvolnění dočasné paměti, ke kterým dochází.</span><span class="sxs-lookup"><span data-stu-id="8b865-436">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="8b865-437">Chcete-li zjistit, co vyvolalo uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-437">To determine what triggered a garbage collection</span></span>  
  
-   <span data-ttu-id="8b865-438">V ladicím programu WinDbg nebo Visual Studio s rozšířením SOS ladicího programu, načíst zadejte následující příkaz, který zobrazit všechna vlákna s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="8b865-438">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="8b865-439">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="8b865-439">**~\*kb**</span></span>  
  
     <span data-ttu-id="8b865-440">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="8b865-440">This command displays output similar to the following.</span></span>  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     <span data-ttu-id="8b865-441">Pokud kolekce paměti bylo způsobené nedostatečnou pamětí oznámení z operačního systému, zásobník volání je podobné, s tím rozdílem, že vlákno je vlákna finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="8b865-441">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="8b865-442">Vlákno finalizační metodu získá oznámení o asynchronní nedostatek paměti a indukuje kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8b865-442">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>  
  
     <span data-ttu-id="8b865-443">Pokud se uvolňování paměti kolekce byla způsobena přidělení paměti zásobníku se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="8b865-443">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-444">Pomocné rutiny just-in-time (`JIT_New*`) nakonec volá `GCHeap::GarbageCollectGeneration`.</span><span class="sxs-lookup"><span data-stu-id="8b865-444">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="8b865-445">Pokud zjistíte, že kolekce uvolnění paměti generace 2 jsou způsobeny přidělení, je třeba určit objektů, které byly shromážděny sadou 2 uvolnění paměti generace a jak se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="8b865-445">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="8b865-446">To znamená, že budete chtít zjistit rozdíl mezi začátkem a koncem 2 uvolnění paměti generace a objekty, které způsobily 2. generace kolekce.</span><span class="sxs-lookup"><span data-stu-id="8b865-446">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>  
  
     <span data-ttu-id="8b865-447">Například zadejte následující příkaz v ladicím programu zobrazíte od 2. generace kolekce:</span><span class="sxs-lookup"><span data-stu-id="8b865-447">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>  
  
     <span data-ttu-id="8b865-448">**! dumpheap-stat**</span><span class="sxs-lookup"><span data-stu-id="8b865-448">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="8b865-449">Příklad výstupu (zkrácený komentář pro zobrazení objektů, které používají nejvíce místa):</span><span class="sxs-lookup"><span data-stu-id="8b865-449">Example output (abridged to show the objects that use the most space):</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-450">Zopakujte příkaz na konci 2. generace:</span><span class="sxs-lookup"><span data-stu-id="8b865-450">Repeat the command at the end of generation 2:</span></span>  
  
     <span data-ttu-id="8b865-451">**! dumpheap-stat**</span><span class="sxs-lookup"><span data-stu-id="8b865-451">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="8b865-452">Příklad výstupu (zkrácený komentář pro zobrazení objektů, které používají nejvíce místa):</span><span class="sxs-lookup"><span data-stu-id="8b865-452">Example output (abridged to show the objects that use the most space):</span></span>  
  
    ```  
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
  
     <span data-ttu-id="8b865-453">`double[]` Objekty zmizí konci výstupu, což znamená, že byly shromážděny.</span><span class="sxs-lookup"><span data-stu-id="8b865-453">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="8b865-454">Tyto objekty zohlednily přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="8b865-454">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="8b865-455">Většinu zbývajících objektech nezměnil.</span><span class="sxs-lookup"><span data-stu-id="8b865-455">The remaining objects did not change much.</span></span> <span data-ttu-id="8b865-456">Proto tyto `double[]` objekty byly důvod, proč došlo k této kolekce uvolnění paměti generace 2.</span><span class="sxs-lookup"><span data-stu-id="8b865-456">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="8b865-457">Dalším krokem je zjistit, proč `double[]` objekty jsou existuje a proč se ukončila.</span><span class="sxs-lookup"><span data-stu-id="8b865-457">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="8b865-458">Můžete požádat o kód vývojáře, kde tyto objekty pochází, nebo můžete použít **gcroot** příkazu.</span><span class="sxs-lookup"><span data-stu-id="8b865-458">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="8b865-459">Chcete-li zjistit, jestli způsobuje vysoké využití procesoru uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-459">To determine whether high CPU usage is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="8b865-460">Korelace `% Time in GC` hodnota čítače výkonu paměti s časem procesu.</span><span class="sxs-lookup"><span data-stu-id="8b865-460">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>  
  
     <span data-ttu-id="8b865-461">Pokud `% Time in GC` hodnotu špičky ve stejnou dobu jako čas procesu, uvolňování paměti je příčinou vysoké využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="8b865-461">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="8b865-462">V opačném případě profilujte aplikaci, najít, kde dochází k vysoké využití.</span><span class="sxs-lookup"><span data-stu-id="8b865-462">Otherwise, profile the application to find where the high usage is occurring.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b865-463">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b865-463">See also</span></span>

- [<span data-ttu-id="8b865-464">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="8b865-464">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
