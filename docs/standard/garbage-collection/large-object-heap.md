---
title: LOH ve Windows - .NET
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 5125b76dd26ffa4fb363ecf8449f65b490f57b93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283622"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="0f3f5-102">Haldy velkých objektů v systémech Windows</span><span class="sxs-lookup"><span data-stu-id="0f3f5-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="0f3f5-103">Uvolňování paměti .NET (GC) rozděluje objekty na malé a velké objekty.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="0f3f5-104">Pokud je objekt velký, některé jeho atributy se stanou významnějšími než v případě, že je objekt malý.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="0f3f5-105">Například komprimace – to znamená kopírování v paměti jinde na haldě – může být nákladné.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="0f3f5-106">Z tohoto důvodu .NET GarbageCollector umístí velké objekty na haldy velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="0f3f5-107">V tomto tématu se podíváme na haldu velkého objektu do hloubky.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="0f3f5-108">Budeme diskutovat o tom, co kvalifikuje objekt jako velký objekt, jak jsou shromažďovány tyto velké objekty a jaký druh výkonu důsledky velké objekty uložit.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f3f5-109">Toto téma popisuje haldu velkých objektů v rozhraní .NET Framework a .NET Core spuštěné pouze v systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="0f3f5-110">Nezahrnuje LOH spuštěné na implementacích .NET na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="0f3f5-111">Jak objekt skončí na haldě velkého objektu a jak je gc zpracovává</span><span class="sxs-lookup"><span data-stu-id="0f3f5-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="0f3f5-112">Pokud je objekt větší nebo roven velikosti 85 000 bajtů, je považován za velký objekt.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-112">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="0f3f5-113">Toto číslo bylo určeno laděním výkonu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="0f3f5-114">Pokud je požadavek na přidělení objektu pro 85 000 nebo více bajtů, přiděluje jej runtime na haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="0f3f5-115">Chcete-li pochopit, co to znamená, je užitečné prozkoumat některé základy o .NET GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="0f3f5-116">Uvolňování .NET je generační kolektor.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="0f3f5-117">Má tři generace: generace 0, generace 1 a generace 2.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="0f3f5-118">Důvodem pro mít 3 generace je, že v dobře vyladěné aplikaci, většina objektů zemře v gen0.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="0f3f5-119">Například v serverové aplikaci by přidělení přidružená ke každému požadavku měla po dokončení požadavku zemřít.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="0f3f5-120">In-letu přidělení žádosti bude dělat to do gen1 a zemřít tam.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="0f3f5-121">Gen1 v podstatě funguje jako nárazník mezi oblastmi mladých objektů a oblastmi objektů s dlouhou životností.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="0f3f5-122">Malé objekty jsou vždy přiděleny v generaci 0 a v závislosti na jejich životnosti může být povýšen na generaci 1 nebo generace2.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="0f3f5-123">Velké objekty jsou vždy přiděleny v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="0f3f5-124">Velké objekty patří do generace 2, protože jsou shromažďovány pouze během kolekce generace 2.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="0f3f5-125">Když generace jsou shromažďovány, všechny jeho mladší generace jsou také shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="0f3f5-126">Například když generace 1 GC se stane, jak generace 1 a 0 jsou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="0f3f5-127">A když generace 2 GC se stane, celá halda je shromažďována.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="0f3f5-128">Z tohoto důvodu generace 2 GC se také nazývá *úplné GC*.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="0f3f5-129">Tento článek odkazuje na generace 2 GC namísto úplné GC, ale podmínky jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="0f3f5-130">Generace poskytují logický pohled na haldu GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="0f3f5-131">Fyzicky objekty žijí ve spravovaných segmentech haldy.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="0f3f5-132">Segment *spravované haldy* je blok paměti, který gc rezervy z operačního systému voláním [VirtualAlloc funkce](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jménem spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="0f3f5-133">Při načtení CLR GC přiděluje dva počáteční haldy segmenty: jeden pro malé objekty (haldy malý objekt nebo SOH), a jeden pro velké objekty (velký objekt haldy).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="0f3f5-134">Požadavky na přidělení jsou pak splněny umístěním spravované objekty na tyto segmenty spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="0f3f5-135">Pokud je objekt menší než 85 000 bajtů, je umístěn na segment pro SOH; v opačném případě je umístěn na segment LOH.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="0f3f5-136">Segmenty jsou potvrzeny (v menších blocích), protože na ně je přidělováno více a více objektů.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="0f3f5-137">Pro SOH objekty, které přežijí GC jsou povýšeni na další generaci.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="0f3f5-138">Objekty, které přežijí kolekci generace 0, jsou nyní považovány za objekty generace 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="0f3f5-139">Objekty, které přežijí nejstarší generaci, jsou však stále považovány za nejstarší generace.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="0f3f5-140">Jinými slovy, přeživší z generace 2 jsou objekty generace 2; a přeživší z LOH jsou LOH objekty (které jsou shromažďovány s gen2).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="0f3f5-141">Uživatelský kód lze přidělit pouze v generaci 0 (malé objekty) nebo LOH (velké objekty).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="0f3f5-142">Pouze GC může "přidělit" objekty v generaci 1 (podporou přeživších z generace 0) a generace 2 (podporou přeživších z generací 1 a 2).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="0f3f5-143">Při uvolnění paměti je spuštěna, GC trasování prostřednictvím živých objektů a komprimuje je.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="0f3f5-144">Ale protože zhutnění je drahé, GC *zametá* LOH; vytvoří volný seznam z mrtvých objektů, které lze později znovu použít k uspokojení požadavků na přidělení velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="0f3f5-145">Přilehlé mrtvé objekty jsou rozděleny do jednoho volného objektu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="0f3f5-146">.NET Core a .NET Framework (počínaje rozhraním .NET <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> Framework 4.5.1) zahrnují vlastnost, která uživatelům umožňuje určit, že loh by měl být komprimován během dalšího úplného blokování GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="0f3f5-147">A v budoucnu .NET může rozhodnout o komprimovat LOH automaticky.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="0f3f5-148">To znamená, že pokud přidělujete velké objekty a chcete se ujistit, že se nepohybují, měli byste je stále připnout.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="0f3f5-149">Obrázek 1 znázorňuje scénář, kde GC tvoří generace `Obj1` `Obj3` 1 po první generaci 0 GC kde a `Obj2` `Obj5` jsou mrtvé a tvoří generace 2 po první generaci 1 GC kde a jsou mrtvé.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="0f3f5-150">Všimněte si, že tyto a následující obrázky jsou pouze pro ilustrační účely; obsahují jen velmi málo objektů, aby lépe ukázat, co se děje na haldě.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="0f3f5-151">Ve skutečnosti mnoho dalších objektů jsou obvykle zapojeny do GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-151">In reality, many more objects are typically involved in a GC.</span></span>

![Obrázek 1: A gen 0 GC a gen 1 GC](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="0f3f5-153">Obrázek 1: Generace 0 a generace 1 GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="0f3f5-154">Obrázek 2 ukazuje, že po `Obj1` generaci `Obj2` 2 GC, která viděla, že a jsou mrtvé, GC `Obj1` `Obj2`tvoří souvislé volné místo z `Obj4`paměti, které byly použity a , který pak byl použit k uspokojení požadavku na přidělení pro .</span><span class="sxs-lookup"><span data-stu-id="0f3f5-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="0f3f5-155">Mezeru za posledním `Obj3`objektem , na konec segmentu lze také použít ke splnění požadavků na přidělení.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Obrázek 2: Po gen 2 GC](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="0f3f5-157">Obrázek 2: Po generaci 2 GC</span><span class="sxs-lookup"><span data-stu-id="0f3f5-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="0f3f5-158">Pokud není dostatek volného místa pro požadavky na přidělení velkých objektů, gc nejprve pokusí získat více segmentů z operačního prostoru.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="0f3f5-159">Pokud se to nepodaří, spustí generaci 2 GC v naději, že uvolní nějaký prostor.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="0f3f5-160">Během generace 1 nebo generace 2 GC uvolňování uvolní segmenty, které nemají žádné živé objekty na ně zpět do operačního systému voláním [VirtualFree funkce](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="0f3f5-161">Mezera za poslední živý objekt na konci segmentu je zrušena (s výjimkou dočasného segmentu, kde gen0/gen1 live, kde uvolňování paměti zachovat některé potvrzené, protože vaše aplikace bude přidělování v něm hned).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="0f3f5-162">A volné prostory zůstávají potvrzeny, i když jsou resetovány, což znamená, že operační systém nemusí zapisovat data do nich zpět na disk.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="0f3f5-163">Vzhledem k tomu, že LOH se shromažďuje pouze během generace 2 GC, může být segment LOH uvolněn pouze během takového GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="0f3f5-164">Obrázek 3 znázorňuje scénář, kde uvolňování uvolní jeden segment (segment 2) zpět do operačního systému a zruší potvrzení více místa na zbývající segmenty.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="0f3f5-165">Pokud potřebuje použít zrušené místo na konci segmentu k uspokojení požadavků na přidělení velkých objektů, znovu potvrdí paměť.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="0f3f5-166">(Vysvětlení potvrzení/vyřazení naleznete v dokumentaci k [aplikaci VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Obrázek 3: LOH po gen 2 GC](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="0f3f5-168">Obrázek 3: LOH po generaci 2 GC</span><span class="sxs-lookup"><span data-stu-id="0f3f5-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="0f3f5-169">Kdy je velký objekt shromážděn?</span><span class="sxs-lookup"><span data-stu-id="0f3f5-169">When is a large object collected?</span></span>

<span data-ttu-id="0f3f5-170">Obecně platí, že GC nastane, když dojde k jedné z následujících podmínek 3:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-170">In general, a GC occurs when one of the following 3 conditions happens:</span></span>

- <span data-ttu-id="0f3f5-171">Přidělení překračuje prahovou hodnotu generace 0 nebo velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="0f3f5-172">Prahová hodnota je vlastností generace.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="0f3f5-173">Prahová hodnota pro generaci je nastavena, když do ní systém uvolňování paměti přiděluje objekty.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="0f3f5-174">Při překročení prahové hodnoty gc je aktivována na tuto generaci.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="0f3f5-175">Při přidělování malé nebo velké objekty, spotřebovávají generace 0 a LOH prahové hodnoty, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="0f3f5-176">Při uvolňování přiděluje do generace 1 a 2, spotřebovává jejich prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="0f3f5-177">Tyto prahové hodnoty jsou dynamicky vyladěny při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="0f3f5-178">To je typický případ; většina řadičů domény dochází z důvodu přidělení na spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="0f3f5-179">Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> je volána.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="0f3f5-180">Pokud je <xref:System.GC.Collect?displayProperty=nameWithType> volána metoda bez parametrů <xref:System.GC.MaxGeneration?displayProperty=nameWithType> nebo jiné přetížení je předán jako argument, LOH je shromažďována spolu se zbytkem spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="0f3f5-181">Systém je v situaci nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="0f3f5-182">K tomu dochází, když systém uvolňování paměti obdrží oznámení vysoké paměti z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="0f3f5-183">Pokud systém uvolňování paměti si myslí, že provedení generace 2 GC bude produktivní, aktivuje jeden.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="0f3f5-184">Důsledky výkonu LOH</span><span class="sxs-lookup"><span data-stu-id="0f3f5-184">LOH Performance Implications</span></span>

<span data-ttu-id="0f3f5-185">Přidělení haldy velkého objektu ovlivňují výkon následujícími způsoby.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="0f3f5-186">Náklady na přidělení.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-186">Allocation cost.</span></span>

  <span data-ttu-id="0f3f5-187">CLR poskytuje záruku, že paměť pro každý nový objekt, který vydává, je vymazána.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="0f3f5-188">To znamená, že náklady na přidělení velkého objektu je zcela dominuje vymazání paměti (pokud se aktivuje GC).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="0f3f5-189">Pokud trvá 2 cykly vymazat jeden bajt, trvá 170 000 cyklů vymazat nejmenší velký objekt.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="0f3f5-190">Vymazání paměti objektu 16 MB v počítači s frekvencí 2 GHz trvá přibližně 16 ms.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="0f3f5-191">To je poměrně velká cena.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-191">That's a rather large cost.</span></span>

- <span data-ttu-id="0f3f5-192">Náklady na vyzvednutí.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-192">Collection cost.</span></span>

  <span data-ttu-id="0f3f5-193">Vzhledem k tomu, že LOH a generace 2 jsou shromažďovány společně, pokud je překročena prahová hodnota jednoho z nich, je spuštěna kolekce generace 2.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="0f3f5-194">Pokud generace 2 kolekce se aktivuje z důvodu LOH, generace 2 nemusí být nutně mnohem menší po GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="0f3f5-195">Pokud není mnoho dat na generaci 2, to má minimální dopad.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="0f3f5-196">Ale pokud generace 2 je velký, může způsobit problémy s výkonem, pokud jsou spuštěny mnoho generace 2 GCs.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="0f3f5-197">Pokud mnoho velkých objektů jsou přiděleny na velmi dočasné bázi a máte velký SOH, můžete trávit příliš mnoho času dělá GCs.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="0f3f5-198">Kromě toho náklady na přidělení může opravdu sečíst, pokud budete mít přidělování a pustil opravdu velké objekty.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="0f3f5-199">Prvky pole s typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-199">Array elements with reference types.</span></span>

  <span data-ttu-id="0f3f5-200">Velmi velké objekty na LOH jsou obvykle pole (je velmi vzácné mít objekt instance, který je opravdu velký).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="0f3f5-201">Pokud prvky pole jsou bohaté na odkazy, vzniknou náklady, které nejsou k dispozici, pokud prvky nejsou bohaté na odkazy.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="0f3f5-202">Pokud prvek neobsahuje žádné odkazy, systém uvolňování paměti nemusí vůbec procházet polem.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="0f3f5-203">Pokud například použijete pole k ukládání uzlů v binárním stromu, jedním ze způsobů, jak jej implementovat, je odkazovat na pravý a levý uzel uzlu skutečnými uzly:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="0f3f5-204">Pokud `num_nodes` je velký, uvolňování musí projít alespoň dva odkazy na prvek.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="0f3f5-205">Alternativním přístupem je uložení indexu pravého a levého uzlu:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="0f3f5-206">Místo toho, aby odkazoval data levého uzlu jako `left.d` `binary_tr[left_index].d`, budete odkazovat na to jako .</span><span class="sxs-lookup"><span data-stu-id="0f3f5-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="0f3f5-207">A uvolňování nemusí hledat žádné odkazy pro levý a pravý uzel.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="0f3f5-208">Ze tří faktorů jsou první dva obvykle významnější než třetí.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="0f3f5-209">Z tohoto důvodu doporučujeme přidělit fond velkých objektů, které znovu použít namísto přidělování dočasných.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="0f3f5-210">Shromažďování údajů o výkonu pro LOH</span><span class="sxs-lookup"><span data-stu-id="0f3f5-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="0f3f5-211">Před shromažďováním údajů o výkonu pro určitou oblast byste již měli provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="0f3f5-212">Našel jsem důkaz, že byste se měl podívat do této oblasti.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="0f3f5-213">Vyčerpané další oblasti, které znáte, aniž byste našli něco, co by mohlo vysvětlit problém s výkonem, který jste viděli.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="0f3f5-214">Podívejte se na blog [Pochopit problém, než se pokusíte najít řešení](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) pro další informace o základech paměti a cpu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-214">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="0f3f5-215">Ke shromažďování dat o výkonu LOH můžete použít následující nástroje:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="0f3f5-216">Čítače výkonu paměti CLR rozhraní NET</span><span class="sxs-lookup"><span data-stu-id="0f3f5-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="0f3f5-217">Trasování událostí pro Windows – události</span><span class="sxs-lookup"><span data-stu-id="0f3f5-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="0f3f5-218">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="0f3f5-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="0f3f5-219">Čítače výkonu paměti CLR rozhraní NET</span><span class="sxs-lookup"><span data-stu-id="0f3f5-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="0f3f5-220">Tyto čítače výkonu jsou obvykle dobrým prvním krokem při zkoumání problémů s výkonem (i když doporučujeme použít [události ETW](#etw-events)).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="0f3f5-221">Sledování výkonu nakonfigurujete přidáním požadovaných čítačů, jak ukazuje obrázek 4.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="0f3f5-222">Ty, které jsou relevantní pro LOH jsou:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="0f3f5-223">**Gen 2 Sbírky**</span><span class="sxs-lookup"><span data-stu-id="0f3f5-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="0f3f5-224">Zobrazuje počet, kolikrát došlo ke vzniku 2 GOd od zahájení procesu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="0f3f5-225">Čítač se zintáčí na konci kolekce generace 2 (také nazývá úplné uvolnění paměti).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="0f3f5-226">Tento čítač zobrazuje poslední pozorovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="0f3f5-227">**Velikost haldy velkých objektů**</span><span class="sxs-lookup"><span data-stu-id="0f3f5-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="0f3f5-228">Zobrazí aktuální velikost loh v bajtech, včetně volného místa.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="0f3f5-229">Tento čítač je aktualizován na konci uvolňování paměti, nikoli při každém přidělení.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="0f3f5-230">Běžný způsob, jak se podívat na čítače výkonu je s Sledování výkonu (perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="0f3f5-231">Pomocí funkce Přidat čítače přidejte zajímavý čítač pro procesy, na kterých vám záleží.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="0f3f5-232">Data čítače výkonu můžete uložit do souboru protokolu, jak ukazuje obrázek 4:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="0f3f5-233">![Snímek obrazovky s přidáním čítačů výkonu](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="0f3f5-233">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="0f3f5-234">Obrázek 4: LOH po generaci 2 GC</span><span class="sxs-lookup"><span data-stu-id="0f3f5-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="0f3f5-235">Čítače výkonu lze také dotazovat programově.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="0f3f5-236">Mnoho lidí je sbírat tímto způsobem jako součást jejich rutinní testování procesu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="0f3f5-237">Když si všimnou čítačů s hodnotami, které jsou neobvyklé, používají jiné prostředky, aby získali podrobnější údaje, které pomáhají s vyšetřováním.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="0f3f5-238">Doporučujeme použít události ETW namísto čítačů výkonu, protože ETW poskytuje mnohem bohatší informace.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="0f3f5-239">Trasování událostí pro Windows – události</span><span class="sxs-lookup"><span data-stu-id="0f3f5-239">ETW events</span></span>

<span data-ttu-id="0f3f5-240">Systém uvolňování paměti poskytuje bohatou sadu událostí ETW, které vám pomohou pochopit, co halda dělá a proč.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="0f3f5-241">Následující blogové příspěvky ukazují, jak shromažďovat a chápat události GC s ETW:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="0f3f5-242">Gc ETW Události - 1</span><span class="sxs-lookup"><span data-stu-id="0f3f5-242">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="0f3f5-243">Gc ETW Události - 2</span><span class="sxs-lookup"><span data-stu-id="0f3f5-243">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="0f3f5-244">Gc ETW Události - 3</span><span class="sxs-lookup"><span data-stu-id="0f3f5-244">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="0f3f5-245">Gc ETW Události - 4</span><span class="sxs-lookup"><span data-stu-id="0f3f5-245">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="0f3f5-246">Chcete-li identifikovat nadměrné generování 2 GCs způsobené dočasné přidělení LOH, podívejte se na aktivační důvod sloupec pro g.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="0f3f5-247">Pro jednoduchý test, který přiděluje pouze dočasné velké objekty, můžete shromažďovat informace o událostech ETW s následujícím příkazovým řádkem [PerfView:](https://www.microsoft.com/download/details.aspx?id=28567)</span><span class="sxs-lookup"><span data-stu-id="0f3f5-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="0f3f5-248">Výsledkem je něco jako toto:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-248">The result is something like this:</span></span>

<span data-ttu-id="0f3f5-249">![Snímek obrazovky, který zobrazuje události ETW v PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="0f3f5-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="0f3f5-250">Obrázek 5: Události ETW zobrazené pomocí perfview</span><span class="sxs-lookup"><span data-stu-id="0f3f5-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="0f3f5-251">Jak můžete vidět, všechny gcs jsou generace 2 GC a všechny jsou spuštěny AllocLarge, což znamená, že přidělení velkého objektu spustilo tento GC.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="0f3f5-252">Víme, že tyto příděly jsou dočasné, protože **loh míra přežití %** sloupec říká, že 1%.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="0f3f5-253">Můžete shromažďovat další události ETW, které vám řeknou, kdo tyto velké objekty přidělil.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="0f3f5-254">Následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="0f3f5-255">shromažďuje AllocationTick událost, která je aktivována přibližně každý 100 kB v hodnotě přidělení.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="0f3f5-256">Jinými slovy událost je aktivována pokaždé, když je přidělen velký objekt.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="0f3f5-257">Pak se můžete podívat na jeden z gc haldy Alloc zobrazení, které ukazují volání zásobníky, které přiděleny velké objekty:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="0f3f5-258">![Snímek obrazovky, který zobrazuje zobrazení haldy systému uvolňování paměti.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="0f3f5-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="0f3f5-259">Obrázek 6: Zobrazení Alloc haldy GC</span><span class="sxs-lookup"><span data-stu-id="0f3f5-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="0f3f5-260">Jak můžete vidět, jedná se o velmi jednoduchý test, `Main` který právě přiděluje velké objekty z jeho metody.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="0f3f5-261">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="0f3f5-261">A debugger</span></span>

<span data-ttu-id="0f3f5-262">Pokud vše, co máte, je výpis stavu paměti a je třeba se podívat na jaké objekty jsou ve skutečnosti na LOH, můžete použít [rozšíření ladicího programu SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) poskytované rozhraním .NET.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="0f3f5-263">Ladicí příkazy uvedené v této části jsou použitelné pro [ladicí program systému Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="0f3f5-264">Následující ukazuje ukázkový výstup z analýzy LOH:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-264">The following shows sample output from analyzing the LOH:</span></span>

```console
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

<span data-ttu-id="0f3f5-265">Velikost haldy LOH je (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtů.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="0f3f5-266">Mezi adresami 023e1000 a 033db630, 8,008,736 bajtů <xref:System.Object?displayProperty=nameWithType> jsou obsazeny pole objektů, 6,663,696 <xref:System.Byte?displayProperty=nameWithType> bajtů jsou obsazeny pole objektů a 2,081,792 bajty jsou obsazeny volné místo.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="0f3f5-267">V některých případech ladicí program ukazuje, že celková velikost LOH je menší než 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="0f3f5-268">K tomu dochází, protože samotný runtime používá LOH přidělit některé objekty, které jsou menší než velký objekt.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="0f3f5-269">Vzhledem k tomu, LOH není zhutněn, někdy LOH je myšlenka být zdrojem fragmentace.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="0f3f5-270">Fragmentací se rozumí:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-270">Fragmentation means:</span></span>

- <span data-ttu-id="0f3f5-271">Fragmentace spravované haldy, která je označena množstvím volného místa mezi spravovanými objekty.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="0f3f5-272">V SoS `!dumpheap –type Free` příkaz zobrazí velikost volného místa mezi spravovanými objekty.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="0f3f5-273">Fragmentace adresního prostoru virtuální paměti (VM), `MEM_FREE`což je paměť označená jako .</span><span class="sxs-lookup"><span data-stu-id="0f3f5-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="0f3f5-274">Můžete si ji pomocí různých ladicích příkazů v windbg.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="0f3f5-275">Následující příklad ukazuje fragmentaci v prostoru virtuálního montovana:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-275">The following example shows fragmentation in the VM space:</span></span>

   ```console
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

<span data-ttu-id="0f3f5-276">Je běžnější zobrazit fragmentaci virtuálního trhu způsobenou dočasnými velkými objekty, které vyžadují, aby systém uvolňování paměti často získával nové segmenty spravované haldy z operačního systému a uvolnil prázdné zpět do operačního systému.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="0f3f5-277">Chcete-li ověřit, zda LOH způsobuje fragmentaci virtuálního počítače, můžete nastavit zarážku na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) a [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) zobrazíte, kdo je volat.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="0f3f5-278">Chcete-li například zjistit, kdo se pokusil přidělit bloky virtuální paměti větší než 8MBB z operačního systému, můžete nastavit zarážku takto:</span><span class="sxs-lookup"><span data-stu-id="0f3f5-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="0f3f5-279">Tento příkaz se rozdělí do ladicího programu a zobrazí zásobník volání pouze v [případě, že virtualalloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) je volána s velikostí přidělení větší než 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-279">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="0f3f5-280">CLR 2.0 přidal funkci s názvem *Hromadění virtuálních počítačích,* která může být užitečná pro scénáře, kde jsou často získávány a vydávány segmenty (včetně velkých a malých objektů).</span><span class="sxs-lookup"><span data-stu-id="0f3f5-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="0f3f5-281">Chcete-li zadat hromadění virtuálních montovny, zadejte příznak spuštění volaný `STARTUP_HOARD_GC_VM` prostřednictvím hostitelského rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="0f3f5-282">Místo uvolnění prázdné segmenty zpět do operačního systému, CLR zruší potvrzení paměti na tyto segmenty a umístí je do pohotovostního seznamu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="0f3f5-283">(Všimněte si, že CLR neumožňuje pro segmenty, které jsou příliš velké.) CLR později používá tyto segmenty k uspokojení nových požadavků segmentu.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="0f3f5-284">Při příštím, že vaše aplikace potřebuje nový segment, CLR používá jeden z tohoto seznamu pohotovostního režimu, pokud může najít ten, který je dostatečně velký.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="0f3f5-285">Hromadění virtuálních počítačů je také užitečné pro aplikace, které se chtějí držet segmenty, které již získaly, jako jsou některé serverové aplikace, které jsou dominantní aplikace spuštěné v systému, aby se zabránilo výjimkám z paměti.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="0f3f5-286">Důrazně doporučujeme, abyste pečlivě otestovali aplikaci při použití této funkce, abyste zajistili, že vaše aplikace má poměrně stabilní využití paměti.</span><span class="sxs-lookup"><span data-stu-id="0f3f5-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
