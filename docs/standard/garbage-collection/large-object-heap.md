---
title: Halda velkého objektu v systémech Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68513d2535ea9e19a42f9e58b9d423e17008f9de
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="f4a35-102">Halda velkého objektu v systémech Windows</span><span class="sxs-lookup"><span data-stu-id="f4a35-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="f4a35-103">Systém uvolňování paměti .NET (GC) vyfiltruje objekty do malých a velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="f4a35-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="f4a35-104">Po velký objekt některé jeho atributy závažnější než pokud je objekt malá.</span><span class="sxs-lookup"><span data-stu-id="f4a35-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="f4a35-105">Kompresi ho – který se kopírování v paměti jinde v haldě – například může být náročné.</span><span class="sxs-lookup"><span data-stu-id="f4a35-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="f4a35-106">Z toho důvodu Garbage Collector v rozhraní .NET umístí rozsáhlé objekty v haldě velkého objektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="f4a35-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="f4a35-107">V tomto tématu se podíváme velkého objektu haldy podrobněji.</span><span class="sxs-lookup"><span data-stu-id="f4a35-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="f4a35-108">Probereme co vyfiltrování objekt jako velkého objektu, jak se shromažďují tyto rozsáhlé objekty a co druh důsledky velké objekty výkonu použít.</span><span class="sxs-lookup"><span data-stu-id="f4a35-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4a35-109">Toto téma popisuje velkého objektu haldy v rozhraní .NET Framework a .NET Core spuštěna pouze pro systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="f4a35-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="f4a35-110">Nepokrývá LOH systémem implementace rozhraní .NET na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="f4a35-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="f4a35-111">Jak objekt skončilo v haldě velkého objektu a jak je GC zpracovává</span><span class="sxs-lookup"><span data-stu-id="f4a35-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="f4a35-112">Pokud objekt je větší než nebo rovna 85,000 bajtů, považuje za velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="f4a35-113">Toto číslo bylo určeno optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="f4a35-114">Při požadavku na přidělení objekt je pro 85,000 nebo více bajtů, modul runtime jí v haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="f4a35-115">Zjistit, co to znamená, je užitečné k prozkoumání některých základní informace o GC rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f4a35-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="f4a35-116">Uvolňování paměti rozhraní .NET je generační kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4a35-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="f4a35-117">Má tři generace: generování 0, 1. generace a 2. generace.</span><span class="sxs-lookup"><span data-stu-id="f4a35-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="f4a35-118">Důvodem pro 3 generace předpokládají, že v dobře ujít aplikaci, většina die objekty v gen0.</span><span class="sxs-lookup"><span data-stu-id="f4a35-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="f4a35-119">V aplikaci pomocí serveru, by například přidělení související s každou žádostí kostka, po dokončení požadavku.</span><span class="sxs-lookup"><span data-stu-id="f4a35-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="f4a35-120">Požadavky během letu přidělení vytvořit do gen1 a kostka existuje.</span><span class="sxs-lookup"><span data-stu-id="f4a35-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="f4a35-121">V podstatě gen1 funguje jako vyrovnávací paměť mezi malí objekt oblasti a oblasti dlohotrvající objektu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="f4a35-122">Malé objekty jsou vždy přidělené v generace 0 a v závislosti na své životnosti, může být převeden na generace 1 nebo generation2.</span><span class="sxs-lookup"><span data-stu-id="f4a35-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="f4a35-123">Rozsáhlé objekty jsou vždy přidělené v 2. generace.</span><span class="sxs-lookup"><span data-stu-id="f4a35-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="f4a35-124">Rozsáhlé objekty patří do generace 2, protože jsou shromážděná pouze během 2. generace kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4a35-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="f4a35-125">Když jsou shromažďována generace, jeho mladší generation(s) se také shromažďují.</span><span class="sxs-lookup"><span data-stu-id="f4a35-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="f4a35-126">Například když se stane GC 1. generace, se shromažďují obě generace 1 a 0.</span><span class="sxs-lookup"><span data-stu-id="f4a35-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="f4a35-127">A když se stane GC 2. generace, jsou shromažďovány celou halda.</span><span class="sxs-lookup"><span data-stu-id="f4a35-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="f4a35-128">Z tohoto důvodu se také nazývá GC 2. generace *úplné GC*.</span><span class="sxs-lookup"><span data-stu-id="f4a35-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="f4a35-129">Tento článek odkazuje na 2. generace GC místo úplný úklid GC, ale podmínky jsou uvedeny zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="f4a35-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="f4a35-130">Generace poskytují logické zobrazení haldě GC.</span><span class="sxs-lookup"><span data-stu-id="f4a35-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="f4a35-131">Fyzicky objekty existují v spravovaná halda segmenty.</span><span class="sxs-lookup"><span data-stu-id="f4a35-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="f4a35-132">A *spravovaná halda segment* se považuje blok, paměti, která globální Katalog rezerv z operačního systému při volání [VirtualAlloc funkce](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) jménem spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) on behalf of managed code.</span></span> <span data-ttu-id="f4a35-133">Při načítání modulu CLR, globální Katalog přiděluje dva segmenty počáteční haldy: jeden pro malé objekty (malé objektu haldy, nebo SOH) a jeden pro velké objekty (velkého objektu haldy).</span><span class="sxs-lookup"><span data-stu-id="f4a35-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="f4a35-134">Přidělení požadavky jsou pak splněny umístěním spravované objekty v těchto spravovaná halda segmenty.</span><span class="sxs-lookup"><span data-stu-id="f4a35-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="f4a35-135">Pokud se objekt menší než 85,000 bajtů, jsou uváděny v segmentu pro SOH; jinak jsou uváděny v LOH segmentu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="f4a35-136">Segmenty jsou (v menší bloky dat) jako informace a další objekty, které jsou přiděleny do nich.</span><span class="sxs-lookup"><span data-stu-id="f4a35-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="f4a35-137">Pro prohlášení o stavu objekty, které zůstanou platné i po globální Katalog povýšené na nové generace.</span><span class="sxs-lookup"><span data-stu-id="f4a35-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="f4a35-138">Objekty, které zůstanou platné i po 0. generace kolekce jsou nyní považovány za objekty 1. generace a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f4a35-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="f4a35-139">Ale objekty, které zůstanou platné i po nejstarší generace jsou stále považování za nejstarší generování.</span><span class="sxs-lookup"><span data-stu-id="f4a35-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="f4a35-140">Jinými slovy přesun z 2. generace jsou objekty 2. generace; a přesun z LOH jsou objekty LOH, (které se vybírají pomocí gen2).</span><span class="sxs-lookup"><span data-stu-id="f4a35-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span> 

<span data-ttu-id="f4a35-141">Uživatelský kód můžete přidělit pouze při generování, 0 (malé objekty) nebo LOH (rozsáhlé objekty).</span><span class="sxs-lookup"><span data-stu-id="f4a35-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="f4a35-142">Pouze globální Katalog "přidělit" objekty v 1. generace (podporou přesun z generace 0) a generace 2 (podporou přesun z generace 1 a 2).</span><span class="sxs-lookup"><span data-stu-id="f4a35-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="f4a35-143">Když se aktivuje uvolňování paměti, globální Katalog trasování prostřednictvím živé objekty a zkomprimuje je.</span><span class="sxs-lookup"><span data-stu-id="f4a35-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="f4a35-144">Ale protože je náročné, komprimace globální Katalog *přesune* LOH; umožňuje volné seznamu mimo neaktivní objekty, které lze znovu použít později pro uspokojení požadavků na přidělení velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="f4a35-145">Sousední neaktivní objekty jsou vytvářeny do volného jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="f4a35-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="f4a35-146">.NET core a rozhraní .NET Framework (od verze rozhraní .NET Framework 4.5.1) obsahují <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> vlastnost, která umožňuje uživatelům určit, že LOH má probíhat během další úplné blokování GC.</span><span class="sxs-lookup"><span data-stu-id="f4a35-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="f4a35-147">A v budoucnu, mohou rozhodnout .NET compact LOH automaticky.</span><span class="sxs-lookup"><span data-stu-id="f4a35-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="f4a35-148">To znamená, že pokud přidělit rozsáhlé objekty a ujistěte se, že nelze přesunout, by měl stále připnete je.</span><span class="sxs-lookup"><span data-stu-id="f4a35-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="f4a35-149">Obrázek 1 ukazuje scénář, kde globální Katalog forms generace 1 po GC 0. generace první kde `Obj1` a `Obj3` jsou neaktivní a forms generace 2 po GC 1. generace první kde `Obj2` a `Obj5` jsou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="f4a35-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="f4a35-150">Upozorňujeme, že toto a následující údaje jsou pouze pro účely obrázku; obsahují velmi několik objektů na lépe zobrazit, co se stane, že v haldě.</span><span class="sxs-lookup"><span data-stu-id="f4a35-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="f4a35-151">Ve skutečnosti se obvykle podílejí celou řadu dalších objektů v globálním Katalogem.</span><span class="sxs-lookup"><span data-stu-id="f4a35-151">In reality, many more objects are typically involved in a GC.</span></span>

![Obrázek 1: 0. generace GC a GC 1. generace](media/loh/loh-figure-1.jpg)   
<span data-ttu-id="f4a35-153">Obrázek 1: Generace 0 a 1. generace GC.</span><span class="sxs-lookup"><span data-stu-id="f4a35-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="f4a35-154">Obrázek 2 ukazuje, že po GC 2. generace, která viděli `Obj1` a `Obj2` jsou neaktivní, globální Katalog forms souvislého volného místa, nedostatek paměti, která používá na kterém je umístěna `Obj1` a `Obj2`, který pak byl použit pro uspokojení požadavku na přidělení pro `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="f4a35-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="f4a35-155">Prostor po poslední objekt, `Obj3`, na konec segmentu lze také pro uspokojení požadavků na přidělení.</span><span class="sxs-lookup"><span data-stu-id="f4a35-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>
 
![Obrázek 2: po GC 2. generace](media/loh/loh-figure-2.jpg)  
<span data-ttu-id="f4a35-157">Obrázek 2: po GC 2. generace</span><span class="sxs-lookup"><span data-stu-id="f4a35-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="f4a35-158">Pokud není k dispozici dostatek volného místa pro uložení požadavků na přidělení velkého objektu, globální Katalog napřed pokusí získat další segmenty z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f4a35-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="f4a35-159">Pokud to nepomůže, aktivuje GC 2. generace v naděje z uvolněte místo.</span><span class="sxs-lookup"><span data-stu-id="f4a35-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="f4a35-160">Během generace 1 nebo 2. generace GC, bude systém uvolňování uvolní segmentech, které mají žádné objekty v za provozu na nich zpět do operačního systému při volání [virtualfree – funkce](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="f4a35-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span></span> <span data-ttu-id="f4a35-161">Prostor po poslední za provozu objekt na konec segmentu je nepotvrzená (s výjimkou v dočasných segmentu, kde gen0/gen1 za provozu, kde bude systém uvolňování ponechat některé potvrzené, protože bude možné přidělování vaší aplikace v ní hned).</span><span class="sxs-lookup"><span data-stu-id="f4a35-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="f4a35-162">A volné prostory zůstanou potvrdit, když dojde k jejich vynulování, což znamená, že nemusí zapisovat data v nich zpět na disk operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f4a35-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="f4a35-163">Vzhledem k tomu, že LOH se shromažďují pouze během GC 2. generace, může být LOH segment uvolněno pouze během globální Katalog.</span><span class="sxs-lookup"><span data-stu-id="f4a35-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="f4a35-164">Obrázek 3 ukazuje scénář, kde bude systém uvolňování uvolní jednoho segmentu (segment 2) zpět do operačního systému a decommits více místa na zbývající segmenty.</span><span class="sxs-lookup"><span data-stu-id="f4a35-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="f4a35-165">Pokud je třeba použít Nepotvrzená místa na konci tohoto segmentu pro uspokojení požadavků na přidělení velkého objektu, potvrdí paměť znovu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="f4a35-166">(Další informace o potvrzení nebo zruší, naleznete v dokumentaci k [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="f4a35-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span></span>
 
![Obrázek 3: LOH po GC 2. generace](media/loh/loh-figure-3.jpg)  
<span data-ttu-id="f4a35-168">Obrázek 3: LOH po GC 2. generace</span><span class="sxs-lookup"><span data-stu-id="f4a35-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="f4a35-169">Když se shromažďují velkého objektu?</span><span class="sxs-lookup"><span data-stu-id="f4a35-169">When is a large object collected?</span></span>

<span data-ttu-id="f4a35-170">Obecně platí globální Katalog dojde, pokud jeden z následujících podmínek následující 3 se stane:</span><span class="sxs-lookup"><span data-stu-id="f4a35-170">In general, a GC occurs when one of the following following 3 conditions happens:</span></span>

- <span data-ttu-id="f4a35-171">Přidělení překračuje generace 0 nebo velkého objektu prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

   <span data-ttu-id="f4a35-172">Prahová hodnota je vlastností generace.</span><span class="sxs-lookup"><span data-stu-id="f4a35-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="f4a35-173">Prahová hodnota pro generace nastavena při uvolňování paměti přidělí objekty do ní.</span><span class="sxs-lookup"><span data-stu-id="f4a35-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="f4a35-174">Pokud je překročena prahová hodnota, aktivuje se v této generaci serverem globálního katalogu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="f4a35-175">Při přidělování objektů malý nebo velký, můžete využívat generace 0 a prahové hodnoty LOH, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f4a35-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="f4a35-176">Při uvolňování paměti přidělí do generace 1 a 2, využívá příslušné prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f4a35-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="f4a35-177">Tyto prahové hodnoty jsou dynamicky přizpůsobená po spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-177">These thresholds are dynamically tuned as the program runs.</span></span>

   <span data-ttu-id="f4a35-178">Toto je obvyklý případ; Většina GC dojít z důvodu přidělování v haldě spravované.</span><span class="sxs-lookup"><span data-stu-id="f4a35-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="f4a35-179"><xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="f4a35-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

   <span data-ttu-id="f4a35-180">Pokud bez parametrů <xref:System.GC.Collect?displayProperty=nameWithType> metoda je volána nebo jiné přetížení, je předaná <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, jsou shromažďovány LOH spolu s ostatními spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="f4a35-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="f4a35-181">Systém je v případě nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="f4a35-181">The system is in low memory situation.</span></span>

   <span data-ttu-id="f4a35-182">K tomu dochází, když má systém uvolňování obdrží oznámení velkého množství paměti z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f4a35-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="f4a35-183">Pokud garbage collector v se domnívá, že to GC 2. generace bude produktivní, aktivuje jeden.</span><span class="sxs-lookup"><span data-stu-id="f4a35-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="f4a35-184">Ovlivnit výkon LOH</span><span class="sxs-lookup"><span data-stu-id="f4a35-184">LOH Performance Implications</span></span>

<span data-ttu-id="f4a35-185">Přidělování v haldě velkého objektu dopad na výkon následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="f4a35-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="f4a35-186">Přidělení náklady.</span><span class="sxs-lookup"><span data-stu-id="f4a35-186">Allocation cost.</span></span>

   <span data-ttu-id="f4a35-187">Modul CLR Díky záruku, že není zaškrtnuto paměti pro všechny nové objekty, že nabízí.</span><span class="sxs-lookup"><span data-stu-id="f4a35-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="f4a35-188">To znamená, že náklady na přidělení velkého objektu je zcela ovládnutí paměti vymazání (Pokud aktivuje globální Katalog).</span><span class="sxs-lookup"><span data-stu-id="f4a35-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="f4a35-189">Pokud bude trvat 2 cykly zrušte jeden bajt, trvá 170,000 cykly zrušte nejmenší velký objekt.</span><span class="sxs-lookup"><span data-stu-id="f4a35-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="f4a35-190">Vymazání memmory objektu 16MB na počítači, 2GHz trvá přibližně 16ms.</span><span class="sxs-lookup"><span data-stu-id="f4a35-190">Clearing the memmory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="f4a35-191">To je místo velkých náklady.</span><span class="sxs-lookup"><span data-stu-id="f4a35-191">That's a rather large cost.</span></span>

- <span data-ttu-id="f4a35-192">Kolekce náklady.</span><span class="sxs-lookup"><span data-stu-id="f4a35-192">Collection cost.</span></span>

   <span data-ttu-id="f4a35-193">Protože LOH a 2. generace jsou seskupeny, pokud je překročena mezní hodnota některé z nich je, aktivuje se 2. generace kolekce.</span><span class="sxs-lookup"><span data-stu-id="f4a35-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="f4a35-194">Pokud generování, které se z důvodu LOH aktivuje 2 kolekce, 2. generace nebudou nutně mnohem menší po globální Katalog.</span><span class="sxs-lookup"><span data-stu-id="f4a35-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="f4a35-195">Pokud na 2. generace není množství dat, to má minimální dopad.</span><span class="sxs-lookup"><span data-stu-id="f4a35-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="f4a35-196">Ale pokud generace 2 je velká, může to způsobit problémy s výkonem Pokud aktivaci mnoho GC 2. generace.</span><span class="sxs-lookup"><span data-stu-id="f4a35-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="f4a35-197">Mnoho velkých objektů jsou přiděleny velmi dočasné a máte velké prohlášení o stavu, může výdaje příliš mnoho času provádění GC.</span><span class="sxs-lookup"><span data-stu-id="f4a35-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="f4a35-198">Kromě toho náklady na přidělení můžete skutečně dohromady Pokud necháte přidělování, když necháte přejděte skutečně velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="f4a35-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="f4a35-199">Elementy pole s odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="f4a35-199">Array elements with reference types.</span></span>

   <span data-ttu-id="f4a35-200">Velmi velkých objektů na LOH jsou obvykle pole (je velmi výjimečných tak, aby měl instance objektu, který skutečně velké).</span><span class="sxs-lookup"><span data-stu-id="f4a35-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="f4a35-201">Pokud jsou elementy pole odkaz bohaté, způsobuje náklady, které není k dispozici, pokud nejsou elementy bohaté odkaz.</span><span class="sxs-lookup"><span data-stu-id="f4a35-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="f4a35-202">Pokud element neobsahuje žádné odkazy, bude systém uvolňování nemusí vůbec projít pole.</span><span class="sxs-lookup"><span data-stu-id="f4a35-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="f4a35-203">Například pokud použijete pole k uložení uzly v binárního stromu, jedním ze způsobů implementaci je k odkazování na uzlu vlevo a vpravo uzlu skutečné uzly:</span><span class="sxs-lookup"><span data-stu-id="f4a35-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      Node left;
      Node right;
   };

   Node[] binary_tr = new Node [num_nodes];
   ```

   <span data-ttu-id="f4a35-204">Pokud `num_nodes` je velký, bude systém uvolňování musí projít, aspoň dva odkazy na jeden element.</span><span class="sxs-lookup"><span data-stu-id="f4a35-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="f4a35-205">Alternativní způsob je index pravé a levé uzly úložiště:</span><span class="sxs-lookup"><span data-stu-id="f4a35-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      uint left_index;
      uint right_index;
   } ;
   ```

   <span data-ttu-id="f4a35-206">Místo odkazující data levém uzlu jako `left.d`, můžete použít informace jako `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="f4a35-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="f4a35-207">A uvolňování nemusí podívejte se na všechny odkazy pro levý a pravý uzel.</span><span class="sxs-lookup"><span data-stu-id="f4a35-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="f4a35-208">Mimo třech faktorech jsou obvykle větších než třetí první dvě.</span><span class="sxs-lookup"><span data-stu-id="f4a35-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="f4a35-209">Z toho důvodu doporučujeme, že přidělíte fond rozsáhlé objekty, které znovu použít místo přidělování dočasné ty.</span><span class="sxs-lookup"><span data-stu-id="f4a35-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span> 

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="f4a35-210">Shromažďování dat výkonu pro LOH</span><span class="sxs-lookup"><span data-stu-id="f4a35-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="f4a35-211">Předtím, než můžete shromažďovat údaje o výkonu pro určitou oblast, musí již uděláte následující:</span><span class="sxs-lookup"><span data-stu-id="f4a35-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="f4a35-212">Najít důkaz, že jste měli vyhledávání v této oblasti.</span><span class="sxs-lookup"><span data-stu-id="f4a35-212">Found evidence that you should be looking at this area.</span></span>

1. <span data-ttu-id="f4a35-213">Další oblasti, které znáte služby, aniž byste hledání nic může vysvětlující problému s výkonem, které jste viděli vyčerpá.</span><span class="sxs-lookup"><span data-stu-id="f4a35-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="f4a35-214">Naleznete v blogu [problém pochopit, teprve pak zkuste najít řešení](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) Další informace o základní informace o paměti a procesoru.</span><span class="sxs-lookup"><span data-stu-id="f4a35-214">See the blog [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="f4a35-215">Tyto nástroje můžete použít ke shromažďování dat na výkon LOH:</span><span class="sxs-lookup"><span data-stu-id="f4a35-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="f4a35-216">Čítače výkonu paměti .NET CLR</span><span class="sxs-lookup"><span data-stu-id="f4a35-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="f4a35-217">Události trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="f4a35-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="f4a35-218">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="f4a35-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="f4a35-219">Čítače výkonu paměti .NET CLR</span><span class="sxs-lookup"><span data-stu-id="f4a35-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="f4a35-220">Tyto čítače výkonu jsou obvykle dobrou prvním krokem při zkoumání problémů s výkonem (i když vám doporučujeme používat [události trasování událostí](#etw)).</span><span class="sxs-lookup"><span data-stu-id="f4a35-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw)).</span></span> <span data-ttu-id="f4a35-221">Nakonfigurujete sledování výkonu přidáním čítačů, které potřebujete, jak ukazuje obrázek 4.</span><span class="sxs-lookup"><span data-stu-id="f4a35-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="f4a35-222">Ty, které jsou relevantní pro LOH jsou:</span><span class="sxs-lookup"><span data-stu-id="f4a35-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="f4a35-223">**\# 2. generace kolekce**</span><span class="sxs-lookup"><span data-stu-id="f4a35-223">**\# Gen 2 Collections**</span></span>

   <span data-ttu-id="f4a35-224">Zobrazí počet opakovaných 2. generace GC došlo od spuštění procesu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="f4a35-225">Hodnota čítače je zvýšena na konec kolekce 2. generace (také nazývané úplný uvolňování).</span><span class="sxs-lookup"><span data-stu-id="f4a35-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="f4a35-226">Čítač zobrazí naposledy zjištěnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="f4a35-227">**Velká velikost objektu haldy**</span><span class="sxs-lookup"><span data-stu-id="f4a35-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="f4a35-228">Zobrazí aktuální velikost v bajtech, včetně volné místo LOH.</span><span class="sxs-lookup"><span data-stu-id="f4a35-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="f4a35-229">Toto počítadlo je aktualizováno na konci uvolňování, ne v každém přidělení.</span><span class="sxs-lookup"><span data-stu-id="f4a35-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="f4a35-230">Podívejte se na čítače výkonu běžný způsob je pomocí sledování výkonu (perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="f4a35-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="f4a35-231">Pomocí "Přidat čítače" přidat čítač zajímavé pro procesy, které kterých vám nejvíc záleží.</span><span class="sxs-lookup"><span data-stu-id="f4a35-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="f4a35-232">Data čítače výkonu můžete uložit do souboru protokolu, jak ukazuje obrázek 4.</span><span class="sxs-lookup"><span data-stu-id="f4a35-232">You can save the performance counter data to a log file, as Figure 4 shows.</span></span>

![Obrázek 4: Přidání čítačů výkonu.](media/loh/perfcounter.png)    
<span data-ttu-id="f4a35-234">Obrázek 4: LOH po GC 2. generace</span><span class="sxs-lookup"><span data-stu-id="f4a35-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="f4a35-235">Čítače výkonu může být dotazována také prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="f4a35-236">Spousta lidí shromažďovat, je tímto způsobem v rámci své běžné testování procesu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="f4a35-237">Při jejich přímé čítače s hodnotami, které jsou neobvyklého, používají jiným způsobem získat podrobnější data, které pomáhají při šetření.</span><span class="sxs-lookup"><span data-stu-id="f4a35-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="f4a35-238">Doporučujeme, aby vám umožní používat události trasování událostí místo výkonu čítače, protože trasování událostí pro Windows poskytuje mnohem širší informace.</span><span class="sxs-lookup"><span data-stu-id="f4a35-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw"></a><span data-ttu-id="f4a35-239">Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="f4a35-239">ETW</span></span>

<span data-ttu-id="f4a35-240">Uvolňování paměti poskytuje bohatou sadu události trasování událostí, které vám pomohou pochopit, co je to halda a proč.</span><span class="sxs-lookup"><span data-stu-id="f4a35-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="f4a35-241">V následujících příspěvcích na blogu ukazují, jak shromažďovat a pochopit uvolňování paměti události trasování událostí pro Windows:</span><span class="sxs-lookup"><span data-stu-id="f4a35-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="f4a35-242">Události trasování událostí pro Windows GC - 1 </span><span class="sxs-lookup"><span data-stu-id="f4a35-242">GC ETW Events - 1 </span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/22/gc-etw-events.aspx)

- [<span data-ttu-id="f4a35-243">Události trasování událostí pro Windows GC - 2</span><span class="sxs-lookup"><span data-stu-id="f4a35-243">GC ETW Events - 2</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-2.aspx)

- [<span data-ttu-id="f4a35-244">Události trasování událostí pro Windows GC - 3</span><span class="sxs-lookup"><span data-stu-id="f4a35-244">GC ETW Events - 3</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-3.aspx) 

- [<span data-ttu-id="f4a35-245">Události trasování událostí pro Windows GC - 4</span><span class="sxs-lookup"><span data-stu-id="f4a35-245">GC ETW Events - 4</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/30/gc-etw-events-4.aspx)

<span data-ttu-id="f4a35-246">K identifikaci nadměrné generace 2 GC způsobeno dočasnou LOH přidělení, podívejte se na sloupce důvod aktivační událost pro GC.</span><span class="sxs-lookup"><span data-stu-id="f4a35-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="f4a35-247">Pro jednoduchý test, který pouze přiděluje dočasné objekty velké, může shromažďovat informace o události trasování událostí s následující [nástroje PerfView](https://www.microsoft.com/download/details.aspx?id=28567) příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="f4a35-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="f4a35-248">Výsledkem je přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="f4a35-248">The result is something like this:</span></span>
 
![Obrázek 5: Prozkoumání události trasování událostí pro Windows pomocí nástroje PerfView](media/loh/perfview.png)  
<span data-ttu-id="f4a35-250">Obrázek 5: Události trasování událostí pro Windows zobrazí pomocí nástroje PerfView</span><span class="sxs-lookup"><span data-stu-id="f4a35-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="f4a35-251">Jak vidíte, jsou všechny GC 2. generace GC a se všechny spouštějí AllocLarge, což znamená, že přidělování velkého objektu aktivaci tato globální Katalog.</span><span class="sxs-lookup"><span data-stu-id="f4a35-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="f4a35-252">Víme, že jsou tyto přidělení dočasné protože **LOH základními míra %** sloupec uvádí 1 %.</span><span class="sxs-lookup"><span data-stu-id="f4a35-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="f4a35-253">Můžete shromažďovat další události trasování událostí pro Windows, které zjistíte, kdo přidělené tyto velké objekty.</span><span class="sxs-lookup"><span data-stu-id="f4a35-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="f4a35-254">Následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f4a35-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="f4a35-255">shromažďuje AllocationTick událost, která je aktivována, přibližně každých 100 kB vhodné přidělení.</span><span class="sxs-lookup"><span data-stu-id="f4a35-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="f4a35-256">Jinými slovy vyvolání události pokaždé, když je přidělen velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="f4a35-257">Pak můžete najít v některém z alokační haldě GC zobrazení, která ukazují callstacks, která přidělena rozsáhlé objekty:</span><span class="sxs-lookup"><span data-stu-id="f4a35-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>
 
![Obrázek 6: Alokační haldě GC zobrazení](media/loh/perfview2.png)  
<span data-ttu-id="f4a35-259">Obrázek 6: Alokační haldě GC zobrazení</span><span class="sxs-lookup"><span data-stu-id="f4a35-259">Figure 6: A GC Heap Alloc view</span></span>
 
<span data-ttu-id="f4a35-260">Jak vidíte, to je velmi jednoduchý test, který právě přiděluje rozsáhlé objekty z jeho `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="f4a35-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="f4a35-261">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="f4a35-261">A debugger</span></span>

<span data-ttu-id="f4a35-262">Pokud máte je výpis stavu paměti a potřebujete podívat, jaké objekty jsou ve skutečnosti na LOH, můžete použít [rozšíření ladění SoS](http://msdn2.microsoft.com/ms404370.aspx) poskytované .NET.</span><span class="sxs-lookup"><span data-stu-id="f4a35-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](http://msdn2.microsoft.com/ms404370.aspx) provided by .NET.</span></span> 

> [!NOTE]
> <span data-ttu-id="f4a35-263">Ladění příkazy uvedené v této části se vztahují na [ladicí programy Windows](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="f4a35-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="f4a35-264">Následuje příklad výstupu z analýza LOH:</span><span class="sxs-lookup"><span data-stu-id="f4a35-264">The following shows sample output from analyzing the LOH:</span></span>

```
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

<span data-ttu-id="f4a35-265">Velikost haldy LOH je (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtů.</span><span class="sxs-lookup"><span data-stu-id="f4a35-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="f4a35-266">Mezi 023e1000 adresy a 033db630 8,008,736 bajtů obsazena pole <xref:System.Object?displayProperty=fullName> objekty, 6,663,696 bajtů jsou obsazena pole <xref:System.Byte?displayProperty=nameWithType> objekty a 2,081,792 bajtů obsazena volného místa.</span><span class="sxs-lookup"><span data-stu-id="f4a35-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=fullName> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="f4a35-267">V některých případech ladicí program ukazuje, že je celková velikost LOH je menší než 85,000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="f4a35-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="f4a35-268">K tomu dochází, protože modul runtime, samotné používá LOH přidělit některé objekty, které jsou menší než velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="f4a35-269">Vzhledem k tomu LOH není komprimován, někdy LOH je thoought jako zdroj fragmentace.</span><span class="sxs-lookup"><span data-stu-id="f4a35-269">Because the LOH is not compacted, sometimes the LOH is thoought to be the source of fragmentation.</span></span> <span data-ttu-id="f4a35-270">Fragmentace znamená:</span><span class="sxs-lookup"><span data-stu-id="f4a35-270">Fragmentation means:</span></span>

- <span data-ttu-id="f4a35-271">Fragmentace spravovaná halda, což je indikován množství volného místa mezi spravovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="f4a35-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="f4a35-272">V SoS `!dumpheap –type Free` příkaz zobrazí množství volného místa mezi spravovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="f4a35-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="f4a35-273">Fragmentace adresního prostoru virtuální paměti (VM), což je paměť označen jako `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="f4a35-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="f4a35-274">Můžete ho získat pomocí různých příkazů ladicího programu v windbg.</span><span class="sxs-lookup"><span data-stu-id="f4a35-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="f4a35-275">Následující příklad ukazuje fragmentace v prostoru virtuálních počítačů:</span><span class="sxs-lookup"><span data-stu-id="f4a35-275">The following example shows fragmentation in the VM space:</span></span>

   ```
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

<span data-ttu-id="f4a35-276">Je dnes běžné zobrazíte fragmentace virtuálního počítače, způsobené dočasné velkých objektů, které vyžadují uvolňování často získat nové spravovaná halda segmenty z operačního systému a verze prázdných zpět do operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f4a35-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="f4a35-277">Pokud chcete ověřit, zda LOH způsobuje fragmentace virtuálních počítačů, můžete nastavit zarážky [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) a [virtualfree –](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) zobrazíte, který je volání.</span><span class="sxs-lookup"><span data-stu-id="f4a35-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) and [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) to see who call them.</span></span> <span data-ttu-id="f4a35-278">Například pokud chcete zjistit, kdo se pokusil přidělit bloky virtuální paměti větší než 8MBB z operačního systému, můžete nastavit zarážky takto:</span><span class="sxs-lookup"><span data-stu-id="f4a35-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="f4a35-279">Tento příkaz do ladicího programu a zobrazuje jenom pokud zásobník volání [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) je volán s velikost alokační větší než 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="f4a35-279">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="f4a35-280">Přidat funkci CLR 2.0 *Hoarding virtuálních počítačů* , může být užitečná pro scenarious kde segmentuje (včetně velkých a malých objektu haldách) jsou často získali a vydání.</span><span class="sxs-lookup"><span data-stu-id="f4a35-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="f4a35-281">Pokud chcete zadat Hoarding virtuálního počítače, zadejte příznak spuštění `STARTUP_HOARD_GC_VM` prostřednictvím rozhraní API hostování.</span><span class="sxs-lookup"><span data-stu-id="f4a35-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="f4a35-282">Místo vydání prázdný segmenty zpět do operačního systému, modul CLR decommits paměť na tyto segmenty a vloží je na seznamu pohotovostní.</span><span class="sxs-lookup"><span data-stu-id="f4a35-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="f4a35-283">(Všimněte si, že modulu CLR není tomu segmentů, které jsou příliš velké.) Modul CLR později používá tyto segmenty vyhovět nové žádosti o segmentu.</span><span class="sxs-lookup"><span data-stu-id="f4a35-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="f4a35-284">Další čas, které aplikace potřebuje nový segment, modul CLR používá jednu z tohoto seznamu pohotovostní Pokud nemůže najít ten, který je dost velký.</span><span class="sxs-lookup"><span data-stu-id="f4a35-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="f4a35-285">Virtuální počítač hoarding je také užitečné pro aplikace, které má být blokování do segmentů, které se již získal, zvolte například některé serveru aplikací, které jsou dominantní aplikace běžící v systému, aby se zabránilo nedostatek paměti výjimky.</span><span class="sxs-lookup"><span data-stu-id="f4a35-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="f4a35-286">Důrazně doporučujeme při použití této funkce zajistit, že aplikace má využití poměrně stálé paměti pečlivě otestovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f4a35-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
<span data-ttu-id="f4a35-287">BP kernel32! virtualalloc "j (dwo (@esp+ 8) > 800000), kb';' g. "</span><span class="sxs-lookup"><span data-stu-id="f4a35-287">bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"</span></span>
```

This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).

CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released. To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API. Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list. (Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests. The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.

VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.

We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.
