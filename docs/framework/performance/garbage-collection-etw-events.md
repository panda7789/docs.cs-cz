---
title: Události Trasování událostí pro Windows kolekci paměti
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13f7e935ab999ccc3cd3ea1e308e8d686bed4171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396932"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="0ddb7-102">Události Trasování událostí pro Windows kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="0ddb7-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="0ddb7-103">Tyto události shromažďovat informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="0ddb7-104">Mohou pomoci v diagnostice a ladění, včetně určení, jak často uvolňování byla provedena, kolik paměti byl uvolněn při uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="0ddb7-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="0ddb7-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="0ddb7-106">GCStart_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="0ddb7-107">GCEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="0ddb7-108">GCHeapStats_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="0ddb7-109">GCCreateSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="0ddb7-110">GCFreeSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="0ddb7-111">GCRestartEEBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="0ddb7-112">GCRestartEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="0ddb7-113">GCSuspendEE_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="0ddb7-114">GCSuspendEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="0ddb7-115">GCAllocationTick_V2 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="0ddb7-116">GCFinalizersBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="0ddb7-117">GCFinalizersEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="0ddb7-118">GCCreateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="0ddb7-119">GCTerminateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="0ddb7-120">GCStart_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-121">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="0ddb7-122">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0ddb7-123">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-123">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-124">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-126">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-127">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-128">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-128">Event</span></span>|<span data-ttu-id="0ddb7-129">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-129">Event ID</span></span>|<span data-ttu-id="0ddb7-130">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="0ddb7-131">1</span><span class="sxs-lookup"><span data-stu-id="0ddb7-131">1</span></span>|<span data-ttu-id="0ddb7-132">Kolekce paměti bylo zahájeno.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="0ddb7-133">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-134">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-134">Field name</span></span>|<span data-ttu-id="0ddb7-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-135">Data type</span></span>|<span data-ttu-id="0ddb7-136">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-137">Počet</span><span class="sxs-lookup"><span data-stu-id="0ddb7-137">Count</span></span>|<span data-ttu-id="0ddb7-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-138">win:UInt32</span></span>|<span data-ttu-id="0ddb7-139">*n*tý uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="0ddb7-140">Hloubka</span><span class="sxs-lookup"><span data-stu-id="0ddb7-140">Depth</span></span>|<span data-ttu-id="0ddb7-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-141">win:UInt32</span></span>|<span data-ttu-id="0ddb7-142">Generování, jež jsou shromažďována.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="0ddb7-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="0ddb7-143">Reason</span></span>|<span data-ttu-id="0ddb7-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-144">win:UInt32</span></span>|<span data-ttu-id="0ddb7-145">Proč byla aktivována uvolnění paměti:</span><span class="sxs-lookup"><span data-stu-id="0ddb7-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="0ddb7-146">0x0 - přidělení haldy malé objektu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="0ddb7-147">0x1 - vyvolané.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="0ddb7-148">0x2 - nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="0ddb7-149">0x3 - prázdný.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="0ddb7-150">0x4 - přidělení haldy velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="0ddb7-151">0x5 – volné místo (pro malé objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="0ddb7-152">0x6 – volné místo (pro velkého objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="0ddb7-153">0x7 - vyvolané ale nejsou vynucené jako blokování.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="0ddb7-154">Typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-154">Type</span></span>|<span data-ttu-id="0ddb7-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-155">win:UInt32</span></span>|<span data-ttu-id="0ddb7-156">došlo k blokování uvolňování 0x0 - mimo kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="0ddb7-157">0x1 – kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="0ddb7-158">0x2 – uvolňování paměti blokování došlo k chybě během kolekce paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="0ddb7-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-159">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-160">win:UInt16</span></span>|<span data-ttu-id="0ddb7-161">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0ddb7-162">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="0ddb7-163">GCEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-164">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-165">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-165">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-166">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-168">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-169">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-170">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-170">Event</span></span>|<span data-ttu-id="0ddb7-171">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-171">Event ID</span></span>|<span data-ttu-id="0ddb7-172">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="0ddb7-173">2</span><span class="sxs-lookup"><span data-stu-id="0ddb7-173">2</span></span>|<span data-ttu-id="0ddb7-174">Kolekce paměti byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="0ddb7-175">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-176">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-176">Field name</span></span>|<span data-ttu-id="0ddb7-177">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-177">Data type</span></span>|<span data-ttu-id="0ddb7-178">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-179">Počet</span><span class="sxs-lookup"><span data-stu-id="0ddb7-179">Count</span></span>|<span data-ttu-id="0ddb7-180">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-180">win:UInt32</span></span>|<span data-ttu-id="0ddb7-181">*n*tý uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="0ddb7-182">Hloubka</span><span class="sxs-lookup"><span data-stu-id="0ddb7-182">Depth</span></span>|<span data-ttu-id="0ddb7-183">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-183">win:UInt32</span></span>|<span data-ttu-id="0ddb7-184">Generování, která nebyla shromážděna.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="0ddb7-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-185">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-186">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-186">win:UInt16</span></span>|<span data-ttu-id="0ddb7-187">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0ddb7-188">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="0ddb7-189">GCHeapStats_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-190">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-191">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-191">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-192">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-194">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-195">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-196">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-196">Event</span></span>|<span data-ttu-id="0ddb7-197">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-197">Event ID</span></span>|<span data-ttu-id="0ddb7-198">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="0ddb7-199">4</span><span class="sxs-lookup"><span data-stu-id="0ddb7-199">4</span></span>|<span data-ttu-id="0ddb7-200">Zobrazuje statistiku haldy na konci každé uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="0ddb7-201">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-202">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-202">Field name</span></span>|<span data-ttu-id="0ddb7-203">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-203">Data type</span></span>|<span data-ttu-id="0ddb7-204">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="0ddb7-205">GenerationSize0</span></span>|<span data-ttu-id="0ddb7-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-206">win:UInt64</span></span>|<span data-ttu-id="0ddb7-207">Velikost v bajtech, generace 0 paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="0ddb7-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="0ddb7-208">TotalPromotedSize0</span></span>|<span data-ttu-id="0ddb7-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-209">win:UInt64</span></span>|<span data-ttu-id="0ddb7-210">Počet bajtů, které jsou povýší z generace 0 na 1. generace.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="0ddb7-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="0ddb7-211">GenerationSize1</span></span>|<span data-ttu-id="0ddb7-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-212">win:UInt64</span></span>|<span data-ttu-id="0ddb7-213">Velikost v bajtech paměti generace 1.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="0ddb7-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="0ddb7-214">TotalPromotedSize1</span></span>|<span data-ttu-id="0ddb7-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-215">win:UInt64</span></span>|<span data-ttu-id="0ddb7-216">Počet bajtů, které jsou povýší z generace 1 na 2. generace.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="0ddb7-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="0ddb7-217">GenerationSize2</span></span>|<span data-ttu-id="0ddb7-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-218">win:UInt64</span></span>|<span data-ttu-id="0ddb7-219">Velikost v bajtech, paměti, 2. generace.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="0ddb7-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="0ddb7-220">TotalPromotedSize2</span></span>|<span data-ttu-id="0ddb7-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-221">win:UInt64</span></span>|<span data-ttu-id="0ddb7-222">Počet bajtů, které přežil v generace 2 po poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="0ddb7-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="0ddb7-223">GenerationSize3</span></span>|<span data-ttu-id="0ddb7-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-224">win:UInt64</span></span>|<span data-ttu-id="0ddb7-225">Velikost v bajtech haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="0ddb7-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="0ddb7-226">TotalPromotedSize3</span></span>|<span data-ttu-id="0ddb7-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-227">win:UInt64</span></span>|<span data-ttu-id="0ddb7-228">Počet bajtů, které přežil v haldě velkého objektu po poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="0ddb7-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="0ddb7-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="0ddb7-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-230">win:UInt64</span></span>|<span data-ttu-id="0ddb7-231">Celková velikost v bajtech objektů, které jsou připravené pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="0ddb7-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="0ddb7-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="0ddb7-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-233">win:UInt64</span></span>|<span data-ttu-id="0ddb7-234">Počet objektů, které jsou připravené pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="0ddb7-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="0ddb7-235">PinnedObjectCount</span></span>|<span data-ttu-id="0ddb7-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-236">win:UInt32</span></span>|<span data-ttu-id="0ddb7-237">Počet připojených objektů (nepřesunutelnou).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="0ddb7-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="0ddb7-238">SinkBlockCount</span></span>|<span data-ttu-id="0ddb7-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-239">win:UInt32</span></span>|<span data-ttu-id="0ddb7-240">Počet bloků synchronizace používá.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="0ddb7-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="0ddb7-241">GCHandleCount</span></span>|<span data-ttu-id="0ddb7-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-242">win:UInt32</span></span>|<span data-ttu-id="0ddb7-243">Počet uvolňování zpracovává používán.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="0ddb7-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-244">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-245">win:UInt16</span></span>|<span data-ttu-id="0ddb7-246">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0ddb7-247">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="0ddb7-248">GCCreateSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-249">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-250">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-250">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-251">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-253">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-254">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-255">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-255">Event</span></span>|<span data-ttu-id="0ddb7-256">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-256">Event ID</span></span>|<span data-ttu-id="0ddb7-257">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="0ddb7-258">5</span><span class="sxs-lookup"><span data-stu-id="0ddb7-258">5</span></span>|<span data-ttu-id="0ddb7-259">Byl vytvořen nový segment kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="0ddb7-260">Kromě toho pokud je povoleno sledování na procesu, který je již spuštěn, tato událost je aktivována pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="0ddb7-261">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-262">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-262">Field name</span></span>|<span data-ttu-id="0ddb7-263">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-263">Data type</span></span>|<span data-ttu-id="0ddb7-264">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-265">Adresa</span><span class="sxs-lookup"><span data-stu-id="0ddb7-265">Address</span></span>|<span data-ttu-id="0ddb7-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-266">win:UInt64</span></span>|<span data-ttu-id="0ddb7-267">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-267">The address of the segment.</span></span>|  
|<span data-ttu-id="0ddb7-268">Velikost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-268">Size</span></span>|<span data-ttu-id="0ddb7-269">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-269">win:UInt64</span></span>|<span data-ttu-id="0ddb7-270">Velikost segmentu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-270">The size of the segment.</span></span>|  
|<span data-ttu-id="0ddb7-271">Typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-271">Type</span></span>|<span data-ttu-id="0ddb7-272">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-272">win:UInt32</span></span>|<span data-ttu-id="0ddb7-273">0x0 - malé objekty.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="0ddb7-274">0x1 - velké objekty.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="0ddb7-275">0x2 - haldy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="0ddb7-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-276">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-277">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-277">win:UInt16</span></span>|<span data-ttu-id="0ddb7-278">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="0ddb7-279">Všimněte si, že velikost segmentů přidělené modulem garbage collector závisí na implementaci a mohou podléhat změnám kdykoli, včetně v pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="0ddb7-280">Vaše aplikace by nikdy Zkontrolujte předpoklady o nebo závisí na velikosti určitý segment, ani pokusit nakonfigurovat množství paměti k dispozici pro přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="0ddb7-281">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="0ddb7-282">GCFreeSegment_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-283">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-284">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-284">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-285">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-287">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-288">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-289">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-289">Event</span></span>|<span data-ttu-id="0ddb7-290">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-290">Event ID</span></span>|<span data-ttu-id="0ddb7-291">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="0ddb7-292">6</span><span class="sxs-lookup"><span data-stu-id="0ddb7-292">6</span></span>|<span data-ttu-id="0ddb7-293">Byla vydána segment kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="0ddb7-294">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-295">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-295">Field name</span></span>|<span data-ttu-id="0ddb7-296">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-296">Data type</span></span>|<span data-ttu-id="0ddb7-297">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-298">Adresa</span><span class="sxs-lookup"><span data-stu-id="0ddb7-298">Address</span></span>|<span data-ttu-id="0ddb7-299">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-299">win:UInt64</span></span>|<span data-ttu-id="0ddb7-300">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-300">The address of the segment.</span></span>|  
|<span data-ttu-id="0ddb7-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-301">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-302">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-302">win:UInt16</span></span>|<span data-ttu-id="0ddb7-303">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0ddb7-304">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="0ddb7-305">GCRestartEEBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-306">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-307">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-307">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-308">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-310">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-311">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-312">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-312">Event</span></span>|<span data-ttu-id="0ddb7-313">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-313">Event ID</span></span>|<span data-ttu-id="0ddb7-314">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="0ddb7-315">7</span><span class="sxs-lookup"><span data-stu-id="0ddb7-315">7</span></span>|<span data-ttu-id="0ddb7-316">Obnovení z běžných pozastavení runtime jazyka byl zahájen.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="0ddb7-317">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-317">No event data.</span></span>  
  
 [<span data-ttu-id="0ddb7-318">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="0ddb7-319">GCRestartEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-320">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-321">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-321">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-322">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-324">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-325">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-326">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-326">Event</span></span>|<span data-ttu-id="0ddb7-327">Id události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-327">Event Id</span></span>|<span data-ttu-id="0ddb7-328">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="0ddb7-329">3</span><span class="sxs-lookup"><span data-stu-id="0ddb7-329">3</span></span>|<span data-ttu-id="0ddb7-330">Obnovení z běžných pozastavení runtime jazyka byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="0ddb7-331">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-331">No event data.</span></span>  
  
 [<span data-ttu-id="0ddb7-332">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="0ddb7-333">GCSuspendEE_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-334">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-335">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-335">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-336">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-338">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-339">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-340">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-340">Event</span></span>|<span data-ttu-id="0ddb7-341">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-341">Event ID</span></span>|<span data-ttu-id="0ddb7-342">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="0ddb7-343">9</span><span class="sxs-lookup"><span data-stu-id="0ddb7-343">9</span></span>|<span data-ttu-id="0ddb7-344">Začátek pozastavení provádění modul pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="0ddb7-345">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-346">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-346">Field name</span></span>|<span data-ttu-id="0ddb7-347">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-347">Data type</span></span>|<span data-ttu-id="0ddb7-348">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-349">Důvod</span><span class="sxs-lookup"><span data-stu-id="0ddb7-349">Reason</span></span>|<span data-ttu-id="0ddb7-350">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-350">win:UInt16</span></span>|<span data-ttu-id="0ddb7-351">0x0 - Další.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="0ddb7-352">0x1 – uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="0ddb7-353">0x2 - ukončení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="0ddb7-354">0x3 - pitching kódu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="0ddb7-355">0x4 - vypnutí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="0ddb7-356">0x5 - ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="0ddb7-357">0x6 - přípravy pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="0ddb7-358">Počet</span><span class="sxs-lookup"><span data-stu-id="0ddb7-358">Count</span></span>|<span data-ttu-id="0ddb7-359">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-359">win:UInt32</span></span>|<span data-ttu-id="0ddb7-360">Počet uvolňování paměti v době.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-360">The GC count at the time.</span></span> <span data-ttu-id="0ddb7-361">Obvykle zobrazí se následných událostí GC spuštění po této a jeho počet by tento počet + 1 jsme zvýšit GC index během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="0ddb7-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-362">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-363">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-363">win:UInt16</span></span>|<span data-ttu-id="0ddb7-364">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0ddb7-365">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="0ddb7-366">GCSuspendEEEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-367">V následující tabulce jsou uvedeny – klíčové slovo a úroveň:</span><span class="sxs-lookup"><span data-stu-id="0ddb7-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="0ddb7-368">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-368">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-369">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-371">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-372">V následující tabulce jsou uvedeny informace o události:</span><span class="sxs-lookup"><span data-stu-id="0ddb7-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="0ddb7-373">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-373">Event</span></span>|<span data-ttu-id="0ddb7-374">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-374">Event ID</span></span>|<span data-ttu-id="0ddb7-375">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="0ddb7-376">8</span><span class="sxs-lookup"><span data-stu-id="0ddb7-376">8</span></span>|<span data-ttu-id="0ddb7-377">Konec pozastavení provádění modul pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="0ddb7-378">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-378">No event data.</span></span>  
  
 [<span data-ttu-id="0ddb7-379">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="0ddb7-380">GCAllocationTick_V2 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="0ddb7-381">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-382">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-382">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-383">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-385">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-386">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-387">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-387">Event</span></span>|<span data-ttu-id="0ddb7-388">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-388">Event ID</span></span>|<span data-ttu-id="0ddb7-389">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="0ddb7-390">10</span><span class="sxs-lookup"><span data-stu-id="0ddb7-390">10</span></span>|<span data-ttu-id="0ddb7-391">Pokaždé, když je přidělen přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="0ddb7-392">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-393">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-393">Field name</span></span>|<span data-ttu-id="0ddb7-394">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-394">Data type</span></span>|<span data-ttu-id="0ddb7-395">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="0ddb7-396">AllocationAmount</span></span>|<span data-ttu-id="0ddb7-397">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-397">win:UInt32</span></span>|<span data-ttu-id="0ddb7-398">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-398">The allocation size, in bytes.</span></span> <span data-ttu-id="0ddb7-399">Tato hodnota je přesný pro přidělení, které jsou menší než délka ULONG (4,294,967,295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="0ddb7-400">Pokud přidělení je vyšší, toto pole obsahuje zkrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="0ddb7-401">Použití `AllocationAmount64` pro velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="0ddb7-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="0ddb7-402">AllocationKind</span></span>|<span data-ttu-id="0ddb7-403">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-403">win:UInt32</span></span>|<span data-ttu-id="0ddb7-404">0x0 - malé objekt přidělení (přidělení je v malých objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="0ddb7-405">0x1 - přidělení velkého objektu (přidělení je v haldě rozsáhlý objekt).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="0ddb7-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-406">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-407">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-407">win:UInt16</span></span>|<span data-ttu-id="0ddb7-408">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="0ddb7-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-409">AllocationAmount64</span></span>|<span data-ttu-id="0ddb7-410">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0ddb7-410">win:UInt64</span></span>|<span data-ttu-id="0ddb7-411">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-411">The allocation size, in bytes.</span></span> <span data-ttu-id="0ddb7-412">Tato hodnota je přesný pro velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="0ddb7-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="0ddb7-413">TypeId</span></span>|<span data-ttu-id="0ddb7-414">Win: ukazatele</span><span class="sxs-lookup"><span data-stu-id="0ddb7-414">win:Pointer</span></span>|<span data-ttu-id="0ddb7-415">Adresa MethodTable.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-415">The address of the MethodTable.</span></span> <span data-ttu-id="0ddb7-416">Pokud existuje několik typů objektů, které byly přiděleny během této události, to je adresa MethodTable, která odpovídá na poslední objekt přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="0ddb7-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="0ddb7-417">TypeName</span></span>|<span data-ttu-id="0ddb7-418">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0ddb7-418">win:UnicodeString</span></span>|<span data-ttu-id="0ddb7-419">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-419">The name of the type that was allocated.</span></span> <span data-ttu-id="0ddb7-420">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ objektu poslední přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).</span><span class="sxs-lookup"><span data-stu-id="0ddb7-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="0ddb7-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="0ddb7-421">HeapIndex</span></span>|<span data-ttu-id="0ddb7-422">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-422">win:UInt32</span></span>|<span data-ttu-id="0ddb7-423">Halda, kde byl přidělen objektu.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-423">The heap where the object was allocated.</span></span> <span data-ttu-id="0ddb7-424">Tato hodnota je 0 (nula) při spuštění s uvolňování paměti pracovních stanic.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="0ddb7-425">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="0ddb7-426">GCFinalizersBegin_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-427">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-428">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-428">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-429">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-431">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-432">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-433">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-433">Event</span></span>|<span data-ttu-id="0ddb7-434">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-434">Event ID</span></span>|<span data-ttu-id="0ddb7-435">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="0ddb7-436">14</span><span class="sxs-lookup"><span data-stu-id="0ddb7-436">14</span></span>|<span data-ttu-id="0ddb7-437">Počáteční spouštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="0ddb7-438">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-438">No event data.</span></span>  
  
 [<span data-ttu-id="0ddb7-439">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="0ddb7-440">GCFinalizersEnd_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-441">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-442">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-442">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-443">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-445">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-446">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-447">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-447">Event</span></span>|<span data-ttu-id="0ddb7-448">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-448">Event ID</span></span>|<span data-ttu-id="0ddb7-449">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="0ddb7-450">13</span><span class="sxs-lookup"><span data-stu-id="0ddb7-450">13</span></span>|<span data-ttu-id="0ddb7-451">Konec systémem finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="0ddb7-452">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0ddb7-453">Název pole</span><span class="sxs-lookup"><span data-stu-id="0ddb7-453">Field name</span></span>|<span data-ttu-id="0ddb7-454">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0ddb7-454">Data type</span></span>|<span data-ttu-id="0ddb7-455">Popis</span><span class="sxs-lookup"><span data-stu-id="0ddb7-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0ddb7-456">Počet</span><span class="sxs-lookup"><span data-stu-id="0ddb7-456">Count</span></span>|<span data-ttu-id="0ddb7-457">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0ddb7-457">win:UInt32</span></span>|<span data-ttu-id="0ddb7-458">Počet finalizační metody, které byly spuštěné.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="0ddb7-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0ddb7-459">ClrInstanceID</span></span>|<span data-ttu-id="0ddb7-460">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0ddb7-460">win:UInt16</span></span>|<span data-ttu-id="0ddb7-461">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0ddb7-462">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="0ddb7-463">GCCreateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-464">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-465">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-465">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-466">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-468">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-468">Informational (4)</span></span>|  
|<span data-ttu-id="0ddb7-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0ddb7-470">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-471">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-472">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-472">Event</span></span>|<span data-ttu-id="0ddb7-473">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-473">Event ID</span></span>|<span data-ttu-id="0ddb7-474">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="0ddb7-475">11</span><span class="sxs-lookup"><span data-stu-id="0ddb7-475">11</span></span>|<span data-ttu-id="0ddb7-476">Byl vytvořen souběžné uvolňování paměti kolekce přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="0ddb7-477">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-477">No event data.</span></span>  
  
 [<span data-ttu-id="0ddb7-478">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="0ddb7-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="0ddb7-479">GCTerminateConcurrentThread_V1 událostí</span><span class="sxs-lookup"><span data-stu-id="0ddb7-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="0ddb7-480">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0ddb7-481">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-481">Keyword for raising the event</span></span>|<span data-ttu-id="0ddb7-482">úroveň</span><span class="sxs-lookup"><span data-stu-id="0ddb7-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0ddb7-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0ddb7-484">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-484">Informational (4)</span></span>|  
|<span data-ttu-id="0ddb7-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0ddb7-486">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="0ddb7-487">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0ddb7-488">Událost</span><span class="sxs-lookup"><span data-stu-id="0ddb7-488">Event</span></span>|<span data-ttu-id="0ddb7-489">ID události</span><span class="sxs-lookup"><span data-stu-id="0ddb7-489">Event ID</span></span>|<span data-ttu-id="0ddb7-490">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="0ddb7-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="0ddb7-491">12</span><span class="sxs-lookup"><span data-stu-id="0ddb7-491">12</span></span>|<span data-ttu-id="0ddb7-492">Souběžné uvolňování paměti kolekce vlákno byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="0ddb7-493">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="0ddb7-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ddb7-494">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ddb7-494">See Also</span></span>  
 [<span data-ttu-id="0ddb7-495">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="0ddb7-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
