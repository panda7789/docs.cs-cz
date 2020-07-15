---
title: Události Trasování událostí pro Windows uvolnění paměti
description: Zobrazí podrobné informace o událostech ETW pro uvolňování paměti. Mezi zahrnuté události patří GCStart_V1, GCEnd_V1, GCHeapStats_V1, GCCreateSegment_V1 a další.
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309739"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="0f0a3-104">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="0f0a3-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="0f0a3-105">Tyto události shromažďují informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="0f0a3-106">Pomáhá při diagnostice a ladění, včetně určení počtu provedených uvolnění paměti, o tom, kolik paměti bylo uvolněno během uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="0f0a3-107">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="0f0a3-108">Událost GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="0f0a3-109">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="0f0a3-110">Událost GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="0f0a3-111">Událost GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-111">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="0f0a3-112">Událost GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-112">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="0f0a3-113">Událost GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-113">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="0f0a3-114">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-114">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="0f0a3-115">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-115">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="0f0a3-116">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-116">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="0f0a3-117">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="0f0a3-117">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="0f0a3-118">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-118">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="0f0a3-119">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-119">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="0f0a3-120">Událost GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-120">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="0f0a3-121">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-121">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="0f0a3-122">Událost GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-122">GCStart_V1 Event</span></span>  

<span data-ttu-id="0f0a3-123">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-123">The following table shows the keyword and level.</span></span> <span data-ttu-id="0f0a3-124">Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-124">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="0f0a3-125">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-125">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-126">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-127">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-127">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-128">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-128">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-129">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-129">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-130">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-130">Event</span></span>|<span data-ttu-id="0f0a3-131">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-131">Event ID</span></span>|<span data-ttu-id="0f0a3-132">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="0f0a3-133">1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-133">1</span></span>|<span data-ttu-id="0f0a3-134">Bylo zahájeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-134">A garbage collection has started.</span></span>|

<span data-ttu-id="0f0a3-135">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-135">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-136">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-136">Field name</span></span>|<span data-ttu-id="0f0a3-137">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-137">Data type</span></span>|<span data-ttu-id="0f0a3-138">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-138">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-139">Count</span><span class="sxs-lookup"><span data-stu-id="0f0a3-139">Count</span></span>|<span data-ttu-id="0f0a3-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-140">win:UInt32</span></span>|<span data-ttu-id="0f0a3-141">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-141">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="0f0a3-142">Úrovní</span><span class="sxs-lookup"><span data-stu-id="0f0a3-142">Depth</span></span>|<span data-ttu-id="0f0a3-143">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-143">win:UInt32</span></span>|<span data-ttu-id="0f0a3-144">Shromažďovaná generace.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-144">The generation that is being collected.</span></span>|
|<span data-ttu-id="0f0a3-145">Důvod</span><span class="sxs-lookup"><span data-stu-id="0f0a3-145">Reason</span></span>|<span data-ttu-id="0f0a3-146">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-146">win:UInt32</span></span>|<span data-ttu-id="0f0a3-147">Proč se uvolňování paměti aktivovalo:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-147">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="0f0a3-148">0x0 – malé přidělení haldy objektů.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-148">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="0f0a3-149">0x1 – vyvolané.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-149">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="0f0a3-150">0x2 – nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="0f0a3-150">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="0f0a3-151">0x3 – prázdné.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-151">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="0f0a3-152">0x4 – přidělení haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-152">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="0f0a3-153">0x5 – nedostatek místa (pro haldu malých objektů)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-153">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="0f0a3-154">0x6 mimo prostor (pro haldu velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-154">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="0f0a3-155">0x7 – vyvolané, ale nevynucené jako blokující</span><span class="sxs-lookup"><span data-stu-id="0f0a3-155">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="0f0a3-156">Typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-156">Type</span></span>|<span data-ttu-id="0f0a3-157">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-157">win:UInt32</span></span>|<span data-ttu-id="0f0a3-158">0x0 – blokující uvolňování paměti se nevyskytlo mimo uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-158">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="0f0a3-159">0x1 – uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="0f0a3-159">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="0f0a3-160">0x2 – blokující uvolňování paměti došlo během uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-160">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="0f0a3-161">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-161">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-162">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-162">win:UInt16</span></span>|<span data-ttu-id="0f0a3-163">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="0f0a3-164">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-164">GCEnd_V1 Event</span></span>

<span data-ttu-id="0f0a3-165">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-165">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-166">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-166">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-167">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-168">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-168">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-169">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-169">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-170">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-170">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-171">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-171">Event</span></span>|<span data-ttu-id="0f0a3-172">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-172">Event ID</span></span>|<span data-ttu-id="0f0a3-173">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="0f0a3-174">2</span><span class="sxs-lookup"><span data-stu-id="0f0a3-174">2</span></span>|<span data-ttu-id="0f0a3-175">Uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-175">The garbage collection has ended.</span></span>|

<span data-ttu-id="0f0a3-176">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-176">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-177">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-177">Field name</span></span>|<span data-ttu-id="0f0a3-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-178">Data type</span></span>|<span data-ttu-id="0f0a3-179">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-179">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-180">Count</span><span class="sxs-lookup"><span data-stu-id="0f0a3-180">Count</span></span>|<span data-ttu-id="0f0a3-181">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-181">win:UInt32</span></span>|<span data-ttu-id="0f0a3-182">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-182">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="0f0a3-183">Úrovní</span><span class="sxs-lookup"><span data-stu-id="0f0a3-183">Depth</span></span>|<span data-ttu-id="0f0a3-184">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-184">win:UInt32</span></span>|<span data-ttu-id="0f0a3-185">Shromážděná generace.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-185">The generation that was collected.</span></span>|
|<span data-ttu-id="0f0a3-186">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-186">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-187">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-187">win:UInt16</span></span>|<span data-ttu-id="0f0a3-188">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-188">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="0f0a3-189">Událost GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-189">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="0f0a3-190">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-190">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-191">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-191">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-192">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-192">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-193">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-194">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-194">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-195">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-195">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-196">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-196">Event</span></span>|<span data-ttu-id="0f0a3-197">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-197">Event ID</span></span>|<span data-ttu-id="0f0a3-198">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-198">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="0f0a3-199">4</span><span class="sxs-lookup"><span data-stu-id="0f0a3-199">4</span></span>|<span data-ttu-id="0f0a3-200">Zobrazuje statistiku haldy na konci každého uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-200">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="0f0a3-201">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-201">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-202">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-202">Field name</span></span>|<span data-ttu-id="0f0a3-203">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-203">Data type</span></span>|<span data-ttu-id="0f0a3-204">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-204">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="0f0a3-205">GenerationSize0</span></span>|<span data-ttu-id="0f0a3-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-206">win:UInt64</span></span>|<span data-ttu-id="0f0a3-207">Velikost paměti generace 0 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-207">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="0f0a3-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="0f0a3-208">TotalPromotedSize0</span></span>|<span data-ttu-id="0f0a3-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-209">win:UInt64</span></span>|<span data-ttu-id="0f0a3-210">Počet bajtů, které jsou povýšeny z generace 0 na generaci 1.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="0f0a3-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-211">GenerationSize1</span></span>|<span data-ttu-id="0f0a3-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-212">win:UInt64</span></span>|<span data-ttu-id="0f0a3-213">Velikost paměti 1. generace v bajtech</span><span class="sxs-lookup"><span data-stu-id="0f0a3-213">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="0f0a3-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-214">TotalPromotedSize1</span></span>|<span data-ttu-id="0f0a3-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-215">win:UInt64</span></span>|<span data-ttu-id="0f0a3-216">Počet bajtů, které jsou povýšeny z generace 1 na generaci 2.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="0f0a3-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="0f0a3-217">GenerationSize2</span></span>|<span data-ttu-id="0f0a3-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-218">win:UInt64</span></span>|<span data-ttu-id="0f0a3-219">Velikost paměti generace 2 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-219">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="0f0a3-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="0f0a3-220">TotalPromotedSize2</span></span>|<span data-ttu-id="0f0a3-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-221">win:UInt64</span></span>|<span data-ttu-id="0f0a3-222">Počet bajtů, které byly zachovány v generaci 2 po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="0f0a3-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="0f0a3-223">GenerationSize3</span></span>|<span data-ttu-id="0f0a3-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-224">win:UInt64</span></span>|<span data-ttu-id="0f0a3-225">Velikost haldy velkých objektů v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-225">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="0f0a3-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="0f0a3-226">TotalPromotedSize3</span></span>|<span data-ttu-id="0f0a3-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-227">win:UInt64</span></span>|<span data-ttu-id="0f0a3-228">Počet bajtů, které byly zachovány v haldě velkých objektů po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="0f0a3-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="0f0a3-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="0f0a3-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-230">win:UInt64</span></span>|<span data-ttu-id="0f0a3-231">Celková velikost objektů, které jsou připraveny k dokončení, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="0f0a3-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="0f0a3-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="0f0a3-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-233">win:UInt64</span></span>|<span data-ttu-id="0f0a3-234">Počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-234">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="0f0a3-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="0f0a3-235">PinnedObjectCount</span></span>|<span data-ttu-id="0f0a3-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-236">win:UInt32</span></span>|<span data-ttu-id="0f0a3-237">Počet připnutých (nepohyblivých) objektů.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-237">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="0f0a3-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="0f0a3-238">SinkBlockCount</span></span>|<span data-ttu-id="0f0a3-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-239">win:UInt32</span></span>|<span data-ttu-id="0f0a3-240">Počet používaných synchronizačních bloků.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-240">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="0f0a3-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="0f0a3-241">GCHandleCount</span></span>|<span data-ttu-id="0f0a3-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-242">win:UInt32</span></span>|<span data-ttu-id="0f0a3-243">Počet používaných obslužných rutin uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-243">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="0f0a3-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-244">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-245">win:UInt16</span></span>|<span data-ttu-id="0f0a3-246">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="0f0a3-247">Událost GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-247">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="0f0a3-248">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-248">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-249">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-249">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-250">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-250">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-251">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-251">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-252">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-252">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-253">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-253">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-254">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-254">Event</span></span>|<span data-ttu-id="0f0a3-255">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-255">Event ID</span></span>|<span data-ttu-id="0f0a3-256">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-256">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="0f0a3-257">5</span><span class="sxs-lookup"><span data-stu-id="0f0a3-257">5</span></span>|<span data-ttu-id="0f0a3-258">Vytvořil se nový segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-258">A new garbage collection segment has been created.</span></span> <span data-ttu-id="0f0a3-259">Kromě toho, když je trasování povoleno na procesu, který je již spuštěn, tato událost je vyvolána pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-259">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="0f0a3-260">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-260">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-261">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-261">Field name</span></span>|<span data-ttu-id="0f0a3-262">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-262">Data type</span></span>|<span data-ttu-id="0f0a3-263">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-263">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-264">Adresa</span><span class="sxs-lookup"><span data-stu-id="0f0a3-264">Address</span></span>|<span data-ttu-id="0f0a3-265">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-265">win:UInt64</span></span>|<span data-ttu-id="0f0a3-266">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-266">The address of the segment.</span></span>|
|<span data-ttu-id="0f0a3-267">Velikost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-267">Size</span></span>|<span data-ttu-id="0f0a3-268">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-268">win:UInt64</span></span>|<span data-ttu-id="0f0a3-269">Velikost segmentu</span><span class="sxs-lookup"><span data-stu-id="0f0a3-269">The size of the segment.</span></span>|
|<span data-ttu-id="0f0a3-270">Typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-270">Type</span></span>|<span data-ttu-id="0f0a3-271">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-271">win:UInt32</span></span>|<span data-ttu-id="0f0a3-272">0x0 – malá halda objektu.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-272">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="0f0a3-273">0x1 – halda velkých objektů</span><span class="sxs-lookup"><span data-stu-id="0f0a3-273">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="0f0a3-274">0x2 – halda jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-274">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="0f0a3-275">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-275">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-276">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-276">win:UInt16</span></span>|<span data-ttu-id="0f0a3-277">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-277">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="0f0a3-278">Všimněte si, že velikost segmentů přidělených systémem uvolňování paměti je specifická pro konkrétní implementaci a může se kdykoli změnit, včetně pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-278">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="0f0a3-279">Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-279">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="0f0a3-280">Událost GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-280">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="0f0a3-281">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-281">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-282">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-282">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-283">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-283">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-284">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-284">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-285">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-285">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-286">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-286">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-287">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-287">Event</span></span>|<span data-ttu-id="0f0a3-288">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-288">Event ID</span></span>|<span data-ttu-id="0f0a3-289">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-289">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="0f0a3-290">6</span><span class="sxs-lookup"><span data-stu-id="0f0a3-290">6</span></span>|<span data-ttu-id="0f0a3-291">Byl uvolněn segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-291">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="0f0a3-292">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-292">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-293">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-293">Field name</span></span>|<span data-ttu-id="0f0a3-294">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-294">Data type</span></span>|<span data-ttu-id="0f0a3-295">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-295">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-296">Adresa</span><span class="sxs-lookup"><span data-stu-id="0f0a3-296">Address</span></span>|<span data-ttu-id="0f0a3-297">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-297">win:UInt64</span></span>|<span data-ttu-id="0f0a3-298">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-298">The address of the segment.</span></span>|
|<span data-ttu-id="0f0a3-299">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-299">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-300">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-300">win:UInt16</span></span>|<span data-ttu-id="0f0a3-301">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-301">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="0f0a3-302">Událost GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-302">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="0f0a3-303">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-303">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-304">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-304">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-305">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-305">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-306">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-306">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-307">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-307">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-308">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-308">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-309">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-309">Event</span></span>|<span data-ttu-id="0f0a3-310">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-310">Event ID</span></span>|<span data-ttu-id="0f0a3-311">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-311">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="0f0a3-312">7</span><span class="sxs-lookup"><span data-stu-id="0f0a3-312">7</span></span>|<span data-ttu-id="0f0a3-313">Bylo zahájeno obnovení z pozastavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-313">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="0f0a3-314">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-314">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="0f0a3-315">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-315">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="0f0a3-316">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-316">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-317">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-317">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-318">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-318">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-319">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-319">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-320">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-320">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-321">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-321">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-322">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-322">Event</span></span>|<span data-ttu-id="0f0a3-323">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-323">Event Id</span></span>|<span data-ttu-id="0f0a3-324">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-324">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="0f0a3-325">3</span><span class="sxs-lookup"><span data-stu-id="0f0a3-325">3</span></span>|<span data-ttu-id="0f0a3-326">Obnovení z odložení modulu CLR (Common Language Runtime) skončilo.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-326">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="0f0a3-327">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-327">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="0f0a3-328">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-328">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="0f0a3-329">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-329">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-330">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-330">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-331">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-331">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-332">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-332">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-333">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-333">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-334">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-334">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-335">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-335">Event</span></span>|<span data-ttu-id="0f0a3-336">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-336">Event ID</span></span>|<span data-ttu-id="0f0a3-337">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-337">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="0f0a3-338">9</span><span class="sxs-lookup"><span data-stu-id="0f0a3-338">9</span></span>|<span data-ttu-id="0f0a3-339">Začátek pozastavení spouštěcího modulu pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-339">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="0f0a3-340">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-340">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-341">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-341">Field name</span></span>|<span data-ttu-id="0f0a3-342">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-342">Data type</span></span>|<span data-ttu-id="0f0a3-343">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-343">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-344">Důvod</span><span class="sxs-lookup"><span data-stu-id="0f0a3-344">Reason</span></span>|<span data-ttu-id="0f0a3-345">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-345">win:UInt16</span></span>|<span data-ttu-id="0f0a3-346">0x0 – ostatní</span><span class="sxs-lookup"><span data-stu-id="0f0a3-346">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="0f0a3-347">0x1 – uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0f0a3-347">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="0f0a3-348">0x2 – vypnutí aplikační domény</span><span class="sxs-lookup"><span data-stu-id="0f0a3-348">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="0f0a3-349">0x3 – rozteč kódu.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-349">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="0f0a3-350">0x4 – vypnutí</span><span class="sxs-lookup"><span data-stu-id="0f0a3-350">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="0f0a3-351">0x5 – ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-351">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="0f0a3-352">0x6 – příprava pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0f0a3-352">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="0f0a3-353">Count</span><span class="sxs-lookup"><span data-stu-id="0f0a3-353">Count</span></span>|<span data-ttu-id="0f0a3-354">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-354">win:UInt32</span></span>|<span data-ttu-id="0f0a3-355">Počet GC v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-355">The GC count at the time.</span></span> <span data-ttu-id="0f0a3-356">Obvykle se vám po tomto zobrazení zobrazí další počáteční událost GC a její počet by byl tento počet + 1, protože během uvolňování paměti narůstá index GC.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-356">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="0f0a3-357">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-357">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-358">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-358">win:UInt16</span></span>|<span data-ttu-id="0f0a3-359">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-359">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="0f0a3-360">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-360">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="0f0a3-361">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-361">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-362">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-362">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-363">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-363">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-364">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-364">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-365">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-365">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-366">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-366">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-367">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-367">Event</span></span>|<span data-ttu-id="0f0a3-368">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-368">Event ID</span></span>|<span data-ttu-id="0f0a3-369">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-369">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="0f0a3-370">8</span><span class="sxs-lookup"><span data-stu-id="0f0a3-370">8</span></span>|<span data-ttu-id="0f0a3-371">Konec pozastavení prováděcího modulu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0f0a3-371">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="0f0a3-372">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-372">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="0f0a3-373">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="0f0a3-373">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="0f0a3-374">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-374">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-375">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-375">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-376">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-376">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-377">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-377">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-378">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-378">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-379">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-379">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-380">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-380">Event</span></span>|<span data-ttu-id="0f0a3-381">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-381">Event ID</span></span>|<span data-ttu-id="0f0a3-382">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-382">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="0f0a3-383">10</span><span class="sxs-lookup"><span data-stu-id="0f0a3-383">10</span></span>|<span data-ttu-id="0f0a3-384">Pokaždé, když se přidělí přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-384">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="0f0a3-385">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-385">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-386">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-386">Field name</span></span>|<span data-ttu-id="0f0a3-387">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-387">Data type</span></span>|<span data-ttu-id="0f0a3-388">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-388">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-389">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="0f0a3-389">AllocationAmount</span></span>|<span data-ttu-id="0f0a3-390">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-390">win:UInt32</span></span>|<span data-ttu-id="0f0a3-391">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-391">The allocation size, in bytes.</span></span> <span data-ttu-id="0f0a3-392">Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4 294 967 295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-392">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="0f0a3-393">Pokud je přidělení větší, obsahuje toto pole zkrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-393">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="0f0a3-394">Použijte `AllocationAmount64` pro velmi velké alokace.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-394">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="0f0a3-395">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="0f0a3-395">AllocationKind</span></span>|<span data-ttu-id="0f0a3-396">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-396">win:UInt32</span></span>|<span data-ttu-id="0f0a3-397">0x0 – malé přidělení objektů (přidělení je v haldě malých objektů).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-397">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="0f0a3-398">0x1 – velké přidělení objektů (přidělení je v haldě velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-398">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="0f0a3-399">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-399">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-400">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-400">win:UInt16</span></span>|<span data-ttu-id="0f0a3-401">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-401">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="0f0a3-402">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-402">AllocationAmount64</span></span>|<span data-ttu-id="0f0a3-403">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="0f0a3-403">win:UInt64</span></span>|<span data-ttu-id="0f0a3-404">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-404">The allocation size, in bytes.</span></span> <span data-ttu-id="0f0a3-405">Tato hodnota je přesné pro velmi velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-405">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="0f0a3-406">TypeId</span><span class="sxs-lookup"><span data-stu-id="0f0a3-406">TypeId</span></span>|<span data-ttu-id="0f0a3-407">Win: ukazatel</span><span class="sxs-lookup"><span data-stu-id="0f0a3-407">win:Pointer</span></span>|<span data-ttu-id="0f0a3-408">Adresa metody.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-408">The address of the MethodTable.</span></span> <span data-ttu-id="0f0a3-409">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o adresu metody, která odpovídá poslednímu přidělenému objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-409">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="0f0a3-410">TypeName</span><span class="sxs-lookup"><span data-stu-id="0f0a3-410">TypeName</span></span>|<span data-ttu-id="0f0a3-411">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0f0a3-411">win:UnicodeString</span></span>|<span data-ttu-id="0f0a3-412">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-412">The name of the type that was allocated.</span></span> <span data-ttu-id="0f0a3-413">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ posledního přiděleného objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="0f0a3-413">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="0f0a3-414">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="0f0a3-414">HeapIndex</span></span>|<span data-ttu-id="0f0a3-415">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-415">win:UInt32</span></span>|<span data-ttu-id="0f0a3-416">Halda, ve které byl objekt přidělen.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-416">The heap where the object was allocated.</span></span> <span data-ttu-id="0f0a3-417">Tato hodnota je 0 (nula) při spuštění s uvolňováním paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-417">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="0f0a3-418">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-418">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="0f0a3-419">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-419">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-420">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-420">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-421">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-421">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-422">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-422">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-423">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-423">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-424">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-424">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-425">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-425">Event</span></span>|<span data-ttu-id="0f0a3-426">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-426">Event ID</span></span>|<span data-ttu-id="0f0a3-427">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-427">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="0f0a3-428">14</span><span class="sxs-lookup"><span data-stu-id="0f0a3-428">14</span></span>|<span data-ttu-id="0f0a3-429">Začátek spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-429">The start of running finalizers.</span></span>|

<span data-ttu-id="0f0a3-430">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-430">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="0f0a3-431">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-431">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="0f0a3-432">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-432">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-433">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-433">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-434">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-435">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-435">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-436">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-436">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-437">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-437">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-438">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-438">Event</span></span>|<span data-ttu-id="0f0a3-439">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-439">Event ID</span></span>|<span data-ttu-id="0f0a3-440">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-440">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="0f0a3-441">13</span><span class="sxs-lookup"><span data-stu-id="0f0a3-441">13</span></span>|<span data-ttu-id="0f0a3-442">Konec spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-442">The end of running finalizers.</span></span>|

<span data-ttu-id="0f0a3-443">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-443">The following table shows the event data:</span></span>

|<span data-ttu-id="0f0a3-444">Název pole</span><span class="sxs-lookup"><span data-stu-id="0f0a3-444">Field name</span></span>|<span data-ttu-id="0f0a3-445">Datový typ</span><span class="sxs-lookup"><span data-stu-id="0f0a3-445">Data type</span></span>|<span data-ttu-id="0f0a3-446">Popis</span><span class="sxs-lookup"><span data-stu-id="0f0a3-446">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0f0a3-447">Count</span><span class="sxs-lookup"><span data-stu-id="0f0a3-447">Count</span></span>|<span data-ttu-id="0f0a3-448">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0f0a3-448">win:UInt32</span></span>|<span data-ttu-id="0f0a3-449">Počet finalizační metody, které byly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-449">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="0f0a3-450">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0f0a3-450">ClrInstanceID</span></span>|<span data-ttu-id="0f0a3-451">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0f0a3-451">win:UInt16</span></span>|<span data-ttu-id="0f0a3-452">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-452">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="0f0a3-453">Událost GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-453">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="0f0a3-454">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-454">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-455">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-455">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-456">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-456">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-457">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-457">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-458">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-458">Informational (4)</span></span>|
|<span data-ttu-id="0f0a3-459">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-459">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0f0a3-460">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-460">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-461">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-461">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-462">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-462">Event</span></span>|<span data-ttu-id="0f0a3-463">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-463">Event ID</span></span>|<span data-ttu-id="0f0a3-464">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-464">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="0f0a3-465">11</span><span class="sxs-lookup"><span data-stu-id="0f0a3-465">11</span></span>|<span data-ttu-id="0f0a3-466">Bylo vytvořeno souběžné vlákno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-466">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="0f0a3-467">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-467">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="0f0a3-468">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-468">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="0f0a3-469">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-469">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0f0a3-470">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-470">Keyword for raising the event</span></span>|<span data-ttu-id="0f0a3-471">Level</span><span class="sxs-lookup"><span data-stu-id="0f0a3-471">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0f0a3-472">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="0f0a3-472">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0f0a3-473">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-473">Informational (4)</span></span>|
|<span data-ttu-id="0f0a3-474">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-474">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0f0a3-475">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="0f0a3-475">Informational (4)</span></span>|

<span data-ttu-id="0f0a3-476">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="0f0a3-476">The following table shows the event information:</span></span>

|<span data-ttu-id="0f0a3-477">Událost</span><span class="sxs-lookup"><span data-stu-id="0f0a3-477">Event</span></span>|<span data-ttu-id="0f0a3-478">ID události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-478">Event ID</span></span>|<span data-ttu-id="0f0a3-479">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="0f0a3-479">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="0f0a3-480">12</span><span class="sxs-lookup"><span data-stu-id="0f0a3-480">12</span></span>|<span data-ttu-id="0f0a3-481">Vlákno souběžného uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="0f0a3-481">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="0f0a3-482">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="0f0a3-482">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f0a3-483">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f0a3-483">See also</span></span>

- [<span data-ttu-id="0f0a3-484">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="0f0a3-484">CLR ETW Events</span></span>](clr-etw-events.md)
