---
title: Události Trasování událostí pro Windows uvolnění paměti
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149731"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="9712b-102">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="9712b-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="9712b-103">Tyto události shromažďovat informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="9712b-104">Pomáhají v Diagnostika a ladění, včetně určení, kolikrát uvolňování paměti byla provedena, kolik paměti byl uvolněn při uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9712b-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="9712b-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="9712b-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="9712b-106">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="9712b-107">GCEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="9712b-108">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="9712b-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="9712b-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="9712b-111">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="9712b-112">GCRestartEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="9712b-113">GCSuspendEE_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="9712b-114">GCSuspendEEEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="9712b-115">GCAllocationTick_V2 události</span><span class="sxs-lookup"><span data-stu-id="9712b-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="9712b-116">GCFinalizersBegin_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="9712b-117">GCFinalizersEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="9712b-118">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="9712b-119">GCTerminateConcurrentThread_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="9712b-120">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="9712b-121">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="9712b-122">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="9712b-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="9712b-123">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-123">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-124">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-124">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-125">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-125">(0x1)</span></span>|<span data-ttu-id="9712b-126">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-127">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-128">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-128">Event</span></span>|<span data-ttu-id="9712b-129">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-129">Event ID</span></span>|<span data-ttu-id="9712b-130">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="9712b-131">1</span><span class="sxs-lookup"><span data-stu-id="9712b-131">1</span></span>|<span data-ttu-id="9712b-132">Uvolňování paměti byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9712b-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="9712b-133">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-134">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-134">Field name</span></span>|<span data-ttu-id="9712b-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-135">Data type</span></span>|<span data-ttu-id="9712b-136">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-137">Počet</span><span class="sxs-lookup"><span data-stu-id="9712b-137">Count</span></span>|<span data-ttu-id="9712b-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-138">win:UInt32</span></span>|<span data-ttu-id="9712b-139">*n*th uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="9712b-140">Hloubka</span><span class="sxs-lookup"><span data-stu-id="9712b-140">Depth</span></span>|<span data-ttu-id="9712b-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-141">win:UInt32</span></span>|<span data-ttu-id="9712b-142">Generování, jež jsou shromažďována.</span><span class="sxs-lookup"><span data-stu-id="9712b-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="9712b-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="9712b-143">Reason</span></span>|<span data-ttu-id="9712b-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-144">win:UInt32</span></span>|<span data-ttu-id="9712b-145">Proč byla aktivována. uvolnění:</span><span class="sxs-lookup"><span data-stu-id="9712b-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="9712b-146">0x0 - přidělení haldy malých objektů.</span><span class="sxs-lookup"><span data-stu-id="9712b-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="9712b-147">0x1 - vyvolaných.</span><span class="sxs-lookup"><span data-stu-id="9712b-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="9712b-148">0x2 - nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="9712b-149">0x3 - prázdný.</span><span class="sxs-lookup"><span data-stu-id="9712b-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="9712b-150">0x4 - přidělení haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="9712b-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="9712b-151">0x5 - nedostatek místa (pro haldu malých objektů).</span><span class="sxs-lookup"><span data-stu-id="9712b-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="9712b-152">0x6 - nedostatek místa (pro haldu velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="9712b-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="9712b-153">0x7 - vyvolané, ale nejsou vynucené jako blokování.</span><span class="sxs-lookup"><span data-stu-id="9712b-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="9712b-154">Type</span><span class="sxs-lookup"><span data-stu-id="9712b-154">Type</span></span>|<span data-ttu-id="9712b-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-155">win:UInt32</span></span>|<span data-ttu-id="9712b-156">0x0 - mimo uvolňování paměti na pozadí došlo k blokování uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="9712b-157">0x1 – uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9712b-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="9712b-158">0x2 - blokující uvolňování paměti došlo k chybě během uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9712b-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="9712b-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-159">ClrInstanceID</span></span>|<span data-ttu-id="9712b-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-160">win:UInt16</span></span>|<span data-ttu-id="9712b-161">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9712b-162">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="9712b-163">GCEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="9712b-164">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-165">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-165">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-166">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-166">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-167">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-167">(0x1)</span></span>|<span data-ttu-id="9712b-168">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-169">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-170">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-170">Event</span></span>|<span data-ttu-id="9712b-171">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-171">Event ID</span></span>|<span data-ttu-id="9712b-172">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="9712b-173">2</span><span class="sxs-lookup"><span data-stu-id="9712b-173">2</span></span>|<span data-ttu-id="9712b-174">Kolekce paměti bylo již ukončeno.</span><span class="sxs-lookup"><span data-stu-id="9712b-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="9712b-175">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-176">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-176">Field name</span></span>|<span data-ttu-id="9712b-177">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-177">Data type</span></span>|<span data-ttu-id="9712b-178">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-179">Počet</span><span class="sxs-lookup"><span data-stu-id="9712b-179">Count</span></span>|<span data-ttu-id="9712b-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-180">win:UInt32</span></span>|<span data-ttu-id="9712b-181">*n*th uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="9712b-182">Hloubka</span><span class="sxs-lookup"><span data-stu-id="9712b-182">Depth</span></span>|<span data-ttu-id="9712b-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-183">win:UInt32</span></span>|<span data-ttu-id="9712b-184">Generace, která byla shromážděna.</span><span class="sxs-lookup"><span data-stu-id="9712b-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="9712b-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-185">ClrInstanceID</span></span>|<span data-ttu-id="9712b-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-186">win:UInt16</span></span>|<span data-ttu-id="9712b-187">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9712b-188">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="9712b-189">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="9712b-190">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-191">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-191">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-192">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-192">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-193">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-193">(0x1)</span></span>|<span data-ttu-id="9712b-194">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-195">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-196">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-196">Event</span></span>|<span data-ttu-id="9712b-197">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-197">Event ID</span></span>|<span data-ttu-id="9712b-198">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="9712b-199">4</span><span class="sxs-lookup"><span data-stu-id="9712b-199">4</span></span>|<span data-ttu-id="9712b-200">Zobrazuje statistiku haldě na konci každé uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="9712b-201">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-202">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-202">Field name</span></span>|<span data-ttu-id="9712b-203">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-203">Data type</span></span>|<span data-ttu-id="9712b-204">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="9712b-205">GenerationSize0</span></span>|<span data-ttu-id="9712b-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-206">win:UInt64</span></span>|<span data-ttu-id="9712b-207">Velikost v bajtech paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="9712b-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="9712b-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="9712b-208">TotalPromotedSize0</span></span>|<span data-ttu-id="9712b-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-209">win:UInt64</span></span>|<span data-ttu-id="9712b-210">Počet bajtů, které jsou přesunuty z 0. generace do 1. generace.</span><span class="sxs-lookup"><span data-stu-id="9712b-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="9712b-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="9712b-211">GenerationSize1</span></span>|<span data-ttu-id="9712b-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-212">win:UInt64</span></span>|<span data-ttu-id="9712b-213">Velikost v bajtech paměti generace 1.</span><span class="sxs-lookup"><span data-stu-id="9712b-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="9712b-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="9712b-214">TotalPromotedSize1</span></span>|<span data-ttu-id="9712b-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-215">win:UInt64</span></span>|<span data-ttu-id="9712b-216">Počet bajtů, které jsou přesunuty z 1. generace do 2. generace.</span><span class="sxs-lookup"><span data-stu-id="9712b-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="9712b-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="9712b-217">GenerationSize2</span></span>|<span data-ttu-id="9712b-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-218">win:UInt64</span></span>|<span data-ttu-id="9712b-219">Velikost v bajtech paměti generace 2.</span><span class="sxs-lookup"><span data-stu-id="9712b-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="9712b-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="9712b-220">TotalPromotedSize2</span></span>|<span data-ttu-id="9712b-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-221">win:UInt64</span></span>|<span data-ttu-id="9712b-222">Počet bajtů, které zůstat naživu v generaci 2 po poslední.</span><span class="sxs-lookup"><span data-stu-id="9712b-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="9712b-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="9712b-223">GenerationSize3</span></span>|<span data-ttu-id="9712b-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-224">win:UInt64</span></span>|<span data-ttu-id="9712b-225">Velikost v bajtech, velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="9712b-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="9712b-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="9712b-226">TotalPromotedSize3</span></span>|<span data-ttu-id="9712b-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-227">win:UInt64</span></span>|<span data-ttu-id="9712b-228">Počet bajtů, které zůstat naživu haldy velkých objektů po poslední.</span><span class="sxs-lookup"><span data-stu-id="9712b-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="9712b-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="9712b-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="9712b-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-230">win:UInt64</span></span>|<span data-ttu-id="9712b-231">Celková velikost v bajtech, objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="9712b-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="9712b-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="9712b-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="9712b-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-233">win:UInt64</span></span>|<span data-ttu-id="9712b-234">Počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="9712b-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="9712b-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="9712b-235">PinnedObjectCount</span></span>|<span data-ttu-id="9712b-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-236">win:UInt32</span></span>|<span data-ttu-id="9712b-237">Počet připojených objektů (o nepřesunutelnou).</span><span class="sxs-lookup"><span data-stu-id="9712b-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="9712b-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="9712b-238">SinkBlockCount</span></span>|<span data-ttu-id="9712b-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-239">win:UInt32</span></span>|<span data-ttu-id="9712b-240">Počet bloků synchronizace používá.</span><span class="sxs-lookup"><span data-stu-id="9712b-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="9712b-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="9712b-241">GCHandleCount</span></span>|<span data-ttu-id="9712b-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-242">win:UInt32</span></span>|<span data-ttu-id="9712b-243">Počet uvolňování zpracovává používá.</span><span class="sxs-lookup"><span data-stu-id="9712b-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="9712b-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-244">ClrInstanceID</span></span>|<span data-ttu-id="9712b-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-245">win:UInt16</span></span>|<span data-ttu-id="9712b-246">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9712b-247">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="9712b-248">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="9712b-249">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-250">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-250">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-251">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-251">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-252">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-252">(0x1)</span></span>|<span data-ttu-id="9712b-253">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-254">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-255">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-255">Event</span></span>|<span data-ttu-id="9712b-256">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-256">Event ID</span></span>|<span data-ttu-id="9712b-257">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="9712b-258">5</span><span class="sxs-lookup"><span data-stu-id="9712b-258">5</span></span>|<span data-ttu-id="9712b-259">Vytvořil se nový segment kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="9712b-260">Kromě toho když je povoleno trasování procesu, který je již spuštěn, tato událost je aktivována pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="9712b-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="9712b-261">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-262">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-262">Field name</span></span>|<span data-ttu-id="9712b-263">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-263">Data type</span></span>|<span data-ttu-id="9712b-264">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-265">Adresa</span><span class="sxs-lookup"><span data-stu-id="9712b-265">Address</span></span>|<span data-ttu-id="9712b-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-266">win:UInt64</span></span>|<span data-ttu-id="9712b-267">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="9712b-267">The address of the segment.</span></span>|  
|<span data-ttu-id="9712b-268">Velikost</span><span class="sxs-lookup"><span data-stu-id="9712b-268">Size</span></span>|<span data-ttu-id="9712b-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-269">win:UInt64</span></span>|<span data-ttu-id="9712b-270">Velikost segmentu.</span><span class="sxs-lookup"><span data-stu-id="9712b-270">The size of the segment.</span></span>|  
|<span data-ttu-id="9712b-271">Type</span><span class="sxs-lookup"><span data-stu-id="9712b-271">Type</span></span>|<span data-ttu-id="9712b-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-272">win:UInt32</span></span>|<span data-ttu-id="9712b-273">0x0 - haldy malých objektů.</span><span class="sxs-lookup"><span data-stu-id="9712b-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="9712b-274">0x1 - velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="9712b-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="9712b-275">0x2 - haldy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9712b-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="9712b-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-276">ClrInstanceID</span></span>|<span data-ttu-id="9712b-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-277">win:UInt16</span></span>|<span data-ttu-id="9712b-278">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="9712b-279">Mějte na paměti, že velikost segmentů přidělaná systému uvolňování paměti je specifický pro implementaci a může se změnit kdykoli, včetně v pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="9712b-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="9712b-280">Vaše aplikace by nikdy vytvořit předpoklady o nebo závisí na velikosti konkrétního segmentu, ani snažit konfigurace množství paměti k přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="9712b-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="9712b-281">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="9712b-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="9712b-283">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-284">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-284">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-285">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-285">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-286">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-286">(0x1)</span></span>|<span data-ttu-id="9712b-287">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-288">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-289">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-289">Event</span></span>|<span data-ttu-id="9712b-290">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-290">Event ID</span></span>|<span data-ttu-id="9712b-291">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="9712b-292">6</span><span class="sxs-lookup"><span data-stu-id="9712b-292">6</span></span>|<span data-ttu-id="9712b-293">Segment uvolňování paměti kolekce byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="9712b-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="9712b-294">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-295">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-295">Field name</span></span>|<span data-ttu-id="9712b-296">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-296">Data type</span></span>|<span data-ttu-id="9712b-297">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-298">Adresa</span><span class="sxs-lookup"><span data-stu-id="9712b-298">Address</span></span>|<span data-ttu-id="9712b-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-299">win:UInt64</span></span>|<span data-ttu-id="9712b-300">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="9712b-300">The address of the segment.</span></span>|  
|<span data-ttu-id="9712b-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-301">ClrInstanceID</span></span>|<span data-ttu-id="9712b-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-302">win:UInt16</span></span>|<span data-ttu-id="9712b-303">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9712b-304">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="9712b-305">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="9712b-306">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-307">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-307">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-308">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-308">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-309">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-309">(0x1)</span></span>|<span data-ttu-id="9712b-310">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-311">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-312">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-312">Event</span></span>|<span data-ttu-id="9712b-313">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-313">Event ID</span></span>|<span data-ttu-id="9712b-314">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="9712b-315">7</span><span class="sxs-lookup"><span data-stu-id="9712b-315">7</span></span>|<span data-ttu-id="9712b-316">Bylo zahájeno obnovení z common language runtime pozastavení.</span><span class="sxs-lookup"><span data-stu-id="9712b-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="9712b-317">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="9712b-317">No event data.</span></span>  
  
 [<span data-ttu-id="9712b-318">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="9712b-319">GCRestartEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="9712b-320">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-321">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-321">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-322">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-322">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-323">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-323">(0x1)</span></span>|<span data-ttu-id="9712b-324">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-325">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-326">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-326">Event</span></span>|<span data-ttu-id="9712b-327">Id události</span><span class="sxs-lookup"><span data-stu-id="9712b-327">Event Id</span></span>|<span data-ttu-id="9712b-328">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="9712b-329">3</span><span class="sxs-lookup"><span data-stu-id="9712b-329">3</span></span>|<span data-ttu-id="9712b-330">Obnovení z common language runtime pozastavení skončila.</span><span class="sxs-lookup"><span data-stu-id="9712b-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="9712b-331">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="9712b-331">No event data.</span></span>  
  
 [<span data-ttu-id="9712b-332">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="9712b-333">GCSuspendEE_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="9712b-334">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-335">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-335">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-336">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-336">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-337">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-337">(0x1)</span></span>|<span data-ttu-id="9712b-338">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-339">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-340">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-340">Event</span></span>|<span data-ttu-id="9712b-341">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-341">Event ID</span></span>|<span data-ttu-id="9712b-342">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="9712b-343">9</span><span class="sxs-lookup"><span data-stu-id="9712b-343">9</span></span>|<span data-ttu-id="9712b-344">Začátek pozastavení prováděcí modul pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="9712b-345">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-346">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-346">Field name</span></span>|<span data-ttu-id="9712b-347">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-347">Data type</span></span>|<span data-ttu-id="9712b-348">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-349">Důvod</span><span class="sxs-lookup"><span data-stu-id="9712b-349">Reason</span></span>|<span data-ttu-id="9712b-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-350">win:UInt16</span></span>|<span data-ttu-id="9712b-351">0x0 – ostatní.</span><span class="sxs-lookup"><span data-stu-id="9712b-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="9712b-352">0x1 – uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="9712b-353">0x2 – ukončení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9712b-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="9712b-354">0x3 - pitching kódu.</span><span class="sxs-lookup"><span data-stu-id="9712b-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="9712b-355">0x4 – vypnutí.</span><span class="sxs-lookup"><span data-stu-id="9712b-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="9712b-356">0x5 – ladicí program.</span><span class="sxs-lookup"><span data-stu-id="9712b-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="9712b-357">0x6 – Příprava pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="9712b-358">Počet</span><span class="sxs-lookup"><span data-stu-id="9712b-358">Count</span></span>|<span data-ttu-id="9712b-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-359">win:UInt32</span></span>|<span data-ttu-id="9712b-360">Uvolňování paměti – počet v době.</span><span class="sxs-lookup"><span data-stu-id="9712b-360">The GC count at the time.</span></span> <span data-ttu-id="9712b-361">Obvykle zobrazí následující události Start uvolňování paměti po to a její vlastnosti Count by tento počet + 1 jsme zvýšit index uvolňování paměti během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="9712b-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-362">ClrInstanceID</span></span>|<span data-ttu-id="9712b-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-363">win:UInt16</span></span>|<span data-ttu-id="9712b-364">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9712b-365">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="9712b-366">GCSuspendEEEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="9712b-367">V následující tabulce jsou uvedeny – klíčové slovo a úroveň:</span><span class="sxs-lookup"><span data-stu-id="9712b-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="9712b-368">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-368">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-369">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-369">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-370">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-370">(0x1)</span></span>|<span data-ttu-id="9712b-371">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-372">V následující tabulce jsou uvedeny informace o události:</span><span class="sxs-lookup"><span data-stu-id="9712b-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="9712b-373">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-373">Event</span></span>|<span data-ttu-id="9712b-374">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-374">Event ID</span></span>|<span data-ttu-id="9712b-375">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="9712b-376">8</span><span class="sxs-lookup"><span data-stu-id="9712b-376">8</span></span>|<span data-ttu-id="9712b-377">Konec pozastavení prováděcí modul pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9712b-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="9712b-378">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="9712b-378">No event data.</span></span>  
  
 [<span data-ttu-id="9712b-379">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="9712b-380">GCAllocationTick_V2 události</span><span class="sxs-lookup"><span data-stu-id="9712b-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="9712b-381">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-382">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-382">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-383">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-383">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-384">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-384">(0x1)</span></span>|<span data-ttu-id="9712b-385">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-386">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-387">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-387">Event</span></span>|<span data-ttu-id="9712b-388">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-388">Event ID</span></span>|<span data-ttu-id="9712b-389">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="9712b-390">10</span><span class="sxs-lookup"><span data-stu-id="9712b-390">10</span></span>|<span data-ttu-id="9712b-391">Pokaždé, když je přidělen přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="9712b-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="9712b-392">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-393">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-393">Field name</span></span>|<span data-ttu-id="9712b-394">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-394">Data type</span></span>|<span data-ttu-id="9712b-395">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="9712b-396">AllocationAmount</span></span>|<span data-ttu-id="9712b-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-397">win:UInt32</span></span>|<span data-ttu-id="9712b-398">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9712b-398">The allocation size, in bytes.</span></span> <span data-ttu-id="9712b-399">Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4,294,967,295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="9712b-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="9712b-400">Pokud přidělení paměti je větší, toto pole obsahuje zkrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="9712b-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="9712b-401">Použití `AllocationAmount64` velmi velkého přidělení.</span><span class="sxs-lookup"><span data-stu-id="9712b-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="9712b-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="9712b-402">AllocationKind</span></span>|<span data-ttu-id="9712b-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-403">win:UInt32</span></span>|<span data-ttu-id="9712b-404">0x0 - přidělení malých objektů (přidělení je haldy malých objektů).</span><span class="sxs-lookup"><span data-stu-id="9712b-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="9712b-405">0x1 – rozdělení velkých objektů (přidělení je v haldy velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="9712b-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="9712b-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-406">ClrInstanceID</span></span>|<span data-ttu-id="9712b-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-407">win:UInt16</span></span>|<span data-ttu-id="9712b-408">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="9712b-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="9712b-409">AllocationAmount64</span></span>|<span data-ttu-id="9712b-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9712b-410">win:UInt64</span></span>|<span data-ttu-id="9712b-411">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9712b-411">The allocation size, in bytes.</span></span> <span data-ttu-id="9712b-412">Tato hodnota je přesné pro velmi velkého přidělení.</span><span class="sxs-lookup"><span data-stu-id="9712b-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="9712b-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="9712b-413">TypeId</span></span>|<span data-ttu-id="9712b-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="9712b-414">win:Pointer</span></span>|<span data-ttu-id="9712b-415">Adresa MethodTable.</span><span class="sxs-lookup"><span data-stu-id="9712b-415">The address of the MethodTable.</span></span> <span data-ttu-id="9712b-416">Když existuje několik typů objektů, které byly přiděleny během této události, jde o adresu MethodTable, která odpovídá na poslední objekt přidělený (objekt, který způsobil překročení prahovou hodnotu 100 KB).</span><span class="sxs-lookup"><span data-stu-id="9712b-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="9712b-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="9712b-417">TypeName</span></span>|<span data-ttu-id="9712b-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9712b-418">win:UnicodeString</span></span>|<span data-ttu-id="9712b-419">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="9712b-419">The name of the type that was allocated.</span></span> <span data-ttu-id="9712b-420">Když existuje několik typů objektů, které byly přiděleny během této události, toto je typ objektu poslední přidělené (objekt, který způsobil překročení prahovou hodnotu 100 KB).</span><span class="sxs-lookup"><span data-stu-id="9712b-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="9712b-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="9712b-421">HeapIndex</span></span>|<span data-ttu-id="9712b-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-422">win:UInt32</span></span>|<span data-ttu-id="9712b-423">Haldy, ve kterém byla objektu přidělena.</span><span class="sxs-lookup"><span data-stu-id="9712b-423">The heap where the object was allocated.</span></span> <span data-ttu-id="9712b-424">Tato hodnota je 0 (nula), když budou běžet s uvolnění paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="9712b-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="9712b-425">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="9712b-426">GCFinalizersBegin_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="9712b-427">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-428">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-428">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-429">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-429">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-430">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-430">(0x1)</span></span>|<span data-ttu-id="9712b-431">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-432">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-433">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-433">Event</span></span>|<span data-ttu-id="9712b-434">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-434">Event ID</span></span>|<span data-ttu-id="9712b-435">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="9712b-436">14</span><span class="sxs-lookup"><span data-stu-id="9712b-436">14</span></span>|<span data-ttu-id="9712b-437">Zahájení spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="9712b-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="9712b-438">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="9712b-438">No event data.</span></span>  
  
 [<span data-ttu-id="9712b-439">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="9712b-440">GCFinalizersEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="9712b-441">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-442">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-442">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-443">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-443">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-444">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-444">(0x1)</span></span>|<span data-ttu-id="9712b-445">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-446">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-447">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-447">Event</span></span>|<span data-ttu-id="9712b-448">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-448">Event ID</span></span>|<span data-ttu-id="9712b-449">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="9712b-450">13</span><span class="sxs-lookup"><span data-stu-id="9712b-450">13</span></span>|<span data-ttu-id="9712b-451">Konec spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="9712b-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="9712b-452">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="9712b-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9712b-453">Název pole</span><span class="sxs-lookup"><span data-stu-id="9712b-453">Field name</span></span>|<span data-ttu-id="9712b-454">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9712b-454">Data type</span></span>|<span data-ttu-id="9712b-455">Popis</span><span class="sxs-lookup"><span data-stu-id="9712b-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9712b-456">Počet</span><span class="sxs-lookup"><span data-stu-id="9712b-456">Count</span></span>|<span data-ttu-id="9712b-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="9712b-457">win:UInt32</span></span>|<span data-ttu-id="9712b-458">Počet finalizační metody, které byly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="9712b-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="9712b-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9712b-459">ClrInstanceID</span></span>|<span data-ttu-id="9712b-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="9712b-460">win:UInt16</span></span>|<span data-ttu-id="9712b-461">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9712b-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9712b-462">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="9712b-463">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9712b-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="9712b-464">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-465">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-465">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-466">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-466">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-467">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-467">(0x1)</span></span>|<span data-ttu-id="9712b-468">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-468">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="9712b-469">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="9712b-469">(0x10000)</span></span>|<span data-ttu-id="9712b-470">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-471">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-472">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-472">Event</span></span>|<span data-ttu-id="9712b-473">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-473">Event ID</span></span>|<span data-ttu-id="9712b-474">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="9712b-475">11</span><span class="sxs-lookup"><span data-stu-id="9712b-475">11</span></span>|<span data-ttu-id="9712b-476">Souběžné uvolňování paměti kolekce vlákno bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="9712b-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="9712b-477">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="9712b-477">No event data.</span></span>  
  
 [<span data-ttu-id="9712b-478">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="9712b-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="9712b-479">GCTerminateConcurrentThread_V1 události</span><span class="sxs-lookup"><span data-stu-id="9712b-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="9712b-480">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="9712b-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9712b-481">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9712b-481">Keyword for raising the event</span></span>|<span data-ttu-id="9712b-482">úroveň</span><span class="sxs-lookup"><span data-stu-id="9712b-482">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="9712b-483">(0x1)</span><span class="sxs-lookup"><span data-stu-id="9712b-483">(0x1)</span></span>|<span data-ttu-id="9712b-484">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-484">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="9712b-485">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="9712b-485">(0x10000)</span></span>|<span data-ttu-id="9712b-486">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="9712b-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="9712b-487">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="9712b-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9712b-488">Událost</span><span class="sxs-lookup"><span data-stu-id="9712b-488">Event</span></span>|<span data-ttu-id="9712b-489">ID události</span><span class="sxs-lookup"><span data-stu-id="9712b-489">Event ID</span></span>|<span data-ttu-id="9712b-490">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9712b-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="9712b-491">12</span><span class="sxs-lookup"><span data-stu-id="9712b-491">12</span></span>|<span data-ttu-id="9712b-492">Vlákno souběžné uvolňování paměti byla ukončena.</span><span class="sxs-lookup"><span data-stu-id="9712b-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="9712b-493">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="9712b-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9712b-494">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9712b-494">See also</span></span>

- [<span data-ttu-id="9712b-495">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="9712b-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
