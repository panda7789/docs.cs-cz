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
ms.openlocfilehash: ec90d022a0c72782f413a84b6fbd2c1b8d663a73
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046495"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="de670-102">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="de670-102">Garbage Collection ETW Events</span></span>
<a name="top"></a><span data-ttu-id="de670-103">Tyto události shromažďují informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="de670-104">Pomáhá při diagnostice a ladění, včetně určení počtu provedených uvolnění paměti, o tom, kolik paměti bylo uvolněno během uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="de670-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="de670-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="de670-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="de670-106">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
- [<span data-ttu-id="de670-107">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
- [<span data-ttu-id="de670-108">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
- [<span data-ttu-id="de670-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
- [<span data-ttu-id="de670-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
- [<span data-ttu-id="de670-111">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
- [<span data-ttu-id="de670-112">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
- [<span data-ttu-id="de670-113">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="de670-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
- [<span data-ttu-id="de670-114">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
- [<span data-ttu-id="de670-115">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="de670-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
- [<span data-ttu-id="de670-116">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="de670-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
- [<span data-ttu-id="de670-117">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
- [<span data-ttu-id="de670-118">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
- [<span data-ttu-id="de670-119">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="de670-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstart_v1-event"></a><span data-ttu-id="de670-120">Událost GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="de670-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="de670-121">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="de670-122">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="de670-122">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="de670-123">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-123">Keyword for raising the event</span></span>|<span data-ttu-id="de670-124">Level</span><span class="sxs-lookup"><span data-stu-id="de670-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-126">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-127">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-128">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-128">Event</span></span>|<span data-ttu-id="de670-129">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-129">Event ID</span></span>|<span data-ttu-id="de670-130">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="de670-131">1</span><span class="sxs-lookup"><span data-stu-id="de670-131">1</span></span>|<span data-ttu-id="de670-132">Bylo zahájeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="de670-133">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-134">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-134">Field name</span></span>|<span data-ttu-id="de670-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-135">Data type</span></span>|<span data-ttu-id="de670-136">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-137">Count</span><span class="sxs-lookup"><span data-stu-id="de670-137">Count</span></span>|<span data-ttu-id="de670-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-138">win:UInt32</span></span>|<span data-ttu-id="de670-139">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="de670-140">Úrovní</span><span class="sxs-lookup"><span data-stu-id="de670-140">Depth</span></span>|<span data-ttu-id="de670-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-141">win:UInt32</span></span>|<span data-ttu-id="de670-142">Shromažďovaná generace.</span><span class="sxs-lookup"><span data-stu-id="de670-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="de670-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="de670-143">Reason</span></span>|<span data-ttu-id="de670-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-144">win:UInt32</span></span>|<span data-ttu-id="de670-145">Proč se uvolňování paměti aktivovalo:</span><span class="sxs-lookup"><span data-stu-id="de670-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="de670-146">0x0 – malé přidělení haldy objektů.</span><span class="sxs-lookup"><span data-stu-id="de670-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="de670-147">0x1 – vyvolané.</span><span class="sxs-lookup"><span data-stu-id="de670-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="de670-148">0x2 – nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="de670-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="de670-149">0x3 – prázdné.</span><span class="sxs-lookup"><span data-stu-id="de670-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="de670-150">0x4 – přidělení haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="de670-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="de670-151">0x5 – nedostatek místa (pro haldu malých objektů)</span><span class="sxs-lookup"><span data-stu-id="de670-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="de670-152">0x6 mimo prostor (pro haldu velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="de670-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="de670-153">0x7 – vyvolané, ale nevynucené jako blokující</span><span class="sxs-lookup"><span data-stu-id="de670-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="de670-154">type</span><span class="sxs-lookup"><span data-stu-id="de670-154">Type</span></span>|<span data-ttu-id="de670-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-155">win:UInt32</span></span>|<span data-ttu-id="de670-156">0x0 – blokující uvolňování paměti se nevyskytlo mimo uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="de670-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="de670-157">0x1 – uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="de670-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="de670-158">0x2 – blokující uvolňování paměti došlo během uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="de670-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="de670-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-159">ClrInstanceID</span></span>|<span data-ttu-id="de670-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-160">win:UInt16</span></span>|<span data-ttu-id="de670-161">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="de670-162">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcend_v1-event"></a><span data-ttu-id="de670-163">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="de670-164">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-165">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-165">Keyword for raising the event</span></span>|<span data-ttu-id="de670-166">Level</span><span class="sxs-lookup"><span data-stu-id="de670-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-168">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-169">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-170">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-170">Event</span></span>|<span data-ttu-id="de670-171">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-171">Event ID</span></span>|<span data-ttu-id="de670-172">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="de670-173">2</span><span class="sxs-lookup"><span data-stu-id="de670-173">2</span></span>|<span data-ttu-id="de670-174">Uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="de670-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="de670-175">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-176">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-176">Field name</span></span>|<span data-ttu-id="de670-177">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-177">Data type</span></span>|<span data-ttu-id="de670-178">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-179">Count</span><span class="sxs-lookup"><span data-stu-id="de670-179">Count</span></span>|<span data-ttu-id="de670-180">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-180">win:UInt32</span></span>|<span data-ttu-id="de670-181">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="de670-182">Úrovní</span><span class="sxs-lookup"><span data-stu-id="de670-182">Depth</span></span>|<span data-ttu-id="de670-183">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-183">win:UInt32</span></span>|<span data-ttu-id="de670-184">Shromážděná generace.</span><span class="sxs-lookup"><span data-stu-id="de670-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="de670-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-185">ClrInstanceID</span></span>|<span data-ttu-id="de670-186">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-186">win:UInt16</span></span>|<span data-ttu-id="de670-187">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="de670-188">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstats_v1-event"></a><span data-ttu-id="de670-189">Událost GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="de670-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="de670-190">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-191">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-191">Keyword for raising the event</span></span>|<span data-ttu-id="de670-192">Level</span><span class="sxs-lookup"><span data-stu-id="de670-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-194">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-195">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-196">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-196">Event</span></span>|<span data-ttu-id="de670-197">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-197">Event ID</span></span>|<span data-ttu-id="de670-198">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="de670-199">4</span><span class="sxs-lookup"><span data-stu-id="de670-199">4</span></span>|<span data-ttu-id="de670-200">Zobrazuje statistiku haldy na konci každého uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="de670-201">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-202">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-202">Field name</span></span>|<span data-ttu-id="de670-203">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-203">Data type</span></span>|<span data-ttu-id="de670-204">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="de670-205">GenerationSize0</span></span>|<span data-ttu-id="de670-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-206">win:UInt64</span></span>|<span data-ttu-id="de670-207">Velikost paměti generace 0 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="de670-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="de670-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="de670-208">TotalPromotedSize0</span></span>|<span data-ttu-id="de670-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-209">win:UInt64</span></span>|<span data-ttu-id="de670-210">Počet bajtů, které jsou povýšeny z generace 0 na generaci 1.</span><span class="sxs-lookup"><span data-stu-id="de670-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="de670-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="de670-211">GenerationSize1</span></span>|<span data-ttu-id="de670-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-212">win:UInt64</span></span>|<span data-ttu-id="de670-213">Velikost paměti 1. generace v bajtech</span><span class="sxs-lookup"><span data-stu-id="de670-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="de670-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="de670-214">TotalPromotedSize1</span></span>|<span data-ttu-id="de670-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-215">win:UInt64</span></span>|<span data-ttu-id="de670-216">Počet bajtů, které jsou povýšeny z generace 1 na generaci 2.</span><span class="sxs-lookup"><span data-stu-id="de670-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="de670-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="de670-217">GenerationSize2</span></span>|<span data-ttu-id="de670-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-218">win:UInt64</span></span>|<span data-ttu-id="de670-219">Velikost paměti generace 2 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="de670-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="de670-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="de670-220">TotalPromotedSize2</span></span>|<span data-ttu-id="de670-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-221">win:UInt64</span></span>|<span data-ttu-id="de670-222">Počet bajtů, které byly zachovány v generaci 2 po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="de670-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="de670-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="de670-223">GenerationSize3</span></span>|<span data-ttu-id="de670-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-224">win:UInt64</span></span>|<span data-ttu-id="de670-225">Velikost haldy velkých objektů v bajtech.</span><span class="sxs-lookup"><span data-stu-id="de670-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="de670-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="de670-226">TotalPromotedSize3</span></span>|<span data-ttu-id="de670-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-227">win:UInt64</span></span>|<span data-ttu-id="de670-228">Počet bajtů, které byly zachovány v haldě velkých objektů po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="de670-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="de670-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="de670-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="de670-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-230">win:UInt64</span></span>|<span data-ttu-id="de670-231">Celková velikost objektů, které jsou připraveny k dokončení, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="de670-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="de670-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="de670-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="de670-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-233">win:UInt64</span></span>|<span data-ttu-id="de670-234">Počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="de670-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="de670-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="de670-235">PinnedObjectCount</span></span>|<span data-ttu-id="de670-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-236">win:UInt32</span></span>|<span data-ttu-id="de670-237">Počet připnutých (nepohyblivých) objektů.</span><span class="sxs-lookup"><span data-stu-id="de670-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="de670-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="de670-238">SinkBlockCount</span></span>|<span data-ttu-id="de670-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-239">win:UInt32</span></span>|<span data-ttu-id="de670-240">Počet používaných synchronizačních bloků.</span><span class="sxs-lookup"><span data-stu-id="de670-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="de670-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="de670-241">GCHandleCount</span></span>|<span data-ttu-id="de670-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-242">win:UInt32</span></span>|<span data-ttu-id="de670-243">Počet používaných obslužných rutin uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="de670-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-244">ClrInstanceID</span></span>|<span data-ttu-id="de670-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-245">win:UInt16</span></span>|<span data-ttu-id="de670-246">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="de670-247">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="de670-248">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="de670-249">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-250">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-250">Keyword for raising the event</span></span>|<span data-ttu-id="de670-251">Level</span><span class="sxs-lookup"><span data-stu-id="de670-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-253">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-254">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-255">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-255">Event</span></span>|<span data-ttu-id="de670-256">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-256">Event ID</span></span>|<span data-ttu-id="de670-257">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="de670-258">5</span><span class="sxs-lookup"><span data-stu-id="de670-258">5</span></span>|<span data-ttu-id="de670-259">Vytvořil se nový segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="de670-260">Kromě toho, když je trasování povoleno na procesu, který je již spuštěn, tato událost je vyvolána pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="de670-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="de670-261">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-262">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-262">Field name</span></span>|<span data-ttu-id="de670-263">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-263">Data type</span></span>|<span data-ttu-id="de670-264">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-265">Adresa</span><span class="sxs-lookup"><span data-stu-id="de670-265">Address</span></span>|<span data-ttu-id="de670-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-266">win:UInt64</span></span>|<span data-ttu-id="de670-267">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="de670-267">The address of the segment.</span></span>|  
|<span data-ttu-id="de670-268">Velikost</span><span class="sxs-lookup"><span data-stu-id="de670-268">Size</span></span>|<span data-ttu-id="de670-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-269">win:UInt64</span></span>|<span data-ttu-id="de670-270">Velikost segmentu</span><span class="sxs-lookup"><span data-stu-id="de670-270">The size of the segment.</span></span>|  
|<span data-ttu-id="de670-271">type</span><span class="sxs-lookup"><span data-stu-id="de670-271">Type</span></span>|<span data-ttu-id="de670-272">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-272">win:UInt32</span></span>|<span data-ttu-id="de670-273">0x0 – malá halda objektu.</span><span class="sxs-lookup"><span data-stu-id="de670-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="de670-274">0x1 – halda velkých objektů</span><span class="sxs-lookup"><span data-stu-id="de670-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="de670-275">0x2 – halda jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="de670-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="de670-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-276">ClrInstanceID</span></span>|<span data-ttu-id="de670-277">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-277">win:UInt16</span></span>|<span data-ttu-id="de670-278">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="de670-279">Všimněte si, že velikost segmentů přidělených systémem uvolňování paměti je specifická pro konkrétní implementaci a může se kdykoli změnit, včetně pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="de670-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="de670-280">Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.</span><span class="sxs-lookup"><span data-stu-id="de670-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="de670-281">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="de670-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="de670-283">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-284">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-284">Keyword for raising the event</span></span>|<span data-ttu-id="de670-285">Level</span><span class="sxs-lookup"><span data-stu-id="de670-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-287">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-288">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-289">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-289">Event</span></span>|<span data-ttu-id="de670-290">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-290">Event ID</span></span>|<span data-ttu-id="de670-291">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="de670-292">6</span><span class="sxs-lookup"><span data-stu-id="de670-292">6</span></span>|<span data-ttu-id="de670-293">Byl uvolněn segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="de670-294">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-295">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-295">Field name</span></span>|<span data-ttu-id="de670-296">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-296">Data type</span></span>|<span data-ttu-id="de670-297">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-298">Adresa</span><span class="sxs-lookup"><span data-stu-id="de670-298">Address</span></span>|<span data-ttu-id="de670-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-299">win:UInt64</span></span>|<span data-ttu-id="de670-300">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="de670-300">The address of the segment.</span></span>|  
|<span data-ttu-id="de670-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-301">ClrInstanceID</span></span>|<span data-ttu-id="de670-302">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-302">win:UInt16</span></span>|<span data-ttu-id="de670-303">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="de670-304">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="de670-305">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="de670-306">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-307">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-307">Keyword for raising the event</span></span>|<span data-ttu-id="de670-308">Level</span><span class="sxs-lookup"><span data-stu-id="de670-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-310">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-311">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-312">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-312">Event</span></span>|<span data-ttu-id="de670-313">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-313">Event ID</span></span>|<span data-ttu-id="de670-314">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="de670-315">7</span><span class="sxs-lookup"><span data-stu-id="de670-315">7</span></span>|<span data-ttu-id="de670-316">Bylo zahájeno obnovení z pozastavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="de670-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="de670-317">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="de670-317">No event data.</span></span>  
  
 [<span data-ttu-id="de670-318">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="de670-319">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="de670-320">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-321">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-321">Keyword for raising the event</span></span>|<span data-ttu-id="de670-322">Level</span><span class="sxs-lookup"><span data-stu-id="de670-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-324">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-325">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-326">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-326">Event</span></span>|<span data-ttu-id="de670-327">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-327">Event Id</span></span>|<span data-ttu-id="de670-328">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="de670-329">3</span><span class="sxs-lookup"><span data-stu-id="de670-329">3</span></span>|<span data-ttu-id="de670-330">Obnovení z odložení modulu CLR (Common Language Runtime) skončilo.</span><span class="sxs-lookup"><span data-stu-id="de670-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="de670-331">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="de670-331">No event data.</span></span>  
  
 [<span data-ttu-id="de670-332">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="de670-333">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="de670-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="de670-334">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-335">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-335">Keyword for raising the event</span></span>|<span data-ttu-id="de670-336">Level</span><span class="sxs-lookup"><span data-stu-id="de670-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-338">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-339">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-340">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-340">Event</span></span>|<span data-ttu-id="de670-341">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-341">Event ID</span></span>|<span data-ttu-id="de670-342">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="de670-343">9</span><span class="sxs-lookup"><span data-stu-id="de670-343">9</span></span>|<span data-ttu-id="de670-344">Začátek pozastavení spouštěcího modulu pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="de670-345">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-346">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-346">Field name</span></span>|<span data-ttu-id="de670-347">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-347">Data type</span></span>|<span data-ttu-id="de670-348">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-349">Důvod</span><span class="sxs-lookup"><span data-stu-id="de670-349">Reason</span></span>|<span data-ttu-id="de670-350">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-350">win:UInt16</span></span>|<span data-ttu-id="de670-351">0x0 – ostatní</span><span class="sxs-lookup"><span data-stu-id="de670-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="de670-352">0x1 – uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="de670-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="de670-353">0x2 – vypnutí aplikační domény</span><span class="sxs-lookup"><span data-stu-id="de670-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="de670-354">0x3 – rozteč kódu.</span><span class="sxs-lookup"><span data-stu-id="de670-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="de670-355">0x4 – vypnutí</span><span class="sxs-lookup"><span data-stu-id="de670-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="de670-356">0x5 – ladicí program.</span><span class="sxs-lookup"><span data-stu-id="de670-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="de670-357">0x6 – příprava pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="de670-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="de670-358">Count</span><span class="sxs-lookup"><span data-stu-id="de670-358">Count</span></span>|<span data-ttu-id="de670-359">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-359">win:UInt32</span></span>|<span data-ttu-id="de670-360">Počet GC v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="de670-360">The GC count at the time.</span></span> <span data-ttu-id="de670-361">Obvykle se vám po tomto zobrazení zobrazí další počáteční událost GC a její počet by byl tento počet + 1, protože během uvolňování paměti narůstá index GC.</span><span class="sxs-lookup"><span data-stu-id="de670-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="de670-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-362">ClrInstanceID</span></span>|<span data-ttu-id="de670-363">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-363">win:UInt16</span></span>|<span data-ttu-id="de670-364">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="de670-365">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="de670-366">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="de670-367">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="de670-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="de670-368">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-368">Keyword for raising the event</span></span>|<span data-ttu-id="de670-369">Level</span><span class="sxs-lookup"><span data-stu-id="de670-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-371">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-372">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="de670-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="de670-373">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-373">Event</span></span>|<span data-ttu-id="de670-374">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-374">Event ID</span></span>|<span data-ttu-id="de670-375">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="de670-376">8</span><span class="sxs-lookup"><span data-stu-id="de670-376">8</span></span>|<span data-ttu-id="de670-377">Konec pozastavení prováděcího modulu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="de670-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="de670-378">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="de670-378">No event data.</span></span>  
  
 [<span data-ttu-id="de670-379">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="de670-380">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="de670-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="de670-381">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-382">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-382">Keyword for raising the event</span></span>|<span data-ttu-id="de670-383">Level</span><span class="sxs-lookup"><span data-stu-id="de670-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-385">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-386">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-387">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-387">Event</span></span>|<span data-ttu-id="de670-388">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-388">Event ID</span></span>|<span data-ttu-id="de670-389">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="de670-390">10</span><span class="sxs-lookup"><span data-stu-id="de670-390">10</span></span>|<span data-ttu-id="de670-391">Pokaždé, když se přidělí přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="de670-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="de670-392">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-393">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-393">Field name</span></span>|<span data-ttu-id="de670-394">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-394">Data type</span></span>|<span data-ttu-id="de670-395">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="de670-396">AllocationAmount</span></span>|<span data-ttu-id="de670-397">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-397">win:UInt32</span></span>|<span data-ttu-id="de670-398">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="de670-398">The allocation size, in bytes.</span></span> <span data-ttu-id="de670-399">Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4 294 967 295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="de670-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="de670-400">Pokud je přidělení větší, obsahuje toto pole zkrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="de670-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="de670-401">Použijte `AllocationAmount64` pro velmi velké alokace.</span><span class="sxs-lookup"><span data-stu-id="de670-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="de670-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="de670-402">AllocationKind</span></span>|<span data-ttu-id="de670-403">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-403">win:UInt32</span></span>|<span data-ttu-id="de670-404">0x0 – malé přidělení objektů (přidělení je v haldě malých objektů).</span><span class="sxs-lookup"><span data-stu-id="de670-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="de670-405">0x1 – velké přidělení objektů (přidělení je v haldě velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="de670-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="de670-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-406">ClrInstanceID</span></span>|<span data-ttu-id="de670-407">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-407">win:UInt16</span></span>|<span data-ttu-id="de670-408">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="de670-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="de670-409">AllocationAmount64</span></span>|<span data-ttu-id="de670-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="de670-410">win:UInt64</span></span>|<span data-ttu-id="de670-411">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="de670-411">The allocation size, in bytes.</span></span> <span data-ttu-id="de670-412">Tato hodnota je přesné pro velmi velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="de670-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="de670-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="de670-413">TypeId</span></span>|<span data-ttu-id="de670-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="de670-414">win:Pointer</span></span>|<span data-ttu-id="de670-415">Adresa metody.</span><span class="sxs-lookup"><span data-stu-id="de670-415">The address of the MethodTable.</span></span> <span data-ttu-id="de670-416">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o adresu metody, která odpovídá poslednímu přidělenému objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="de670-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="de670-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="de670-417">TypeName</span></span>|<span data-ttu-id="de670-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="de670-418">win:UnicodeString</span></span>|<span data-ttu-id="de670-419">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="de670-419">The name of the type that was allocated.</span></span> <span data-ttu-id="de670-420">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ posledního přiděleného objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="de670-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="de670-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="de670-421">HeapIndex</span></span>|<span data-ttu-id="de670-422">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-422">win:UInt32</span></span>|<span data-ttu-id="de670-423">Halda, ve které byl objekt přidělen.</span><span class="sxs-lookup"><span data-stu-id="de670-423">The heap where the object was allocated.</span></span> <span data-ttu-id="de670-424">Tato hodnota je 0 (nula) při spuštění s uvolňováním paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="de670-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="de670-425">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="de670-426">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="de670-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="de670-427">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-428">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-428">Keyword for raising the event</span></span>|<span data-ttu-id="de670-429">Level</span><span class="sxs-lookup"><span data-stu-id="de670-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-431">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-432">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-433">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-433">Event</span></span>|<span data-ttu-id="de670-434">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-434">Event ID</span></span>|<span data-ttu-id="de670-435">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="de670-436">14</span><span class="sxs-lookup"><span data-stu-id="de670-436">14</span></span>|<span data-ttu-id="de670-437">Začátek spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="de670-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="de670-438">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="de670-438">No event data.</span></span>  
  
 [<span data-ttu-id="de670-439">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="de670-440">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="de670-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="de670-441">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-442">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-442">Keyword for raising the event</span></span>|<span data-ttu-id="de670-443">Level</span><span class="sxs-lookup"><span data-stu-id="de670-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-445">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-446">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-447">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-447">Event</span></span>|<span data-ttu-id="de670-448">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-448">Event ID</span></span>|<span data-ttu-id="de670-449">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="de670-450">13</span><span class="sxs-lookup"><span data-stu-id="de670-450">13</span></span>|<span data-ttu-id="de670-451">Konec spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="de670-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="de670-452">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="de670-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="de670-453">Název pole</span><span class="sxs-lookup"><span data-stu-id="de670-453">Field name</span></span>|<span data-ttu-id="de670-454">Datový typ</span><span class="sxs-lookup"><span data-stu-id="de670-454">Data type</span></span>|<span data-ttu-id="de670-455">Popis</span><span class="sxs-lookup"><span data-stu-id="de670-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="de670-456">Count</span><span class="sxs-lookup"><span data-stu-id="de670-456">Count</span></span>|<span data-ttu-id="de670-457">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="de670-457">win:UInt32</span></span>|<span data-ttu-id="de670-458">Počet finalizační metody, které byly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="de670-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="de670-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="de670-459">ClrInstanceID</span></span>|<span data-ttu-id="de670-460">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="de670-460">win:UInt16</span></span>|<span data-ttu-id="de670-461">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="de670-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="de670-462">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="de670-463">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="de670-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="de670-464">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-465">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-465">Keyword for raising the event</span></span>|<span data-ttu-id="de670-466">Level</span><span class="sxs-lookup"><span data-stu-id="de670-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-468">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-468">Informational (4)</span></span>|  
|<span data-ttu-id="de670-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="de670-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="de670-470">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-471">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-472">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-472">Event</span></span>|<span data-ttu-id="de670-473">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-473">Event ID</span></span>|<span data-ttu-id="de670-474">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="de670-475">11</span><span class="sxs-lookup"><span data-stu-id="de670-475">11</span></span>|<span data-ttu-id="de670-476">Bylo vytvořeno souběžné vlákno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="de670-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="de670-477">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="de670-477">No event data.</span></span>  
  
 [<span data-ttu-id="de670-478">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="de670-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="de670-479">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="de670-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="de670-480">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="de670-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="de670-481">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="de670-481">Keyword for raising the event</span></span>|<span data-ttu-id="de670-482">Level</span><span class="sxs-lookup"><span data-stu-id="de670-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="de670-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="de670-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="de670-484">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-484">Informational (4)</span></span>|  
|<span data-ttu-id="de670-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="de670-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="de670-486">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="de670-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="de670-487">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="de670-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="de670-488">Událost</span><span class="sxs-lookup"><span data-stu-id="de670-488">Event</span></span>|<span data-ttu-id="de670-489">ID události</span><span class="sxs-lookup"><span data-stu-id="de670-489">Event ID</span></span>|<span data-ttu-id="de670-490">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="de670-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="de670-491">12</span><span class="sxs-lookup"><span data-stu-id="de670-491">12</span></span>|<span data-ttu-id="de670-492">Vlákno souběžného uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="de670-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="de670-493">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="de670-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de670-494">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de670-494">See also</span></span>

- [<span data-ttu-id="de670-495">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="de670-495">CLR ETW Events</span></span>](clr-etw-events.md)
