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
ms.openlocfilehash: cd4a4699f115c5b134ea60e703607ff36c229a78
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040586"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="b1f38-102">Události Trasování událostí pro Windows uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="b1f38-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="b1f38-103">Tyto události shromažďují informace týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="b1f38-104">Pomáhá při diagnostice a ladění, včetně určení počtu provedených uvolnění paměti, o tom, kolik paměti bylo uvolněno během uvolňování paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b1f38-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="b1f38-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="b1f38-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="b1f38-106">Událost GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="b1f38-107">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="b1f38-108">Událost GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="b1f38-109">Událost GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="b1f38-110">Událost GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="b1f38-111">Událost GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="b1f38-112">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="b1f38-113">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="b1f38-114">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="b1f38-115">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="b1f38-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="b1f38-116">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="b1f38-117">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="b1f38-118">Událost GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="b1f38-119">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="b1f38-120">Událost GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="b1f38-121">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b1f38-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="b1f38-122">Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b1f38-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="b1f38-123">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-123">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-124">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-126">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-126">Informational (4)</span></span>|

<span data-ttu-id="b1f38-127">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-127">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-128">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-128">Event</span></span>|<span data-ttu-id="b1f38-129">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-129">Event ID</span></span>|<span data-ttu-id="b1f38-130">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="b1f38-131">první</span><span class="sxs-lookup"><span data-stu-id="b1f38-131">1</span></span>|<span data-ttu-id="b1f38-132">Bylo zahájeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-132">A garbage collection has started.</span></span>|

<span data-ttu-id="b1f38-133">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-133">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-134">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-134">Field name</span></span>|<span data-ttu-id="b1f38-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-135">Data type</span></span>|<span data-ttu-id="b1f38-136">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-137">Výpočtu</span><span class="sxs-lookup"><span data-stu-id="b1f38-137">Count</span></span>|<span data-ttu-id="b1f38-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-138">win:UInt32</span></span>|<span data-ttu-id="b1f38-139">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="b1f38-140">Úrovní</span><span class="sxs-lookup"><span data-stu-id="b1f38-140">Depth</span></span>|<span data-ttu-id="b1f38-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-141">win:UInt32</span></span>|<span data-ttu-id="b1f38-142">Shromažďovaná generace.</span><span class="sxs-lookup"><span data-stu-id="b1f38-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="b1f38-143">Důvod</span><span class="sxs-lookup"><span data-stu-id="b1f38-143">Reason</span></span>|<span data-ttu-id="b1f38-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-144">win:UInt32</span></span>|<span data-ttu-id="b1f38-145">Proč se uvolňování paměti aktivovalo:</span><span class="sxs-lookup"><span data-stu-id="b1f38-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="b1f38-146">0x0 – malé přidělení haldy objektů.</span><span class="sxs-lookup"><span data-stu-id="b1f38-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="b1f38-147">0x1 – vyvolané.</span><span class="sxs-lookup"><span data-stu-id="b1f38-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="b1f38-148">0x2 – nedostatek paměti</span><span class="sxs-lookup"><span data-stu-id="b1f38-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="b1f38-149">0x3 – prázdné.</span><span class="sxs-lookup"><span data-stu-id="b1f38-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="b1f38-150">0x4 – přidělení haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="b1f38-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="b1f38-151">0x5 – nedostatek místa (pro haldu malých objektů)</span><span class="sxs-lookup"><span data-stu-id="b1f38-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="b1f38-152">0x6 mimo prostor (pro haldu velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="b1f38-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="b1f38-153">0x7 – vyvolané, ale nevynucené jako blokující</span><span class="sxs-lookup"><span data-stu-id="b1f38-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="b1f38-154">Typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-154">Type</span></span>|<span data-ttu-id="b1f38-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-155">win:UInt32</span></span>|<span data-ttu-id="b1f38-156">0x0 – blokující uvolňování paměti se nevyskytlo mimo uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b1f38-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="b1f38-157">0x1 – uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="b1f38-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="b1f38-158">0x2 – blokující uvolňování paměti došlo během uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b1f38-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="b1f38-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-159">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-160">win:UInt16</span></span>|<span data-ttu-id="b1f38-161">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="b1f38-162">Událost GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="b1f38-163">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-164">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-164">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-165">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-167">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-167">Informational (4)</span></span>|

<span data-ttu-id="b1f38-168">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-168">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-169">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-169">Event</span></span>|<span data-ttu-id="b1f38-170">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-170">Event ID</span></span>|<span data-ttu-id="b1f38-171">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="b1f38-172">odst</span><span class="sxs-lookup"><span data-stu-id="b1f38-172">2</span></span>|<span data-ttu-id="b1f38-173">Uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="b1f38-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="b1f38-174">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-174">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-175">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-175">Field name</span></span>|<span data-ttu-id="b1f38-176">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-176">Data type</span></span>|<span data-ttu-id="b1f38-177">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-178">Výpočtu</span><span class="sxs-lookup"><span data-stu-id="b1f38-178">Count</span></span>|<span data-ttu-id="b1f38-179">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-179">win:UInt32</span></span>|<span data-ttu-id="b1f38-180">*N*-tou kolekci uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="b1f38-181">Úrovní</span><span class="sxs-lookup"><span data-stu-id="b1f38-181">Depth</span></span>|<span data-ttu-id="b1f38-182">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-182">win:UInt32</span></span>|<span data-ttu-id="b1f38-183">Shromážděná generace.</span><span class="sxs-lookup"><span data-stu-id="b1f38-183">The generation that was collected.</span></span>|
|<span data-ttu-id="b1f38-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-184">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-185">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-185">win:UInt16</span></span>|<span data-ttu-id="b1f38-186">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="b1f38-187">Událost GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="b1f38-188">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-189">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-189">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-190">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-192">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-192">Informational (4)</span></span>|

<span data-ttu-id="b1f38-193">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-193">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-194">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-194">Event</span></span>|<span data-ttu-id="b1f38-195">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-195">Event ID</span></span>|<span data-ttu-id="b1f38-196">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="b1f38-197">4</span><span class="sxs-lookup"><span data-stu-id="b1f38-197">4</span></span>|<span data-ttu-id="b1f38-198">Zobrazuje statistiku haldy na konci každého uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="b1f38-199">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-199">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-200">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-200">Field name</span></span>|<span data-ttu-id="b1f38-201">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-201">Data type</span></span>|<span data-ttu-id="b1f38-202">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="b1f38-203">GenerationSize0</span></span>|<span data-ttu-id="b1f38-204">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-204">win:UInt64</span></span>|<span data-ttu-id="b1f38-205">Velikost paměti generace 0 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b1f38-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="b1f38-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="b1f38-206">TotalPromotedSize0</span></span>|<span data-ttu-id="b1f38-207">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-207">win:UInt64</span></span>|<span data-ttu-id="b1f38-208">Počet bajtů, které jsou povýšeny z generace 0 na generaci 1.</span><span class="sxs-lookup"><span data-stu-id="b1f38-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="b1f38-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="b1f38-209">GenerationSize1</span></span>|<span data-ttu-id="b1f38-210">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-210">win:UInt64</span></span>|<span data-ttu-id="b1f38-211">Velikost paměti 1. generace v bajtech</span><span class="sxs-lookup"><span data-stu-id="b1f38-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="b1f38-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="b1f38-212">TotalPromotedSize1</span></span>|<span data-ttu-id="b1f38-213">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-213">win:UInt64</span></span>|<span data-ttu-id="b1f38-214">Počet bajtů, které jsou povýšeny z generace 1 na generaci 2.</span><span class="sxs-lookup"><span data-stu-id="b1f38-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="b1f38-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="b1f38-215">GenerationSize2</span></span>|<span data-ttu-id="b1f38-216">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-216">win:UInt64</span></span>|<span data-ttu-id="b1f38-217">Velikost paměti generace 2 v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b1f38-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="b1f38-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="b1f38-218">TotalPromotedSize2</span></span>|<span data-ttu-id="b1f38-219">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-219">win:UInt64</span></span>|<span data-ttu-id="b1f38-220">Počet bajtů, které byly zachovány v generaci 2 po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="b1f38-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="b1f38-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="b1f38-221">GenerationSize3</span></span>|<span data-ttu-id="b1f38-222">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-222">win:UInt64</span></span>|<span data-ttu-id="b1f38-223">Velikost haldy velkých objektů v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b1f38-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="b1f38-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="b1f38-224">TotalPromotedSize3</span></span>|<span data-ttu-id="b1f38-225">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-225">win:UInt64</span></span>|<span data-ttu-id="b1f38-226">Počet bajtů, které byly zachovány v haldě velkých objektů po poslední kolekci.</span><span class="sxs-lookup"><span data-stu-id="b1f38-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="b1f38-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="b1f38-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="b1f38-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-228">win:UInt64</span></span>|<span data-ttu-id="b1f38-229">Celková velikost objektů, které jsou připraveny k dokončení, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b1f38-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="b1f38-230">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="b1f38-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="b1f38-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-231">win:UInt64</span></span>|<span data-ttu-id="b1f38-232">Počet objektů, které jsou připraveny k dokončení.</span><span class="sxs-lookup"><span data-stu-id="b1f38-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="b1f38-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="b1f38-233">PinnedObjectCount</span></span>|<span data-ttu-id="b1f38-234">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-234">win:UInt32</span></span>|<span data-ttu-id="b1f38-235">Počet připnutých (nepohyblivých) objektů.</span><span class="sxs-lookup"><span data-stu-id="b1f38-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="b1f38-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="b1f38-236">SinkBlockCount</span></span>|<span data-ttu-id="b1f38-237">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-237">win:UInt32</span></span>|<span data-ttu-id="b1f38-238">Počet používaných synchronizačních bloků.</span><span class="sxs-lookup"><span data-stu-id="b1f38-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="b1f38-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="b1f38-239">GCHandleCount</span></span>|<span data-ttu-id="b1f38-240">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-240">win:UInt32</span></span>|<span data-ttu-id="b1f38-241">Počet používaných obslužných rutin uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="b1f38-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-242">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-243">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-243">win:UInt16</span></span>|<span data-ttu-id="b1f38-244">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="b1f38-245">Událost GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="b1f38-246">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-247">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-247">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-248">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-250">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-250">Informational (4)</span></span>|

<span data-ttu-id="b1f38-251">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-251">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-252">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-252">Event</span></span>|<span data-ttu-id="b1f38-253">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-253">Event ID</span></span>|<span data-ttu-id="b1f38-254">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="b1f38-255">5</span><span class="sxs-lookup"><span data-stu-id="b1f38-255">5</span></span>|<span data-ttu-id="b1f38-256">Vytvořil se nový segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="b1f38-257">Kromě toho, když je trasování povoleno na procesu, který je již spuštěn, tato událost je vyvolána pro každý existující segment.</span><span class="sxs-lookup"><span data-stu-id="b1f38-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="b1f38-258">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-258">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-259">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-259">Field name</span></span>|<span data-ttu-id="b1f38-260">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-260">Data type</span></span>|<span data-ttu-id="b1f38-261">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-262">Adresáře</span><span class="sxs-lookup"><span data-stu-id="b1f38-262">Address</span></span>|<span data-ttu-id="b1f38-263">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-263">win:UInt64</span></span>|<span data-ttu-id="b1f38-264">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="b1f38-264">The address of the segment.</span></span>|
|<span data-ttu-id="b1f38-265">Velikost</span><span class="sxs-lookup"><span data-stu-id="b1f38-265">Size</span></span>|<span data-ttu-id="b1f38-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-266">win:UInt64</span></span>|<span data-ttu-id="b1f38-267">Velikost segmentu</span><span class="sxs-lookup"><span data-stu-id="b1f38-267">The size of the segment.</span></span>|
|<span data-ttu-id="b1f38-268">Typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-268">Type</span></span>|<span data-ttu-id="b1f38-269">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-269">win:UInt32</span></span>|<span data-ttu-id="b1f38-270">0x0 – malá halda objektu.</span><span class="sxs-lookup"><span data-stu-id="b1f38-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="b1f38-271">0x1 – halda velkých objektů</span><span class="sxs-lookup"><span data-stu-id="b1f38-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="b1f38-272">0x2 – halda jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b1f38-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="b1f38-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-273">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-274">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-274">win:UInt16</span></span>|<span data-ttu-id="b1f38-275">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="b1f38-276">Všimněte si, že velikost segmentů přidělených systémem uvolňování paměti je specifická pro konkrétní implementaci a může se kdykoli změnit, včetně pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="b1f38-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="b1f38-277">Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.</span><span class="sxs-lookup"><span data-stu-id="b1f38-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="b1f38-278">Událost GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="b1f38-279">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-280">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-280">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-281">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-283">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-283">Informational (4)</span></span>|

<span data-ttu-id="b1f38-284">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-284">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-285">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-285">Event</span></span>|<span data-ttu-id="b1f38-286">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-286">Event ID</span></span>|<span data-ttu-id="b1f38-287">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="b1f38-288">6</span><span class="sxs-lookup"><span data-stu-id="b1f38-288">6</span></span>|<span data-ttu-id="b1f38-289">Byl uvolněn segment uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="b1f38-290">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-290">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-291">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-291">Field name</span></span>|<span data-ttu-id="b1f38-292">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-292">Data type</span></span>|<span data-ttu-id="b1f38-293">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-294">Adresáře</span><span class="sxs-lookup"><span data-stu-id="b1f38-294">Address</span></span>|<span data-ttu-id="b1f38-295">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-295">win:UInt64</span></span>|<span data-ttu-id="b1f38-296">Adresa segmentu.</span><span class="sxs-lookup"><span data-stu-id="b1f38-296">The address of the segment.</span></span>|
|<span data-ttu-id="b1f38-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-297">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-298">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-298">win:UInt16</span></span>|<span data-ttu-id="b1f38-299">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="b1f38-300">Událost GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="b1f38-301">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-302">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-302">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-303">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-305">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-305">Informational (4)</span></span>|

<span data-ttu-id="b1f38-306">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-306">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-307">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-307">Event</span></span>|<span data-ttu-id="b1f38-308">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-308">Event ID</span></span>|<span data-ttu-id="b1f38-309">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="b1f38-310">čl</span><span class="sxs-lookup"><span data-stu-id="b1f38-310">7</span></span>|<span data-ttu-id="b1f38-311">Bylo zahájeno obnovení z pozastavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b1f38-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="b1f38-312">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="b1f38-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="b1f38-313">Událost GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="b1f38-314">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-315">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-315">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-316">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-318">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-318">Informational (4)</span></span>|

<span data-ttu-id="b1f38-319">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-319">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-320">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-320">Event</span></span>|<span data-ttu-id="b1f38-321">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-321">Event Id</span></span>|<span data-ttu-id="b1f38-322">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="b1f38-323">3</span><span class="sxs-lookup"><span data-stu-id="b1f38-323">3</span></span>|<span data-ttu-id="b1f38-324">Obnovení z odložení modulu CLR (Common Language Runtime) skončilo.</span><span class="sxs-lookup"><span data-stu-id="b1f38-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="b1f38-325">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="b1f38-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="b1f38-326">Událost GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="b1f38-327">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-328">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-328">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-329">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-331">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-331">Informational (4)</span></span>|

<span data-ttu-id="b1f38-332">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-332">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-333">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-333">Event</span></span>|<span data-ttu-id="b1f38-334">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-334">Event ID</span></span>|<span data-ttu-id="b1f38-335">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="b1f38-336">9</span><span class="sxs-lookup"><span data-stu-id="b1f38-336">9</span></span>|<span data-ttu-id="b1f38-337">Začátek pozastavení spouštěcího modulu pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="b1f38-338">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-338">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-339">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-339">Field name</span></span>|<span data-ttu-id="b1f38-340">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-340">Data type</span></span>|<span data-ttu-id="b1f38-341">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-342">Důvod</span><span class="sxs-lookup"><span data-stu-id="b1f38-342">Reason</span></span>|<span data-ttu-id="b1f38-343">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-343">win:UInt16</span></span>|<span data-ttu-id="b1f38-344">0x0 – ostatní</span><span class="sxs-lookup"><span data-stu-id="b1f38-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="b1f38-345">0x1 – uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b1f38-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="b1f38-346">0x2 – vypnutí aplikační domény</span><span class="sxs-lookup"><span data-stu-id="b1f38-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="b1f38-347">0x3 – rozteč kódu.</span><span class="sxs-lookup"><span data-stu-id="b1f38-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="b1f38-348">0x4 – vypnutí</span><span class="sxs-lookup"><span data-stu-id="b1f38-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="b1f38-349">0x5 – ladicí program.</span><span class="sxs-lookup"><span data-stu-id="b1f38-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="b1f38-350">0x6 – příprava pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b1f38-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="b1f38-351">Výpočtu</span><span class="sxs-lookup"><span data-stu-id="b1f38-351">Count</span></span>|<span data-ttu-id="b1f38-352">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-352">win:UInt32</span></span>|<span data-ttu-id="b1f38-353">Počet GC v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="b1f38-353">The GC count at the time.</span></span> <span data-ttu-id="b1f38-354">Obvykle se vám po tomto zobrazení zobrazí další počáteční událost GC a její počet by byl tento počet + 1, protože během uvolňování paměti narůstá index GC.</span><span class="sxs-lookup"><span data-stu-id="b1f38-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="b1f38-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-355">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-356">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-356">win:UInt16</span></span>|<span data-ttu-id="b1f38-357">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="b1f38-358">Událost GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="b1f38-359">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-360">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-360">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-361">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-363">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-363">Informational (4)</span></span>|

<span data-ttu-id="b1f38-364">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-364">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-365">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-365">Event</span></span>|<span data-ttu-id="b1f38-366">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-366">Event ID</span></span>|<span data-ttu-id="b1f38-367">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="b1f38-368">8</span><span class="sxs-lookup"><span data-stu-id="b1f38-368">8</span></span>|<span data-ttu-id="b1f38-369">Konec pozastavení prováděcího modulu pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b1f38-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="b1f38-370">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="b1f38-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="b1f38-371">Událost GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="b1f38-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="b1f38-372">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-373">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-373">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-374">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-376">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-376">Informational (4)</span></span>|

<span data-ttu-id="b1f38-377">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-377">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-378">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-378">Event</span></span>|<span data-ttu-id="b1f38-379">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-379">Event ID</span></span>|<span data-ttu-id="b1f38-380">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="b1f38-381">10pruhový</span><span class="sxs-lookup"><span data-stu-id="b1f38-381">10</span></span>|<span data-ttu-id="b1f38-382">Pokaždé, když se přidělí přibližně 100 KB.</span><span class="sxs-lookup"><span data-stu-id="b1f38-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="b1f38-383">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-383">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-384">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-384">Field name</span></span>|<span data-ttu-id="b1f38-385">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-385">Data type</span></span>|<span data-ttu-id="b1f38-386">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="b1f38-387">AllocationAmount</span></span>|<span data-ttu-id="b1f38-388">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-388">win:UInt32</span></span>|<span data-ttu-id="b1f38-389">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="b1f38-389">The allocation size, in bytes.</span></span> <span data-ttu-id="b1f38-390">Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4 294 967 295 bajtů).</span><span class="sxs-lookup"><span data-stu-id="b1f38-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="b1f38-391">Pokud je přidělení větší, obsahuje toto pole zkrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1f38-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="b1f38-392">Pro velmi velké alokace použijte `AllocationAmount64`.</span><span class="sxs-lookup"><span data-stu-id="b1f38-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="b1f38-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="b1f38-393">AllocationKind</span></span>|<span data-ttu-id="b1f38-394">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-394">win:UInt32</span></span>|<span data-ttu-id="b1f38-395">0x0 – malé přidělení objektů (přidělení je v haldě malých objektů).</span><span class="sxs-lookup"><span data-stu-id="b1f38-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="b1f38-396">0x1 – velké přidělení objektů (přidělení je v haldě velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="b1f38-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="b1f38-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-397">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-398">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-398">win:UInt16</span></span>|<span data-ttu-id="b1f38-399">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="b1f38-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="b1f38-400">AllocationAmount64</span></span>|<span data-ttu-id="b1f38-401">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b1f38-401">win:UInt64</span></span>|<span data-ttu-id="b1f38-402">Velikost alokace (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="b1f38-402">The allocation size, in bytes.</span></span> <span data-ttu-id="b1f38-403">Tato hodnota je přesné pro velmi velké přidělení.</span><span class="sxs-lookup"><span data-stu-id="b1f38-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="b1f38-404">TypeId</span><span class="sxs-lookup"><span data-stu-id="b1f38-404">TypeId</span></span>|<span data-ttu-id="b1f38-405">Win: ukazatel</span><span class="sxs-lookup"><span data-stu-id="b1f38-405">win:Pointer</span></span>|<span data-ttu-id="b1f38-406">Adresa metody.</span><span class="sxs-lookup"><span data-stu-id="b1f38-406">The address of the MethodTable.</span></span> <span data-ttu-id="b1f38-407">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o adresu metody, která odpovídá poslednímu přidělenému objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="b1f38-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="b1f38-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="b1f38-408">TypeName</span></span>|<span data-ttu-id="b1f38-409">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b1f38-409">win:UnicodeString</span></span>|<span data-ttu-id="b1f38-410">Název typu, který byl přidělen.</span><span class="sxs-lookup"><span data-stu-id="b1f38-410">The name of the type that was allocated.</span></span> <span data-ttu-id="b1f38-411">Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ posledního přiděleného objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).</span><span class="sxs-lookup"><span data-stu-id="b1f38-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="b1f38-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="b1f38-412">HeapIndex</span></span>|<span data-ttu-id="b1f38-413">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-413">win:UInt32</span></span>|<span data-ttu-id="b1f38-414">Halda, ve které byl objekt přidělen.</span><span class="sxs-lookup"><span data-stu-id="b1f38-414">The heap where the object was allocated.</span></span> <span data-ttu-id="b1f38-415">Tato hodnota je 0 (nula) při spuštění s uvolňováním paměti pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="b1f38-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="b1f38-416">Událost GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="b1f38-417">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-418">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-418">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-419">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-421">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-421">Informational (4)</span></span>|

<span data-ttu-id="b1f38-422">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-422">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-423">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-423">Event</span></span>|<span data-ttu-id="b1f38-424">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-424">Event ID</span></span>|<span data-ttu-id="b1f38-425">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="b1f38-426">čtrnáct</span><span class="sxs-lookup"><span data-stu-id="b1f38-426">14</span></span>|<span data-ttu-id="b1f38-427">Začátek spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b1f38-427">The start of running finalizers.</span></span>|

<span data-ttu-id="b1f38-428">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="b1f38-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="b1f38-429">Událost GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="b1f38-430">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-431">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-431">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-432">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-434">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-434">Informational (4)</span></span>|

<span data-ttu-id="b1f38-435">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-435">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-436">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-436">Event</span></span>|<span data-ttu-id="b1f38-437">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-437">Event ID</span></span>|<span data-ttu-id="b1f38-438">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="b1f38-439">13,5</span><span class="sxs-lookup"><span data-stu-id="b1f38-439">13</span></span>|<span data-ttu-id="b1f38-440">Konec spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b1f38-440">The end of running finalizers.</span></span>|

<span data-ttu-id="b1f38-441">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="b1f38-441">The following table shows the event data:</span></span>

|<span data-ttu-id="b1f38-442">název pole</span><span class="sxs-lookup"><span data-stu-id="b1f38-442">Field name</span></span>|<span data-ttu-id="b1f38-443">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b1f38-443">Data type</span></span>|<span data-ttu-id="b1f38-444">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f38-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="b1f38-445">Výpočtu</span><span class="sxs-lookup"><span data-stu-id="b1f38-445">Count</span></span>|<span data-ttu-id="b1f38-446">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b1f38-446">win:UInt32</span></span>|<span data-ttu-id="b1f38-447">Počet finalizační metody, které byly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="b1f38-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="b1f38-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b1f38-448">ClrInstanceID</span></span>|<span data-ttu-id="b1f38-449">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b1f38-449">win:UInt16</span></span>|<span data-ttu-id="b1f38-450">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b1f38-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="b1f38-451">Událost GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="b1f38-452">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-453">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-453">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-454">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-456">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-456">Informational (4)</span></span>|
|<span data-ttu-id="b1f38-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="b1f38-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="b1f38-458">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-458">Informational (4)</span></span>|

<span data-ttu-id="b1f38-459">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-459">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-460">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-460">Event</span></span>|<span data-ttu-id="b1f38-461">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-461">Event ID</span></span>|<span data-ttu-id="b1f38-462">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="b1f38-463">odst</span><span class="sxs-lookup"><span data-stu-id="b1f38-463">11</span></span>|<span data-ttu-id="b1f38-464">Bylo vytvořeno souběžné vlákno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b1f38-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="b1f38-465">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="b1f38-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="b1f38-466">Událost GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="b1f38-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="b1f38-467">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="b1f38-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="b1f38-468">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b1f38-468">Keyword for raising the event</span></span>|<span data-ttu-id="b1f38-469">Obsah</span><span class="sxs-lookup"><span data-stu-id="b1f38-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="b1f38-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="b1f38-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b1f38-471">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-471">Informational (4)</span></span>|
|<span data-ttu-id="b1f38-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="b1f38-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="b1f38-473">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="b1f38-473">Informational (4)</span></span>|

<span data-ttu-id="b1f38-474">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="b1f38-474">The following table shows the event information:</span></span>

|<span data-ttu-id="b1f38-475">Událost</span><span class="sxs-lookup"><span data-stu-id="b1f38-475">Event</span></span>|<span data-ttu-id="b1f38-476">ID události</span><span class="sxs-lookup"><span data-stu-id="b1f38-476">Event ID</span></span>|<span data-ttu-id="b1f38-477">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="b1f38-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="b1f38-478">12,5</span><span class="sxs-lookup"><span data-stu-id="b1f38-478">12</span></span>|<span data-ttu-id="b1f38-479">Vlákno souběžného uvolňování paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="b1f38-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="b1f38-480">Žádná data události</span><span class="sxs-lookup"><span data-stu-id="b1f38-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1f38-481">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1f38-481">See also</span></span>

- [<span data-ttu-id="b1f38-482">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="b1f38-482">CLR ETW Events</span></span>](clr-etw-events.md)
