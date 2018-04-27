---
title: Kolekce paměti a výkon
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: daf70cdb7344f895059d0bc8b986edddbf7d53bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="873c5-102">Kolekce paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="873c5-102">Garbage Collection and Performance</span></span>
<a name="top"></a> <span data-ttu-id="873c5-103">Toto téma popisuje problémy týkající se shromažďování a paměti využití paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="873c5-104">Ho řeší problémy, které se týkají spravovaná halda a vysvětluje, jak, aby se minimalizoval vliv uvolňování paměti na vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="873c5-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="873c5-105">Každý problém obsahuje odkazy na postupy, které můžete použít k prozkoumání problémů.</span><span class="sxs-lookup"><span data-stu-id="873c5-105">Each issue has links to procedures that you can use to investigate problems.</span></span>  
  
 <span data-ttu-id="873c5-106">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="873c5-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="873c5-107">Nástrojů pro analýzu výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-107">Performance Analysis Tools</span></span>](#performance_analysis_tools)  
  
-   [<span data-ttu-id="873c5-108">Řešení potíží s výkonem</span><span class="sxs-lookup"><span data-stu-id="873c5-108">Troubleshooting Performance Issues</span></span>](#troubleshooting_performance_issues)  
  
-   [<span data-ttu-id="873c5-109">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="873c5-109">Troubleshooting Guidelines</span></span>](#troubleshooting_guidelines)  
  
-   [<span data-ttu-id="873c5-110">Postupy kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-110">Performance Check Procedures</span></span>](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a><span data-ttu-id="873c5-111">Nástrojů pro analýzu výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-111">Performance Analysis Tools</span></span>  
 <span data-ttu-id="873c5-112">Následující části popisují nástroje, které jsou k dispozici pro příčin problémů kolekce paměti a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-112">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="873c5-113">[Postupy](#performance_check_procedures) později v tomto tématu najdete na těchto nástrojů.</span><span class="sxs-lookup"><span data-stu-id="873c5-113">The [procedures](#performance_check_procedures) provided later in this topic refer to these tools.</span></span>  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a><span data-ttu-id="873c5-114">Čítače výkonu paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-114">Memory Performance Counters</span></span>  
 <span data-ttu-id="873c5-115">Čítače výkonu můžete použít ke shromažďování dat výkonu.</span><span class="sxs-lookup"><span data-stu-id="873c5-115">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="873c5-116">Pokyny najdete v tématu [běhová profilace](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="873c5-116">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="873c5-117">Využívání paměti rozhraním .NET CLR kategorie čítačů výkonu, jak je popsáno v [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), poskytuje informace o systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-117">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a><span data-ttu-id="873c5-118">Ladění pomocí SOS</span><span class="sxs-lookup"><span data-stu-id="873c5-118">Debugging with SOS</span></span>  
 <span data-ttu-id="873c5-119">Můžete použít [ladicí program systému Windows (WinDbg)](/windows-hardware/drivers/debugger/index) kontrola objekty v spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-119">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>
 
 <span data-ttu-id="873c5-120">Nainstalovat WinDbg, nainstalovat ladění nástrojů pro Windows z [stáhnout ladění nástrojů pro Windows](/windows-hardware/drivers/debugger/debugger-download-tools) stránky.</span><span class="sxs-lookup"><span data-stu-id="873c5-120">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a><span data-ttu-id="873c5-121">Události Trasování událostí pro Windows kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-121">Garbage Collection ETW Events</span></span>  
 <span data-ttu-id="873c5-122">Trasování událostí pro Windows (ETW) je systém trasování, které doplňují profilování a ladění v rozhraní .NET Framework poskytuje podporu.</span><span class="sxs-lookup"><span data-stu-id="873c5-122">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="873c5-123">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md) zaznamenat užitečné informace pro spravovaná halda z hlediska statistické analýze.</span><span class="sxs-lookup"><span data-stu-id="873c5-123">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="873c5-124">Například `GCStart_V1` událost, která se vyvolá, když je kolekce paměti dojde, obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="873c5-124">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>  
  
-   <span data-ttu-id="873c5-125">Které generování objektů, které jsou shromažďována.</span><span class="sxs-lookup"><span data-stu-id="873c5-125">Which generation of objects is being collected.</span></span>  
  
-   <span data-ttu-id="873c5-126">Co aktivuje uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-126">What triggered the garbage collection.</span></span>  
  
-   <span data-ttu-id="873c5-127">Typ kolekce paměti (souběžných nebo není souběžných).</span><span class="sxs-lookup"><span data-stu-id="873c5-127">Type of garbage collection (concurrent or not concurrent).</span></span>  
  
 <span data-ttu-id="873c5-128">Protokolování událostí trasování událostí pro Windows je efektivní a nebude maskování žádné problémy s výkonem přidružené uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-128">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="873c5-129">Proces můžete zadat vlastní události ve spojení s události trasování událostí.</span><span class="sxs-lookup"><span data-stu-id="873c5-129">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="873c5-130">Při přihlášení, můžete určit, jak a kdy dojde k problémům haldy korelační události aplikace a události kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-130">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="873c5-131">Serverová aplikace může například zadat události na začátku a na konci požadavku klienta.</span><span class="sxs-lookup"><span data-stu-id="873c5-131">For example, a server application could provide events at the start and end of a client request.</span></span>  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a><span data-ttu-id="873c5-132">Rozhraní API pro profilaci</span><span class="sxs-lookup"><span data-stu-id="873c5-132">The Profiling API</span></span>  
 <span data-ttu-id="873c5-133">Běžné language runtime (CLR) profilování rozhraní poskytují podrobné informace o objekty, které během uvolňování situace měla vliv na.</span><span class="sxs-lookup"><span data-stu-id="873c5-133">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="873c5-134">Kolekce paměti zahájení a ukončení, můžete být upozorněni profileru.</span><span class="sxs-lookup"><span data-stu-id="873c5-134">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="873c5-135">Na spravované haldě, včetně identifikaci objektů v každé generování může poskytovat sestavy o objektech.</span><span class="sxs-lookup"><span data-stu-id="873c5-135">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="873c5-136">Další informace najdete v tématu [přehled profilace](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="873c5-136">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>  
  
 <span data-ttu-id="873c5-137">Profilery může poskytovat komplexní informace.</span><span class="sxs-lookup"><span data-stu-id="873c5-137">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="873c5-138">Komplexní profilery však mohou potenciálně změnit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="873c5-138">However, complex profilers can potentially modify an application's behavior.</span></span>  
  
### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="873c5-139">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="873c5-139">Application Domain Resource Monitoring</span></span>  
 <span data-ttu-id="873c5-140">Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], prostředků domény aplikace monitorování (ARM) umožňuje hostitelům sledování využití procesoru a paměti aplikační doménou.</span><span class="sxs-lookup"><span data-stu-id="873c5-140">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="873c5-141">Další informace najdete v tématu [sledování prostředků domény aplikace](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="873c5-141">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>  
  
 [<span data-ttu-id="873c5-142">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="873c5-142">Back to top</span></span>](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="873c5-143">Řešení potíží s výkonem</span><span class="sxs-lookup"><span data-stu-id="873c5-143">Troubleshooting Performance Issues</span></span>  
 <span data-ttu-id="873c5-144">Prvním krokem je [určit, zda problém je ve skutečnosti uvolňování](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="873c5-144">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="873c5-145">Pokud zjistíte, že se jedná, vyberte z následujícího seznamu k vyřešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="873c5-145">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>  
  
-   [<span data-ttu-id="873c5-146">Je vyvolána výjimka z důvodu nedostatku paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-146">An out-of-memory exception is thrown</span></span>](#Issue_OOM)  
  
-   [<span data-ttu-id="873c5-147">Proces využívá příliš mnoho paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-147">The process uses too much memory</span></span>](#Issue_TooMuchMemory)  
  
-   [<span data-ttu-id="873c5-148">Uvolňování paměti nezíská objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="873c5-148">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)  
  
-   [<span data-ttu-id="873c5-149">Spravovaná halda je příliš fragmentovaná.</span><span class="sxs-lookup"><span data-stu-id="873c5-149">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)  
  
-   [<span data-ttu-id="873c5-150">Jsou příliš dlouhé pozastaví kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-150">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)  
  
-   [<span data-ttu-id="873c5-151">Generace 0 je příliš velký.</span><span class="sxs-lookup"><span data-stu-id="873c5-151">Generation 0 is too big</span></span>](#Issue_Gen0)  
  
-   [<span data-ttu-id="873c5-152">Využití procesoru během uvolňování paměti je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="873c5-152">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="873c5-153">Problém: Je vyvolána výjimka z důvodu nedostatku paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-153">Issue: An Out-of-Memory Exception Is Thrown</span></span>  
 <span data-ttu-id="873c5-154">Existují dvě legitimní případů pro spravované <xref:System.OutOfMemoryException> vyvolání:</span><span class="sxs-lookup"><span data-stu-id="873c5-154">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>  
  
-   <span data-ttu-id="873c5-155">Nedostatek virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-155">Running out of virtual memory.</span></span>  
  
     <span data-ttu-id="873c5-156">Uvolňování paměti přidělí paměť ze systému v segmentech předem určená velikost.</span><span class="sxs-lookup"><span data-stu-id="873c5-156">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="873c5-157">Pokud přidělení vyžaduje další segment, ale neexistuje žádné souvislý volné blok left v prostoru virtuální paměti procesu, přidělení pro spravovaná halda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="873c5-157">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>  
  
-   <span data-ttu-id="873c5-158">Nemá dost fyzické paměti k přidělení.</span><span class="sxs-lookup"><span data-stu-id="873c5-158">Not having enough physical memory to allocate.</span></span>  
  
|<span data-ttu-id="873c5-159">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-159">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="873c5-160">Určete, zda je spravovat výjimky nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-160">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="873c5-161">Určete, kolik virtuální paměti může být vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="873c5-161">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="873c5-162">Určí, zda je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-162">Determine whether there is enough physical memory.</span></span>](#Physical)|  
  
 <span data-ttu-id="873c5-163">Pokud zjistíte, že výjimka není oprávněné, obraťte se na Microsoft zákaznický servis a podporu s následujícími informacemi:</span><span class="sxs-lookup"><span data-stu-id="873c5-163">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>  
  
-   <span data-ttu-id="873c5-164">Zásobník s spravované výjimky nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-164">The stack with the managed out-of-memory exception.</span></span>  
  
-   <span data-ttu-id="873c5-165">Úplný výpis stavu paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-165">Full memory dump.</span></span>  
  
-   <span data-ttu-id="873c5-166">Data, která prokáže, že se nejedná o potřebné výjimky nedostatku paměti, včetně dat, která ukazuje, že virtuální nebo fyzická paměť není problém.</span><span class="sxs-lookup"><span data-stu-id="873c5-166">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="873c5-167">Problém: Proces využívá příliš mnoho paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-167">Issue: The Process Uses Too Much Memory</span></span>  
 <span data-ttu-id="873c5-168">Běžné předpokladem je, že zobrazení využití paměti na **výkonu** karty Správce úloh systému Windows může naznačit, když se používá příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-168">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="873c5-169">Ale zobrazované se vztahují na pracovní sady; neobsahuje informace o využití virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-169">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>  
  
 <span data-ttu-id="873c5-170">Pokud zjistíte, že problém je způsoben spravovaná halda, musí měření spravovaná halda v čase k určení všech vzory.</span><span class="sxs-lookup"><span data-stu-id="873c5-170">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>  
  
 <span data-ttu-id="873c5-171">Pokud zjistíte, že není spravovaná halda příčinou problému, je nutné použít nativní ladění.</span><span class="sxs-lookup"><span data-stu-id="873c5-171">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>  
  
|<span data-ttu-id="873c5-172">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-172">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="873c5-173">Určete, kolik virtuální paměti může být vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="873c5-173">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="873c5-174">Určete, kolik paměti je spravovaná halda potvrzení.</span><span class="sxs-lookup"><span data-stu-id="873c5-174">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="873c5-175">Určete, kolik paměti si vyhrazuje spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-175">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="873c5-176">Určení rozsáhlé objekty v 2. generace.</span><span class="sxs-lookup"><span data-stu-id="873c5-176">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="873c5-177">Určí, odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="873c5-177">Determine references to objects.</span></span>](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="873c5-178">Problém: Uvolňování nezíská objekty dostatečně rychle</span><span class="sxs-lookup"><span data-stu-id="873c5-178">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>  
 <span data-ttu-id="873c5-179">Jakmile se zobrazí, jako kdyby objekty nejsou převzata podle očekávání pro uvolňování paměti, je třeba určit, zda jsou všechny silné odkazy na tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="873c5-179">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>  
  
 <span data-ttu-id="873c5-180">Tento problém může se zobrazit, pokud byl žádné uvolňování paměti pro generování, která obsahuje objekt neaktivní, který označuje, že finalizační metodu pro neaktivní objekt nebyl spuštěn.</span><span class="sxs-lookup"><span data-stu-id="873c5-180">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="873c5-181">Například to je možné při spouštění aplikace single-threaded apartment (STA) a vlákno této služby, které nelze volat finalizační metodu fronty do ní.</span><span class="sxs-lookup"><span data-stu-id="873c5-181">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>  
  
|<span data-ttu-id="873c5-182">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-182">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="873c5-183">Zkontrolujte odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="873c5-183">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="873c5-184">Určí, zda byl spuštěn finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="873c5-184">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="873c5-185">Zjistěte, jestli jsou objekty čekají na Dokončit.</span><span class="sxs-lookup"><span data-stu-id="873c5-185">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="873c5-186">Problém: Je spravovaná halda je příliš fragmentovaná.</span><span class="sxs-lookup"><span data-stu-id="873c5-186">Issue: The Managed Heap Is Too fragmented</span></span>  
 <span data-ttu-id="873c5-187">Úroveň fragmentace se vypočítá jako podíl volné místo přes celkové přidělené paměti pro generování.</span><span class="sxs-lookup"><span data-stu-id="873c5-187">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="873c5-188">Přijatelnou úroveň fragmentace pro 2. generace, je více než 20 %.</span><span class="sxs-lookup"><span data-stu-id="873c5-188">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="873c5-189">Vzhledem k tomu, že generace 2 můžete získat velmi velkých poměr fragmentace je důležitější než absolutní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="873c5-189">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>  
  
 <span data-ttu-id="873c5-190">S velké množství volného místa ve generace 0 se nejedná o problém protože to je generace, kde jsou přiděleny nové objekty.</span><span class="sxs-lookup"><span data-stu-id="873c5-190">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>  
  
 <span data-ttu-id="873c5-191">Není zkomprimovanou bude vždy fragmentace dochází v haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="873c5-191">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="873c5-192">Volné objekty, které jsou přiléhající přirozeně sbalené do jednoho místa pro uspokojení požadavků na přidělení velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="873c5-192">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>  
  
 <span data-ttu-id="873c5-193">Fragmentace se může stát problém v generace 1 a generace 2.</span><span class="sxs-lookup"><span data-stu-id="873c5-193">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="873c5-194">Pokud tyto generace máte velké množství volného místa po uvolnění paměti, využití aplikace objektu může být nutné změny a měli byste zvážit, znovu vyhodnocení dobu trvání dlouhodobé objektů.</span><span class="sxs-lookup"><span data-stu-id="873c5-194">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>  
  
 <span data-ttu-id="873c5-195">Nadměrné Připnutí objektů může zvýšit fragmentace.</span><span class="sxs-lookup"><span data-stu-id="873c5-195">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="873c5-196">Pokud fragmentace vysoké, může být připnuli příliš mnoho objektů.</span><span class="sxs-lookup"><span data-stu-id="873c5-196">If fragmentation is high, too many objects could be pinned.</span></span>  
  
 <span data-ttu-id="873c5-197">Pokud fragmentace virtuální paměti znemožňuje přidávání segmenty uvolňování paměti, může být příčin jednu z těchto možností:</span><span class="sxs-lookup"><span data-stu-id="873c5-197">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>  
  
-   <span data-ttu-id="873c5-198">Časté načítání a uvolňování mnoho malých sestavení.</span><span class="sxs-lookup"><span data-stu-id="873c5-198">Frequent loading and unloading of many small assemblies.</span></span>  
  
-   <span data-ttu-id="873c5-199">Když spolupráce s nespravovaným kódem, který uchovává příliš mnoho odkazů na objekty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="873c5-199">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>  
  
-   <span data-ttu-id="873c5-200">Vytváření rozsáhlé přechodný objekty, což způsobí, že velkého objektu haldy alokace a často volné haldy segmenty.</span><span class="sxs-lookup"><span data-stu-id="873c5-200">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>  
  
     <span data-ttu-id="873c5-201">Aplikace hostování CLR, může požádat o, bude systém uvolňování zachovali jeho segmenty.</span><span class="sxs-lookup"><span data-stu-id="873c5-201">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="873c5-202">Tím se snižuje frekvence přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="873c5-202">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="873c5-203">To lze provést pomocí příznaku STARTUP_HOARD_GC_VM v [STARTUP_FLAGS – výčet](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="873c5-203">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
|<span data-ttu-id="873c5-204">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-204">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="873c5-205">Určete množství volného místa v spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-205">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="873c5-206">Určete počet připojených objektů.</span><span class="sxs-lookup"><span data-stu-id="873c5-206">Determine the number of pinned objects.</span></span>](#Pinned)|  
  
 <span data-ttu-id="873c5-207">Pokud si myslíte, že neexistuje žádná legitimní příčinu fragmentaci, obraťte se na oddělení zákaznických služeb a podpory.</span><span class="sxs-lookup"><span data-stu-id="873c5-207">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="873c5-208">Problém: Jsou příliš dlouhé pozastaví kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-208">Issue: Garbage Collection Pauses Are Too Long</span></span>  
 <span data-ttu-id="873c5-209">Uvolňování paměti funguje v reálném čase logicky, takže aplikace musí být schopen tolerovat možnost, zastaví se některé.</span><span class="sxs-lookup"><span data-stu-id="873c5-209">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="873c5-210">Kritéria pro logicky reálném čase je, že 95 % operací musí dokončit v době.</span><span class="sxs-lookup"><span data-stu-id="873c5-210">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>  
  
 <span data-ttu-id="873c5-211">V souběžné uvolňování paměti je povoleno spustit během kolekce, což znamená, že jsou velmi minimální pozastaví spravovaných vláknech.</span><span class="sxs-lookup"><span data-stu-id="873c5-211">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>  
  
 <span data-ttu-id="873c5-212">Dočasné kolekce (generace 0 a 1) poslední pouze několik milisekund, takže snížení pozastaví obvykle není možné je.</span><span class="sxs-lookup"><span data-stu-id="873c5-212">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="873c5-213">Však může snížit pozastaví v 2. generace kolekce tak, že změníte vzorec, podle požadavků na přidělení jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="873c5-213">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>  
  
 <span data-ttu-id="873c5-214">Jiné, přesnější, metodou je použití [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="873c5-214">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="873c5-215">Přidáním časové razítko rozdíly pro posloupnost událostí, můžete najít časování pro kolekce.</span><span class="sxs-lookup"><span data-stu-id="873c5-215">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="873c5-216">Pořadí celé kolekce obsahuje pozastavení modul provádění, samotná kolekce paměti a obnovení modulu provádění.</span><span class="sxs-lookup"><span data-stu-id="873c5-216">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>  
  
 <span data-ttu-id="873c5-217">Můžete použít [oznámení pro uvolňování paměti](../../../docs/standard/garbage-collection/notifications.md) určit, zda server dojde ke kolekci 2. generace a jestli přesměrování spojnic požadavky na jiný server by mělo odlehčit případné potíže s pozastaví.</span><span class="sxs-lookup"><span data-stu-id="873c5-217">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>  
  
|<span data-ttu-id="873c5-218">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-218">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="873c5-219">Určete dobu v uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-219">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="873c5-220">Určete, co způsobilo uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-220">Determine what caused a garbage collection.</span></span>](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="873c5-221">Problém: 0. generace je příliš velký.</span><span class="sxs-lookup"><span data-stu-id="873c5-221">Issue: Generation 0 Is Too Big</span></span>  
 <span data-ttu-id="873c5-222">Generace 0 je mohou mít větší počet objektů na 64bitovém systému, zejména v případě, že místo uvolňování paměti pracovních stanic použijete kolekce paměti na serveru.</span><span class="sxs-lookup"><span data-stu-id="873c5-222">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="873c5-223">Je to proto, že je vyšší v těchto prostředích prahové hodnoty pro aktivaci uvolňování 0. generace a 0. generace kolekce může získat mnohem větší.</span><span class="sxs-lookup"><span data-stu-id="873c5-223">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="873c5-224">Výkon je vyšší, pokud aplikace přiděluje víc paměti než se aktivuje uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-224">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="873c5-225">Problém: Využití procesoru během uvolňování paměti je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="873c5-225">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>  
 <span data-ttu-id="873c5-226">Během uvolňování paměti bude vysoké využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="873c5-226">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="873c5-227">Pokud významné množství času procesu je věnovaný uvolnění paměti, počet kolekcí, je příliš časté nebo kolekce je trvá příliš dlouho.</span><span class="sxs-lookup"><span data-stu-id="873c5-227">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="873c5-228">Počet objektů na spravovaná halda vyšší přidělení způsobí, že uvolňování paměti častěji.</span><span class="sxs-lookup"><span data-stu-id="873c5-228">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="873c5-229">Snížení míry přidělení snižuje frekvence kolekce.</span><span class="sxs-lookup"><span data-stu-id="873c5-229">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>  
  
 <span data-ttu-id="873c5-230">Přidělení sazby můžete monitorovat pomocí `Allocated Bytes/second` čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="873c5-230">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="873c5-231">Další informace najdete v tématu [čítače výkonu v rozhraní .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="873c5-231">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
 <span data-ttu-id="873c5-232">Doba trvání v kolekci je primárně faktor počet objektů, které zůstanou platné i po po přidělení.</span><span class="sxs-lookup"><span data-stu-id="873c5-232">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="873c5-233">Uvolňování paměti musí projít velké množství paměti, pokud zůstanou mnoho objektů, které se mají shromažďovat.</span><span class="sxs-lookup"><span data-stu-id="873c5-233">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="873c5-234">Pracovní kompaktních přesun je časově náročná.</span><span class="sxs-lookup"><span data-stu-id="873c5-234">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="873c5-235">Pokud chcete zjistit, kolik objekty byly zpracovány během kolekce, nastavte zarážky v ladicím programu na konci uvolňování paměti pro zadané generaci.</span><span class="sxs-lookup"><span data-stu-id="873c5-235">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>  
  
|<span data-ttu-id="873c5-236">Kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-236">Performance checks</span></span>|  
|------------------------|  
|[<span data-ttu-id="873c5-237">Určí, pokud vysoké využití procesoru je způsobena uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-237">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="873c5-238">Nastavte zarážky na konci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-238">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|  
  
 [<span data-ttu-id="873c5-239">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="873c5-239">Back to top</span></span>](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a><span data-ttu-id="873c5-240">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="873c5-240">Troubleshooting Guidelines</span></span>  
 <span data-ttu-id="873c5-241">Tato část popisuje pokyny, které byste měli zvážit při začnete vaší šetření.</span><span class="sxs-lookup"><span data-stu-id="873c5-241">This section describes guidelines that you should consider as you begin your investigations.</span></span>  
  
### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="873c5-242">Pracovní stanice nebo kolekce paměti na serveru</span><span class="sxs-lookup"><span data-stu-id="873c5-242">Workstation or Server Garbage Collection</span></span>  
 <span data-ttu-id="873c5-243">Určí, pokud používáte správný typ uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-243">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="873c5-244">Pokud vaše aplikace používá více vláken a instance objektů, použijte místo uvolňování paměti pracovních stanic kolekce paměti na serveru.</span><span class="sxs-lookup"><span data-stu-id="873c5-244">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="873c5-245">Kolekce paměti na serveru funguje na více vláken, zatímco vyžaduje více instancí aplikace ke spuštění vlastní vláken kolekce paměti a pokouší o čas procesoru uvolňování paměti pracovních stanic.</span><span class="sxs-lookup"><span data-stu-id="873c5-245">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>  
  
 <span data-ttu-id="873c5-246">Aplikace, který má nízkou zatížení a které provádí úlohy zřídka v pozadí, třeba služby, použít uvolňování paměti pracovních stanic s souběžné uvolňování zakázána.</span><span class="sxs-lookup"><span data-stu-id="873c5-246">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>  
  
### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="873c5-247">Když pro měření velikosti spravovaná halda</span><span class="sxs-lookup"><span data-stu-id="873c5-247">When to Measure the Managed Heap Size</span></span>  
 <span data-ttu-id="873c5-248">Pokud používáte profileru, budete muset vytvořit konzistentní měřicí vzor efektivně diagnostikovat problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="873c5-248">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="873c5-249">Mějte na paměti následující body k vytvoření plánu:</span><span class="sxs-lookup"><span data-stu-id="873c5-249">Consider the following points to establish a schedule:</span></span>  
  
-   <span data-ttu-id="873c5-250">Pokud budete vyhodnocovat po uvolnění paměti generace 2, celý spravovaná halda je bezplatná paměti (neaktivní objekty).</span><span class="sxs-lookup"><span data-stu-id="873c5-250">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>  
  
-   <span data-ttu-id="873c5-251">Pokud budete vyhodnocovat okamžitě po uvolnění paměti generace 0, nebudou shromažďovány ještě objekty v generace 1 a 2.</span><span class="sxs-lookup"><span data-stu-id="873c5-251">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>  
  
-   <span data-ttu-id="873c5-252">Pokud budete vyhodnocovat bezprostředně před uvolnění paměti, budou měřit tolik přidělení nejdříve, před zahájením uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-252">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>  
  
-   <span data-ttu-id="873c5-253">Měření během uvolňování paměti je problematické, protože nejsou v platném stavu pro traversal datové struktury systém uvolňování paměti a nemusí být možné tak, abyste získali výsledků.</span><span class="sxs-lookup"><span data-stu-id="873c5-253">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="873c5-254">Toto je záměrné.</span><span class="sxs-lookup"><span data-stu-id="873c5-254">This is by design.</span></span>  
  
-   <span data-ttu-id="873c5-255">Při použití uvolňování paměti pracovních stanic s souběžné uvolňování paměti, nejsou regenerovaný objekty komprimován, takže velikost haldy může být stejné nebo větší (fragmentace může vypadat musí být větší).</span><span class="sxs-lookup"><span data-stu-id="873c5-255">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>  
  
-   <span data-ttu-id="873c5-256">Souběžné uvolňování paměti v generaci 2 je zpožděno. při zatížení fyzická paměť je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="873c5-256">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>  
  
 <span data-ttu-id="873c5-257">Následující postup popisuje, jak nastavit bod přerušení, můžete změřit spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-257">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="873c5-258">Chcete-li nastavit zarážky na konci uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-258">To set a breakpoint at the end of garbage collection</span></span>  
  
-   <span data-ttu-id="873c5-259">V WinDbg s příponou ladicí program SOS načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-259">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="873c5-260">**BP mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2), kb';' g. "**</span><span class="sxs-lookup"><span data-stu-id="873c5-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>  
  
     <span data-ttu-id="873c5-261">kde **GcCondemnedGeneration** nastavená na požadované generování.</span><span class="sxs-lookup"><span data-stu-id="873c5-261">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="873c5-262">Tento příkaz vyžaduje soukromých symbolů.</span><span class="sxs-lookup"><span data-stu-id="873c5-262">This command requires private symbols.</span></span>  
  
     <span data-ttu-id="873c5-263">Tento příkaz vynutí zalomení, když **RestartEE** se spustí po objekty 2. generace bylo uvolněno pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-263">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>  
  
     <span data-ttu-id="873c5-264">Kolekce paměti na serveru, volá pouze jedno vlákno **RestartEE**, takže zarážce během uvolňování paměti 2. generace dojde pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="873c5-264">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>  
  
 [<span data-ttu-id="873c5-265">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="873c5-265">Back to top</span></span>](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a><span data-ttu-id="873c5-266">Postupy kontroly výkonu</span><span class="sxs-lookup"><span data-stu-id="873c5-266">Performance Check Procedures</span></span>  
 <span data-ttu-id="873c5-267">Tato část popisuje následující postup najít příčinu problém výkonu:</span><span class="sxs-lookup"><span data-stu-id="873c5-267">This section describes the following procedures to isolate the cause of your performance issue:</span></span>  
  
-   [<span data-ttu-id="873c5-268">Určí, zda je problém způsoben uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-268">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)  
  
-   [<span data-ttu-id="873c5-269">Určete, zda je spravovat výjimky nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-269">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)  
  
-   [<span data-ttu-id="873c5-270">Určete, kolik virtuální paměti může být vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="873c5-270">Determine how much virtual memory can be reserved.</span></span>](#GetVM)  
  
-   [<span data-ttu-id="873c5-271">Určí, zda je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-271">Determine whether there is enough physical memory.</span></span>](#Physical)  
  
-   [<span data-ttu-id="873c5-272">Určete, kolik paměti je spravovaná halda potvrzení.</span><span class="sxs-lookup"><span data-stu-id="873c5-272">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)  
  
-   [<span data-ttu-id="873c5-273">Určete, kolik paměti si vyhrazuje spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-273">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)  
  
-   [<span data-ttu-id="873c5-274">Určení rozsáhlé objekty v 2. generace.</span><span class="sxs-lookup"><span data-stu-id="873c5-274">Determine large objects in generation 2.</span></span>](#ExamineGen2)  
  
-   [<span data-ttu-id="873c5-275">Určí, odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="873c5-275">Determine references to objects.</span></span>](#ObjRef)  
  
-   [<span data-ttu-id="873c5-276">Určí, zda byl spuštěn finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="873c5-276">Determine whether a finalizer has been run.</span></span>](#Induce)  
  
-   [<span data-ttu-id="873c5-277">Zjistěte, jestli jsou objekty čekají na Dokončit.</span><span class="sxs-lookup"><span data-stu-id="873c5-277">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)  
  
-   [<span data-ttu-id="873c5-278">Určete množství volného místa v spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-278">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)  
  
-   [<span data-ttu-id="873c5-279">Určete počet připojených objektů.</span><span class="sxs-lookup"><span data-stu-id="873c5-279">Determine the number of pinned objects.</span></span>](#Pinned)  
  
-   [<span data-ttu-id="873c5-280">Určete dobu v uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-280">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)  
  
-   [<span data-ttu-id="873c5-281">Zjistěte, co aktivuje uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-281">Determine what triggered a garbage collection.</span></span>](#Triggered)  
  
-   [<span data-ttu-id="873c5-282">Určí, zda vysoké využití procesoru je způsobena uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-282">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="873c5-283">Chcete-li zjistit, zda je problém způsoben uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-283">To determine whether the problem is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="873c5-284">Zkontrolujte následující čítače výkonu dvě paměti:</span><span class="sxs-lookup"><span data-stu-id="873c5-284">Examine the following two memory performance counters:</span></span>  
  
    -   <span data-ttu-id="873c5-285">**Čas**.</span><span class="sxs-lookup"><span data-stu-id="873c5-285">**% Time in GC**.</span></span> <span data-ttu-id="873c5-286">Zobrazuje procentuální hodnotu uplynulého času stráveného provádění úklidu po poslední cyklus sběru uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-286">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="873c5-287">Tento čítač slouží k určení, zda má systém uvolňování tráví příliš mnoho času, aby spravovaná halda místo k dispozici.</span><span class="sxs-lookup"><span data-stu-id="873c5-287">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="873c5-288">Pokud čas strávený v uvolňování paměti je relativně nízký, který by to znamenat problém prostředků mimo spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-288">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="873c5-289">Tento čítač nemusí být přesné při souběžných nebo je zahrnuta kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="873c5-289">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>  
  
    -   <span data-ttu-id="873c5-290">**# Celkový počet potvrzených bajtů**.</span><span class="sxs-lookup"><span data-stu-id="873c5-290">**# Total committed Bytes**.</span></span> <span data-ttu-id="873c5-291">Zobrazuje velikost virtuální paměti aktuálně potvrzeno modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="873c5-291">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="873c5-292">Tento čítač použijte k určení, zda je paměť spotřebovávají uvolňování nadměrné část paměti, která vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="873c5-292">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>  
  
     <span data-ttu-id="873c5-293">Většina čítačů výkonu paměti jsou aktualizovány na konci každé uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-293">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="873c5-294">Proto nemusí odráží aktuální podmínky, které chcete získat informace o.</span><span class="sxs-lookup"><span data-stu-id="873c5-294">Therefore, they may not reflect the current conditions that you want information about.</span></span>  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="873c5-295">Chcete-li zjistit, jestli je spravovaný výjimky nedostatku paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-295">To determine whether the out-of-memory exception is managed</span></span>  
  
1.  <span data-ttu-id="873c5-296">V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst, zadejte v tiskové výjimky (**pe**) příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-296">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>  
  
     <span data-ttu-id="873c5-297">**! pe**</span><span class="sxs-lookup"><span data-stu-id="873c5-297">**!pe**</span></span>  
  
     <span data-ttu-id="873c5-298">Pokud je spravováno výjimku, <xref:System.OutOfMemoryException> zobrazí jako typ výjimky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="873c5-298">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2.  <span data-ttu-id="873c5-299">Pokud výstup neurčuje výjimku, budete muset určit, které vlákno výjimky nedostatku paměti je z.</span><span class="sxs-lookup"><span data-stu-id="873c5-299">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="873c5-300">Zadejte následující příkaz v ladicím programu zobrazíte všechna vlákna s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="873c5-300">Type the following command in the debugger to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="873c5-301">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="873c5-301">**~\*kb**</span></span>  
  
     <span data-ttu-id="873c5-302">Vlákno se zásobníkem, který má výjimka volání je indikován `RaiseTheException` argument.</span><span class="sxs-lookup"><span data-stu-id="873c5-302">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="873c5-303">Toto je objekt spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="873c5-303">This is the managed exception object.</span></span>  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3.  <span data-ttu-id="873c5-304">Tento příkaz můžete dump vnořené výjimky.</span><span class="sxs-lookup"><span data-stu-id="873c5-304">You can use the following command to dump nested exceptions.</span></span>  
  
     <span data-ttu-id="873c5-305">**! pe-vnořené**</span><span class="sxs-lookup"><span data-stu-id="873c5-305">**!pe -nested**</span></span>  
  
     <span data-ttu-id="873c5-306">Pokud nenajdete žádné výjimky, výjimky nedostatku paměti pochází z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="873c5-306">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="873c5-307">Chcete-li zjistit, kolik virtuální paměti může být vyhrazeno</span><span class="sxs-lookup"><span data-stu-id="873c5-307">To determine how much virtual memory can be reserved</span></span>  
  
-   <span data-ttu-id="873c5-308">V WinDbg s příponou ladicí program SOS načíst zadejte následující příkaz k získání největší volné oblasti:</span><span class="sxs-lookup"><span data-stu-id="873c5-308">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>  
  
     <span data-ttu-id="873c5-309">**! adres – souhrn**</span><span class="sxs-lookup"><span data-stu-id="873c5-309">**!address -summary**</span></span>  
  
     <span data-ttu-id="873c5-310">Největší volné oblasti se zobrazí, jak je znázorněno v následující výstup.</span><span class="sxs-lookup"><span data-stu-id="873c5-310">The largest free region is displayed as shown in the following output.</span></span>  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     <span data-ttu-id="873c5-311">V tomto příkladu je velikost největší volné oblasti přibližně 24000 KB (3A980 v šestnáctkové).</span><span class="sxs-lookup"><span data-stu-id="873c5-311">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="873c5-312">Tato oblast je mnohem menší než jaké uvolňování potřebuje pro segment.</span><span class="sxs-lookup"><span data-stu-id="873c5-312">This region is much smaller than what the garbage collector needs for a segment.</span></span>  
  
     <span data-ttu-id="873c5-313">-nebo-</span><span class="sxs-lookup"><span data-stu-id="873c5-313">-or-</span></span>  
  
-   <span data-ttu-id="873c5-314">Použití **vmstat** příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-314">Use the **vmstat** command:</span></span>  
  
     <span data-ttu-id="873c5-315">**! vmstat**</span><span class="sxs-lookup"><span data-stu-id="873c5-315">**!vmstat**</span></span>  
  
     <span data-ttu-id="873c5-316">Největší volné oblast je největší hodnotu ve sloupci maximální, jak je znázorněno v následující výstup.</span><span class="sxs-lookup"><span data-stu-id="873c5-316">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>  
  
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
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="873c5-317">Chcete-li určit, zda je dostatek fyzické paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-317">To determine whether there is enough physical memory</span></span>  
  
1.  <span data-ttu-id="873c5-318">Spuštění Správce úloh systému Windows.</span><span class="sxs-lookup"><span data-stu-id="873c5-318">Start Windows Task Manager.</span></span>  
  
2.  <span data-ttu-id="873c5-319">Na **výkonu** kartě, podívejte se na potvrzení hodnotu.</span><span class="sxs-lookup"><span data-stu-id="873c5-319">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="873c5-320">(V systému Windows 7, podívejte se na **potvrzení (KB)** v **systémové skupiny**.)</span><span class="sxs-lookup"><span data-stu-id="873c5-320">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>  
  
     <span data-ttu-id="873c5-321">Pokud **celkový** blízko **Limit**, je málo na fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-321">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="873c5-322">Chcete-li určit, kolik paměti je potvrzením spravovaná halda</span><span class="sxs-lookup"><span data-stu-id="873c5-322">To determine how much memory the managed heap is committing</span></span>  
  
-   <span data-ttu-id="873c5-323">Použití `# Total committed bytes` čítače výkonu paměti získat počet bajtů, které je spravovaná halda potvrzení.</span><span class="sxs-lookup"><span data-stu-id="873c5-323">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="873c5-324">Uvolňování paměti potvrdí bloků v segmentu, podle potřeby, ne všechny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="873c5-324">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="873c5-325">Nepoužívejte `# Bytes in all Heaps` čítače výkonu, protože nepředstavuje skutečné využití paměti podle spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="873c5-325">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="873c5-326">Velikost generace je součástí tuto hodnotu a je ve skutečnosti jeho velikost mezní hodnoty, to znamená, velikost, kterou indukuje uvolnění paměti-li generování objektů.</span><span class="sxs-lookup"><span data-stu-id="873c5-326">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="873c5-327">Tato hodnota je proto obvykle nula.</span><span class="sxs-lookup"><span data-stu-id="873c5-327">Therefore, this value is usually zero.</span></span>  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="873c5-328">Chcete-li určit, kolik paměti si vyhrazuje spravovaná halda</span><span class="sxs-lookup"><span data-stu-id="873c5-328">To determine how much memory the managed heap reserves</span></span>  
  
-   <span data-ttu-id="873c5-329">Použití `# Total reserved bytes` čítače výkonu paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-329">Use the `# Total reserved bytes` memory performance counter.</span></span>  
  
     <span data-ttu-id="873c5-330">Rezervuje má systém uvolňování paměti v segmentech, a můžete určit, kde segment spustí pomocí **eeheap** příkaz.</span><span class="sxs-lookup"><span data-stu-id="873c5-330">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="873c5-331">I když může určit množství paměti, kterou uvolňování paměti přidělí pro každý segment, velikost segmentu závisí na implementaci a mohou podléhat změnám kdykoli, včetně v pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="873c5-331">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="873c5-332">Vaše aplikace by nikdy Zkontrolujte předpoklady o nebo závisí na velikosti určitý segment, ani pokusit nakonfigurovat množství paměti k dispozici pro přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="873c5-332">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
-   <span data-ttu-id="873c5-333">V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-333">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="873c5-334">**! eeheap – uvolňování paměti**</span><span class="sxs-lookup"><span data-stu-id="873c5-334">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="873c5-335">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="873c5-335">The result is as follows.</span></span>  
  
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
  
     <span data-ttu-id="873c5-336">Adresy indikován "segment" jsou počáteční adresy segmentů.</span><span class="sxs-lookup"><span data-stu-id="873c5-336">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="873c5-337">Chcete-li zjistit rozsáhlé objekty v 2. generace</span><span class="sxs-lookup"><span data-stu-id="873c5-337">To determine large objects in generation 2</span></span>  
  
-   <span data-ttu-id="873c5-338">V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-338">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="873c5-339">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="873c5-339">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="873c5-340">Pokud je příliš velká, spravovaná halda **dumpheap** může trvat dokončení.</span><span class="sxs-lookup"><span data-stu-id="873c5-340">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>  
  
     <span data-ttu-id="873c5-341">Můžete začít analýza za posledních několika řádků výstupu, protože jejich seznam objektů, které používají nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="873c5-341">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="873c5-342">Příklad:</span><span class="sxs-lookup"><span data-stu-id="873c5-342">For example:</span></span>  
  
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
  
     <span data-ttu-id="873c5-343">Poslední objekt uvedené je řetězec a zabírá nejvíce místa.</span><span class="sxs-lookup"><span data-stu-id="873c5-343">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="873c5-344">Můžete zkontrolovat aplikace, abyste viděli, jak lze optimalizovat řetězcových objektů.</span><span class="sxs-lookup"><span data-stu-id="873c5-344">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="873c5-345">Pokud chcete zobrazit řetězce, které jsou v rozmezí od 150 až 200 bajtů, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-345">To see strings that are between 150 and 200 bytes, type the following:</span></span>  
  
     <span data-ttu-id="873c5-346">**! dumpheap-zadejte 150 - max -min System.String 200**</span><span class="sxs-lookup"><span data-stu-id="873c5-346">**!dumpheap -type System.String -min 150 -max 200**</span></span>  
  
     <span data-ttu-id="873c5-347">Příklad výsledků je následující.</span><span class="sxs-lookup"><span data-stu-id="873c5-347">An example of the results is as follows.</span></span>  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     <span data-ttu-id="873c5-348">Pomocí celé místo řetězec pro ID může být efektivnější.</span><span class="sxs-lookup"><span data-stu-id="873c5-348">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="873c5-349">Pokud do jednoho řetězce je opakováno tisíce časy, vezměte v úvahu interning řetězec.</span><span class="sxs-lookup"><span data-stu-id="873c5-349">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="873c5-350">Další informace o řetězce interning najdete v tématu referenční téma pro <xref:System.String.Intern%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="873c5-350">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a><span data-ttu-id="873c5-351">Chcete-li zjistit odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="873c5-351">To determine references to objects</span></span>  
  
-   <span data-ttu-id="873c5-352">V WinDbg s příponou ladicí program SOS načíst zadejte následující příkaz, který seznamu odkazů na objekty:</span><span class="sxs-lookup"><span data-stu-id="873c5-352">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>  
  
     <span data-ttu-id="873c5-353">**! gcroot**</span><span class="sxs-lookup"><span data-stu-id="873c5-353">**!gcroot**</span></span>  
  
     `-or-`  
  
-   <span data-ttu-id="873c5-354">Pokud chcete zjistit odkazy pro konkrétní objekt, patří adresu:</span><span class="sxs-lookup"><span data-stu-id="873c5-354">To determine the references for a specific object, include the address:</span></span>  
  
     <span data-ttu-id="873c5-355">**! gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="873c5-355">**!gcroot 1c37b2ac**</span></span>  
  
     <span data-ttu-id="873c5-356">Kořeny najít na zásobníky může být falešně pozitivních zjištění.</span><span class="sxs-lookup"><span data-stu-id="873c5-356">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="873c5-357">Další informace získáte pomocí příkazu `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="873c5-357">For more information, use the command `!help gcroot`.</span></span>  
  
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
  
     <span data-ttu-id="873c5-358">**Gcroot** příkaz může trvat dlouhou dobu na Dokončit.</span><span class="sxs-lookup"><span data-stu-id="873c5-358">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="873c5-359">Libovolný objekt, který není uvolněn systémem uvolňování paměti je objekt za provozu.</span><span class="sxs-lookup"><span data-stu-id="873c5-359">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="873c5-360">To znamená, že některé kořenová je přímo nebo nepřímo přidržte na objekt, takže **gcroot** by měla vrátit informace o cestě k objektu.</span><span class="sxs-lookup"><span data-stu-id="873c5-360">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="873c5-361">Měli byste zkontrolujte grafy vrátil a najdete v části Proč stále odkazují tyto objekty.</span><span class="sxs-lookup"><span data-stu-id="873c5-361">You should examine the graphs returned and see why these objects are still referenced.</span></span>  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="873c5-362">Chcete-li zjistit, zda byl spuštěn finalizační metody</span><span class="sxs-lookup"><span data-stu-id="873c5-362">To determine whether a finalizer has been run</span></span>  
  
-   <span data-ttu-id="873c5-363">Spusťte program test, který obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="873c5-363">Run a test program that contains the following code:</span></span>  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     <span data-ttu-id="873c5-364">Pokud test řeší problém, znamená to, zda má systém uvolňování nebyl opětovného získání objekty, protože finalizační metody pro tyto objekty měl bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="873c5-364">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="873c5-365"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metoda umožňuje finalizační metody k dokončení úkolů a opravy problému.</span><span class="sxs-lookup"><span data-stu-id="873c5-365">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="873c5-366">Chcete-li určit, jestli jsou objekty čekají na Dokončit.</span><span class="sxs-lookup"><span data-stu-id="873c5-366">To determine whether there are objects waiting to be finalized</span></span>  
  
1.  <span data-ttu-id="873c5-367">V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-367">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="873c5-368">**! finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="873c5-368">**!finalizequeue**</span></span>  
  
     <span data-ttu-id="873c5-369">Podívejte se na počet objektů, které jsou připravené pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="873c5-369">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="873c5-370">Pokud je číslo vysoké, musíte prozkoumat Proč nelze tyto finalizační metody průběhu vůbec nebo nelze průběh rychlý dostatečně.</span><span class="sxs-lookup"><span data-stu-id="873c5-370">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>  
  
2.  <span data-ttu-id="873c5-371">Chcete-li získat výstup vláken, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-371">To get an output of threads, type the following command:</span></span>  
  
     <span data-ttu-id="873c5-372">**vláken - speciální**</span><span class="sxs-lookup"><span data-stu-id="873c5-372">**threads -special**</span></span>  
  
     <span data-ttu-id="873c5-373">Tento příkaz poskytuje výstupu, jako následující.</span><span class="sxs-lookup"><span data-stu-id="873c5-373">This command provides output such as the following.</span></span>  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     <span data-ttu-id="873c5-374">Vlákno finalizační metodu Určuje, které finalizační metodu, pokud existuje, je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="873c5-374">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="873c5-375">Pokud vlákno finalizační metodu neběží žádné finalizační metody, čeká na událost můžete určit, aby jeho práci.</span><span class="sxs-lookup"><span data-stu-id="873c5-375">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="873c5-376">Ve většině případů se zobrazí finalizační metodu vlákno v tomto stavu protože spouští v THREAD_HIGHEST_PRIORITY a má spuštěn finalizační metody, pouze pokud existuje, velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="873c5-376">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="873c5-377">Chcete-li zjistit množství volného místa v spravovaná halda</span><span class="sxs-lookup"><span data-stu-id="873c5-377">To determine the amount of free space in the managed heap</span></span>  
  
-   <span data-ttu-id="873c5-378">V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-378">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="873c5-379">**! dumpheap-Free - zadejte stat**</span><span class="sxs-lookup"><span data-stu-id="873c5-379">**!dumpheap -type Free -stat**</span></span>  
  
     <span data-ttu-id="873c5-380">Tento příkaz zobrazí celková velikost všech volné objektů na spravované haldě, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="873c5-380">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   <span data-ttu-id="873c5-381">K určení volné místo v 0. generace, zadejte následující příkaz pro informace spotřeba paměti podle generace:</span><span class="sxs-lookup"><span data-stu-id="873c5-381">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>  
  
     <span data-ttu-id="873c5-382">**! eeheap – uvolňování paměti**</span><span class="sxs-lookup"><span data-stu-id="873c5-382">**!eeheap -gc**</span></span>  
  
     <span data-ttu-id="873c5-383">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="873c5-383">This command displays output similar to the following.</span></span> <span data-ttu-id="873c5-384">Poslední řádek ukazuje dočasné segmentu.</span><span class="sxs-lookup"><span data-stu-id="873c5-384">The last line shows the ephemeral segment.</span></span>  
  
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
  
-   <span data-ttu-id="873c5-385">Vypočítejte místo využité generace 0:</span><span class="sxs-lookup"><span data-stu-id="873c5-385">Calculate the space used by generation 0:</span></span>  
  
     <span data-ttu-id="873c5-386">**? 49e05d04 0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="873c5-386">**? 49e05d04-0x49521f8c**</span></span>  
  
     <span data-ttu-id="873c5-387">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="873c5-387">The result is as follows.</span></span> <span data-ttu-id="873c5-388">Generace 0 je přibližně 9 MB.</span><span class="sxs-lookup"><span data-stu-id="873c5-388">Generation 0 is approximately 9 MB.</span></span>  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   <span data-ttu-id="873c5-389">Tento příkaz vypíše volné místo v rozsahu 0. generace:</span><span class="sxs-lookup"><span data-stu-id="873c5-389">The following command dumps the free space within the generation 0 range:</span></span>  
  
     <span data-ttu-id="873c5-390">**! dumpheap-typu Free - stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="873c5-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>  
  
     <span data-ttu-id="873c5-391">Výsledek je následující.</span><span class="sxs-lookup"><span data-stu-id="873c5-391">The result is as follows.</span></span>  
  
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
  
     <span data-ttu-id="873c5-392">Výstup ukazuje, že část generace 0 halda používá 9 MB volného místa pro objekty a že má 7 MB volného místa.</span><span class="sxs-lookup"><span data-stu-id="873c5-392">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="873c5-393">Tato analysis zobrazuje v rozsahu, ke kterému generace 0 přispívá k fragmentace.</span><span class="sxs-lookup"><span data-stu-id="873c5-393">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="873c5-394">Toto množství používání haldy by měl odečtena od celkové jako příčinu fragmentace dlouhodobé objekty.</span><span class="sxs-lookup"><span data-stu-id="873c5-394">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="873c5-395">K určení počtu připojených objektů</span><span class="sxs-lookup"><span data-stu-id="873c5-395">To determine the number of pinned objects</span></span>  
  
-   <span data-ttu-id="873c5-396">V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="873c5-396">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>  
  
     <span data-ttu-id="873c5-397">**! gchandles**</span><span class="sxs-lookup"><span data-stu-id="873c5-397">**!gchandles**</span></span>  
  
     <span data-ttu-id="873c5-398">Statistické údaje zobrazené zahrnuje počet popisovačů definovaného, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="873c5-398">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="873c5-399">Určit dobu v kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-399">To determine the length of time in a garbage collection</span></span>  
  
-   <span data-ttu-id="873c5-400">Zkontrolujte `% Time in GC` čítače výkonu paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-400">Examine the `% Time in GC` memory performance counter.</span></span>  
  
     <span data-ttu-id="873c5-401">Hodnota se počítá pomocí vzorovému časovému intervalu.</span><span class="sxs-lookup"><span data-stu-id="873c5-401">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="873c5-402">Protože čítače jsou aktualizovány na konci každé uvolňování aktuální Ukázka bude mít stejnou hodnotu jako v předchozím příkladu, pokud žádné kolekce došlo k chybě během intervalu.</span><span class="sxs-lookup"><span data-stu-id="873c5-402">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>  
  
     <span data-ttu-id="873c5-403">Čas kolekci je dána vynásobením časový interval vzorku s procentuální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="873c5-403">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>  
  
     <span data-ttu-id="873c5-404">Následující data znázorňuje čtyři během intervalů vzorkování dvou sekund pro studie 8 sekundu.</span><span class="sxs-lookup"><span data-stu-id="873c5-404">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="873c5-405">`Gen0`, `Gen1`, A `Gen2` sloupcích se zobrazují počet kolekce, k nimž došlo během tohoto intervalu pro této generaci.</span><span class="sxs-lookup"><span data-stu-id="873c5-405">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     <span data-ttu-id="873c5-406">Tyto informace se nezobrazuje, pokud došlo k uvolnění paměti, ale můžete určit počet kolekce, k nimž došlo v časový interval.</span><span class="sxs-lookup"><span data-stu-id="873c5-406">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="873c5-407">Za předpokladu, že nejhorším případě, desetinu 0 uvolnění paměti generace dokončen na začátku druhé intervalu a jedenáctá 0 uvolnění paměti generace dokončení na konci páté intervalu.</span><span class="sxs-lookup"><span data-stu-id="873c5-407">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="873c5-408">Doba mezi koncem na desetinu a konec jedenáctá uvolňování je o 2 sekund a čítač výkonu zobrazuje 3 %, byl trvání jedenáctá 0. generace uvolňování (% 2 sekundy \* 3 = 60ms).</span><span class="sxs-lookup"><span data-stu-id="873c5-408">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>  
  
     <span data-ttu-id="873c5-409">V tomto příkladu jsou 5 tečky.</span><span class="sxs-lookup"><span data-stu-id="873c5-409">In this example, there are 5 periods.</span></span>  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     <span data-ttu-id="873c5-410">Druhé generace uvolňování 2 během třetí intervalu spuštění a dokončení v páté intervalu.</span><span class="sxs-lookup"><span data-stu-id="873c5-410">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="873c5-411">Za předpokladu, že nejhorším případě, byl poslední uvolnění paměti pro generování 0 kolekci, která dokončení na začátku druhé interval a generace 2 uvolňování dokončil na konci páté interval.</span><span class="sxs-lookup"><span data-stu-id="873c5-411">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="873c5-412">Doba mezi koncem uvolňování generace 0 a konec uvolňování generace 2 je proto 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="873c5-412">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="873c5-413">Protože `% Time in GC` čítač je 20 %, maximální množství času je generace 2 uvolňování paměti může provedených (4 sekundy \* 20 % = 800ms).</span><span class="sxs-lookup"><span data-stu-id="873c5-413">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>  
  
-   <span data-ttu-id="873c5-414">Alternativně můžete zjistit délku uvolnění paměti pomocí [události trasování událostí pro Windows kolekci paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)a analyzovat informace k určení doby trvání uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-414">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>  
  
     <span data-ttu-id="873c5-415">Například následující data zobrazují v sekvenci událostí, které došlo během nesouběžného uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-415">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>  
  
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
  
     <span data-ttu-id="873c5-416">Pozastavení spravované vlákno trvalo 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="873c5-416">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>  
  
     <span data-ttu-id="873c5-417">Skutečné uvolňování trvalo 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="873c5-417">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>  
  
     <span data-ttu-id="873c5-418">Obnovení spravovaných vláknech trvalo 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="873c5-418">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>  
  
     <span data-ttu-id="873c5-419">Následující výstup představuje příklad kolekce paměti na pozadí a obsahuje proces, vlákna a pole událostí.</span><span class="sxs-lookup"><span data-stu-id="873c5-419">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="873c5-420">(Všechna data budou zobrazeny.)</span><span class="sxs-lookup"><span data-stu-id="873c5-420">(Not all data is shown.)</span></span>  
  
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
  
     <span data-ttu-id="873c5-421">`GCStart_V1` Událost v 42504816 označuje, že to je uvolňování paměti na pozadí, protože je poslední pole `1`.</span><span class="sxs-lookup"><span data-stu-id="873c5-421">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="873c5-422">To se stane uvolňování ne.</span><span class="sxs-lookup"><span data-stu-id="873c5-422">This becomes garbage collection No.</span></span> <span data-ttu-id="873c5-423">102019.</span><span class="sxs-lookup"><span data-stu-id="873c5-423">102019.</span></span>  
  
     <span data-ttu-id="873c5-424">`GCStart` Události dojde, protože je potřeba uvolnění dočasné paměti před zahájením uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="873c5-424">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="873c5-425">To se stane uvolňování ne.</span><span class="sxs-lookup"><span data-stu-id="873c5-425">This becomes garbage collection No.</span></span> <span data-ttu-id="873c5-426">102020.</span><span class="sxs-lookup"><span data-stu-id="873c5-426">102020.</span></span>  
  
     <span data-ttu-id="873c5-427">Při uvolňování 42514170, číslo.</span><span class="sxs-lookup"><span data-stu-id="873c5-427">At 42514170, garbage collection No.</span></span> <span data-ttu-id="873c5-428">102020 dokončení.</span><span class="sxs-lookup"><span data-stu-id="873c5-428">102020 finishes.</span></span> <span data-ttu-id="873c5-429">V tomto okamžiku se restartují spravovaných vláknech.</span><span class="sxs-lookup"><span data-stu-id="873c5-429">The managed threads are restarted at this point.</span></span> <span data-ttu-id="873c5-430">To uděláte ve vlákně 4372, která spustí této kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="873c5-430">This is completed on thread 4372, which triggered this background garbage collection.</span></span>  
  
     <span data-ttu-id="873c5-431">Ve vlákně 4744 dojde k pozastavení.</span><span class="sxs-lookup"><span data-stu-id="873c5-431">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="873c5-432">Toto je pouze čas, kdy má uvolňování paměti na pozadí na pozastavení spravovaných vláknech.</span><span class="sxs-lookup"><span data-stu-id="873c5-432">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="873c5-433">Tato doba trvání je přibližně 99ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="873c5-433">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>  
  
     <span data-ttu-id="873c5-434">`GCEnd` Je událost pro uvolňování paměti na pozadí na 89931423.</span><span class="sxs-lookup"><span data-stu-id="873c5-434">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="873c5-435">To znamená, že uvolňování paměti na pozadí trvala o 47seconds ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="873c5-435">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>  
  
     <span data-ttu-id="873c5-436">Při spravovaných vláknech, uvidíte libovolný počet kolekcí dočasné paměti, ke kterým dochází.</span><span class="sxs-lookup"><span data-stu-id="873c5-436">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="873c5-437">Chcete-li zjistit, co aktivaci kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-437">To determine what triggered a garbage collection</span></span>  
  
-   <span data-ttu-id="873c5-438">V ladicím programu WinDbg nebo Visual Studio s příponou ladicí program SOS načíst zadejte následující příkaz zobrazíte všechna vlákna s jejich zásobníky volání:</span><span class="sxs-lookup"><span data-stu-id="873c5-438">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>  
  
     <span data-ttu-id="873c5-439">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="873c5-439">**~\*kb**</span></span>  
  
     <span data-ttu-id="873c5-440">Tento příkaz zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="873c5-440">This command displays output similar to the following.</span></span>  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     <span data-ttu-id="873c5-441">Pokud kolekce paměti bylo způsobeno nedostatečnou pamětí oznámení z operačního systému, zásobníku volání je podobné, s tím rozdílem, že vlákno se vlákno finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="873c5-441">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="873c5-442">Vlákno finalizační metodu získá oznámení o asynchronní nedostatek paměti a indukuje uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="873c5-442">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>  
  
     <span data-ttu-id="873c5-443">Pokud kolekce paměti bylo způsobeno přidělení paměti, zobrazí se následující zásobník:</span><span class="sxs-lookup"><span data-stu-id="873c5-443">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>  
  
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
  
     <span data-ttu-id="873c5-444">Pomocné rutiny za běhu (`JIT_New*`) nakonec volá `GCHeap::GarbageCollectGeneration`.</span><span class="sxs-lookup"><span data-stu-id="873c5-444">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="873c5-445">Pokud zjistíte, že generace 2 kolekce jsou způsobeny přidělení, musíte určit objektů, které byly shromážděny sadou uvolňování 2. generace a jak se vyhnout je.</span><span class="sxs-lookup"><span data-stu-id="873c5-445">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="873c5-446">To znamená, že budete chtít určení rozdílu mezi začátku a konci generace 2 uvolňování paměti a objekty, které způsobilo 2. generace kolekce.</span><span class="sxs-lookup"><span data-stu-id="873c5-446">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>  
  
     <span data-ttu-id="873c5-447">Například zadejte následující příkaz v ladicím programu zobrazíte začátek 2. generace kolekce:</span><span class="sxs-lookup"><span data-stu-id="873c5-447">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>  
  
     <span data-ttu-id="873c5-448">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="873c5-448">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="873c5-449">Příklad výstupu (zkrácený komentář zobrazit objekty, které používají nejvíce místa na):</span><span class="sxs-lookup"><span data-stu-id="873c5-449">Example output (abridged to show the objects that use the most space):</span></span>  
  
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
  
     <span data-ttu-id="873c5-450">Zopakujte příkaz na konci generace 2:</span><span class="sxs-lookup"><span data-stu-id="873c5-450">Repeat the command at the end of generation 2:</span></span>  
  
     <span data-ttu-id="873c5-451">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="873c5-451">**!dumpheap –stat**</span></span>  
  
     <span data-ttu-id="873c5-452">Příklad výstupu (zkrácený komentář zobrazit objekty, které používají nejvíce místa na):</span><span class="sxs-lookup"><span data-stu-id="873c5-452">Example output (abridged to show the objects that use the most space):</span></span>  
  
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
  
     <span data-ttu-id="873c5-453">`double[]` Objekty smazán od konce výstup, což znamená, že byly shromážděny.</span><span class="sxs-lookup"><span data-stu-id="873c5-453">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="873c5-454">Tyto objekty účtu pro přibližně 70 MB.</span><span class="sxs-lookup"><span data-stu-id="873c5-454">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="873c5-455">Zbývající objekty mnohem nezměnila.</span><span class="sxs-lookup"><span data-stu-id="873c5-455">The remaining objects did not change much.</span></span> <span data-ttu-id="873c5-456">Proto tyto `double[]` objekty byly z důvodu, proč tento 2. generace uvolňování paměti došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="873c5-456">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="873c5-457">Dalším krokem je určit, proč `double[]` objekty jsou existuje a proč se ukončilo činnost.</span><span class="sxs-lookup"><span data-stu-id="873c5-457">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="873c5-458">Můžete požádat kód vývojáře, kde tyto objekty pochází, nebo můžete použít **gcroot** příkaz.</span><span class="sxs-lookup"><span data-stu-id="873c5-458">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="873c5-459">Chcete-li zjistit, zda vysoké využití procesoru je způsobena uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-459">To determine whether high CPU usage is caused by garbage collection</span></span>  
  
-   <span data-ttu-id="873c5-460">Korelovat `% Time in GC` hodnota čítače výkonu paměti s doba zpracování.</span><span class="sxs-lookup"><span data-stu-id="873c5-460">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>  
  
     <span data-ttu-id="873c5-461">Pokud `% Time in GC` hodnota špičky ve stejnou dobu jako doba zpracování, uvolňování paměti je příčinou vysoké využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="873c5-461">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="873c5-462">Profil aplikace místo, kde dochází k vysoké využití, jinak hodnota</span><span class="sxs-lookup"><span data-stu-id="873c5-462">Otherwise, profile the application to find where the high usage is occurring.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873c5-463">Viz také</span><span class="sxs-lookup"><span data-stu-id="873c5-463">See Also</span></span>  
 [<span data-ttu-id="873c5-464">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="873c5-464">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
