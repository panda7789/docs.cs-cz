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
ms.workload: dotnet
ms.openlocfilehash: 133d48baa9613ea698b6d6a21f0dfe88a798859c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="24212-102">Události Trasování událostí pro Windows kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="24212-102">Garbage Collection ETW Events</span></span>
<a name="top"></a><span data-ttu-id="24212-103">Tyto události shromažďovat informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="24212-104">Mohou pomoci v diagnostice a ladění, včetně určení, jak často uvolňování byla provedena, kolik paměti byl uvolněn při uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="24212-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="24212-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="24212-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="24212-106">GCStart_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="24212-107">GCEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="24212-108">GCHeapStats_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="24212-109">GCCreateSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="24212-110">GCFreeSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="24212-111">GCRestartEEBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="24212-112">GCRestartEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="24212-113">GCSuspendEE_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="24212-114">GCSuspendEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="24212-115">GCAllocationTick_V2 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="24212-116">GCFinalizersBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="24212-117">GCFinalizersEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="24212-118">GCCreateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="24212-119">GCTerminateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="24212-120">GCStart_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="24212-121">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="24212-122">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="24212-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="24212-123">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-123">Keyword for raising the event</span></span>|<span data-ttu-id="24212-124">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-125">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-126">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-127">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-128">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-128">Event</span></span>|<span data-ttu-id="24212-129">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-129">Event ID</span></span>|<span data-ttu-id="24212-130">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="24212-131">1</span><span class="sxs-lookup"><span data-stu-id="24212-131">1</span></span>|<span data-ttu-id="24212-132">Kolekce paměti bylo zahájeno.</span><span class="sxs-lookup"><span data-stu-id="24212-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="24212-133">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-134">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-134">Field name</span></span>|<span data-ttu-id="24212-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-135">Data type</span></span>|<span data-ttu-id="24212-136">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-137">Počet</span><span class="sxs-lookup"><span data-stu-id="24212-137">Count</span></span>|<span data-ttu-id="24212-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-138">win:UInt32</span></span>|<span data-ttu-id="24212-139"> *n* Tý uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="24212-140">Hloubka</span><span class="sxs-lookup"><span data-stu-id="24212-140">Depth</span></span>|<span data-ttu-id="24212-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-141">win:UInt32</span></span>|<span data-ttu-id="24212-142">Generování, jež jsou shromažďována.</span><span class="sxs-lookup"><span data-stu-id="24212-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="24212-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="24212-143">Reason</span></span>|<span data-ttu-id="24212-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-144">win:UInt32</span></span>|<span data-ttu-id="24212-145">Proč byla aktivována uvolnění paměti:</span><span class="sxs-lookup"><span data-stu-id="24212-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="24212-146">0x0 - přidělení haldy malé objektu.</span><span class="sxs-lookup"><span data-stu-id="24212-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="24212-147">0x1 - vyvolané.</span><span class="sxs-lookup"><span data-stu-id="24212-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="24212-148">0x2 - nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="24212-149">0x3 - prázdný.</span><span class="sxs-lookup"><span data-stu-id="24212-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="24212-150">0x4 - přidělení haldy velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="24212-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="24212-151">0x5 – volné místo (pro malé objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="24212-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="24212-152">0x6 – volné místo (pro velkého objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="24212-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="24212-153">0x7 - vyvolané ale nejsou vynucené jako blokování.</span><span class="sxs-lookup"><span data-stu-id="24212-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="24212-154">Typ</span><span class="sxs-lookup"><span data-stu-id="24212-154">Type</span></span>|<span data-ttu-id="24212-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-155">win:UInt32</span></span>|<span data-ttu-id="24212-156">došlo k blokování uvolňování 0x0 - mimo kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="24212-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="24212-157">0x1 – kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="24212-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="24212-158">0x2 – uvolňování paměti blokování došlo k chybě během kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="24212-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="24212-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-159">ClrInstanceID</span></span>|<span data-ttu-id="24212-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-160">win:UInt16</span></span>|<span data-ttu-id="24212-161">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="24212-162">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="24212-163">GCEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="24212-164">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-165">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-165">Keyword for raising the event</span></span>|<span data-ttu-id="24212-166">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-167">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-168">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-169">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-170">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-170">Event</span></span>|<span data-ttu-id="24212-171">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-171">Event ID</span></span>|<span data-ttu-id="24212-172">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="24212-173">2</span><span class="sxs-lookup"><span data-stu-id="24212-173">2</span></span>|<span data-ttu-id="24212-174">Kolekce paměti byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="24212-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="24212-175">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-176">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-176">Field name</span></span>|<span data-ttu-id="24212-177">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-177">Data type</span></span>|<span data-ttu-id="24212-178">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-179">Počet</span><span class="sxs-lookup"><span data-stu-id="24212-179">Count</span></span>|<span data-ttu-id="24212-180">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-180">win:UInt32</span></span>|<span data-ttu-id="24212-181"> *n* Tý uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="24212-182">Hloubka</span><span class="sxs-lookup"><span data-stu-id="24212-182">Depth</span></span>|<span data-ttu-id="24212-183">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-183">win:UInt32</span></span>|<span data-ttu-id="24212-184">Generování, která nebyla shromážděna.</span><span class="sxs-lookup"><span data-stu-id="24212-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="24212-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-185">ClrInstanceID</span></span>|<span data-ttu-id="24212-186">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-186">win:UInt16</span></span>|<span data-ttu-id="24212-187">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="24212-188">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="24212-189">GCHeapStats_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="24212-190">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-191">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-191">Keyword for raising the event</span></span>|<span data-ttu-id="24212-192">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-193">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-194">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-195">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-196">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-196">Event</span></span>|<span data-ttu-id="24212-197">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-197">Event ID</span></span>|<span data-ttu-id="24212-198">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="24212-199">4</span><span class="sxs-lookup"><span data-stu-id="24212-199">4</span></span>|<span data-ttu-id="24212-200">Zobrazuje statistiku haldy na konci každé uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="24212-201">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-202">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-202">Field name</span></span>|<span data-ttu-id="24212-203">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-203">Data type</span></span>|<span data-ttu-id="24212-204">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="24212-205">GenerationSize0</span></span>|<span data-ttu-id="24212-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-206">win:UInt64</span></span>|<span data-ttu-id="24212-207">Velikost v bajtech, generace 0 paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="24212-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="24212-208">TotalPromotedSize0</span></span>|<span data-ttu-id="24212-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-209">win:UInt64</span></span>|<span data-ttu-id="24212-210">Počet bajtů, které jsou povýší z generace 0 na 1. generace.</span><span class="sxs-lookup"><span data-stu-id="24212-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="24212-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="24212-211">GenerationSize1</span></span>|<span data-ttu-id="24212-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-212">win:UInt64</span></span>|<span data-ttu-id="24212-213">Velikost v bajtech paměti generace 1.</span><span class="sxs-lookup"><span data-stu-id="24212-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="24212-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="24212-214">TotalPromotedSize1</span></span>|<span data-ttu-id="24212-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-215">win:UInt64</span></span>|<span data-ttu-id="24212-216">Počet bajtů, které jsou povýší z generace 1 na 2. generace.</span><span class="sxs-lookup"><span data-stu-id="24212-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="24212-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="24212-217">GenerationSize2</span></span>|<span data-ttu-id="24212-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-218">win:UInt64</span></span>|<span data-ttu-id="24212-219">Velikost v bajtech, paměti, 2. generace.</span><span class="sxs-lookup"><span data-stu-id="24212-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="24212-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="24212-220">TotalPromotedSize2</span></span>|<span data-ttu-id="24212-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-221">win:UInt64</span></span>|<span data-ttu-id="24212-222">Počet bajtů, které přežil v generace 2 po poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="24212-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="24212-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="24212-223">GenerationSize3</span></span>|<span data-ttu-id="24212-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-224">win:UInt64</span></span>|<span data-ttu-id="24212-225">Velikost v bajtech haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="24212-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="24212-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="24212-226">TotalPromotedSize3</span></span>|<span data-ttu-id="24212-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-227">win:UInt64</span></span>|<span data-ttu-id="24212-228">Počet bajtů, které přežil v haldě velkého objektu po poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="24212-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="24212-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="24212-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="24212-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-230">win:UInt64</span></span>|<span data-ttu-id="24212-231">Celková velikost v bajtech objektů, které jsou připravené pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="24212-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="24212-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="24212-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="24212-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-233">win:UInt64</span></span>|<span data-ttu-id="24212-234">Počet objektů, které jsou připravené pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="24212-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="24212-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="24212-235">PinnedObjectCount</span></span>|<span data-ttu-id="24212-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-236">win:UInt32</span></span>|<span data-ttu-id="24212-237">Počet připojených objektů (nepřesunutelnou).</span><span class="sxs-lookup"><span data-stu-id="24212-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="24212-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="24212-238">SinkBlockCount</span></span>|<span data-ttu-id="24212-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-239">win:UInt32</span></span>|<span data-ttu-id="24212-240">Počet bloků synchronizace používá.</span><span class="sxs-lookup"><span data-stu-id="24212-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="24212-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="24212-241">GCHandleCount</span></span>|<span data-ttu-id="24212-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-242">win:UInt32</span></span>|<span data-ttu-id="24212-243">Počet uvolňování zpracovává používán.</span><span class="sxs-lookup"><span data-stu-id="24212-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="24212-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-244">ClrInstanceID</span></span>|<span data-ttu-id="24212-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-245">win:UInt16</span></span>|<span data-ttu-id="24212-246">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="24212-247">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="24212-248">GCCreateSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="24212-249">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-250">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-250">Keyword for raising the event</span></span>|<span data-ttu-id="24212-251">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-252">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-253">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-254">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-255">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-255">Event</span></span>|<span data-ttu-id="24212-256">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-256">Event ID</span></span>|<span data-ttu-id="24212-257">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="24212-258">5</span><span class="sxs-lookup"><span data-stu-id="24212-258">5</span></span>|<span data-ttu-id="24212-259">Byl vytvořen nový segment kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="24212-260">Kromě toho pokud je povoleno sledování na procesu, který je již spuštěn, tato událost je aktivována pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="24212-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="24212-261">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-262">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-262">Field name</span></span>|<span data-ttu-id="24212-263">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-263">Data type</span></span>|<span data-ttu-id="24212-264">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-265">Adresa</span><span class="sxs-lookup"><span data-stu-id="24212-265">Address</span></span>|<span data-ttu-id="24212-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-266">win:UInt64</span></span>|<span data-ttu-id="24212-267">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="24212-267">The address of the segment.</span></span>|  
|<span data-ttu-id="24212-268">Velikost</span><span class="sxs-lookup"><span data-stu-id="24212-268">Size</span></span>|<span data-ttu-id="24212-269">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-269">win:UInt64</span></span>|<span data-ttu-id="24212-270">Velikost segmentu.</span><span class="sxs-lookup"><span data-stu-id="24212-270">The size of the segment.</span></span>|  
|<span data-ttu-id="24212-271">Typ</span><span class="sxs-lookup"><span data-stu-id="24212-271">Type</span></span>|<span data-ttu-id="24212-272">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-272">win:UInt32</span></span>|<span data-ttu-id="24212-273">0x0 - malé objekty.</span><span class="sxs-lookup"><span data-stu-id="24212-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="24212-274">0x1 - velké objekty.</span><span class="sxs-lookup"><span data-stu-id="24212-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="24212-275">0x2 - haldy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="24212-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="24212-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-276">ClrInstanceID</span></span>|<span data-ttu-id="24212-277">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-277">win:UInt16</span></span>|<span data-ttu-id="24212-278">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="24212-279">Všimněte si, že velikost segmentů přidělené modulem garbage collector závisí na implementaci a mohou podléhat změnám kdykoli, včetně v pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="24212-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="24212-280">Vaše aplikace by nikdy Zkontrolujte předpoklady o nebo závisí na velikosti určitý segment, ani pokusit nakonfigurovat množství paměti k dispozici pro přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="24212-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="24212-281">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="24212-282">GCFreeSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="24212-283">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-284">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-284">Keyword for raising the event</span></span>|<span data-ttu-id="24212-285">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-286">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-287">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-288">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-289">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-289">Event</span></span>|<span data-ttu-id="24212-290">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-290">Event ID</span></span>|<span data-ttu-id="24212-291">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="24212-292">6</span><span class="sxs-lookup"><span data-stu-id="24212-292">6</span></span>|<span data-ttu-id="24212-293">Byla vydána segment kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="24212-294">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-295">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-295">Field name</span></span>|<span data-ttu-id="24212-296">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-296">Data type</span></span>|<span data-ttu-id="24212-297">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-298">Adresa</span><span class="sxs-lookup"><span data-stu-id="24212-298">Address</span></span>|<span data-ttu-id="24212-299">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-299">win:UInt64</span></span>|<span data-ttu-id="24212-300">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="24212-300">The address of the segment.</span></span>|  
|<span data-ttu-id="24212-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-301">ClrInstanceID</span></span>|<span data-ttu-id="24212-302">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-302">win:UInt16</span></span>|<span data-ttu-id="24212-303">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="24212-304">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="24212-305">GCRestartEEBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="24212-306">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-307">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-307">Keyword for raising the event</span></span>|<span data-ttu-id="24212-308">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-309">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-310">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-311">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-312">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-312">Event</span></span>|<span data-ttu-id="24212-313">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-313">Event ID</span></span>|<span data-ttu-id="24212-314">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="24212-315">7</span><span class="sxs-lookup"><span data-stu-id="24212-315">7</span></span>|<span data-ttu-id="24212-316">Obnovení z běžných pozastavení runtime jazyka byl zahájen.</span><span class="sxs-lookup"><span data-stu-id="24212-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="24212-317">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="24212-317">No event data.</span></span>  
  
 [<span data-ttu-id="24212-318">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="24212-319">GCRestartEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="24212-320">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-321">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-321">Keyword for raising the event</span></span>|<span data-ttu-id="24212-322">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-323">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-324">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-325">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-326">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-326">Event</span></span>|<span data-ttu-id="24212-327">Id události</span><span class="sxs-lookup"><span data-stu-id="24212-327">Event Id</span></span>|<span data-ttu-id="24212-328">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="24212-329">3</span><span class="sxs-lookup"><span data-stu-id="24212-329">3</span></span>|<span data-ttu-id="24212-330">Obnovení z běžných pozastavení runtime jazyka byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="24212-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="24212-331">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="24212-331">No event data.</span></span>  
  
 [<span data-ttu-id="24212-332">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="24212-333">GCSuspendEE_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="24212-334">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-335">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-335">Keyword for raising the event</span></span>|<span data-ttu-id="24212-336">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-337">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-338">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-339">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-340">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-340">Event</span></span>|<span data-ttu-id="24212-341">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-341">Event ID</span></span>|<span data-ttu-id="24212-342">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="24212-343">9</span><span class="sxs-lookup"><span data-stu-id="24212-343">9</span></span>|<span data-ttu-id="24212-344">Začátek pozastavení provádění modul pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="24212-345">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-346">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-346">Field name</span></span>|<span data-ttu-id="24212-347">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-347">Data type</span></span>|<span data-ttu-id="24212-348">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-349">Důvod</span><span class="sxs-lookup"><span data-stu-id="24212-349">Reason</span></span>|<span data-ttu-id="24212-350">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-350">win:UInt16</span></span>|<span data-ttu-id="24212-351">0x0 - Další.</span><span class="sxs-lookup"><span data-stu-id="24212-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="24212-352">0x1 – uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="24212-353">0x2 - ukončení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="24212-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="24212-354">0x3 - pitching kódu.</span><span class="sxs-lookup"><span data-stu-id="24212-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="24212-355">0x4 - vypnutí.</span><span class="sxs-lookup"><span data-stu-id="24212-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="24212-356">0x5 - ladicí program.</span><span class="sxs-lookup"><span data-stu-id="24212-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="24212-357">0x6 - přípravy pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="24212-358">Počet</span><span class="sxs-lookup"><span data-stu-id="24212-358">Count</span></span>|<span data-ttu-id="24212-359">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-359">win:UInt32</span></span>|<span data-ttu-id="24212-360">Počet uvolňování paměti v době.</span><span class="sxs-lookup"><span data-stu-id="24212-360">The GC count at the time.</span></span> <span data-ttu-id="24212-361">Obvykle zobrazí se následných událostí GC spuštění po této a jeho počet by tento počet + 1 jsme zvýšit GC index během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="24212-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-362">ClrInstanceID</span></span>|<span data-ttu-id="24212-363">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-363">win:UInt16</span></span>|<span data-ttu-id="24212-364">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="24212-365">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="24212-366">GCSuspendEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="24212-367">V následující tabulce jsou uvedeny – klíčové slovo a úroveň:</span><span class="sxs-lookup"><span data-stu-id="24212-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="24212-368">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-368">Keyword for raising the event</span></span>|<span data-ttu-id="24212-369">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-370">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-371">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-372">V následující tabulce jsou uvedeny informace o události:</span><span class="sxs-lookup"><span data-stu-id="24212-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="24212-373">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-373">Event</span></span>|<span data-ttu-id="24212-374">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-374">Event ID</span></span>|<span data-ttu-id="24212-375">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="24212-376">8</span><span class="sxs-lookup"><span data-stu-id="24212-376">8</span></span>|<span data-ttu-id="24212-377">Konec pozastavení provádění modul pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="24212-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="24212-378">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="24212-378">No event data.</span></span>  
  
 [<span data-ttu-id="24212-379">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="24212-380">GCAllocationTick_V2 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="24212-381">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-382">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-382">Keyword for raising the event</span></span>|<span data-ttu-id="24212-383">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-384">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-385">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-386">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-387">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-387">Event</span></span>|<span data-ttu-id="24212-388">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-388">Event ID</span></span>|<span data-ttu-id="24212-389">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="24212-390">10</span><span class="sxs-lookup"><span data-stu-id="24212-390">10</span></span>|<span data-ttu-id="24212-391">Pokaždé, když je přidělen přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="24212-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="24212-392">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-393">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-393">Field name</span></span>|<span data-ttu-id="24212-394">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-394">Data type</span></span>|<span data-ttu-id="24212-395">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="24212-396">AllocationAmount</span></span>|<span data-ttu-id="24212-397">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-397">win:UInt32</span></span>|<span data-ttu-id="24212-398">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="24212-398">The allocation size, in bytes.</span></span> <span data-ttu-id="24212-399">Tato hodnota je přesný pro přidělení, které jsou menší než délka ULONG (4,294,967,295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="24212-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="24212-400">Pokud přidělení je vyšší, toto pole obsahuje zkrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="24212-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="24212-401">Použití `AllocationAmount64` pro velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="24212-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="24212-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="24212-402">AllocationKind</span></span>|<span data-ttu-id="24212-403">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-403">win:UInt32</span></span>|<span data-ttu-id="24212-404">0x0 - malé objekt přidělení (přidělení je v malých objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="24212-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="24212-405">0x1 - přidělení velkého objektu (přidělení je v haldě rozsáhlý objekt).</span><span class="sxs-lookup"><span data-stu-id="24212-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="24212-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-406">ClrInstanceID</span></span>|<span data-ttu-id="24212-407">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-407">win:UInt16</span></span>|<span data-ttu-id="24212-408">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="24212-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="24212-409">AllocationAmount64</span></span>|<span data-ttu-id="24212-410">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="24212-410">win:UInt64</span></span>|<span data-ttu-id="24212-411">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="24212-411">The allocation size, in bytes.</span></span> <span data-ttu-id="24212-412">Tato hodnota je přesný pro velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="24212-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="24212-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="24212-413">TypeId</span></span>|<span data-ttu-id="24212-414">Win: ukazatele</span><span class="sxs-lookup"><span data-stu-id="24212-414">win:Pointer</span></span>|<span data-ttu-id="24212-415">Adresa MethodTable.</span><span class="sxs-lookup"><span data-stu-id="24212-415">The address of the MethodTable.</span></span> <span data-ttu-id="24212-416">Pokud existuje několik typů objektů, které byly přiděleny během této události, to je adresa MethodTable, která odpovídá na poslední objekt přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).</span><span class="sxs-lookup"><span data-stu-id="24212-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="24212-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="24212-417">TypeName</span></span>|<span data-ttu-id="24212-418">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="24212-418">win:UnicodeString</span></span>|<span data-ttu-id="24212-419">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="24212-419">The name of the type that was allocated.</span></span> <span data-ttu-id="24212-420">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ objektu poslední přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).</span><span class="sxs-lookup"><span data-stu-id="24212-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="24212-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="24212-421">HeapIndex</span></span>|<span data-ttu-id="24212-422">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-422">win:UInt32</span></span>|<span data-ttu-id="24212-423">Halda, kde byl přidělen objektu.</span><span class="sxs-lookup"><span data-stu-id="24212-423">The heap where the object was allocated.</span></span> <span data-ttu-id="24212-424">Tato hodnota je 0 (nula) při spuštění s uvolňování paměti pracovních stanic.</span><span class="sxs-lookup"><span data-stu-id="24212-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="24212-425">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="24212-426">GCFinalizersBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="24212-427">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-428">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-428">Keyword for raising the event</span></span>|<span data-ttu-id="24212-429">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-430">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-431">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-432">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-433">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-433">Event</span></span>|<span data-ttu-id="24212-434">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-434">Event ID</span></span>|<span data-ttu-id="24212-435">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="24212-436">14</span><span class="sxs-lookup"><span data-stu-id="24212-436">14</span></span>|<span data-ttu-id="24212-437">Počáteční spouštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="24212-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="24212-438">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="24212-438">No event data.</span></span>  
  
 [<span data-ttu-id="24212-439">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="24212-440">GCFinalizersEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="24212-441">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-442">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-442">Keyword for raising the event</span></span>|<span data-ttu-id="24212-443">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-444">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-445">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-446">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-447">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-447">Event</span></span>|<span data-ttu-id="24212-448">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-448">Event ID</span></span>|<span data-ttu-id="24212-449">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="24212-450">13</span><span class="sxs-lookup"><span data-stu-id="24212-450">13</span></span>|<span data-ttu-id="24212-451">Konec systémem finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="24212-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="24212-452">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="24212-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="24212-453">Název pole</span><span class="sxs-lookup"><span data-stu-id="24212-453">Field name</span></span>|<span data-ttu-id="24212-454">Datový typ</span><span class="sxs-lookup"><span data-stu-id="24212-454">Data type</span></span>|<span data-ttu-id="24212-455">Popis</span><span class="sxs-lookup"><span data-stu-id="24212-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="24212-456">Počet</span><span class="sxs-lookup"><span data-stu-id="24212-456">Count</span></span>|<span data-ttu-id="24212-457">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="24212-457">win:UInt32</span></span>|<span data-ttu-id="24212-458">Počet finalizační metody, které byly spuštěné.</span><span class="sxs-lookup"><span data-stu-id="24212-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="24212-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="24212-459">ClrInstanceID</span></span>|<span data-ttu-id="24212-460">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="24212-460">win:UInt16</span></span>|<span data-ttu-id="24212-461">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="24212-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="24212-462">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="24212-463">GCCreateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="24212-464">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-465">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-465">Keyword for raising the event</span></span>|<span data-ttu-id="24212-466">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-467">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-468">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-468">Informational (4)</span></span>|  
|<span data-ttu-id="24212-469">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="24212-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="24212-470">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-471">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-472">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-472">Event</span></span>|<span data-ttu-id="24212-473">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-473">Event ID</span></span>|<span data-ttu-id="24212-474">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="24212-475">11</span><span class="sxs-lookup"><span data-stu-id="24212-475">11</span></span>|<span data-ttu-id="24212-476">Byl vytvořen souběžné uvolňování paměti kolekce přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="24212-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="24212-477">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="24212-477">No event data.</span></span>  
  
 [<span data-ttu-id="24212-478">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="24212-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="24212-479">GCTerminateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="24212-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="24212-480">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="24212-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="24212-481">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="24212-481">Keyword for raising the event</span></span>|<span data-ttu-id="24212-482">úroveň</span><span class="sxs-lookup"><span data-stu-id="24212-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="24212-483">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="24212-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="24212-484">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-484">Informational (4)</span></span>|  
|<span data-ttu-id="24212-485">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="24212-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="24212-486">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="24212-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="24212-487">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="24212-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="24212-488">Událost</span><span class="sxs-lookup"><span data-stu-id="24212-488">Event</span></span>|<span data-ttu-id="24212-489">ID události</span><span class="sxs-lookup"><span data-stu-id="24212-489">Event ID</span></span>|<span data-ttu-id="24212-490">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="24212-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="24212-491">12</span><span class="sxs-lookup"><span data-stu-id="24212-491">12</span></span>|<span data-ttu-id="24212-492">Souběžné uvolňování paměti kolekce vlákno byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="24212-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="24212-493">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="24212-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24212-494">Viz také</span><span class="sxs-lookup"><span data-stu-id="24212-494">See Also</span></span>  
 [<span data-ttu-id="24212-495">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="24212-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
