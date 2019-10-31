---
title: Halda velkých objektů v systémech Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 618db9faff137e6ff0f878c928e3a889cff37838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120940"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="e6898-102">Halda velkých objektů v systémech Windows</span><span class="sxs-lookup"><span data-stu-id="e6898-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="e6898-103">Uvolňování paměti .NET (GC) rozděluje objekty až do malých a velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="e6898-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="e6898-104">Když je objekt rozsáhlý, některé z jeho atributů se stanou důležitější, než když je objekt malý.</span><span class="sxs-lookup"><span data-stu-id="e6898-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="e6898-105">Například jeho komprimací – to znamená, že je třeba ho zkopírovat do paměti jinde na haldě – může být nákladné.</span><span class="sxs-lookup"><span data-stu-id="e6898-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="e6898-106">Z tohoto důvodu systém uvolňování paměti .NET umístí velké objekty na haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="e6898-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="e6898-107">V tomto tématu se podrobněji podíváme na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="e6898-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="e6898-108">Probereme, co tento objekt jako velký má, jak se shromažďují tyto velké objekty a jaký druh vlivu na výkon mají velké objekty.</span><span class="sxs-lookup"><span data-stu-id="e6898-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6898-109">Toto téma popisuje haldu velkých objektů v .NET Framework a .NET Core, které běží pouze na systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="e6898-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="e6898-110">Nepokrývá LOH běžící na implementacích .NET na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="e6898-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="e6898-111">Jak objekt skončí na haldě velkých objektů a jak je v GC zpracovává</span><span class="sxs-lookup"><span data-stu-id="e6898-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="e6898-112">Pokud je objekt větší nebo roven 85 000 bajtů, je považován za velký objekt.</span><span class="sxs-lookup"><span data-stu-id="e6898-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="e6898-113">Toto číslo bylo určeno vyladěním výkonu.</span><span class="sxs-lookup"><span data-stu-id="e6898-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="e6898-114">Pokud je požadavek na přidělení objektu na 85 000 nebo více bajtů, modul runtime ho přidělí na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="e6898-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="e6898-115">Pro pochopení toho, co to znamená, je vhodné si prostudovat některé zásadní informace o modulu .NET GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="e6898-116">Uvolňování paměti .NET je kolekce.</span><span class="sxs-lookup"><span data-stu-id="e6898-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="e6898-117">Má tři generace: generace 0, generace 1 a generace 2.</span><span class="sxs-lookup"><span data-stu-id="e6898-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="e6898-118">Důvodem pro 3 generace je to, že v dobře vyladěné aplikaci většina objektů v gen0.</span><span class="sxs-lookup"><span data-stu-id="e6898-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="e6898-119">Například v serverové aplikaci musí být přidělení přidružená ke každé žádosti po dokončení žádosti kostka.</span><span class="sxs-lookup"><span data-stu-id="e6898-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="e6898-120">Požadavky na přidělení v letadle provedou Gen1 a Die.</span><span class="sxs-lookup"><span data-stu-id="e6898-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="e6898-121">Gen1 v podstatě funguje jako vyrovnávací paměť mezi mladými oblastmi objektů a dlouhodobými oblastmi objektů.</span><span class="sxs-lookup"><span data-stu-id="e6898-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="e6898-122">Malé objekty jsou vždy přiděleny v generaci 0 a v závislosti na jejich životnosti mohou být povýšeny na generaci 1 nebo generation2.</span><span class="sxs-lookup"><span data-stu-id="e6898-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="e6898-123">Velké objekty jsou vždy přiděleny v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="e6898-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="e6898-124">Velké objekty patří do generace 2, protože jsou shromažďovány pouze během kolekce generace 2.</span><span class="sxs-lookup"><span data-stu-id="e6898-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="e6898-125">Po shromáždění generace se shromažďují také všechny jeho mladší generace.</span><span class="sxs-lookup"><span data-stu-id="e6898-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="e6898-126">Například když dojde k 1. generaci GC, shromažďují se obě generace 1 a 0.</span><span class="sxs-lookup"><span data-stu-id="e6898-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="e6898-127">A když dojde k GC generace 2, bude shromážděna celá halda.</span><span class="sxs-lookup"><span data-stu-id="e6898-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="e6898-128">Z tohoto důvodu se také označuje jako *úplný GC*. generace 2 GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="e6898-129">Tento článek odkazuje na generaci 2 GC místo úplného uvolňování paměti, ale tyto výrazy jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="e6898-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="e6898-130">Generace poskytují logické zobrazení haldy GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="e6898-131">Fyzicky objekty ve spravovaných segmentech haldy jsou živé.</span><span class="sxs-lookup"><span data-stu-id="e6898-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="e6898-132">*Segment spravované haldy* je blok paměti, který GC vyhradí z operačního systému voláním [funkce VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jménem spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e6898-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="e6898-133">Když je modul CLR načten, uvolňování paměti přidělí dva počáteční segmenty haldy: jeden pro malé objekty (halda malých objektů nebo SOH) a jeden pro velké objekty (Large Object halda).</span><span class="sxs-lookup"><span data-stu-id="e6898-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="e6898-134">Žádosti o přidělení se pak splní vložením spravovaných objektů na tyto spravované segmenty haldy.</span><span class="sxs-lookup"><span data-stu-id="e6898-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="e6898-135">Pokud je objekt menší než 85 000 bajtů, je umístěn do segmentu pro SOH; v opačném případě je umístěn na segment LOH.</span><span class="sxs-lookup"><span data-stu-id="e6898-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="e6898-136">Segmenty jsou potvrzeny (v menších blocích), protože jsou jim přiděleny další a více objektů.</span><span class="sxs-lookup"><span data-stu-id="e6898-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="e6898-137">Pro SOH jsou objekty, které jsou v GC, povýšeny na novou generaci.</span><span class="sxs-lookup"><span data-stu-id="e6898-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="e6898-138">Objekty, které jsou zachovány kolekcí 0. generace, se nyní považují za objekty generace 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e6898-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="e6898-139">Nicméně objekty, které zůstávají nejstarší generace, jsou stále považovány za nejstarší generace.</span><span class="sxs-lookup"><span data-stu-id="e6898-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="e6898-140">Jinými slovy, pozůstaly od generace 2 objekty generace 2; a zbývající objekty z LOH jsou objekty LOH (které jsou shromažďovány pomocí Gen2).</span><span class="sxs-lookup"><span data-stu-id="e6898-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="e6898-141">Uživatelský kód může přidělit pouze v generaci 0 (malé objekty) nebo LOH (velké objekty).</span><span class="sxs-lookup"><span data-stu-id="e6898-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="e6898-142">Pouze GC může "přidělit" objekty v generaci 1 (zvýšením úrovně pozůstalcích od generace 0) a generace 2 (zvýšením úrovně podržených z generací 1 a 2).</span><span class="sxs-lookup"><span data-stu-id="e6898-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="e6898-143">Když je aktivováno uvolňování paměti, GC provede trasování v rámci živých objektů a zkomprimuje je.</span><span class="sxs-lookup"><span data-stu-id="e6898-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="e6898-144">Ale vzhledem k tomu, že komprimace je nákladné *, uvolňování* paměti LOH; Vytvoří volný seznam z neaktivních objektů, které lze později znovu použít k uspokojení požadavků na přidělení velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="e6898-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="e6898-145">Sousední nedoručené objekty jsou vytvořeny do jednoho volného objektu.</span><span class="sxs-lookup"><span data-stu-id="e6898-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="e6898-146">Rozhraní .NET Core a .NET Framework (počínaje verzí .NET Framework 4.5.1) obsahují vlastnost <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType>, která umožňuje uživatelům určit, že by měl být LOH při příštím úplném blokování GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="e6898-147">A v budoucnu se může .NET rozhodnout LOH automaticky zkomprimovat.</span><span class="sxs-lookup"><span data-stu-id="e6898-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="e6898-148">To znamená, že pokud přidělíte velké objekty a chcete zajistit, aby se nepřesunuly, měli byste je stále připnout.</span><span class="sxs-lookup"><span data-stu-id="e6898-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="e6898-149">Obrázek 1 znázorňuje situaci, kdy se generace GC vydává 1 po prvním vygenerování GC, kde `Obj1` a `Obj3` jsou neaktivní a generace IT 2 po první generaci 1 GC, kde `Obj2` a `Obj5` jsou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="e6898-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="e6898-150">Všimněte si, že tato a následující čísla jsou pouze pro ilustrační účely; obsahují velmi málo objektů, aby lépe ukázaly, co se děje na haldě.</span><span class="sxs-lookup"><span data-stu-id="e6898-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="e6898-151">Ve skutečnosti je mnoho dalších objektů obvykle součástí GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-151">In reality, many more objects are typically involved in a GC.</span></span>

![Obrázek 1: GC s globálním 0 a GC 1. generace](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="e6898-153">Obrázek 1: generace 0 a 1. generace GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="e6898-154">Obrázek 2 ukazuje, že po 2. generaci GC, který zjistil, že `Obj1` a `Obj2` jsou neaktivní, tvoří GC volné místo v paměti, která se použila k tomu, aby byla obsazená `Obj1` a `Obj2`, která se pak použila k uspokojení žádosti o přidělení pro `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="e6898-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="e6898-155">Místo za posledním objektem `Obj3`, do konce segmentu, lze také použít k uspokojení požadavků na přidělení.</span><span class="sxs-lookup"><span data-stu-id="e6898-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Obrázek 2: po 1. generace GC](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="e6898-157">Obrázek 2: po 2. generaci GC</span><span class="sxs-lookup"><span data-stu-id="e6898-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="e6898-158">Pokud není dostatek volného místa pro uspokojení požadavků na přidělení velkých objektů, GC se nejprve pokusí získat další segmenty z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e6898-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="e6898-159">Pokud se to nepodaří, aktivuje se GC generace 2 v průběhu uvolnění místa.</span><span class="sxs-lookup"><span data-stu-id="e6898-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="e6898-160">Během generace 1 nebo generace 2 GC uvolňuje segmenty uvolňování paměti, které nemají žádné živé objekty, zpět do operačního systému voláním [funkce VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="e6898-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="e6898-161">Místo za posledním živým objektem na konci segmentu je depotvrzeno (s výjimkou dočasného segmentu, kde gen0/Gen1 Live, kde systém uvolňování paměti uchovává nějaké potvrzené, protože vaše aplikace se hned přiděluje).</span><span class="sxs-lookup"><span data-stu-id="e6898-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="e6898-162">A volná místa zůstávají i po resetování, což znamená, že operační systém nemusí zapisovat data do disku zpět na disk.</span><span class="sxs-lookup"><span data-stu-id="e6898-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="e6898-163">Vzhledem k tomu, že je LOH shromážděna pouze během generace 2 GC, segment LOH může být uvolněn pouze během takového GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="e6898-164">Obrázek 3 znázorňuje scénář, ve kterém uvolňování paměti uvolní jeden segment (segment 2) zpátky na operační systém a ve zbývajících segmentech zruší více místa.</span><span class="sxs-lookup"><span data-stu-id="e6898-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="e6898-165">Pokud musí použít odstraněné místo na konci segmentu, aby se splnily požadavky na velké nároky na přidělení objektů, pak se znovu potvrdí.</span><span class="sxs-lookup"><span data-stu-id="e6898-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="e6898-166">(Vysvětlení potvrzení/zrušení potvrzení naleznete v dokumentaci k [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span><span class="sxs-lookup"><span data-stu-id="e6898-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Obrázek 3: LOH po 1. generace GC](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="e6898-168">Obrázek 3: LOH po generaci 2 GC</span><span class="sxs-lookup"><span data-stu-id="e6898-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="e6898-169">Kdy je shromážděn velký objekt?</span><span class="sxs-lookup"><span data-stu-id="e6898-169">When is a large object collected?</span></span>

<span data-ttu-id="e6898-170">Obecně platí, že k GC dojde, když dojde k jedné z následujících 3 podmínek:</span><span class="sxs-lookup"><span data-stu-id="e6898-170">In general, a GC occurs when one of the following 3 conditions happens:</span></span>

- <span data-ttu-id="e6898-171">Přidělení překračuje prahovou hodnotu pro generaci 0 nebo velký objekt.</span><span class="sxs-lookup"><span data-stu-id="e6898-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="e6898-172">Prahová hodnota je vlastnost generace.</span><span class="sxs-lookup"><span data-stu-id="e6898-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="e6898-173">Prahová hodnota pro generování je nastavena, když systém uvolňování paměti přiděluje objekty do objektu.</span><span class="sxs-lookup"><span data-stu-id="e6898-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="e6898-174">Při překročení prahové hodnoty se v této generaci aktivuje GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="e6898-175">Při přidělování malých nebo velkých objektů spotřebováváte generace 0 a prahové hodnoty LOH v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e6898-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="e6898-176">Když systém uvolňování paměti přidělí do generace 1 a 2, spotřebuje jejich prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e6898-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="e6898-177">Tyto prahové hodnoty jsou dynamicky vyladěny při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="e6898-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="e6898-178">Toto je obvyklý případ. k většině GC dochází z důvodu přidělení na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="e6898-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="e6898-179">Je volána metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6898-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="e6898-180">Pokud je volána metoda bez parametrů <xref:System.GC.Collect?displayProperty=nameWithType> nebo je předána <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, je LOH shromážděn spolu se zbytkem spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="e6898-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="e6898-181">Systém je ve stavu nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="e6898-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="e6898-182">K tomu dochází, když systém uvolňování paměti obdrží oznámení o vysoké paměti z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e6898-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="e6898-183">Pokud systém uvolňování paměti předpokládá, že se v GC generace 2 zvýší produktivita, spustí se jedna.</span><span class="sxs-lookup"><span data-stu-id="e6898-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="e6898-184">Důsledky výkonu LOH</span><span class="sxs-lookup"><span data-stu-id="e6898-184">LOH Performance Implications</span></span>

<span data-ttu-id="e6898-185">Alokace u haldy velkých objektů má vliv na výkon následujícími způsoby.</span><span class="sxs-lookup"><span data-stu-id="e6898-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="e6898-186">Náklady na přidělení.</span><span class="sxs-lookup"><span data-stu-id="e6898-186">Allocation cost.</span></span>

  <span data-ttu-id="e6898-187">CLR zajišťuje záruku toho, že paměť pro každý nový objekt, který je vykazuje, je vymazána.</span><span class="sxs-lookup"><span data-stu-id="e6898-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="e6898-188">To znamená, že náklady na přidělení velkého objektu jsou zcela ovládány vymazáním paměti (Pokud se nespustí GC).</span><span class="sxs-lookup"><span data-stu-id="e6898-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="e6898-189">Pokud potrvá dva cykly k vymazání jednoho bajtu, bude trvat 170 000 cyklů, aby se vymazal nejmenší velký objekt.</span><span class="sxs-lookup"><span data-stu-id="e6898-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="e6898-190">Vymazání paměti objektu 16MB na 2GHz počítači trvá přibližně 16MS.</span><span class="sxs-lookup"><span data-stu-id="e6898-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="e6898-191">To je spíše velké náklady.</span><span class="sxs-lookup"><span data-stu-id="e6898-191">That's a rather large cost.</span></span>

- <span data-ttu-id="e6898-192">Náklady na shromažďování.</span><span class="sxs-lookup"><span data-stu-id="e6898-192">Collection cost.</span></span>

  <span data-ttu-id="e6898-193">Vzhledem k tomu, že jsou LOH a generace 2 shromažďovány společně, pokud je překročena prahová hodnota jedné z nich, je aktivována kolekce 2. generace.</span><span class="sxs-lookup"><span data-stu-id="e6898-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="e6898-194">Pokud je kolekce generace 2 aktivována z důvodu LOH, generace 2 nebude nutně po GC mnohem menší.</span><span class="sxs-lookup"><span data-stu-id="e6898-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="e6898-195">Pokud pro generaci 2 není k dispozici žádné množství dat, má minimální dopad.</span><span class="sxs-lookup"><span data-stu-id="e6898-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="e6898-196">Pokud je ale generace 2 Velká, může to způsobit problémy s výkonem, pokud se spustí spousta generace 2 GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="e6898-197">Pokud je mnoho velkých objektů přiděleno velmi dočasnému základu a máte velký počet SOH, může být útrata příliš mnoho času GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="e6898-198">Kromě toho mohou být náklady na přidělení skutečně přidány, pokud budete přiřazovat a vracet ve skutečnosti velké objekty.</span><span class="sxs-lookup"><span data-stu-id="e6898-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="e6898-199">Prvky pole s odkazovým typem.</span><span class="sxs-lookup"><span data-stu-id="e6898-199">Array elements with reference types.</span></span>

  <span data-ttu-id="e6898-200">Velmi velké objekty v LOH jsou obvykle pole (velmi zřídka mají objekt instance, který je ve skutečnosti velký).</span><span class="sxs-lookup"><span data-stu-id="e6898-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="e6898-201">Pokud jsou prvky pole na úrovni reference, dojde k nepřítomnosti nákladů, které nejsou k dispozici, pokud prvky nejsou na přehledně formátované.</span><span class="sxs-lookup"><span data-stu-id="e6898-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="e6898-202">Pokud element neobsahuje žádné odkazy, systém uvolňování paměti nemusí projít všemi poli.</span><span class="sxs-lookup"><span data-stu-id="e6898-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="e6898-203">Například pokud použijete pole k ukládání uzlů v binárním stromu, jedním ze způsobů, jak ho implementovat, je odkazování na pravý a levý uzel uzlu skutečnými uzly:</span><span class="sxs-lookup"><span data-stu-id="e6898-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="e6898-204">Pokud je `num_nodes` velká, musí systém uvolňování paměti projít alespoň dva odkazy na jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="e6898-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="e6898-205">Alternativním přístupem je uložit index pravého a levého uzlu:</span><span class="sxs-lookup"><span data-stu-id="e6898-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="e6898-206">Místo odkazování na data levého uzlu jako `left.d`odkazujte na něj jako `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="e6898-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="e6898-207">A systém uvolňování paměti nemusí pohlížet na žádné odkazy pro levý a pravý uzel.</span><span class="sxs-lookup"><span data-stu-id="e6898-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="e6898-208">Z těchto tří faktorů jsou první dva většinou mnohem významné než třetí.</span><span class="sxs-lookup"><span data-stu-id="e6898-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="e6898-209">Z tohoto důvodu doporučujeme, abyste přidělili fond velkých objektů, které znovu použijete místo přidělení dočasných.</span><span class="sxs-lookup"><span data-stu-id="e6898-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="e6898-210">Shromažďování údajů o výkonu pro LOH</span><span class="sxs-lookup"><span data-stu-id="e6898-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="e6898-211">Předtím, než shromáždíte údaje o výkonu konkrétní oblasti, byste už měli provést následující:</span><span class="sxs-lookup"><span data-stu-id="e6898-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="e6898-212">Bylo nalezeno legitimace, které byste měli v této oblasti prohledat.</span><span class="sxs-lookup"><span data-stu-id="e6898-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="e6898-213">Byly vyčerpány jiné oblasti, o kterých víte, že nenajdete cokoli, co by mohlo vysvětlit problém s výkonem, který jste viděli.</span><span class="sxs-lookup"><span data-stu-id="e6898-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="e6898-214">[Než se pokusíte najít řešení](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) , kde najdete další informace o základech paměti a procesoru, podívejte se na blog.</span><span class="sxs-lookup"><span data-stu-id="e6898-214">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="e6898-215">K shromažďování dat o výkonu LOH můžete použít následující nástroje:</span><span class="sxs-lookup"><span data-stu-id="e6898-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="e6898-216">Čítače výkonu paměti .NET CLR</span><span class="sxs-lookup"><span data-stu-id="e6898-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="e6898-217">Události ETW</span><span class="sxs-lookup"><span data-stu-id="e6898-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="e6898-218">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="e6898-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="e6898-219">Čítače výkonu paměti .NET CLR</span><span class="sxs-lookup"><span data-stu-id="e6898-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="e6898-220">Tyto čítače výkonu jsou obvykle dobrým prvním krokem při zkoumání problémů s výkonem (i když doporučujeme použít [události ETW](#etw-events)).</span><span class="sxs-lookup"><span data-stu-id="e6898-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="e6898-221">Nástroj Sledování výkonu konfigurujete tak, že přidáte čítače, které chcete, jak ukazuje obrázek 4.</span><span class="sxs-lookup"><span data-stu-id="e6898-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="e6898-222">Ty, které jsou relevantní pro LOH, jsou:</span><span class="sxs-lookup"><span data-stu-id="e6898-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="e6898-223">**Kolekce 2. generace**</span><span class="sxs-lookup"><span data-stu-id="e6898-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="e6898-224">Zobrazuje počet, kolikrát od spuštění procesu došlo k GC 2. generace.</span><span class="sxs-lookup"><span data-stu-id="e6898-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="e6898-225">Čítač se zvyšuje na konci kolekce 2. generace (označuje se také jako úplné uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="e6898-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="e6898-226">Tento čítač zobrazuje poslední zjištěnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e6898-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="e6898-227">**Velikost haldy Large Object**</span><span class="sxs-lookup"><span data-stu-id="e6898-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="e6898-228">Zobrazí aktuální velikost LOH v bajtech, včetně volného místa.</span><span class="sxs-lookup"><span data-stu-id="e6898-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="e6898-229">Tento čítač se aktualizuje na konci uvolňování paměti, ne při každém přidělení.</span><span class="sxs-lookup"><span data-stu-id="e6898-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="e6898-230">Běžný způsob, jak si prohlédnout čítače výkonu, je nástroj Performance Monitor (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="e6898-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="e6898-231">Pomocí možnosti Přidat čítače přidejte zajímavé čítače pro procesy, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="e6898-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="e6898-232">Data čítače výkonu můžete uložit do souboru protokolu, jak ukazuje obrázek 4:</span><span class="sxs-lookup"><span data-stu-id="e6898-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="e6898-233">![Screenshow, který ukazuje přidání čítačů výkonu.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="e6898-233">![Screenshow that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="e6898-234">Obrázek 4: LOH po 2. generaci GC</span><span class="sxs-lookup"><span data-stu-id="e6898-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="e6898-235">Čítače výkonu se také dají dotazovat programově.</span><span class="sxs-lookup"><span data-stu-id="e6898-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="e6898-236">Spousta lidí je shromažďuje tímto způsobem v rámci procesu pravidelného testování.</span><span class="sxs-lookup"><span data-stu-id="e6898-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="e6898-237">Když vydávají čítače s hodnotami, které jsou z obyčejného, používají jiné prostředky k získání podrobnějších dat, která vám pomohou s šetřením.</span><span class="sxs-lookup"><span data-stu-id="e6898-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="e6898-238">Doporučujeme místo čítačů výkonu použít události trasování událostí pro Windows, protože trasování událostí pro Windows poskytuje mnohem rozsáhlejší informace.</span><span class="sxs-lookup"><span data-stu-id="e6898-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="e6898-239">Trasování událostí pro Windows – události</span><span class="sxs-lookup"><span data-stu-id="e6898-239">ETW events</span></span>

<span data-ttu-id="e6898-240">Systém uvolňování paměti poskytuje bohatou sadu událostí ETW, které vám pomůžou pochopit, co dělá halda a proč.</span><span class="sxs-lookup"><span data-stu-id="e6898-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="e6898-241">Následující blogové příspěvky ukazují, jak shromažďovat a pochopit události GC pomocí ETW:</span><span class="sxs-lookup"><span data-stu-id="e6898-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="e6898-242">GC – události ETW – 1</span><span class="sxs-lookup"><span data-stu-id="e6898-242">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="e6898-243">GC – události ETW – 2</span><span class="sxs-lookup"><span data-stu-id="e6898-243">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="e6898-244">GC – události ETW – 3</span><span class="sxs-lookup"><span data-stu-id="e6898-244">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="e6898-245">GC – události ETW – 4</span><span class="sxs-lookup"><span data-stu-id="e6898-245">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="e6898-246">Chcete-li identifikovat nadměrné GC 2. generace způsobené dočasným přidělením LOH, podívejte se do sloupce důvod triggeru pro GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="e6898-247">Pro jednoduchý test, který přiděluje pouze dočasné velké objekty, můžete shromažďovat informace o událostech ETW pomocí následujícího příkazového řádku [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) :</span><span class="sxs-lookup"><span data-stu-id="e6898-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="e6898-248">Výsledek je podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="e6898-248">The result is something like this:</span></span>

<span data-ttu-id="e6898-249">![snímek obrazovky, který zobrazuje události ETW v PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="e6898-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="e6898-250">Obrázek 5: události ETW zobrazené pomocí PerfView</span><span class="sxs-lookup"><span data-stu-id="e6898-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="e6898-251">Jak vidíte, všechny GC jsou generace 2 GC a všechny jsou spouštěny v AllocLarge, což znamená, že přidělením velkého objektu aktivovaného tímto GC.</span><span class="sxs-lookup"><span data-stu-id="e6898-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="e6898-252">Víme, že tato přidělení jsou dočasná, protože **sazba LOH pro přežití%** kolony uvádí 1%.</span><span class="sxs-lookup"><span data-stu-id="e6898-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="e6898-253">Můžete shromažďovat další události ETW, které vám sdělí, kdo tyto velké objekty přidělil.</span><span class="sxs-lookup"><span data-stu-id="e6898-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="e6898-254">Následující příkazový řádek:</span><span class="sxs-lookup"><span data-stu-id="e6898-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="e6898-255">shromažďuje událost AllocationTick, která se aktivuje přibližně pro každé 100 tisíc množství přidělení.</span><span class="sxs-lookup"><span data-stu-id="e6898-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="e6898-256">Jinými slovy, událost je vyvolána při každém přidělení velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="e6898-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="e6898-257">Pak se můžete podívat na jedno z zobrazení přidělení haldy GC, které vám ukáže zásobníky voláníi, že se přidělily velké objekty:</span><span class="sxs-lookup"><span data-stu-id="e6898-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="e6898-258">![snímek obrazovky, který ukazuje zobrazení haldy systému uvolňování paměti.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="e6898-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="e6898-259">Obrázek 6: zobrazení přidělení haldy GC</span><span class="sxs-lookup"><span data-stu-id="e6898-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="e6898-260">Jak vidíte, jedná se o velmi jednoduchý test, který pouze přiděluje velké objekty ze své `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="e6898-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="e6898-261">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="e6898-261">A debugger</span></span>

<span data-ttu-id="e6898-262">Pokud je to výpis paměti a potřebujete zjistit, jaké objekty jsou ve skutečnosti na LOH, můžete použít [rozšíření ladicího programu SOS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) , které poskytuje .NET.</span><span class="sxs-lookup"><span data-stu-id="e6898-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="e6898-263">Příkazy ladění uvedené v této části platí pro [ladicí programy systému Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="e6898-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="e6898-264">Následující ukázka ukazuje výstup z analýzy LOH:</span><span class="sxs-lookup"><span data-stu-id="e6898-264">The following shows sample output from analyzing the LOH:</span></span>

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

<span data-ttu-id="e6898-265">Velikost haldy LOH je (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtů.</span><span class="sxs-lookup"><span data-stu-id="e6898-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="e6898-266">Mezi adresami 023e1000 a 033db630, 8 008 736 bajtů, které jsou obsazeny polem objektů <xref:System.Object?displayProperty=nameWithType>, 6 663 696 bajty jsou obsazeny polem <xref:System.Byte?displayProperty=nameWithType> objektů a 2 081 792 bajtů je obsazeno volným místem.</span><span class="sxs-lookup"><span data-stu-id="e6898-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="e6898-267">V některých případech ladicí program zobrazí, že celková velikost LOH je menší než 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="e6898-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="e6898-268">K tomu dochází, protože modul runtime sám používá LOH k přidělení některých objektů, které jsou menší než velký objekt.</span><span class="sxs-lookup"><span data-stu-id="e6898-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="e6898-269">Vzhledem k tomu, že se LOH nekomprimuje, někdy se LOH považuje za zdroj fragmentace.</span><span class="sxs-lookup"><span data-stu-id="e6898-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="e6898-270">Fragmentace znamená:</span><span class="sxs-lookup"><span data-stu-id="e6898-270">Fragmentation means:</span></span>

- <span data-ttu-id="e6898-271">Fragmentace spravované haldy, která je určena množstvím volného místa mezi spravovanými objekty.</span><span class="sxs-lookup"><span data-stu-id="e6898-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="e6898-272">V SoS příkaz `!dumpheap –type Free` zobrazuje velikost volného místa mezi spravovanými objekty.</span><span class="sxs-lookup"><span data-stu-id="e6898-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="e6898-273">Fragmentace adresního prostoru virtuální paměti (VM), což je paměť označená jako `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="e6898-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="e6898-274">Můžete ji získat pomocí různých příkazů ladicího programu v programu WinDbg.</span><span class="sxs-lookup"><span data-stu-id="e6898-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="e6898-275">Následující příklad ukazuje fragmentaci v prostoru virtuálního počítače:</span><span class="sxs-lookup"><span data-stu-id="e6898-275">The following example shows fragmentation in the VM space:</span></span>

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

<span data-ttu-id="e6898-276">Je častěji vidět, že fragmentace virtuálního počítače je způsobená dočasnými velkými objekty, které vyžadují, aby systém uvolňování paměti často získal nové spravované segmenty haldy z operačního systému a uvolnil prázdné hodnoty zpátky do operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e6898-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="e6898-277">Chcete-li ověřit, zda LOH způsobuje fragmentaci virtuálního počítače, můžete nastavit zarážku na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) a [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) , aby bylo možné zjistit, kdo je volá.</span><span class="sxs-lookup"><span data-stu-id="e6898-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="e6898-278">Například chcete-li zjistit, kdo se pokusil přidělit bloky virtuální paměti větší než 8MBB z operačního systému, můžete nastavit zarážku takto:</span><span class="sxs-lookup"><span data-stu-id="e6898-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="e6898-279">Tento příkaz se přeruší do ladicího programu a zobrazí zásobník volání pouze v případě, že je metoda [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) volána s velikostí alokace větší než 8MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="e6898-279">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="e6898-280">CLR 2,0 přidal funkci s názvem *VM hoarding* , která může být užitečná pro scénáře, kdy se často získávají a uvolňují segmenty (včetně v haldách velkých a malých objektů).</span><span class="sxs-lookup"><span data-stu-id="e6898-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="e6898-281">Pokud chcete zadat hoarding virtuálního počítače, zadejte spouštěcí příznak s názvem `STARTUP_HOARD_GC_VM` prostřednictvím rozhraní API pro hostování.</span><span class="sxs-lookup"><span data-stu-id="e6898-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="e6898-282">Místo uvolnění prázdných segmentů zpět do operačního systému modul CLR zruší v těchto segmentech paměť a umístí je do úsporného seznamu.</span><span class="sxs-lookup"><span data-stu-id="e6898-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="e6898-283">(Všimněte si, že modul CLR to neudělá pro segmenty, které jsou příliš velké.) Modul CLR později použije tyto segmenty k uspokojení požadavků na nové segmenty.</span><span class="sxs-lookup"><span data-stu-id="e6898-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="e6898-284">Až aplikace příště potřebuje nový segment, použije modul CLR jeden z těchto seznamů v pohotovostním režimu, pokud může najít dostatečně velký.</span><span class="sxs-lookup"><span data-stu-id="e6898-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="e6898-285">Hoarding virtuálního počítače je také užitečné pro aplikace, které chcete umístit na segmenty, které již získali, například některé serverové aplikace, které jsou dominantní aplikace spuštěné v systému, aby nedocházelo k výjimkám výjimek paměti.</span><span class="sxs-lookup"><span data-stu-id="e6898-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="e6898-286">Důrazně doporučujeme, abyste aplikaci pečlivě otestovali při použití této funkce, abyste zajistili, že má vaše aplikace poměrně stabilní využití paměti.</span><span class="sxs-lookup"><span data-stu-id="e6898-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
