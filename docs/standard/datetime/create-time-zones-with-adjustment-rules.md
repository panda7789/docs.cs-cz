---
title: "Postupy: vytváření časových pásem s pravidly úpravy"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75e1867e810090bf35a0dfc7def5785747f94382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="abce6-102">Postupy: vytváření časových pásem s pravidly úpravy</span><span class="sxs-lookup"><span data-stu-id="abce6-102">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="abce6-103">Informace o přesné časovém pásmu, který je požadován pro aplikace nemusí být na určitém systému k dispozici pro několik důvodů:</span><span class="sxs-lookup"><span data-stu-id="abce6-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="abce6-104">Časové pásmo nikdy byla definována v registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="abce6-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="abce6-105">Data o časovém pásmu byl změněn nebo odstraněn z registru.</span><span class="sxs-lookup"><span data-stu-id="abce6-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="abce6-106">Časové pásmo nemá přesné informace o úpravách časové pásmo pro určité historické období.</span><span class="sxs-lookup"><span data-stu-id="abce6-106">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="abce6-107">V těchto případech můžete volat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda definovat časové pásmo požadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="abce6-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="abce6-108">Přetížení této metody můžete vytvořit časové pásmo s nebo bez pravidel úpravy.</span><span class="sxs-lookup"><span data-stu-id="abce6-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="abce6-109">Pokud se časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly buď pevné nebo plovoucí úpravy.</span><span class="sxs-lookup"><span data-stu-id="abce6-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="abce6-110">(Pro definice těchto podmínkách, najdete v části "Časové pásmo terminologií" v [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="abce6-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abce6-111">Vlastní časová pásma vytvořená voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nejsou přidány do registru.</span><span class="sxs-lookup"><span data-stu-id="abce6-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="abce6-112">Místo toho jsou dostupné pouze prostřednictvím odkazu na objekt vrácený <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="abce6-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="abce6-113">Toto téma ukazuje, jak vytvořit časové pásmo s pravidly úpravy.</span><span class="sxs-lookup"><span data-stu-id="abce6-113">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="abce6-114">Vytvoření časové pásmo, které nepodporuje pravidla úpravy letního času naleznete v tématu [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="abce6-114">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="abce6-115">Chcete-li vytvořit časové pásmo s plovoucí úpravy pravidel</span><span class="sxs-lookup"><span data-stu-id="abce6-115">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="abce6-116">Pro každou úpravu (který je pro každý přechod směrem od a zpět do standardního času v konkrétním časovém intervalu) postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="abce6-116">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="abce6-117">Zadejte počáteční čas přechodu pro úpravu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="abce6-117">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="abce6-118">Je třeba volat <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metoda a předejte ji <xref:System.DateTime> hodnotu, která definuje čas přechodu, celočíselná hodnota, která definuje měsíc přechodu, celočíselná hodnota, která definuje v týdnu, kdy dojde k přechodu, a <xref:System.DayOfWeek> hodnota, která definuje den v týdnu, kdy dojde k přechodu.</span><span class="sxs-lookup"><span data-stu-id="abce6-118">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="abce6-119">Toto volání metody vytváří <xref:System.TimeZoneInfo.TransitionTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="abce6-119">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="abce6-120">Zadejte čas dokončení přechodu pro úpravu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="abce6-120">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="abce6-121">To vyžaduje další volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="abce6-121">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="abce6-122">Toto volání metody vytváří druhý <xref:System.TimeZoneInfo.TransitionTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="abce6-122">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="abce6-123">Volání <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> metoda a předejte ji efektivní počáteční a koncové datum úpravy, <xref:System.TimeSpan> objekt, který definuje množství času v přechodu a dvě <xref:System.TimeZoneInfo.TransitionTime> objekty, které definují při přechody do a z letní čas čas následovat.</span><span class="sxs-lookup"><span data-stu-id="abce6-123">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="abce6-124">Toto volání metody vytváří <xref:System.TimeZoneInfo.AdjustmentRule> objektu.</span><span class="sxs-lookup"><span data-stu-id="abce6-124">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="abce6-125">Přiřazení <xref:System.TimeZoneInfo.AdjustmentRule> objekt, který má pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty.</span><span class="sxs-lookup"><span data-stu-id="abce6-125">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="abce6-126">Definujte časové pásmo zobrazovaný název.</span><span class="sxs-lookup"><span data-stu-id="abce6-126">Define the time zone's display name.</span></span> <span data-ttu-id="abce6-127">Zobrazovaný název následuje poměrně standardní formát, ve kterém posun časového pásma z koordinovaný světový čas (UTC) uzavřený v závorkách a následuje řetězec, který identifikuje časové pásmo, jeden nebo více měst v časovém pásmu, nebo v jednom nebo více cou oložky nebo oblasti v časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="abce6-127">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="abce6-128">Definuje název časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="abce6-128">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="abce6-129">Obvykle se tento řetězec se používá jako identifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="abce6-129">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="abce6-130">Zadejte název časového pásma letní čas.</span><span class="sxs-lookup"><span data-stu-id="abce6-130">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="abce6-131">Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="abce6-131">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="abce6-132">Vytváření instancí <xref:System.TimeSpan> objekt, který definuje posun časového pásma od času UTC.</span><span class="sxs-lookup"><span data-stu-id="abce6-132">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="abce6-133">Časová pásma s časy, které jsou novější než čas UTC mít kladný posun.</span><span class="sxs-lookup"><span data-stu-id="abce6-133">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="abce6-134">Časová pásma s časy, které jsou starší než čas UTC mít záporný posun.</span><span class="sxs-lookup"><span data-stu-id="abce6-134">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="abce6-135">Volání <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metoda pro vytvoření instance nového časového pásma.</span><span class="sxs-lookup"><span data-stu-id="abce6-135">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="abce6-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="abce6-136">Example</span></span>

<span data-ttu-id="abce6-137">V následujícím příkladu definuje centrální standardní časové pásmo pro Spojené státy americké, zahrnující pravidla úprav pro celou řadu časové intervaly z 1918 tohoto.</span><span class="sxs-lookup"><span data-stu-id="abce6-137">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="abce6-138">Časové pásmo vytvořené v tomto příkladu má více pravidel úpravy.</span><span class="sxs-lookup"><span data-stu-id="abce6-138">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="abce6-139">Musí být dbát na to, že efektivní počáteční a koncové datum jakéhokoli pravidla úpravy nepřekrývají s daty z jiné pravidlo úpravy.</span><span class="sxs-lookup"><span data-stu-id="abce6-139">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="abce6-140">Pokud dojde překrytí <xref:System.InvalidTimeZoneException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="abce6-140">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="abce6-141">Pro plovoucí úpravy pravidel, je předána hodnota 5 `week` parametr <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metoda k označení, že dojde k přechodu poslední týden v určitém měsíci.</span><span class="sxs-lookup"><span data-stu-id="abce6-141">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="abce6-142">Při vytváření pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty, které chcete použít v <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> volání metody kód inicializovat pole velikosti požadované počtem úpravy, které mají být vytvořeny pro časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="abce6-142">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="abce6-143">Místo toho tento příklad kódu volá <xref:System.Collections.Generic.List%601.Add%2A> metodu pro přidání do obecný každé pravidlo úpravy <xref:System.Collections.Generic.List%601> kolekce <xref:System.TimeZoneInfo.AdjustmentRule> objekty.</span><span class="sxs-lookup"><span data-stu-id="abce6-143">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="abce6-144">Kód pak zavolá <xref:System.Collections.Generic.List%601.CopyTo%2A> metoda kopírování členy této kolekce do pole.</span><span class="sxs-lookup"><span data-stu-id="abce6-144">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="abce6-145">V příkladu se používá také <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metoda definovat pevným datem.</span><span class="sxs-lookup"><span data-stu-id="abce6-145">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="abce6-146">Toto je podobná volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metoda, s tím rozdílem, že IT oddělení vyžaduje pouze čas, měsíc a den parametrů přechodu.</span><span class="sxs-lookup"><span data-stu-id="abce6-146">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="abce6-147">V příkladu lze otestovat pomocí kódu, například následující:</span><span class="sxs-lookup"><span data-stu-id="abce6-147">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="abce6-148">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="abce6-148">Compiling the code</span></span>

<span data-ttu-id="abce6-149">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="abce6-149">This example requires:</span></span>

* <span data-ttu-id="abce6-150">Aby byl přidán odkaz na System.Core.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="abce6-150">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="abce6-151">Aby byly importované následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="abce6-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="abce6-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="abce6-152">See also</span></span>

<span data-ttu-id="abce6-153">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
[postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="abce6-153">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span></span>
