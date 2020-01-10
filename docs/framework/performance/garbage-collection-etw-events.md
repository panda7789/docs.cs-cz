---
title: Události Trasování událostí pro Windows uvolnění paměti
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 5ff214314b92796f4a4a89ddd33a976d8b1f21d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716073"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="9d9e2-102">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="9d9e2-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="9d9e2-103">Tyto události shromažďují informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="9d9e2-104">Pomáhá při diagnostice a ladění, včetně určení počtu provedených uvolnění paměti, o tom, kolik paměti bylo uvolněno během uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="9d9e2-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="9d9e2-106">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="9d9e2-107">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="9d9e2-108">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="9d9e2-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="9d9e2-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="9d9e2-111">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="9d9e2-112">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="9d9e2-113">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="9d9e2-114">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="9d9e2-115">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="9d9e2-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="9d9e2-116">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="9d9e2-117">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="9d9e2-118">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="9d9e2-119">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="9d9e2-120">Událost GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="9d9e2-121">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="9d9e2-122">Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="9d9e2-123">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-123">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-124">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-126">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-126">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-127">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-127">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-128">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-128">Event</span></span>|<span data-ttu-id="9d9e2-129">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-129">Event ID</span></span>|<span data-ttu-id="9d9e2-130">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="9d9e2-131">1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-131">1</span></span>|<span data-ttu-id="9d9e2-132">Bylo zahájeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-132">A garbage collection has started.</span></span>|

<span data-ttu-id="9d9e2-133">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-133">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-134">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-134">Field name</span></span>|<span data-ttu-id="9d9e2-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-135">Data type</span></span>|<span data-ttu-id="9d9e2-136">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-137">Počet</span><span class="sxs-lookup"><span data-stu-id="9d9e2-137">Count</span></span>|<span data-ttu-id="9d9e2-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-138">win:UInt32</span></span>|<span data-ttu-id="9d9e2-139">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="9d9e2-140">Úrovní</span><span class="sxs-lookup"><span data-stu-id="9d9e2-140">Depth</span></span>|<span data-ttu-id="9d9e2-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-141">win:UInt32</span></span>|<span data-ttu-id="9d9e2-142">Shromažďovaná generace.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="9d9e2-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="9d9e2-143">Reason</span></span>|<span data-ttu-id="9d9e2-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-144">win:UInt32</span></span>|<span data-ttu-id="9d9e2-145">Proč se uvolňování paměti aktivovalo:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="9d9e2-146">0x0 – malé přidělení haldy objektů.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="9d9e2-147">0x1 – vyvolané.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="9d9e2-148">0x2 – nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="9d9e2-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="9d9e2-149">0x3 – prázdné.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="9d9e2-150">0x4 – přidělení haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="9d9e2-151">0x5 – nedostatek místa (pro haldu malých objektů)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="9d9e2-152">0x6 mimo prostor (pro haldu velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="9d9e2-153">0x7 – vyvolané, ale nevynucené jako blokující</span><span class="sxs-lookup"><span data-stu-id="9d9e2-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="9d9e2-154">Type</span><span class="sxs-lookup"><span data-stu-id="9d9e2-154">Type</span></span>|<span data-ttu-id="9d9e2-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-155">win:UInt32</span></span>|<span data-ttu-id="9d9e2-156">0x0 – blokující uvolňování paměti se nevyskytlo mimo uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="9d9e2-157">0x1 – uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="9d9e2-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="9d9e2-158">0x2 – blokující uvolňování paměti došlo během uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="9d9e2-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-159">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-160">win:UInt16</span></span>|<span data-ttu-id="9d9e2-161">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="9d9e2-162">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="9d9e2-163">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-164">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-164">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-165">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-167">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-167">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-168">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-168">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-169">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-169">Event</span></span>|<span data-ttu-id="9d9e2-170">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-170">Event ID</span></span>|<span data-ttu-id="9d9e2-171">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="9d9e2-172">2</span><span class="sxs-lookup"><span data-stu-id="9d9e2-172">2</span></span>|<span data-ttu-id="9d9e2-173">Uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="9d9e2-174">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-174">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-175">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-175">Field name</span></span>|<span data-ttu-id="9d9e2-176">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-176">Data type</span></span>|<span data-ttu-id="9d9e2-177">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-178">Počet</span><span class="sxs-lookup"><span data-stu-id="9d9e2-178">Count</span></span>|<span data-ttu-id="9d9e2-179">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-179">win:UInt32</span></span>|<span data-ttu-id="9d9e2-180">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="9d9e2-181">Úrovní</span><span class="sxs-lookup"><span data-stu-id="9d9e2-181">Depth</span></span>|<span data-ttu-id="9d9e2-182">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-182">win:UInt32</span></span>|<span data-ttu-id="9d9e2-183">Shromážděná generace.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-183">The generation that was collected.</span></span>|
|<span data-ttu-id="9d9e2-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-184">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-185">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-185">win:UInt16</span></span>|<span data-ttu-id="9d9e2-186">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="9d9e2-187">Událost GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="9d9e2-188">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-189">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-189">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-190">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-192">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-192">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-193">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-193">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-194">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-194">Event</span></span>|<span data-ttu-id="9d9e2-195">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-195">Event ID</span></span>|<span data-ttu-id="9d9e2-196">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="9d9e2-197">4</span><span class="sxs-lookup"><span data-stu-id="9d9e2-197">4</span></span>|<span data-ttu-id="9d9e2-198">Zobrazuje statistiku haldy na konci každého uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="9d9e2-199">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-199">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-200">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-200">Field name</span></span>|<span data-ttu-id="9d9e2-201">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-201">Data type</span></span>|<span data-ttu-id="9d9e2-202">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="9d9e2-203">GenerationSize0</span></span>|<span data-ttu-id="9d9e2-204">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-204">win:UInt64</span></span>|<span data-ttu-id="9d9e2-205">Velikost paměti generace 0 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="9d9e2-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="9d9e2-206">TotalPromotedSize0</span></span>|<span data-ttu-id="9d9e2-207">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-207">win:UInt64</span></span>|<span data-ttu-id="9d9e2-208">Počet bajtů, které jsou povýšeny z generace 0 na generaci 1.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="9d9e2-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-209">GenerationSize1</span></span>|<span data-ttu-id="9d9e2-210">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-210">win:UInt64</span></span>|<span data-ttu-id="9d9e2-211">Velikost paměti 1. generace v bajtech</span><span class="sxs-lookup"><span data-stu-id="9d9e2-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="9d9e2-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-212">TotalPromotedSize1</span></span>|<span data-ttu-id="9d9e2-213">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-213">win:UInt64</span></span>|<span data-ttu-id="9d9e2-214">Počet bajtů, které jsou povýšeny z generace 1 na generaci 2.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="9d9e2-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="9d9e2-215">GenerationSize2</span></span>|<span data-ttu-id="9d9e2-216">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-216">win:UInt64</span></span>|<span data-ttu-id="9d9e2-217">Velikost paměti generace 2 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="9d9e2-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="9d9e2-218">TotalPromotedSize2</span></span>|<span data-ttu-id="9d9e2-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-219">win:UInt64</span></span>|<span data-ttu-id="9d9e2-220">Počet bajtů, které byly zachovány v generaci 2 po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="9d9e2-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="9d9e2-221">GenerationSize3</span></span>|<span data-ttu-id="9d9e2-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-222">win:UInt64</span></span>|<span data-ttu-id="9d9e2-223">Velikost haldy velkých objektů v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="9d9e2-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="9d9e2-224">TotalPromotedSize3</span></span>|<span data-ttu-id="9d9e2-225">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-225">win:UInt64</span></span>|<span data-ttu-id="9d9e2-226">Počet bajtů, které byly zachovány v haldě velkých objektů po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="9d9e2-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="9d9e2-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="9d9e2-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-228">win:UInt64</span></span>|<span data-ttu-id="9d9e2-229">Celková velikost objektů, které jsou připraveny k dokončení, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="9d9e2-230">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="9d9e2-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="9d9e2-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-231">win:UInt64</span></span>|<span data-ttu-id="9d9e2-232">Počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="9d9e2-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="9d9e2-233">PinnedObjectCount</span></span>|<span data-ttu-id="9d9e2-234">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-234">win:UInt32</span></span>|<span data-ttu-id="9d9e2-235">Počet připnutých (nepohyblivých) objektů.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="9d9e2-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="9d9e2-236">SinkBlockCount</span></span>|<span data-ttu-id="9d9e2-237">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-237">win:UInt32</span></span>|<span data-ttu-id="9d9e2-238">Počet používaných synchronizačních bloků.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="9d9e2-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="9d9e2-239">GCHandleCount</span></span>|<span data-ttu-id="9d9e2-240">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-240">win:UInt32</span></span>|<span data-ttu-id="9d9e2-241">Počet používaných obslužných rutin uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="9d9e2-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-242">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-243">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-243">win:UInt16</span></span>|<span data-ttu-id="9d9e2-244">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="9d9e2-245">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="9d9e2-246">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-247">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-247">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-248">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-250">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-250">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-251">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-251">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-252">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-252">Event</span></span>|<span data-ttu-id="9d9e2-253">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-253">Event ID</span></span>|<span data-ttu-id="9d9e2-254">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="9d9e2-255">5</span><span class="sxs-lookup"><span data-stu-id="9d9e2-255">5</span></span>|<span data-ttu-id="9d9e2-256">Vytvořil se nový segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="9d9e2-257">Kromě toho, když je trasování povoleno na procesu, který je již spuštěn, tato událost je vyvolána pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="9d9e2-258">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-258">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-259">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-259">Field name</span></span>|<span data-ttu-id="9d9e2-260">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-260">Data type</span></span>|<span data-ttu-id="9d9e2-261">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-262">Adresa</span><span class="sxs-lookup"><span data-stu-id="9d9e2-262">Address</span></span>|<span data-ttu-id="9d9e2-263">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-263">win:UInt64</span></span>|<span data-ttu-id="9d9e2-264">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-264">The address of the segment.</span></span>|
|<span data-ttu-id="9d9e2-265">Velikost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-265">Size</span></span>|<span data-ttu-id="9d9e2-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-266">win:UInt64</span></span>|<span data-ttu-id="9d9e2-267">Velikost segmentu</span><span class="sxs-lookup"><span data-stu-id="9d9e2-267">The size of the segment.</span></span>|
|<span data-ttu-id="9d9e2-268">Type</span><span class="sxs-lookup"><span data-stu-id="9d9e2-268">Type</span></span>|<span data-ttu-id="9d9e2-269">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-269">win:UInt32</span></span>|<span data-ttu-id="9d9e2-270">0x0 – malá halda objektu.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="9d9e2-271">0x1 – halda velkých objektů</span><span class="sxs-lookup"><span data-stu-id="9d9e2-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="9d9e2-272">0x2 – halda jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="9d9e2-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-273">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-274">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-274">win:UInt16</span></span>|<span data-ttu-id="9d9e2-275">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="9d9e2-276">Všimněte si, že velikost segmentů přidělených systémem uvolňování paměti je specifická pro konkrétní implementaci a může se kdykoli změnit, včetně pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="9d9e2-277">Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="9d9e2-278">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="9d9e2-279">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-280">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-280">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-281">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-283">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-283">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-284">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-284">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-285">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-285">Event</span></span>|<span data-ttu-id="9d9e2-286">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-286">Event ID</span></span>|<span data-ttu-id="9d9e2-287">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="9d9e2-288">6</span><span class="sxs-lookup"><span data-stu-id="9d9e2-288">6</span></span>|<span data-ttu-id="9d9e2-289">Byl uvolněn segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="9d9e2-290">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-290">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-291">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-291">Field name</span></span>|<span data-ttu-id="9d9e2-292">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-292">Data type</span></span>|<span data-ttu-id="9d9e2-293">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-294">Adresa</span><span class="sxs-lookup"><span data-stu-id="9d9e2-294">Address</span></span>|<span data-ttu-id="9d9e2-295">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-295">win:UInt64</span></span>|<span data-ttu-id="9d9e2-296">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-296">The address of the segment.</span></span>|
|<span data-ttu-id="9d9e2-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-297">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-298">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-298">win:UInt16</span></span>|<span data-ttu-id="9d9e2-299">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="9d9e2-300">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="9d9e2-301">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-302">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-302">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-303">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-305">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-305">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-306">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-306">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-307">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-307">Event</span></span>|<span data-ttu-id="9d9e2-308">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-308">Event ID</span></span>|<span data-ttu-id="9d9e2-309">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="9d9e2-310">7</span><span class="sxs-lookup"><span data-stu-id="9d9e2-310">7</span></span>|<span data-ttu-id="9d9e2-311">Bylo zahájeno obnovení z pozastavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="9d9e2-312">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="9d9e2-313">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="9d9e2-314">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-315">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-315">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-316">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-318">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-318">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-319">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-319">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-320">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-320">Event</span></span>|<span data-ttu-id="9d9e2-321">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-321">Event Id</span></span>|<span data-ttu-id="9d9e2-322">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="9d9e2-323">3</span><span class="sxs-lookup"><span data-stu-id="9d9e2-323">3</span></span>|<span data-ttu-id="9d9e2-324">Obnovení z odložení modulu CLR (Common Language Runtime) skončilo.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="9d9e2-325">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="9d9e2-326">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="9d9e2-327">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-328">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-328">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-329">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-331">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-331">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-332">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-332">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-333">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-333">Event</span></span>|<span data-ttu-id="9d9e2-334">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-334">Event ID</span></span>|<span data-ttu-id="9d9e2-335">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="9d9e2-336">9</span><span class="sxs-lookup"><span data-stu-id="9d9e2-336">9</span></span>|<span data-ttu-id="9d9e2-337">Začátek pozastavení spouštěcího modulu pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="9d9e2-338">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-338">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-339">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-339">Field name</span></span>|<span data-ttu-id="9d9e2-340">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-340">Data type</span></span>|<span data-ttu-id="9d9e2-341">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-342">Důvod</span><span class="sxs-lookup"><span data-stu-id="9d9e2-342">Reason</span></span>|<span data-ttu-id="9d9e2-343">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-343">win:UInt16</span></span>|<span data-ttu-id="9d9e2-344">0x0 – ostatní</span><span class="sxs-lookup"><span data-stu-id="9d9e2-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="9d9e2-345">0x1 – uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="9d9e2-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="9d9e2-346">0x2 – vypnutí aplikační domény</span><span class="sxs-lookup"><span data-stu-id="9d9e2-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="9d9e2-347">0x3 – rozteč kódu.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="9d9e2-348">0x4 – vypnutí</span><span class="sxs-lookup"><span data-stu-id="9d9e2-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="9d9e2-349">0x5 – ladicí program.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="9d9e2-350">0x6 – příprava pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="9d9e2-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="9d9e2-351">Počet</span><span class="sxs-lookup"><span data-stu-id="9d9e2-351">Count</span></span>|<span data-ttu-id="9d9e2-352">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-352">win:UInt32</span></span>|<span data-ttu-id="9d9e2-353">Počet GC v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-353">The GC count at the time.</span></span> <span data-ttu-id="9d9e2-354">Obvykle se vám po tomto zobrazení zobrazí další počáteční událost GC a její počet by byl tento počet + 1, protože během uvolňování paměti narůstá index GC.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="9d9e2-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-355">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-356">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-356">win:UInt16</span></span>|<span data-ttu-id="9d9e2-357">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="9d9e2-358">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="9d9e2-359">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-360">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-360">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-361">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-363">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-363">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-364">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-364">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-365">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-365">Event</span></span>|<span data-ttu-id="9d9e2-366">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-366">Event ID</span></span>|<span data-ttu-id="9d9e2-367">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="9d9e2-368">8</span><span class="sxs-lookup"><span data-stu-id="9d9e2-368">8</span></span>|<span data-ttu-id="9d9e2-369">Konec pozastavení prováděcího modulu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="9d9e2-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="9d9e2-370">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="9d9e2-371">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="9d9e2-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="9d9e2-372">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-373">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-373">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-374">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-376">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-376">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-377">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-377">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-378">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-378">Event</span></span>|<span data-ttu-id="9d9e2-379">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-379">Event ID</span></span>|<span data-ttu-id="9d9e2-380">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="9d9e2-381">10</span><span class="sxs-lookup"><span data-stu-id="9d9e2-381">10</span></span>|<span data-ttu-id="9d9e2-382">Pokaždé, když se přidělí přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="9d9e2-383">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-383">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-384">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-384">Field name</span></span>|<span data-ttu-id="9d9e2-385">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-385">Data type</span></span>|<span data-ttu-id="9d9e2-386">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="9d9e2-387">AllocationAmount</span></span>|<span data-ttu-id="9d9e2-388">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-388">win:UInt32</span></span>|<span data-ttu-id="9d9e2-389">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-389">The allocation size, in bytes.</span></span> <span data-ttu-id="9d9e2-390">Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4 294 967 295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="9d9e2-391">Pokud je přidělení větší, obsahuje toto pole zkrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="9d9e2-392">Pro velmi velké alokace použijte `AllocationAmount64`.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="9d9e2-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="9d9e2-393">AllocationKind</span></span>|<span data-ttu-id="9d9e2-394">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-394">win:UInt32</span></span>|<span data-ttu-id="9d9e2-395">0x0 – malé přidělení objektů (přidělení je v haldě malých objektů).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="9d9e2-396">0x1 – velké přidělení objektů (přidělení je v haldě velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="9d9e2-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-397">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-398">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-398">win:UInt16</span></span>|<span data-ttu-id="9d9e2-399">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="9d9e2-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-400">AllocationAmount64</span></span>|<span data-ttu-id="9d9e2-401">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="9d9e2-401">win:UInt64</span></span>|<span data-ttu-id="9d9e2-402">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-402">The allocation size, in bytes.</span></span> <span data-ttu-id="9d9e2-403">Tato hodnota je přesné pro velmi velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="9d9e2-404">IDTypu</span><span class="sxs-lookup"><span data-stu-id="9d9e2-404">TypeId</span></span>|<span data-ttu-id="9d9e2-405">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="9d9e2-405">win:Pointer</span></span>|<span data-ttu-id="9d9e2-406">Adresa metody.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-406">The address of the MethodTable.</span></span> <span data-ttu-id="9d9e2-407">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o adresu metody, která odpovídá poslednímu přidělenému objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="9d9e2-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="9d9e2-408">TypeName</span></span>|<span data-ttu-id="9d9e2-409">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9d9e2-409">win:UnicodeString</span></span>|<span data-ttu-id="9d9e2-410">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-410">The name of the type that was allocated.</span></span> <span data-ttu-id="9d9e2-411">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ posledního přiděleného objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="9d9e2-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="9d9e2-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="9d9e2-412">HeapIndex</span></span>|<span data-ttu-id="9d9e2-413">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-413">win:UInt32</span></span>|<span data-ttu-id="9d9e2-414">Halda, ve které byl objekt přidělen.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-414">The heap where the object was allocated.</span></span> <span data-ttu-id="9d9e2-415">Tato hodnota je 0 (nula) při spuštění s uvolňováním paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="9d9e2-416">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="9d9e2-417">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-418">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-418">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-419">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-421">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-421">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-422">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-422">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-423">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-423">Event</span></span>|<span data-ttu-id="9d9e2-424">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-424">Event ID</span></span>|<span data-ttu-id="9d9e2-425">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="9d9e2-426">14</span><span class="sxs-lookup"><span data-stu-id="9d9e2-426">14</span></span>|<span data-ttu-id="9d9e2-427">Začátek spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-427">The start of running finalizers.</span></span>|

<span data-ttu-id="9d9e2-428">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="9d9e2-429">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="9d9e2-430">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-431">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-431">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-432">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-434">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-434">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-435">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-435">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-436">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-436">Event</span></span>|<span data-ttu-id="9d9e2-437">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-437">Event ID</span></span>|<span data-ttu-id="9d9e2-438">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="9d9e2-439">13</span><span class="sxs-lookup"><span data-stu-id="9d9e2-439">13</span></span>|<span data-ttu-id="9d9e2-440">Konec spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-440">The end of running finalizers.</span></span>|

<span data-ttu-id="9d9e2-441">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-441">The following table shows the event data:</span></span>

|<span data-ttu-id="9d9e2-442">Název pole</span><span class="sxs-lookup"><span data-stu-id="9d9e2-442">Field name</span></span>|<span data-ttu-id="9d9e2-443">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9d9e2-443">Data type</span></span>|<span data-ttu-id="9d9e2-444">Popis</span><span class="sxs-lookup"><span data-stu-id="9d9e2-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="9d9e2-445">Počet</span><span class="sxs-lookup"><span data-stu-id="9d9e2-445">Count</span></span>|<span data-ttu-id="9d9e2-446">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9d9e2-446">win:UInt32</span></span>|<span data-ttu-id="9d9e2-447">Počet finalizační metody, které byly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="9d9e2-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9d9e2-448">ClrInstanceID</span></span>|<span data-ttu-id="9d9e2-449">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9d9e2-449">win:UInt16</span></span>|<span data-ttu-id="9d9e2-450">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="9d9e2-451">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="9d9e2-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="9d9e2-452">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-453">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-453">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-454">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-456">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-456">Informational (4)</span></span>|
|<span data-ttu-id="9d9e2-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="9d9e2-458">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-458">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-459">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-459">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-460">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-460">Event</span></span>|<span data-ttu-id="9d9e2-461">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-461">Event ID</span></span>|<span data-ttu-id="9d9e2-462">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="9d9e2-463">11</span><span class="sxs-lookup"><span data-stu-id="9d9e2-463">11</span></span>|<span data-ttu-id="9d9e2-464">Bylo vytvořeno souběžné vlákno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="9d9e2-465">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="9d9e2-466">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="9d9e2-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="9d9e2-467">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="9d9e2-468">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-468">Keyword for raising the event</span></span>|<span data-ttu-id="9d9e2-469">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9d9e2-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="9d9e2-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="9d9e2-471">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-471">Informational (4)</span></span>|
|<span data-ttu-id="9d9e2-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="9d9e2-473">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="9d9e2-473">Informational (4)</span></span>|

<span data-ttu-id="9d9e2-474">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-474">The following table shows the event information:</span></span>

|<span data-ttu-id="9d9e2-475">Událost</span><span class="sxs-lookup"><span data-stu-id="9d9e2-475">Event</span></span>|<span data-ttu-id="9d9e2-476">ID události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-476">Event ID</span></span>|<span data-ttu-id="9d9e2-477">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9d9e2-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="9d9e2-478">12</span><span class="sxs-lookup"><span data-stu-id="9d9e2-478">12</span></span>|<span data-ttu-id="9d9e2-479">Vlákno souběžného uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="9d9e2-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="9d9e2-480">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="9d9e2-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d9e2-481">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d9e2-481">See also</span></span>

- [<span data-ttu-id="9d9e2-482">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="9d9e2-482">CLR ETW Events</span></span>](clr-etw-events.md)
