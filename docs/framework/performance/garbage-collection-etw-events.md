---
title: "Události Trasování událostí pro Windows kolekci paměti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06fc335e4b8011afd92e698b20e4b84572b153c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="6e6b5-102">Události Trasování událostí pro Windows kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="6e6b5-102">Garbage Collection ETW Events</span></span>
<span data-ttu-id="6e6b5-103"><a name="top"></a>Tyto události shromažďovat informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-103"><a name="top"></a> These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="6e6b5-104">Mohou pomoci v diagnostice a ladění, včetně určení, jak často uvolňování byla provedena, kolik paměti byl uvolněn při uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="6e6b5-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="6e6b5-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="6e6b5-106">GCStart_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="6e6b5-107">GCEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="6e6b5-108">GCHeapStats_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="6e6b5-109">GCCreateSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="6e6b5-110">GCFreeSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="6e6b5-111">GCRestartEEBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="6e6b5-112">GCRestartEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="6e6b5-113">GCSuspendEE_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="6e6b5-114">GCSuspendEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="6e6b5-115">GCAllocationTick_V2 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="6e6b5-116">GCFinalizersBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="6e6b5-117">GCFinalizersEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="6e6b5-118">GCCreateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="6e6b5-119">GCTerminateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="6e6b5-120">GCStart_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-121">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="6e6b5-122">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6e6b5-123">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-123">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-124">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-125">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-126">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-127">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-128">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-128">Event</span></span>|<span data-ttu-id="6e6b5-129">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-129">Event ID</span></span>|<span data-ttu-id="6e6b5-130">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="6e6b5-131">1</span><span class="sxs-lookup"><span data-stu-id="6e6b5-131">1</span></span>|<span data-ttu-id="6e6b5-132">Kolekce paměti bylo zahájeno.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="6e6b5-133">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-134">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-134">Field name</span></span>|<span data-ttu-id="6e6b5-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-135">Data type</span></span>|<span data-ttu-id="6e6b5-136">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-137">Počet</span><span class="sxs-lookup"><span data-stu-id="6e6b5-137">Count</span></span>|<span data-ttu-id="6e6b5-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-138">win:UInt32</span></span>|<span data-ttu-id="6e6b5-139">*n* Tý uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="6e6b5-140">Hloubka</span><span class="sxs-lookup"><span data-stu-id="6e6b5-140">Depth</span></span>|<span data-ttu-id="6e6b5-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-141">win:UInt32</span></span>|<span data-ttu-id="6e6b5-142">Generování, jež jsou shromažďována.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="6e6b5-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="6e6b5-143">Reason</span></span>|<span data-ttu-id="6e6b5-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-144">win:UInt32</span></span>|<span data-ttu-id="6e6b5-145">Proč byla aktivována uvolnění paměti:</span><span class="sxs-lookup"><span data-stu-id="6e6b5-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="6e6b5-146">0x0 - přidělení haldy malé objektu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="6e6b5-147">0x1 - vyvolané.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="6e6b5-148">0x2 - nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="6e6b5-149">0x3 - prázdný.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="6e6b5-150">0x4 - přidělení haldy velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="6e6b5-151">0x5 – volné místo (pro malé objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="6e6b5-152">0x6 – volné místo (pro velkého objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="6e6b5-153">0x7 - vyvolané ale nejsou vynucené jako blokování.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="6e6b5-154">Typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-154">Type</span></span>|<span data-ttu-id="6e6b5-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-155">win:UInt32</span></span>|<span data-ttu-id="6e6b5-156">došlo k blokování uvolňování 0x0 - mimo kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="6e6b5-157">0x1 – kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="6e6b5-158">0x2 – uvolňování paměti blokování došlo k chybě během kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="6e6b5-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-159">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-160">win:UInt16</span></span>|<span data-ttu-id="6e6b5-161">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6e6b5-162">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="6e6b5-163">GCEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-164">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-165">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-165">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-166">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-167">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-168">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-169">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-170">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-170">Event</span></span>|<span data-ttu-id="6e6b5-171">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-171">Event ID</span></span>|<span data-ttu-id="6e6b5-172">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="6e6b5-173">2</span><span class="sxs-lookup"><span data-stu-id="6e6b5-173">2</span></span>|<span data-ttu-id="6e6b5-174">Kolekce paměti byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="6e6b5-175">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-176">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-176">Field name</span></span>|<span data-ttu-id="6e6b5-177">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-177">Data type</span></span>|<span data-ttu-id="6e6b5-178">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-179">Počet</span><span class="sxs-lookup"><span data-stu-id="6e6b5-179">Count</span></span>|<span data-ttu-id="6e6b5-180">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-180">win:UInt32</span></span>|<span data-ttu-id="6e6b5-181">*n* Tý uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="6e6b5-182">Hloubka</span><span class="sxs-lookup"><span data-stu-id="6e6b5-182">Depth</span></span>|<span data-ttu-id="6e6b5-183">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-183">win:UInt32</span></span>|<span data-ttu-id="6e6b5-184">Generování, která nebyla shromážděna.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="6e6b5-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-185">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-186">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-186">win:UInt16</span></span>|<span data-ttu-id="6e6b5-187">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6e6b5-188">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="6e6b5-189">GCHeapStats_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-190">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-191">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-191">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-192">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-193">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-194">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-195">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-196">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-196">Event</span></span>|<span data-ttu-id="6e6b5-197">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-197">Event ID</span></span>|<span data-ttu-id="6e6b5-198">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="6e6b5-199">4</span><span class="sxs-lookup"><span data-stu-id="6e6b5-199">4</span></span>|<span data-ttu-id="6e6b5-200">Zobrazuje statistiku haldy na konci každé uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="6e6b5-201">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-202">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-202">Field name</span></span>|<span data-ttu-id="6e6b5-203">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-203">Data type</span></span>|<span data-ttu-id="6e6b5-204">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="6e6b5-205">GenerationSize0</span></span>|<span data-ttu-id="6e6b5-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-206">win:UInt64</span></span>|<span data-ttu-id="6e6b5-207">Velikost v bajtech, generace 0 paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="6e6b5-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="6e6b5-208">TotalPromotedSize0</span></span>|<span data-ttu-id="6e6b5-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-209">win:UInt64</span></span>|<span data-ttu-id="6e6b5-210">Počet bajtů, které jsou povýší z generace 0 na 1. generace.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="6e6b5-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="6e6b5-211">GenerationSize1</span></span>|<span data-ttu-id="6e6b5-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-212">win:UInt64</span></span>|<span data-ttu-id="6e6b5-213">Velikost v bajtech paměti generace 1.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="6e6b5-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="6e6b5-214">TotalPromotedSize1</span></span>|<span data-ttu-id="6e6b5-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-215">win:UInt64</span></span>|<span data-ttu-id="6e6b5-216">Počet bajtů, které jsou povýší z generace 1 na 2. generace.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="6e6b5-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="6e6b5-217">GenerationSize2</span></span>|<span data-ttu-id="6e6b5-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-218">win:UInt64</span></span>|<span data-ttu-id="6e6b5-219">Velikost v bajtech, paměti, 2. generace.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="6e6b5-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="6e6b5-220">TotalPromotedSize2</span></span>|<span data-ttu-id="6e6b5-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-221">win:UInt64</span></span>|<span data-ttu-id="6e6b5-222">Počet bajtů, které přežil v generace 2 po poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="6e6b5-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="6e6b5-223">GenerationSize3</span></span>|<span data-ttu-id="6e6b5-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-224">win:UInt64</span></span>|<span data-ttu-id="6e6b5-225">Velikost v bajtech haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="6e6b5-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="6e6b5-226">TotalPromotedSize3</span></span>|<span data-ttu-id="6e6b5-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-227">win:UInt64</span></span>|<span data-ttu-id="6e6b5-228">Počet bajtů, které přežil v haldě velkého objektu po poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="6e6b5-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="6e6b5-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="6e6b5-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-230">win:UInt64</span></span>|<span data-ttu-id="6e6b5-231">Celková velikost v bajtech objektů, které jsou připravené pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="6e6b5-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="6e6b5-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="6e6b5-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-233">win:UInt64</span></span>|<span data-ttu-id="6e6b5-234">Počet objektů, které jsou připravené pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="6e6b5-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="6e6b5-235">PinnedObjectCount</span></span>|<span data-ttu-id="6e6b5-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-236">win:UInt32</span></span>|<span data-ttu-id="6e6b5-237">Počet připojených objektů (nepřesunutelnou).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="6e6b5-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="6e6b5-238">SinkBlockCount</span></span>|<span data-ttu-id="6e6b5-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-239">win:UInt32</span></span>|<span data-ttu-id="6e6b5-240">Počet bloků synchronizace používá.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="6e6b5-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="6e6b5-241">GCHandleCount</span></span>|<span data-ttu-id="6e6b5-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-242">win:UInt32</span></span>|<span data-ttu-id="6e6b5-243">Počet uvolňování zpracovává používán.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="6e6b5-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-244">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-245">win:UInt16</span></span>|<span data-ttu-id="6e6b5-246">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6e6b5-247">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="6e6b5-248">GCCreateSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-249">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-250">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-250">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-251">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-252">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-253">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-254">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-255">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-255">Event</span></span>|<span data-ttu-id="6e6b5-256">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-256">Event ID</span></span>|<span data-ttu-id="6e6b5-257">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="6e6b5-258">5</span><span class="sxs-lookup"><span data-stu-id="6e6b5-258">5</span></span>|<span data-ttu-id="6e6b5-259">Byl vytvořen nový segment kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="6e6b5-260">Kromě toho pokud je povoleno sledování na procesu, který je již spuštěn, tato událost je aktivována pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="6e6b5-261">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-262">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-262">Field name</span></span>|<span data-ttu-id="6e6b5-263">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-263">Data type</span></span>|<span data-ttu-id="6e6b5-264">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-265">Adresa</span><span class="sxs-lookup"><span data-stu-id="6e6b5-265">Address</span></span>|<span data-ttu-id="6e6b5-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-266">win:UInt64</span></span>|<span data-ttu-id="6e6b5-267">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-267">The address of the segment.</span></span>|  
|<span data-ttu-id="6e6b5-268">Velikost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-268">Size</span></span>|<span data-ttu-id="6e6b5-269">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-269">win:UInt64</span></span>|<span data-ttu-id="6e6b5-270">Velikost segmentu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-270">The size of the segment.</span></span>|  
|<span data-ttu-id="6e6b5-271">Typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-271">Type</span></span>|<span data-ttu-id="6e6b5-272">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-272">win:UInt32</span></span>|<span data-ttu-id="6e6b5-273">0x0 - malé objekty.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="6e6b5-274">0x1 - velké objekty.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="6e6b5-275">0x2 - haldy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="6e6b5-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-276">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-277">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-277">win:UInt16</span></span>|<span data-ttu-id="6e6b5-278">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="6e6b5-279">Všimněte si, že velikost segmentů přidělené modulem garbage collector závisí na implementaci a mohou podléhat změnám kdykoli, včetně v pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="6e6b5-280">Vaše aplikace by nikdy Zkontrolujte předpoklady o nebo závisí na velikosti určitý segment, ani pokusit nakonfigurovat množství paměti k dispozici pro přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="6e6b5-281">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="6e6b5-282">GCFreeSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-283">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-284">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-284">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-285">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-286">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-287">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-288">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-289">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-289">Event</span></span>|<span data-ttu-id="6e6b5-290">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-290">Event ID</span></span>|<span data-ttu-id="6e6b5-291">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="6e6b5-292">6</span><span class="sxs-lookup"><span data-stu-id="6e6b5-292">6</span></span>|<span data-ttu-id="6e6b5-293">Byla vydána segment kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="6e6b5-294">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-295">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-295">Field name</span></span>|<span data-ttu-id="6e6b5-296">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-296">Data type</span></span>|<span data-ttu-id="6e6b5-297">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-298">Adresa</span><span class="sxs-lookup"><span data-stu-id="6e6b5-298">Address</span></span>|<span data-ttu-id="6e6b5-299">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-299">win:UInt64</span></span>|<span data-ttu-id="6e6b5-300">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-300">The address of the segment.</span></span>|  
|<span data-ttu-id="6e6b5-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-301">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-302">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-302">win:UInt16</span></span>|<span data-ttu-id="6e6b5-303">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6e6b5-304">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="6e6b5-305">GCRestartEEBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-306">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-307">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-307">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-308">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-309">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-310">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-311">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-312">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-312">Event</span></span>|<span data-ttu-id="6e6b5-313">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-313">Event ID</span></span>|<span data-ttu-id="6e6b5-314">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="6e6b5-315">7</span><span class="sxs-lookup"><span data-stu-id="6e6b5-315">7</span></span>|<span data-ttu-id="6e6b5-316">Obnovení z běžných pozastavení runtime jazyka byl zahájen.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="6e6b5-317">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-317">No event data.</span></span>  
  
 [<span data-ttu-id="6e6b5-318">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="6e6b5-319">GCRestartEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-320">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-321">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-321">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-322">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-323">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-324">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-325">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-326">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-326">Event</span></span>|<span data-ttu-id="6e6b5-327">Id události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-327">Event Id</span></span>|<span data-ttu-id="6e6b5-328">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="6e6b5-329">3</span><span class="sxs-lookup"><span data-stu-id="6e6b5-329">3</span></span>|<span data-ttu-id="6e6b5-330">Obnovení z běžných pozastavení runtime jazyka byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="6e6b5-331">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-331">No event data.</span></span>  
  
 [<span data-ttu-id="6e6b5-332">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="6e6b5-333">GCSuspendEE_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-334">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-335">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-335">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-336">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-337">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-338">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-339">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-340">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-340">Event</span></span>|<span data-ttu-id="6e6b5-341">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-341">Event ID</span></span>|<span data-ttu-id="6e6b5-342">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="6e6b5-343">9</span><span class="sxs-lookup"><span data-stu-id="6e6b5-343">9</span></span>|<span data-ttu-id="6e6b5-344">Začátek pozastavení provádění modul pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="6e6b5-345">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-346">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-346">Field name</span></span>|<span data-ttu-id="6e6b5-347">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-347">Data type</span></span>|<span data-ttu-id="6e6b5-348">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-349">Důvod</span><span class="sxs-lookup"><span data-stu-id="6e6b5-349">Reason</span></span>|<span data-ttu-id="6e6b5-350">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-350">win:UInt16</span></span>|<span data-ttu-id="6e6b5-351">0x0 - Další.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="6e6b5-352">0x1 – uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="6e6b5-353">0x2 - ukončení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="6e6b5-354">0x3 - pitching kódu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="6e6b5-355">0x4 - vypnutí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="6e6b5-356">0x5 - ladicí program.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="6e6b5-357">0x6 - přípravy pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="6e6b5-358">Počet</span><span class="sxs-lookup"><span data-stu-id="6e6b5-358">Count</span></span>|<span data-ttu-id="6e6b5-359">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-359">win:UInt32</span></span>|<span data-ttu-id="6e6b5-360">Počet uvolňování paměti v době.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-360">The GC count at the time.</span></span> <span data-ttu-id="6e6b5-361">Obvykle zobrazí se následných událostí GC spuštění po této a jeho počet by tento počet + 1 jsme zvýšit GC index během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="6e6b5-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-362">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-363">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-363">win:UInt16</span></span>|<span data-ttu-id="6e6b5-364">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6e6b5-365">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="6e6b5-366">GCSuspendEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-367">V následující tabulce jsou uvedeny – klíčové slovo a úroveň:</span><span class="sxs-lookup"><span data-stu-id="6e6b5-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="6e6b5-368">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-368">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-369">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-370">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-371">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-372">V následující tabulce jsou uvedeny informace o události:</span><span class="sxs-lookup"><span data-stu-id="6e6b5-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="6e6b5-373">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-373">Event</span></span>|<span data-ttu-id="6e6b5-374">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-374">Event ID</span></span>|<span data-ttu-id="6e6b5-375">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="6e6b5-376">8</span><span class="sxs-lookup"><span data-stu-id="6e6b5-376">8</span></span>|<span data-ttu-id="6e6b5-377">Konec pozastavení provádění modul pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="6e6b5-378">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-378">No event data.</span></span>  
  
 [<span data-ttu-id="6e6b5-379">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="6e6b5-380">GCAllocationTick_V2 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="6e6b5-381">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-382">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-382">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-383">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-384">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-385">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-386">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-387">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-387">Event</span></span>|<span data-ttu-id="6e6b5-388">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-388">Event ID</span></span>|<span data-ttu-id="6e6b5-389">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="6e6b5-390">10</span><span class="sxs-lookup"><span data-stu-id="6e6b5-390">10</span></span>|<span data-ttu-id="6e6b5-391">Pokaždé, když je přidělen přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="6e6b5-392">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-393">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-393">Field name</span></span>|<span data-ttu-id="6e6b5-394">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-394">Data type</span></span>|<span data-ttu-id="6e6b5-395">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="6e6b5-396">AllocationAmount</span></span>|<span data-ttu-id="6e6b5-397">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-397">win:UInt32</span></span>|<span data-ttu-id="6e6b5-398">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-398">The allocation size, in bytes.</span></span> <span data-ttu-id="6e6b5-399">Tato hodnota je přesný pro přidělení, které jsou menší než délka ULONG (4,294,967,295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="6e6b5-400">Pokud přidělení je vyšší, toto pole obsahuje zkrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="6e6b5-401">Použití `AllocationAmount64` pro velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="6e6b5-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="6e6b5-402">AllocationKind</span></span>|<span data-ttu-id="6e6b5-403">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-403">win:UInt32</span></span>|<span data-ttu-id="6e6b5-404">0x0 - malé objekt přidělení (přidělení je v malých objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="6e6b5-405">0x1 - přidělení velkého objektu (přidělení je v haldě rozsáhlý objekt).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="6e6b5-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-406">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-407">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-407">win:UInt16</span></span>|<span data-ttu-id="6e6b5-408">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="6e6b5-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-409">AllocationAmount64</span></span>|<span data-ttu-id="6e6b5-410">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6e6b5-410">win:UInt64</span></span>|<span data-ttu-id="6e6b5-411">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-411">The allocation size, in bytes.</span></span> <span data-ttu-id="6e6b5-412">Tato hodnota je přesný pro velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="6e6b5-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="6e6b5-413">TypeId</span></span>|<span data-ttu-id="6e6b5-414">Win: ukazatele</span><span class="sxs-lookup"><span data-stu-id="6e6b5-414">win:Pointer</span></span>|<span data-ttu-id="6e6b5-415">Adresa MethodTable.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-415">The address of the MethodTable.</span></span> <span data-ttu-id="6e6b5-416">Pokud existuje několik typů objektů, které byly přiděleny během této události, to je adresa MethodTable, která odpovídá na poslední objekt přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="6e6b5-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="6e6b5-417">TypeName</span></span>|<span data-ttu-id="6e6b5-418">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6e6b5-418">win:UnicodeString</span></span>|<span data-ttu-id="6e6b5-419">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-419">The name of the type that was allocated.</span></span> <span data-ttu-id="6e6b5-420">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ objektu poslední přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).</span><span class="sxs-lookup"><span data-stu-id="6e6b5-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="6e6b5-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="6e6b5-421">HeapIndex</span></span>|<span data-ttu-id="6e6b5-422">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-422">win:UInt32</span></span>|<span data-ttu-id="6e6b5-423">Halda, kde byl přidělen objektu.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-423">The heap where the object was allocated.</span></span> <span data-ttu-id="6e6b5-424">Tato hodnota je 0 (nula) při spuštění s uvolňování paměti pracovních stanic.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="6e6b5-425">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="6e6b5-426">GCFinalizersBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-427">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-428">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-428">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-429">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-430">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-431">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-432">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-433">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-433">Event</span></span>|<span data-ttu-id="6e6b5-434">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-434">Event ID</span></span>|<span data-ttu-id="6e6b5-435">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="6e6b5-436">14</span><span class="sxs-lookup"><span data-stu-id="6e6b5-436">14</span></span>|<span data-ttu-id="6e6b5-437">Počáteční spouštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="6e6b5-438">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-438">No event data.</span></span>  
  
 [<span data-ttu-id="6e6b5-439">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="6e6b5-440">GCFinalizersEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-441">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-442">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-442">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-443">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-444">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-445">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-446">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-447">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-447">Event</span></span>|<span data-ttu-id="6e6b5-448">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-448">Event ID</span></span>|<span data-ttu-id="6e6b5-449">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="6e6b5-450">13</span><span class="sxs-lookup"><span data-stu-id="6e6b5-450">13</span></span>|<span data-ttu-id="6e6b5-451">Konec systémem finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="6e6b5-452">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6e6b5-453">Název pole</span><span class="sxs-lookup"><span data-stu-id="6e6b5-453">Field name</span></span>|<span data-ttu-id="6e6b5-454">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6e6b5-454">Data type</span></span>|<span data-ttu-id="6e6b5-455">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b5-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e6b5-456">Počet</span><span class="sxs-lookup"><span data-stu-id="6e6b5-456">Count</span></span>|<span data-ttu-id="6e6b5-457">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6e6b5-457">win:UInt32</span></span>|<span data-ttu-id="6e6b5-458">Počet finalizační metody, které byly spuštěné.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="6e6b5-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e6b5-459">ClrInstanceID</span></span>|<span data-ttu-id="6e6b5-460">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6e6b5-460">win:UInt16</span></span>|<span data-ttu-id="6e6b5-461">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6e6b5-462">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="6e6b5-463">GCCreateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-464">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-465">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-465">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-466">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-467">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-468">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-468">Informational (4)</span></span>|  
|<span data-ttu-id="6e6b5-469">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="6e6b5-470">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-471">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-472">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-472">Event</span></span>|<span data-ttu-id="6e6b5-473">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-473">Event ID</span></span>|<span data-ttu-id="6e6b5-474">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="6e6b5-475">11</span><span class="sxs-lookup"><span data-stu-id="6e6b5-475">11</span></span>|<span data-ttu-id="6e6b5-476">Byl vytvořen souběžné uvolňování paměti kolekce přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="6e6b5-477">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-477">No event data.</span></span>  
  
 [<span data-ttu-id="6e6b5-478">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="6e6b5-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="6e6b5-479">GCTerminateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="6e6b5-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="6e6b5-480">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6e6b5-481">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-481">Keyword for raising the event</span></span>|<span data-ttu-id="6e6b5-482">úroveň</span><span class="sxs-lookup"><span data-stu-id="6e6b5-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e6b5-483">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="6e6b5-484">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-484">Informational (4)</span></span>|  
|<span data-ttu-id="6e6b5-485">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="6e6b5-486">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="6e6b5-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="6e6b5-487">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6e6b5-488">Událost</span><span class="sxs-lookup"><span data-stu-id="6e6b5-488">Event</span></span>|<span data-ttu-id="6e6b5-489">ID události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-489">Event ID</span></span>|<span data-ttu-id="6e6b5-490">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="6e6b5-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="6e6b5-491">12</span><span class="sxs-lookup"><span data-stu-id="6e6b5-491">12</span></span>|<span data-ttu-id="6e6b5-492">Souběžné uvolňování paměti kolekce vlákno byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="6e6b5-493">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="6e6b5-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6b5-494">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e6b5-494">See Also</span></span>  
 [<span data-ttu-id="6e6b5-495">CLR ETW – události</span><span class="sxs-lookup"><span data-stu-id="6e6b5-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
