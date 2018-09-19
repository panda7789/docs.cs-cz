---
title: Haldy velkých objektů v systémech Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dfe3fdbf71918a7ed2b6dccca24f58688bc14f2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003084"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="1237a-102">Haldy velkých objektů v systémech Windows</span><span class="sxs-lookup"><span data-stu-id="1237a-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="1237a-103">.NET systému uvolňování paměti (GC) vyfiltruje objekty do malé a velké objekty.</span><span class="sxs-lookup"><span data-stu-id="1237a-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="1237a-104">Je-li objekt velké, některé z jeho atributy výrazný nárůst více než pokud objekt je malý.</span><span class="sxs-lookup"><span data-stu-id="1237a-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="1237a-105">Kompresi –, který se kopírování v paměti jinde v haldě – například může být nákladné.</span><span class="sxs-lookup"><span data-stu-id="1237a-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="1237a-106">Z tohoto důvodu systému uvolňování paměti .NET umístí velkých objektů haldy pro velké objekty (loh modulem GC).</span><span class="sxs-lookup"><span data-stu-id="1237a-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="1237a-107">V tomto tématu se podíváme na velkých objektových haldách do hloubky.</span><span class="sxs-lookup"><span data-stu-id="1237a-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="1237a-108">Probereme, co splňuje podmínky objektu jako velkého objektu, jak se shromažďují tyto velké objekty a jaký druh důsledky velké objekty výkonu uložit.</span><span class="sxs-lookup"><span data-stu-id="1237a-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1237a-109">Toto téma popisuje haldy velkých objektů v rozhraní .NET Framework a .NET Core využívající pouze systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="1237a-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="1237a-110">Nezahrnuje LOH systémem implementace .NET na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="1237a-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="1237a-111">Jak objekt končí na velkých objektových haldách a jak je popisovačů GC</span><span class="sxs-lookup"><span data-stu-id="1237a-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="1237a-112">Pokud objekt je větší než nebo rovna hodnotě o velikosti 85 000 bajtů, se považuje za velké objekty.</span><span class="sxs-lookup"><span data-stu-id="1237a-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="1237a-113">Toto číslo bylo určeno optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="1237a-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="1237a-114">Požadavek na přidělení objektu je o velikosti 85 000 nebo více bajtů, modul runtime se přiděluje na velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="1237a-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="1237a-115">Vysvětlení, co to znamená, je užitečné si prohlédnout některé základní informace o uvolňování paměti .NET.</span><span class="sxs-lookup"><span data-stu-id="1237a-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="1237a-116">Uvolňování paměti .NET je generační kolekcí.</span><span class="sxs-lookup"><span data-stu-id="1237a-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="1237a-117">Má tři generace: 0. generace 1. generace a 2. generace.</span><span class="sxs-lookup"><span data-stu-id="1237a-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="1237a-118">Důvodem pro 3 generací je, že v dobře vyladit aplikaci, většina kostka objekty v gen0.</span><span class="sxs-lookup"><span data-stu-id="1237a-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="1237a-119">V serveru aplikaci, byste například přidělení související s každou žádostí kostka, po dokončení požadavku.</span><span class="sxs-lookup"><span data-stu-id="1237a-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="1237a-120">Žádosti o přidělení vydávaných za pochodu vytvořit do gen1 a kostka existuje.</span><span class="sxs-lookup"><span data-stu-id="1237a-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="1237a-121">V podstatě gen1 funguje jako vyrovnávací paměť mezi mladé objekt oblasti a oblasti s dlouhým poločasem rozpadu objektu.</span><span class="sxs-lookup"><span data-stu-id="1237a-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="1237a-122">Malé objekty jsou vždy přiděleny v generaci 0 a v závislosti na jejich životního cyklu, může být povýšen na 1. generace nebo generation2.</span><span class="sxs-lookup"><span data-stu-id="1237a-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="1237a-123">Velké objekty jsou vždy přiděleny v 2. generace.</span><span class="sxs-lookup"><span data-stu-id="1237a-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="1237a-124">Velké objekty patří do 2. generace, protože jsou shromažďovány pouze během shromažďování generace 2.</span><span class="sxs-lookup"><span data-stu-id="1237a-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="1237a-125">Pokud generace jsou shromažďovány, shromažďují se také všech mladších generation(s).</span><span class="sxs-lookup"><span data-stu-id="1237a-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="1237a-126">Například při uvolnění GC 1. generace dojde, se shromažďují i generace 1 a 0.</span><span class="sxs-lookup"><span data-stu-id="1237a-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="1237a-127">A při uvolnění GC 2. generace dojde, celý haldy jsou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="1237a-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="1237a-128">Z tohoto důvodu se také nazývá uvolnění GC 2. generace *úplné uvolňování paměti*.</span><span class="sxs-lookup"><span data-stu-id="1237a-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="1237a-129">Tento článek odkazuje na 2. generace uvolňování paměti namísto úplný úklid GC, ale podmínky jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="1237a-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="1237a-130">Generace poskytují logické zobrazení haldy uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1237a-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="1237a-131">Fyzicky živé objekty ve spravované haldě segmenty.</span><span class="sxs-lookup"><span data-stu-id="1237a-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="1237a-132">A *spravované haldě segmentu* se považuje blok paměti, která rezervuje GC z operačního systému pomocí volání [VirtualAlloc funkce](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) jménem spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1237a-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) on behalf of managed code.</span></span> <span data-ttu-id="1237a-133">Při načtení modulu CLR uvolňování paměti přiděluje dva segmenty počáteční haldy: jeden pro malé objekty (haldy malých objektů, nebo SOH) a jeden pro velké objekty (haldy pro velké objekty).</span><span class="sxs-lookup"><span data-stu-id="1237a-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="1237a-134">Přidělení požadavky splněny pak vložením spravované objekty v těchto segmentech spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="1237a-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="1237a-135">Pokud je objekt menší než o velikosti 85 000 bajtů, přejde na segment pro SOH; v opačném případě přejde LOH segmentu.</span><span class="sxs-lookup"><span data-stu-id="1237a-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="1237a-136">Segmenty usilujeme o to (do menších bloků) jako další a další objekty přidělovány na ně.</span><span class="sxs-lookup"><span data-stu-id="1237a-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="1237a-137">Pro prohlášení o stavu objekty, které byly zachovány při uvolnění GC jsou povýšeny do příští generace.</span><span class="sxs-lookup"><span data-stu-id="1237a-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="1237a-138">Objekty, které byly zachovány při shromažďování generace 0 jsou nyní považovány za objekty generace 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1237a-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="1237a-139">Ale objekty, které byly zachovány při generování nejstarší jsou stále považovány za nejstarší generování.</span><span class="sxs-lookup"><span data-stu-id="1237a-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="1237a-140">Jinými slovy jsou zachované objekty z 2. generace 2. generace objekty; a jsou zachované objekty z LOH LOH objekty, (které jsou shromážděné pomocí gen2).</span><span class="sxs-lookup"><span data-stu-id="1237a-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="1237a-141">Uživatelský kód můžete pouze přidělit v generaci 0 (malých objektů) nebo LOH (velkých objektů).</span><span class="sxs-lookup"><span data-stu-id="1237a-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="1237a-142">Pouze pro uvolňování paměti může "přidělení paměti pro" objekty v 1. generace (podporou zachované objekty z 0. generace) a 2. generace (podporou zachované objekty z generací 1 a 2).</span><span class="sxs-lookup"><span data-stu-id="1237a-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="1237a-143">Při uvolňování paměti se aktivuje, GC trasování prostřednictvím živé objekty a komprimuje je.</span><span class="sxs-lookup"><span data-stu-id="1237a-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="1237a-144">Ale protože je nákladná záležitost komprimace GC *přesune* LOH; usnadňuje volný seznam mimo neživými objekty, které lze znovu použít později ke splnění požadavků na přidělení velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="1237a-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="1237a-145">Sousední neživými objekty jsou provedeny do jednoho objektu zdarma.</span><span class="sxs-lookup"><span data-stu-id="1237a-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="1237a-146">.NET core a .NET Framework (od verze rozhraní .NET Framework 4.5.1) patří <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> vlastnost, která umožňuje uživatelům určit, že LOH má probíhat během další úplné blokující uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1237a-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="1237a-147">A v budoucnu se mohou rozhodnout automaticky komprimovat LOH .NET.</span><span class="sxs-lookup"><span data-stu-id="1237a-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="1237a-148">To znamená, že pokud přidělení paměti pro velké objekty a ujistěte se, že nelze přesunout, by měl stále připnete je.</span><span class="sxs-lookup"><span data-stu-id="1237a-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="1237a-149">Obrázek 1 ukazuje scénář, kde tvoří GC 1. generace za GC 0. generace první kde `Obj1` a `Obj3` generace 2 po první 1. generace uvolňování paměti forms jsou neaktivní a kde `Obj2` a `Obj5` jsou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="1237a-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="1237a-150">Všimněte si, že to a na následujících obrázcích jsou jen jako ukázka; obsahují velmi málo objekty kterého pochopíte, co se stane, že na haldě.</span><span class="sxs-lookup"><span data-stu-id="1237a-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="1237a-151">Ve skutečnosti jsou celou řadu dalších objektů obvykle součástí serverem globálního katalogu.</span><span class="sxs-lookup"><span data-stu-id="1237a-151">In reality, many more objects are typically involved in a GC.</span></span>

![Obrázek 1: Uvolňování paměti generace 0 a 1. generace GC](media/loh/loh-figure-1.jpg)  
<span data-ttu-id="1237a-153">Obrázek 1: Generace 0 a 1. generace GC.</span><span class="sxs-lookup"><span data-stu-id="1237a-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="1237a-154">Obrázek 2 ukazuje, že po 2. generace GC které si všimli, že `Obj1` a `Obj2` jsou neaktivní, GC forms souvislých volného místa, nedostatek paměti, která používá pravděpodobně obsazena `Obj1` a `Obj2`, která byla použita k vyřízení požadavku na přidělení pro `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="1237a-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="1237a-155">Mezera za poslední objekt `Obj3`na konci segmentu slouží také ke splnění požadavků na přidělení.</span><span class="sxs-lookup"><span data-stu-id="1237a-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Obrázek 2: po uvolňování paměti generace 2](media/loh/loh-figure-2.jpg)  
<span data-ttu-id="1237a-157">Obrázek 2: po uvolnění GC 2. generace</span><span class="sxs-lookup"><span data-stu-id="1237a-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="1237a-158">Pokud není k dispozici dostatek volného místa pro plnění požadavků na přidělení velké objekty, uvolňování paměti se nejprve pokusí získat další segmenty z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="1237a-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="1237a-159">Pokud selže, spustí 2. generace uvolňování paměti v naději, uvolněte nějaké místo.</span><span class="sxs-lookup"><span data-stu-id="1237a-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="1237a-160">Během 1. generace nebo 2. generace uvolňování paměti, uvolňování paměti uvolní segmenty, které mají na ně žádné živé objekty zpět do operačního systému pomocí volání [funkce VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1237a-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span></span> <span data-ttu-id="1237a-161">Mezera za poslední živé objekt na konec segmentu je zrušeny (s výjimkou na dočasný segment, ve kterém gen0/gen1 za provozu, ve kterém systému uvolňování paměti zachovat některé potvrzené, protože se být přidělování vaší aplikace v něm hned).</span><span class="sxs-lookup"><span data-stu-id="1237a-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="1237a-162">A bezplatný prostory stále potvrdit, když dojde k jejich vynulování, což znamená, že není nutné zapisovat data v nich zpět na disk operačního systému.</span><span class="sxs-lookup"><span data-stu-id="1237a-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="1237a-163">Vzhledem k tomu, LOH se shromažďují, pouze během GC 2. generace, můžete segmentu LOH uvolněna pouze během těchto uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1237a-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="1237a-164">Obrázek 3 ukazuje scénář, ve kterém systému uvolňování paměti uvolní jeden segment (segment 2) zpět do operačního systému a rozváže více místa na zbývající segmenty.</span><span class="sxs-lookup"><span data-stu-id="1237a-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="1237a-165">Pokud je třeba použít zrušeny místa na konci segmentu pro splnění požadavků na přidělení velkého objektu, potvrzení paměti znovu.</span><span class="sxs-lookup"><span data-stu-id="1237a-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="1237a-166">(Vysvětlení rozvázání/potvrzení, naleznete v dokumentaci k [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1237a-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span></span>

![Obrázek 3: LOH po uvolňování paměti generace 2](media/loh/loh-figure-3.jpg)  
<span data-ttu-id="1237a-168">Obrázek 3: LOH po 2. generace GC</span><span class="sxs-lookup"><span data-stu-id="1237a-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="1237a-169">Když se shromažďují velké objekty</span><span class="sxs-lookup"><span data-stu-id="1237a-169">When is a large object collected?</span></span>

<span data-ttu-id="1237a-170">Obecně platí globální Katalog dojde, pokud jeden z následujících podmínek následující 3 se stane:</span><span class="sxs-lookup"><span data-stu-id="1237a-170">In general, a GC occurs when one of the following following 3 conditions happens:</span></span>

- <span data-ttu-id="1237a-171">Přidělování překračuje generace 0 nebo velkého objektu prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1237a-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="1237a-172">Prahová hodnota je vlastnost generace.</span><span class="sxs-lookup"><span data-stu-id="1237a-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="1237a-173">Prahová hodnota pro generace je nastavena, když uvolňování paměti přiděluje objekty do něj.</span><span class="sxs-lookup"><span data-stu-id="1237a-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="1237a-174">Pokud je překročena prahová hodnota, globální Katalog se aktivuje v této generací.</span><span class="sxs-lookup"><span data-stu-id="1237a-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="1237a-175">Při přidělování malých nebo velkých objektů můžete využívat 0. generace a LOH prahové hodnoty, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1237a-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="1237a-176">Při uvolňování paměti přiděluje do generace 1 a 2, využívá jejich prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1237a-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="1237a-177">Tyto prahové hodnoty je dynamicky vyladěná po spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="1237a-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="1237a-178">To je obvyklý případ; Většina GC dojít kvůli přidělení na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="1237a-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="1237a-179"><xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="1237a-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="1237a-180">Pokud konstruktor bez parametrů <xref:System.GC.Collect?displayProperty=nameWithType> metoda je volána nebo jiné přetížení se předá <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, jsou shromažďovány LOH spolu se zbývajícími spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="1237a-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="1237a-181">Systém je v případě nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="1237a-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="1237a-182">K tomu dojde, když systému uvolňování paměti obdrží oznámení vysoký poměr paměti z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="1237a-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="1237a-183">Pokud uvolňování domnívá, že to 2. generace GC bude produktivní, spustí jednu.</span><span class="sxs-lookup"><span data-stu-id="1237a-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="1237a-184">Rozbor LOH výkonu</span><span class="sxs-lookup"><span data-stu-id="1237a-184">LOH Performance Implications</span></span>

<span data-ttu-id="1237a-185">Přidělení na haldu velkých objektů dopad na výkon následujícími způsoby.</span><span class="sxs-lookup"><span data-stu-id="1237a-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="1237a-186">Přidělování nákladů.</span><span class="sxs-lookup"><span data-stu-id="1237a-186">Allocation cost.</span></span>

  <span data-ttu-id="1237a-187">Modul CLR provede záruku, že se vymaže paměti pro každý nový objekt, že poskytuje navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="1237a-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="1237a-188">To znamená, že přidělování nákladů ve velkém objektu je zcela léta dominovaly paměti vymazání (Pokud aktivuje GC).</span><span class="sxs-lookup"><span data-stu-id="1237a-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="1237a-189">Pokud trvá 2 cykly zrušte jeden bajt, trvá 170,000 cykly zrušte nejmenší velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="1237a-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="1237a-190">Paměť objektu 16MB na počítači s 2GHz vymazáním trvá přibližně 16ms.</span><span class="sxs-lookup"><span data-stu-id="1237a-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="1237a-191">To je docela rozsáhlá náklady.</span><span class="sxs-lookup"><span data-stu-id="1237a-191">That's a rather large cost.</span></span>

- <span data-ttu-id="1237a-192">Kolekce nákladů.</span><span class="sxs-lookup"><span data-stu-id="1237a-192">Collection cost.</span></span>

  <span data-ttu-id="1237a-193">Protože LOH a 2. generace jsou shromažďovány společně, pokud je překročena mezní hodnota buď jeden z kolekce generace 2 se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="1237a-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="1237a-194">Pokud generace, které se z důvodu LOH aktivuje 2 kolekce, 2. generace nebudou nutně mnohem menší po uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1237a-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="1237a-195">Pokud v 2. generace není množství dat, to má minimální dopad.</span><span class="sxs-lookup"><span data-stu-id="1237a-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="1237a-196">Ale pokud generace 2 je velká, může to způsobit problémy s výkonem Pokud mnoho GC 2. generace se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="1237a-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="1237a-197">Mnoho velkých objektů jsou přiděleny velmi dočasný a máte velký SOH, může spotřebovat příliš mnoho času provádění GC.</span><span class="sxs-lookup"><span data-stu-id="1237a-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="1237a-198">Kromě toho přidělování nákladů můžete ve skutečnosti přidání registrace Pokud uchováváte přidělování a volnost velmi velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="1237a-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="1237a-199">Prvky pole s typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="1237a-199">Array elements with reference types.</span></span>

  <span data-ttu-id="1237a-200">Pole (velmi zřídka dochází k instanci objekt, který je ve skutečnosti velký) jsou obvykle velmi velké objekty na LOH.</span><span class="sxs-lookup"><span data-stu-id="1237a-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="1237a-201">Pokud jsou prvky pole bohatého na odkaz, budou vám účtovány náklady, které není k dispozici, pokud nejsou prvky bohatého na odkaz.</span><span class="sxs-lookup"><span data-stu-id="1237a-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="1237a-202">Pokud element neobsahuje žádné odkazy, systému uvolňování paměti nemusí vůbec projít pole.</span><span class="sxs-lookup"><span data-stu-id="1237a-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="1237a-203">Například pokud použijete pole k uložení uzly v binární strom, jeden ze způsobů implementace je k odkazování na uzlu vpravo a vlevo uzel skutečné uzly:</span><span class="sxs-lookup"><span data-stu-id="1237a-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="1237a-204">Pokud `num_nodes` je velké systému uvolňování paměti musí projít aspoň dva odkazy na jeden element.</span><span class="sxs-lookup"><span data-stu-id="1237a-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="1237a-205">Alternativním přístupem je index pravém a levém uzlů úložiště:</span><span class="sxs-lookup"><span data-stu-id="1237a-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="1237a-206">Namísto odkazování data vlevo uzel jako `left.d`, můžete si ji jako `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="1237a-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="1237a-207">A systému uvolňování paměti nemusí podívat se na všechny odkazy pro uzel doleva a doprava.</span><span class="sxs-lookup"><span data-stu-id="1237a-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="1237a-208">Mimo tři faktory jsou obvykle mnohem závažnější než třetí první dva.</span><span class="sxs-lookup"><span data-stu-id="1237a-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="1237a-209">Z tohoto důvodu doporučujeme vám, že přidělíte fond velkých objektů, které můžete použít namísto přidělení dočasné ty.</span><span class="sxs-lookup"><span data-stu-id="1237a-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="1237a-210">Shromažďování dat výkonu pro LOH</span><span class="sxs-lookup"><span data-stu-id="1237a-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="1237a-211">Předtím, než můžete shromáždit údaje o výkonu pro konkrétní oblasti, můžete byste už mít provedli následující:</span><span class="sxs-lookup"><span data-stu-id="1237a-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="1237a-212">Najít důkaz, že by měl být díváte v této oblasti.</span><span class="sxs-lookup"><span data-stu-id="1237a-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="1237a-213">Vyčerpání další oblasti, které znáte nástroje, aniž byste hledání nic, které může vysvětlovat problému s výkonem, které jste viděli.</span><span class="sxs-lookup"><span data-stu-id="1237a-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="1237a-214">Najdete v blogovém [porozumět danému problému, než se pokusíte na vyhledání řešení](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) Další informace o základní informace o paměti a procesoru.</span><span class="sxs-lookup"><span data-stu-id="1237a-214">See the blog [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="1237a-215">Můžete použít následující nástroje ke shromažďování dat o výkonu LOH:</span><span class="sxs-lookup"><span data-stu-id="1237a-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="1237a-216">Čítače výkonu paměti .NET CLR</span><span class="sxs-lookup"><span data-stu-id="1237a-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="1237a-217">Události trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="1237a-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="1237a-218">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="1237a-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="1237a-219">Čítače výkonu paměti .NET CLR</span><span class="sxs-lookup"><span data-stu-id="1237a-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="1237a-220">Tyto čítače výkonu jsou obvykle dobrý první krok při zkoumání problémů s výkonem (i když vám doporučujeme použít [události trasování událostí pro Windows](#etw)).</span><span class="sxs-lookup"><span data-stu-id="1237a-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw)).</span></span> <span data-ttu-id="1237a-221">Konfigurace sledování výkonu tak, že přidáte čítače, které potřebujete, jak je vidět na obrázku 4.</span><span class="sxs-lookup"><span data-stu-id="1237a-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="1237a-222">Ty, které jsou relevantní pro LOH jsou:</span><span class="sxs-lookup"><span data-stu-id="1237a-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="1237a-223">**Úklidy 2.**</span><span class="sxs-lookup"><span data-stu-id="1237a-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="1237a-224">Zobrazí počet, kolikrát od spuštění procesu došlo k 2. generace GC.</span><span class="sxs-lookup"><span data-stu-id="1237a-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="1237a-225">Hodnota čítače je zvýšena na konci kolekce generace 2 (také nazývané úplného uvolňování paměti kolekce).</span><span class="sxs-lookup"><span data-stu-id="1237a-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="1237a-226">Tento čítač zobrazí naposledy zjištěnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1237a-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="1237a-227">**Velikost velkých objektových haldách**</span><span class="sxs-lookup"><span data-stu-id="1237a-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="1237a-228">Zobrazí aktuální velikost v bajtech, včetně volné místo LOH.</span><span class="sxs-lookup"><span data-stu-id="1237a-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="1237a-229">Tento čítač je aktualizován na konci uvolnění, ne při každém přidělení.</span><span class="sxs-lookup"><span data-stu-id="1237a-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="1237a-230">Běžný způsob, jak zobrazit čítače výkonu je pomocí sledování výkonu (perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="1237a-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="1237a-231">Pomocí "Přidat čítače" přidat čítač zajímavé pro procesy, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="1237a-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="1237a-232">Data čítačů výkonu můžete uložit do souboru protokolu, jak je vidět na obrázku 4.</span><span class="sxs-lookup"><span data-stu-id="1237a-232">You can save the performance counter data to a log file, as Figure 4 shows.</span></span>

![Obrázek 4: Přidání čítačů výkonu.](media/loh/perfcounter.png)  
<span data-ttu-id="1237a-234">Obrázek 4: LOH po 2. generace GC</span><span class="sxs-lookup"><span data-stu-id="1237a-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="1237a-235">Čítače výkonu může být dotazována také prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="1237a-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="1237a-236">Řada lidí je shromažďovat tímto způsobem jako součást svých rutinní proces testování.</span><span class="sxs-lookup"><span data-stu-id="1237a-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="1237a-237">Při jejich zjištění čítače nahraďte hodnotami, které jsou neobvyklého, používají jiným způsobem získat podrobnější údaje, které pomáhají při šetření.</span><span class="sxs-lookup"><span data-stu-id="1237a-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="1237a-238">Doporučujeme, abyste místo výkonu použít trasování událostí pro Windows čítače, protože trasování událostí pro Windows poskytuje mnohem bohatší informace.</span><span class="sxs-lookup"><span data-stu-id="1237a-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw"></a><span data-ttu-id="1237a-239">Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="1237a-239">ETW</span></span>

<span data-ttu-id="1237a-240">Poskytuje širokou škálu události trasování událostí, které vám pomohou pochopit, co dělá haldy systému uvolňování paměti a proč.</span><span class="sxs-lookup"><span data-stu-id="1237a-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="1237a-241">V následujících příspěvcích na blogu ukazují, jak shromažďovat a pochopit uvolňování paměti události trasování událostí pro Windows:</span><span class="sxs-lookup"><span data-stu-id="1237a-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="1237a-242">Události trasování událostí pro Windows uvolňování paměti – 1</span><span class="sxs-lookup"><span data-stu-id="1237a-242">GC ETW Events - 1</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/)

- [<span data-ttu-id="1237a-243">Události trasování událostí pro Windows uvolňování paměti – 2</span><span class="sxs-lookup"><span data-stu-id="1237a-243">GC ETW Events - 2</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/)

- [<span data-ttu-id="1237a-244">Události trasování událostí pro Windows uvolňování paměti – 3</span><span class="sxs-lookup"><span data-stu-id="1237a-244">GC ETW Events - 3</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/)

- [<span data-ttu-id="1237a-245">Události trasování událostí pro Windows uvolňování paměti – 4</span><span class="sxs-lookup"><span data-stu-id="1237a-245">GC ETW Events - 4</span></span>](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/)

<span data-ttu-id="1237a-246">K identifikaci nadměrné generace GC 2 způsobena dočasné LOH přidělení, podívejte se na sloupce důvod aktivace pro GC.</span><span class="sxs-lookup"><span data-stu-id="1237a-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="1237a-247">Pro jednoduchý test, který přiděluje jenom dočasné velké objekty, lze shromažďovat informace o události trasování událostí pro Windows s tímto [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="1237a-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="1237a-248">Výsledkem je přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="1237a-248">The result is something like this:</span></span>

![Obrázek 5: Zkoumání událostí ETW pomocí nástroje PerfView](media/loh/perfview.png)  
<span data-ttu-id="1237a-250">Obrázek 5: Události trasování událostí pro Windows zobrazí, pomocí nástroje PerfView</span><span class="sxs-lookup"><span data-stu-id="1237a-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="1237a-251">Jak vidíte, jsou všechny GC 2. generace GC a všechny jsou aktivované pomocí AllocLarge, což znamená, že přidělování ve velkém objektu aktivuje toto uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1237a-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="1237a-252">Víme, že jsou tyto přidělení dočasné vzhledem k tomu, **míra přežití LOH %** říká sloupce 1 %.</span><span class="sxs-lookup"><span data-stu-id="1237a-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="1237a-253">Můžete shromažďovat další události trasování událostí pro Windows, které informují vás, kteří přidělené tyto velké objekty.</span><span class="sxs-lookup"><span data-stu-id="1237a-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="1237a-254">Na příkazovém řádku následující:</span><span class="sxs-lookup"><span data-stu-id="1237a-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="1237a-255">shromažďuje události AllocationTick, která se aktivuje přibližně každých 100 kB za přidělení.</span><span class="sxs-lookup"><span data-stu-id="1237a-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="1237a-256">Jinými slovy událost se aktivuje pokaždé, když je přiděleno ve velkém objektu.</span><span class="sxs-lookup"><span data-stu-id="1237a-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="1237a-257">Pak můžete se podívat na jedno zobrazení alokační haldy uvolňování paměti, které zobrazují zásobníky volání, která přidělena velké objekty:</span><span class="sxs-lookup"><span data-stu-id="1237a-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

![Obrázek 6: Alokační haldy uvolňování paměti zobrazení](media/loh/perfview2.png)  
<span data-ttu-id="1237a-259">Obrázek 6: Alokační haldy uvolňování paměti zobrazení</span><span class="sxs-lookup"><span data-stu-id="1237a-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="1237a-260">Jak je vidět, to je velmi jednoduchý test, který právě přiděluje rozsáhlé objekty z jeho `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="1237a-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="1237a-261">Ladicí program</span><span class="sxs-lookup"><span data-stu-id="1237a-261">A debugger</span></span>

<span data-ttu-id="1237a-262">Pokud vše, co musíte je výpis paměti a je třeba podívat, jaké objekty jsou skutečně na LOH, můžete použít [rozšíření ladění SoS](http://msdn2.microsoft.com/ms404370.aspx) poskytované rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="1237a-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](http://msdn2.microsoft.com/ms404370.aspx) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="1237a-263">Příkazy ladění, které jsou uvedené v této části se vztahují na [ladicích programů Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="1237a-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="1237a-264">Následuje ukázkový výstup z analýzy LOH:</span><span class="sxs-lookup"><span data-stu-id="1237a-264">The following shows sample output from analyzing the LOH:</span></span>

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

<span data-ttu-id="1237a-265">Velikost haldy LOH je (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtů.</span><span class="sxs-lookup"><span data-stu-id="1237a-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="1237a-266">Mezi 023e1000 adresy a 033db630 8,008,736 bajtů obsazena pole <xref:System.Object?displayProperty=nameWithType> objekty, budou obsazeny 6,663,696 bajtů podle pole <xref:System.Byte?displayProperty=nameWithType> objekty a 2,081,792 bajtů obsazena volného místa.</span><span class="sxs-lookup"><span data-stu-id="1237a-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="1237a-267">V některých případech ladicí program ukazuje, že celková velikost LOH menší než o velikosti 85 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="1237a-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="1237a-268">K tomu dochází, protože samotný modul runtime používá LOH přidělit některé objekty, které jsou menší než ve velkém objektu.</span><span class="sxs-lookup"><span data-stu-id="1237a-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="1237a-269">Vzhledem k tomu, že není setřepána LOH, někdy LOH je thoought zdroj fragmentace.</span><span class="sxs-lookup"><span data-stu-id="1237a-269">Because the LOH is not compacted, sometimes the LOH is thoought to be the source of fragmentation.</span></span> <span data-ttu-id="1237a-270">Fragmentace znamená, že:</span><span class="sxs-lookup"><span data-stu-id="1237a-270">Fragmentation means:</span></span>

- <span data-ttu-id="1237a-271">Fragmentace spravované haldě, které jsou označeny množství volného místa mezi spravované objekty.</span><span class="sxs-lookup"><span data-stu-id="1237a-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="1237a-272">V prodejní objednávky `!dumpheap –type Free` příkaz zobrazí množství volného místa mezi spravované objekty.</span><span class="sxs-lookup"><span data-stu-id="1237a-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="1237a-273">Fragmentace adresního prostoru virtuální paměti (VM), což je paměť, označen jako `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="1237a-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="1237a-274">Můžete ho získat s použitím různých příkazů ladicího programu v rámci windbg.</span><span class="sxs-lookup"><span data-stu-id="1237a-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="1237a-275">Následující příklad ukazuje fragmentaci v prostoru virtuálních počítačů:</span><span class="sxs-lookup"><span data-stu-id="1237a-275">The following example shows fragmentation in the VM space:</span></span>

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

<span data-ttu-id="1237a-276">Je běžné zobrazíte fragmentace virtuálního počítače, způsobené dočasné velké objekty, které vyžadují systému uvolňování paměti se často získat nové spravované haldy segmenty z operačního systému a verze prázdných zpět do operačního systému.</span><span class="sxs-lookup"><span data-stu-id="1237a-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="1237a-277">Pokud chcete ověřit, zda LOH způsobuje fragmentaci na virtuální počítač, můžete nastavit zarážku na [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) a [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) zobrazíte jejich volání.</span><span class="sxs-lookup"><span data-stu-id="1237a-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) and [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) to see who call them.</span></span> <span data-ttu-id="1237a-278">Například pokud chcete zjistit, kdo se pokusil přidělení virtuální paměti bloky dat větší než 8MBB z operačního systému, můžete nastavit zarážku takto:</span><span class="sxs-lookup"><span data-stu-id="1237a-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="1237a-279">Tento příkaz do ladicího programu a zásobník volání pouze tehdy, pokud se zobrazí [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) se nazývá velikost alokační větší než 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="1237a-279">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="1237a-280">Funkci přidali CLR 2.0 *VM Hoarding* , může být užitečné pro scenarious kde segmenty (včetně velkých i malých objektů haldy) jsou často získaných a vydání.</span><span class="sxs-lookup"><span data-stu-id="1237a-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="1237a-281">K určení Hoarding virtuálního počítače, zadejte po spuštění příznak, který volá `STARTUP_HOARD_GC_VM` prostřednictvím hostujícího rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1237a-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="1237a-282">Místo vydání prázdné segmenty zpět do operačního systému, CLR rozváže paměti v těchto segmentech a umístí na seznam pohotovostním režimu.</span><span class="sxs-lookup"><span data-stu-id="1237a-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="1237a-283">(Všimněte si, že modul CLR nebude provést pro segmenty, které jsou moc velká.) Modul CLR později použije tyto segmenty splňovat nové požadavky segmentu.</span><span class="sxs-lookup"><span data-stu-id="1237a-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="1237a-284">Příště, že vaše aplikace potřebuje nový segment CLR používá jednu z tohoto seznamu pohotovostní Pokud nemůže najít takový, který je dostatečně velký.</span><span class="sxs-lookup"><span data-stu-id="1237a-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="1237a-285">Hoarding virtuálního počítače je také užitečné pro aplikace, které chcete opřete se o segmenty, které už získali, jako je například některé serverové aplikace, které jsou dominantní aplikace běžící na systému, aby se zabránilo nedostatek paměti výjimky.</span><span class="sxs-lookup"><span data-stu-id="1237a-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="1237a-286">Důrazně doporučujeme při použití této funkce zajistit, že vaše aplikace má využití poměrně stálé paměti pečlivě otestovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1237a-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
