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
ms.openlocfilehash: 95762cbda4a1a251dd64fd33b2815d474f1fe2b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685214"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="d35f3-102">Události Trasování událostí pro Windows kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="d35f3-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="d35f3-103">Tyto události shromažďovat informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="d35f3-104">Pomáhají v Diagnostika a ladění, včetně určení, kolikrát uvolňování paměti byla provedena, kolik paměti byl uvolněn při uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d35f3-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="d35f3-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="d35f3-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="d35f3-106">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="d35f3-107">GCEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="d35f3-108">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="d35f3-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="d35f3-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="d35f3-111">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="d35f3-112">GCRestartEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="d35f3-113">GCSuspendEE_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="d35f3-114">GCSuspendEEEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="d35f3-115">GCAllocationTick_V2 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="d35f3-116">GCFinalizersBegin_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="d35f3-117">GCFinalizersEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="d35f3-118">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="d35f3-119">GCTerminateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="d35f3-120">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="d35f3-121">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="d35f3-122">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d35f3-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d35f3-123">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-123">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-124">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-126">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-127">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-128">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-128">Event</span></span>|<span data-ttu-id="d35f3-129">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-129">Event ID</span></span>|<span data-ttu-id="d35f3-130">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="d35f3-131">1</span><span class="sxs-lookup"><span data-stu-id="d35f3-131">1</span></span>|<span data-ttu-id="d35f3-132">Uvolňování paměti byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="d35f3-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="d35f3-133">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-134">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-134">Field name</span></span>|<span data-ttu-id="d35f3-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-135">Data type</span></span>|<span data-ttu-id="d35f3-136">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-137">Počet</span><span class="sxs-lookup"><span data-stu-id="d35f3-137">Count</span></span>|<span data-ttu-id="d35f3-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-138">win:UInt32</span></span>|<span data-ttu-id="d35f3-139">*n*th uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="d35f3-140">Hloubka</span><span class="sxs-lookup"><span data-stu-id="d35f3-140">Depth</span></span>|<span data-ttu-id="d35f3-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-141">win:UInt32</span></span>|<span data-ttu-id="d35f3-142">Generování, jež jsou shromažďována.</span><span class="sxs-lookup"><span data-stu-id="d35f3-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="d35f3-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="d35f3-143">Reason</span></span>|<span data-ttu-id="d35f3-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-144">win:UInt32</span></span>|<span data-ttu-id="d35f3-145">Proč byla aktivována. uvolnění:</span><span class="sxs-lookup"><span data-stu-id="d35f3-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="d35f3-146">0x0 - přidělení haldy malých objektů.</span><span class="sxs-lookup"><span data-stu-id="d35f3-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="d35f3-147">0x1 - vyvolaných.</span><span class="sxs-lookup"><span data-stu-id="d35f3-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="d35f3-148">0x2 - nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="d35f3-149">0x3 - prázdný.</span><span class="sxs-lookup"><span data-stu-id="d35f3-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="d35f3-150">0x4 - přidělení haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="d35f3-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="d35f3-151">0x5 - nedostatek místa (pro haldu malých objektů).</span><span class="sxs-lookup"><span data-stu-id="d35f3-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="d35f3-152">0x6 - nedostatek místa (pro haldu velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="d35f3-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="d35f3-153">0x7 - vyvolané, ale nejsou vynucené jako blokování.</span><span class="sxs-lookup"><span data-stu-id="d35f3-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="d35f3-154">Typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-154">Type</span></span>|<span data-ttu-id="d35f3-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-155">win:UInt32</span></span>|<span data-ttu-id="d35f3-156">0x0 - mimo uvolňování paměti na pozadí došlo k blokování uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="d35f3-157">0x1 – uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="d35f3-158">0x2 - blokující uvolňování paměti došlo k chybě během uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="d35f3-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-159">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-160">win:UInt16</span></span>|<span data-ttu-id="d35f3-161">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d35f3-162">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="d35f3-163">GCEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="d35f3-164">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-165">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-165">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-166">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-168">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-169">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-170">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-170">Event</span></span>|<span data-ttu-id="d35f3-171">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-171">Event ID</span></span>|<span data-ttu-id="d35f3-172">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="d35f3-173">2</span><span class="sxs-lookup"><span data-stu-id="d35f3-173">2</span></span>|<span data-ttu-id="d35f3-174">Kolekce paměti bylo již ukončeno.</span><span class="sxs-lookup"><span data-stu-id="d35f3-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="d35f3-175">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-176">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-176">Field name</span></span>|<span data-ttu-id="d35f3-177">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-177">Data type</span></span>|<span data-ttu-id="d35f3-178">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-179">Počet</span><span class="sxs-lookup"><span data-stu-id="d35f3-179">Count</span></span>|<span data-ttu-id="d35f3-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-180">win:UInt32</span></span>|<span data-ttu-id="d35f3-181">*n*th uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="d35f3-182">Hloubka</span><span class="sxs-lookup"><span data-stu-id="d35f3-182">Depth</span></span>|<span data-ttu-id="d35f3-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-183">win:UInt32</span></span>|<span data-ttu-id="d35f3-184">Generace, která byla shromážděna.</span><span class="sxs-lookup"><span data-stu-id="d35f3-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="d35f3-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-185">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-186">win:UInt16</span></span>|<span data-ttu-id="d35f3-187">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d35f3-188">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="d35f3-189">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="d35f3-190">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-191">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-191">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-192">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-194">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-195">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-196">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-196">Event</span></span>|<span data-ttu-id="d35f3-197">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-197">Event ID</span></span>|<span data-ttu-id="d35f3-198">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="d35f3-199">4</span><span class="sxs-lookup"><span data-stu-id="d35f3-199">4</span></span>|<span data-ttu-id="d35f3-200">Zobrazuje statistiku haldě na konci každé uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="d35f3-201">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-202">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-202">Field name</span></span>|<span data-ttu-id="d35f3-203">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-203">Data type</span></span>|<span data-ttu-id="d35f3-204">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="d35f3-205">GenerationSize0</span></span>|<span data-ttu-id="d35f3-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-206">win:UInt64</span></span>|<span data-ttu-id="d35f3-207">Velikost v bajtech paměti generace 0.</span><span class="sxs-lookup"><span data-stu-id="d35f3-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="d35f3-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="d35f3-208">TotalPromotedSize0</span></span>|<span data-ttu-id="d35f3-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-209">win:UInt64</span></span>|<span data-ttu-id="d35f3-210">Počet bajtů, které jsou přesunuty z 0. generace do 1. generace.</span><span class="sxs-lookup"><span data-stu-id="d35f3-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="d35f3-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="d35f3-211">GenerationSize1</span></span>|<span data-ttu-id="d35f3-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-212">win:UInt64</span></span>|<span data-ttu-id="d35f3-213">Velikost v bajtech paměti generace 1.</span><span class="sxs-lookup"><span data-stu-id="d35f3-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="d35f3-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="d35f3-214">TotalPromotedSize1</span></span>|<span data-ttu-id="d35f3-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-215">win:UInt64</span></span>|<span data-ttu-id="d35f3-216">Počet bajtů, které jsou přesunuty z 1. generace do 2. generace.</span><span class="sxs-lookup"><span data-stu-id="d35f3-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="d35f3-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="d35f3-217">GenerationSize2</span></span>|<span data-ttu-id="d35f3-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-218">win:UInt64</span></span>|<span data-ttu-id="d35f3-219">Velikost v bajtech paměti generace 2.</span><span class="sxs-lookup"><span data-stu-id="d35f3-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="d35f3-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="d35f3-220">TotalPromotedSize2</span></span>|<span data-ttu-id="d35f3-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-221">win:UInt64</span></span>|<span data-ttu-id="d35f3-222">Počet bajtů, které zůstat naživu v generaci 2 po poslední.</span><span class="sxs-lookup"><span data-stu-id="d35f3-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="d35f3-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="d35f3-223">GenerationSize3</span></span>|<span data-ttu-id="d35f3-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-224">win:UInt64</span></span>|<span data-ttu-id="d35f3-225">Velikost v bajtech, velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="d35f3-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="d35f3-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="d35f3-226">TotalPromotedSize3</span></span>|<span data-ttu-id="d35f3-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-227">win:UInt64</span></span>|<span data-ttu-id="d35f3-228">Počet bajtů, které zůstat naživu haldy velkých objektů po poslední.</span><span class="sxs-lookup"><span data-stu-id="d35f3-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="d35f3-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="d35f3-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="d35f3-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-230">win:UInt64</span></span>|<span data-ttu-id="d35f3-231">Celková velikost v bajtech, objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="d35f3-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="d35f3-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="d35f3-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="d35f3-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-233">win:UInt64</span></span>|<span data-ttu-id="d35f3-234">Počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="d35f3-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="d35f3-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="d35f3-235">PinnedObjectCount</span></span>|<span data-ttu-id="d35f3-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-236">win:UInt32</span></span>|<span data-ttu-id="d35f3-237">Počet připojených objektů (o nepřesunutelnou).</span><span class="sxs-lookup"><span data-stu-id="d35f3-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="d35f3-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="d35f3-238">SinkBlockCount</span></span>|<span data-ttu-id="d35f3-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-239">win:UInt32</span></span>|<span data-ttu-id="d35f3-240">Počet bloků synchronizace používá.</span><span class="sxs-lookup"><span data-stu-id="d35f3-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="d35f3-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="d35f3-241">GCHandleCount</span></span>|<span data-ttu-id="d35f3-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-242">win:UInt32</span></span>|<span data-ttu-id="d35f3-243">Počet uvolňování zpracovává používá.</span><span class="sxs-lookup"><span data-stu-id="d35f3-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="d35f3-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-244">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-245">win:UInt16</span></span>|<span data-ttu-id="d35f3-246">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d35f3-247">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="d35f3-248">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="d35f3-249">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-250">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-250">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-251">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-253">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-254">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-255">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-255">Event</span></span>|<span data-ttu-id="d35f3-256">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-256">Event ID</span></span>|<span data-ttu-id="d35f3-257">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="d35f3-258">5</span><span class="sxs-lookup"><span data-stu-id="d35f3-258">5</span></span>|<span data-ttu-id="d35f3-259">Vytvořil se nový segment kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="d35f3-260">Kromě toho když je povoleno trasování procesu, který je již spuštěn, tato událost je aktivována pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="d35f3-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="d35f3-261">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-262">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-262">Field name</span></span>|<span data-ttu-id="d35f3-263">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-263">Data type</span></span>|<span data-ttu-id="d35f3-264">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-265">Adresa</span><span class="sxs-lookup"><span data-stu-id="d35f3-265">Address</span></span>|<span data-ttu-id="d35f3-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-266">win:UInt64</span></span>|<span data-ttu-id="d35f3-267">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="d35f3-267">The address of the segment.</span></span>|  
|<span data-ttu-id="d35f3-268">Velikost</span><span class="sxs-lookup"><span data-stu-id="d35f3-268">Size</span></span>|<span data-ttu-id="d35f3-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-269">win:UInt64</span></span>|<span data-ttu-id="d35f3-270">Velikost segmentu.</span><span class="sxs-lookup"><span data-stu-id="d35f3-270">The size of the segment.</span></span>|  
|<span data-ttu-id="d35f3-271">Typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-271">Type</span></span>|<span data-ttu-id="d35f3-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-272">win:UInt32</span></span>|<span data-ttu-id="d35f3-273">0x0 - haldy malých objektů.</span><span class="sxs-lookup"><span data-stu-id="d35f3-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="d35f3-274">0x1 - velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="d35f3-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="d35f3-275">0x2 - haldy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d35f3-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="d35f3-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-276">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-277">win:UInt16</span></span>|<span data-ttu-id="d35f3-278">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="d35f3-279">Mějte na paměti, že velikost segmentů přidělaná systému uvolňování paměti je specifický pro implementaci a může se změnit kdykoli, včetně v pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="d35f3-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="d35f3-280">Vaše aplikace by nikdy vytvořit předpoklady o nebo závisí na velikosti konkrétního segmentu, ani snažit konfigurace množství paměti k přidělení segmentu.</span><span class="sxs-lookup"><span data-stu-id="d35f3-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="d35f3-281">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="d35f3-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="d35f3-283">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-284">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-284">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-285">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-287">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-288">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-289">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-289">Event</span></span>|<span data-ttu-id="d35f3-290">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-290">Event ID</span></span>|<span data-ttu-id="d35f3-291">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="d35f3-292">6</span><span class="sxs-lookup"><span data-stu-id="d35f3-292">6</span></span>|<span data-ttu-id="d35f3-293">Segment uvolňování paměti kolekce byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="d35f3-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="d35f3-294">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-295">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-295">Field name</span></span>|<span data-ttu-id="d35f3-296">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-296">Data type</span></span>|<span data-ttu-id="d35f3-297">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-298">Adresa</span><span class="sxs-lookup"><span data-stu-id="d35f3-298">Address</span></span>|<span data-ttu-id="d35f3-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-299">win:UInt64</span></span>|<span data-ttu-id="d35f3-300">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="d35f3-300">The address of the segment.</span></span>|  
|<span data-ttu-id="d35f3-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-301">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-302">win:UInt16</span></span>|<span data-ttu-id="d35f3-303">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d35f3-304">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="d35f3-305">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="d35f3-306">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-307">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-307">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-308">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-310">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-311">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-312">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-312">Event</span></span>|<span data-ttu-id="d35f3-313">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-313">Event ID</span></span>|<span data-ttu-id="d35f3-314">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="d35f3-315">7</span><span class="sxs-lookup"><span data-stu-id="d35f3-315">7</span></span>|<span data-ttu-id="d35f3-316">Bylo zahájeno obnovení z common language runtime pozastavení.</span><span class="sxs-lookup"><span data-stu-id="d35f3-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="d35f3-317">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="d35f3-317">No event data.</span></span>  
  
 [<span data-ttu-id="d35f3-318">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="d35f3-319">GCRestartEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="d35f3-320">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-321">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-321">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-322">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-324">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-325">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-326">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-326">Event</span></span>|<span data-ttu-id="d35f3-327">Id události</span><span class="sxs-lookup"><span data-stu-id="d35f3-327">Event Id</span></span>|<span data-ttu-id="d35f3-328">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="d35f3-329">3</span><span class="sxs-lookup"><span data-stu-id="d35f3-329">3</span></span>|<span data-ttu-id="d35f3-330">Obnovení z common language runtime pozastavení skončila.</span><span class="sxs-lookup"><span data-stu-id="d35f3-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="d35f3-331">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="d35f3-331">No event data.</span></span>  
  
 [<span data-ttu-id="d35f3-332">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="d35f3-333">GCSuspendEE_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="d35f3-334">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-335">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-335">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-336">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-338">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-339">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-340">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-340">Event</span></span>|<span data-ttu-id="d35f3-341">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-341">Event ID</span></span>|<span data-ttu-id="d35f3-342">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="d35f3-343">9</span><span class="sxs-lookup"><span data-stu-id="d35f3-343">9</span></span>|<span data-ttu-id="d35f3-344">Začátek pozastavení prováděcí modul pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="d35f3-345">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-346">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-346">Field name</span></span>|<span data-ttu-id="d35f3-347">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-347">Data type</span></span>|<span data-ttu-id="d35f3-348">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-349">Důvod</span><span class="sxs-lookup"><span data-stu-id="d35f3-349">Reason</span></span>|<span data-ttu-id="d35f3-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-350">win:UInt16</span></span>|<span data-ttu-id="d35f3-351">0x0 – ostatní.</span><span class="sxs-lookup"><span data-stu-id="d35f3-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="d35f3-352">0x1 – uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="d35f3-353">0x2 – ukončení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d35f3-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="d35f3-354">0x3 - pitching kódu.</span><span class="sxs-lookup"><span data-stu-id="d35f3-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="d35f3-355">0x4 – vypnutí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="d35f3-356">0x5 – ladicí program.</span><span class="sxs-lookup"><span data-stu-id="d35f3-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="d35f3-357">0x6 – Příprava pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="d35f3-358">Počet</span><span class="sxs-lookup"><span data-stu-id="d35f3-358">Count</span></span>|<span data-ttu-id="d35f3-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-359">win:UInt32</span></span>|<span data-ttu-id="d35f3-360">Uvolňování paměti – počet v době.</span><span class="sxs-lookup"><span data-stu-id="d35f3-360">The GC count at the time.</span></span> <span data-ttu-id="d35f3-361">Obvykle zobrazí následující události Start uvolňování paměti po to a její vlastnosti Count by tento počet + 1 jsme zvýšit index uvolňování paměti během uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="d35f3-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-362">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-363">win:UInt16</span></span>|<span data-ttu-id="d35f3-364">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d35f3-365">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="d35f3-366">GCSuspendEEEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="d35f3-367">V následující tabulce jsou uvedeny – klíčové slovo a úroveň:</span><span class="sxs-lookup"><span data-stu-id="d35f3-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="d35f3-368">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-368">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-369">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-371">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-372">V následující tabulce jsou uvedeny informace o události:</span><span class="sxs-lookup"><span data-stu-id="d35f3-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="d35f3-373">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-373">Event</span></span>|<span data-ttu-id="d35f3-374">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-374">Event ID</span></span>|<span data-ttu-id="d35f3-375">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="d35f3-376">8</span><span class="sxs-lookup"><span data-stu-id="d35f3-376">8</span></span>|<span data-ttu-id="d35f3-377">Konec pozastavení prováděcí modul pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d35f3-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="d35f3-378">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="d35f3-378">No event data.</span></span>  
  
 [<span data-ttu-id="d35f3-379">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="d35f3-380">GCAllocationTick_V2 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="d35f3-381">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-382">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-382">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-383">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-385">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-386">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-387">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-387">Event</span></span>|<span data-ttu-id="d35f3-388">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-388">Event ID</span></span>|<span data-ttu-id="d35f3-389">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="d35f3-390">10</span><span class="sxs-lookup"><span data-stu-id="d35f3-390">10</span></span>|<span data-ttu-id="d35f3-391">Pokaždé, když je přidělen přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="d35f3-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="d35f3-392">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-393">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-393">Field name</span></span>|<span data-ttu-id="d35f3-394">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-394">Data type</span></span>|<span data-ttu-id="d35f3-395">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="d35f3-396">AllocationAmount</span></span>|<span data-ttu-id="d35f3-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-397">win:UInt32</span></span>|<span data-ttu-id="d35f3-398">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d35f3-398">The allocation size, in bytes.</span></span> <span data-ttu-id="d35f3-399">Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4,294,967,295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="d35f3-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="d35f3-400">Pokud přidělení paměti je větší, toto pole obsahuje zkrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="d35f3-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="d35f3-401">Použití `AllocationAmount64` velmi velkého přidělení.</span><span class="sxs-lookup"><span data-stu-id="d35f3-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="d35f3-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="d35f3-402">AllocationKind</span></span>|<span data-ttu-id="d35f3-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-403">win:UInt32</span></span>|<span data-ttu-id="d35f3-404">0x0 - přidělení malých objektů (přidělení je haldy malých objektů).</span><span class="sxs-lookup"><span data-stu-id="d35f3-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="d35f3-405">0x1 – rozdělení velkých objektů (přidělení je v haldy velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="d35f3-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="d35f3-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-406">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-407">win:UInt16</span></span>|<span data-ttu-id="d35f3-408">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="d35f3-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="d35f3-409">AllocationAmount64</span></span>|<span data-ttu-id="d35f3-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="d35f3-410">win:UInt64</span></span>|<span data-ttu-id="d35f3-411">Přidělení velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d35f3-411">The allocation size, in bytes.</span></span> <span data-ttu-id="d35f3-412">Tato hodnota je přesné pro velmi velkého přidělení.</span><span class="sxs-lookup"><span data-stu-id="d35f3-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="d35f3-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="d35f3-413">TypeId</span></span>|<span data-ttu-id="d35f3-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="d35f3-414">win:Pointer</span></span>|<span data-ttu-id="d35f3-415">Adresa MethodTable.</span><span class="sxs-lookup"><span data-stu-id="d35f3-415">The address of the MethodTable.</span></span> <span data-ttu-id="d35f3-416">Když existuje několik typů objektů, které byly přiděleny během této události, jde o adresu MethodTable, která odpovídá na poslední objekt přidělený (objekt, který způsobil překročení prahovou hodnotu 100 KB).</span><span class="sxs-lookup"><span data-stu-id="d35f3-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="d35f3-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="d35f3-417">TypeName</span></span>|<span data-ttu-id="d35f3-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="d35f3-418">win:UnicodeString</span></span>|<span data-ttu-id="d35f3-419">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="d35f3-419">The name of the type that was allocated.</span></span> <span data-ttu-id="d35f3-420">Když existuje několik typů objektů, které byly přiděleny během této události, toto je typ objektu poslední přidělené (objekt, který způsobil překročení prahovou hodnotu 100 KB).</span><span class="sxs-lookup"><span data-stu-id="d35f3-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="d35f3-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="d35f3-421">HeapIndex</span></span>|<span data-ttu-id="d35f3-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-422">win:UInt32</span></span>|<span data-ttu-id="d35f3-423">Haldy, ve kterém byla objektu přidělena.</span><span class="sxs-lookup"><span data-stu-id="d35f3-423">The heap where the object was allocated.</span></span> <span data-ttu-id="d35f3-424">Tato hodnota je 0 (nula), když budou běžet s uvolnění paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="d35f3-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="d35f3-425">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="d35f3-426">GCFinalizersBegin_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="d35f3-427">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-428">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-428">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-429">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-431">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-432">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-433">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-433">Event</span></span>|<span data-ttu-id="d35f3-434">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-434">Event ID</span></span>|<span data-ttu-id="d35f3-435">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="d35f3-436">14</span><span class="sxs-lookup"><span data-stu-id="d35f3-436">14</span></span>|<span data-ttu-id="d35f3-437">Zahájení spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d35f3-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="d35f3-438">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="d35f3-438">No event data.</span></span>  
  
 [<span data-ttu-id="d35f3-439">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="d35f3-440">GCFinalizersEnd_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="d35f3-441">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-442">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-442">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-443">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-445">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-446">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-447">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-447">Event</span></span>|<span data-ttu-id="d35f3-448">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-448">Event ID</span></span>|<span data-ttu-id="d35f3-449">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="d35f3-450">13</span><span class="sxs-lookup"><span data-stu-id="d35f3-450">13</span></span>|<span data-ttu-id="d35f3-451">Konec spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d35f3-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="d35f3-452">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="d35f3-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d35f3-453">Název pole</span><span class="sxs-lookup"><span data-stu-id="d35f3-453">Field name</span></span>|<span data-ttu-id="d35f3-454">Datový typ</span><span class="sxs-lookup"><span data-stu-id="d35f3-454">Data type</span></span>|<span data-ttu-id="d35f3-455">Popis</span><span class="sxs-lookup"><span data-stu-id="d35f3-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d35f3-456">Počet</span><span class="sxs-lookup"><span data-stu-id="d35f3-456">Count</span></span>|<span data-ttu-id="d35f3-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="d35f3-457">win:UInt32</span></span>|<span data-ttu-id="d35f3-458">Počet finalizační metody, které byly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="d35f3-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="d35f3-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d35f3-459">ClrInstanceID</span></span>|<span data-ttu-id="d35f3-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="d35f3-460">win:UInt16</span></span>|<span data-ttu-id="d35f3-461">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d35f3-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d35f3-462">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="d35f3-463">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="d35f3-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="d35f3-464">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-465">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-465">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-466">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-468">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-468">Informational (4)</span></span>|  
|<span data-ttu-id="d35f3-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d35f3-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d35f3-470">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-471">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-472">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-472">Event</span></span>|<span data-ttu-id="d35f3-473">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-473">Event ID</span></span>|<span data-ttu-id="d35f3-474">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="d35f3-475">11</span><span class="sxs-lookup"><span data-stu-id="d35f3-475">11</span></span>|<span data-ttu-id="d35f3-476">Souběžné uvolňování paměti kolekce vlákno bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="d35f3-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="d35f3-477">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="d35f3-477">No event data.</span></span>  
  
 [<span data-ttu-id="d35f3-478">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d35f3-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="d35f3-479">GCTerminateConcurrentThread_V1 události</span><span class="sxs-lookup"><span data-stu-id="d35f3-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="d35f3-480">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="d35f3-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d35f3-481">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="d35f3-481">Keyword for raising the event</span></span>|<span data-ttu-id="d35f3-482">úroveň</span><span class="sxs-lookup"><span data-stu-id="d35f3-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d35f3-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="d35f3-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="d35f3-484">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-484">Informational (4)</span></span>|  
|<span data-ttu-id="d35f3-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="d35f3-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d35f3-486">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="d35f3-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="d35f3-487">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="d35f3-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d35f3-488">Událost</span><span class="sxs-lookup"><span data-stu-id="d35f3-488">Event</span></span>|<span data-ttu-id="d35f3-489">ID události</span><span class="sxs-lookup"><span data-stu-id="d35f3-489">Event ID</span></span>|<span data-ttu-id="d35f3-490">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="d35f3-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="d35f3-491">12</span><span class="sxs-lookup"><span data-stu-id="d35f3-491">12</span></span>|<span data-ttu-id="d35f3-492">Vlákno souběžné uvolňování paměti byla ukončena.</span><span class="sxs-lookup"><span data-stu-id="d35f3-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="d35f3-493">Žádná data.</span><span class="sxs-lookup"><span data-stu-id="d35f3-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35f3-494">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d35f3-494">See also</span></span>
- [<span data-ttu-id="d35f3-495">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="d35f3-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
