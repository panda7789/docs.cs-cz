---
title: "Postupy: uživatelům řešení víceznačných časových údajů"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6409e676944f64931b197fda1a6a7b392c268c97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="ac66c-102">Postupy: uživatelům řešení víceznačných časových údajů</span><span class="sxs-lookup"><span data-stu-id="ac66c-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="ac66c-103">Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="ac66c-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="ac66c-104">K tomu dojde, při času hodin se upraví zpět v čase, například při přechodu z letního času časového pásma na jeho (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ac66c-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="ac66c-105">Při zpracování nejednoznačný čas, můžete provést jednu z těchto možností:</span><span class="sxs-lookup"><span data-stu-id="ac66c-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="ac66c-106">Pokud nejednoznačný čas položky data zadaná uživatelem, můžete je nechat uživateli, aby vyřešit nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="ac66c-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="ac66c-107">Zkontrolujte předpoklady o tom, jak mapuje čas UTC.</span><span class="sxs-lookup"><span data-stu-id="ac66c-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="ac66c-108">Například předpokládejte, že který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ac66c-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="ac66c-109">Toto téma ukazuje, jak může uživatel vyřešit nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="ac66c-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="ac66c-110">Aby mohl uživatel, vyřešte nejednoznačný čas</span><span class="sxs-lookup"><span data-stu-id="ac66c-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="ac66c-111">Získá datum a čas zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ac66c-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="ac66c-112">Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metoda k určení, zda je čas nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="ac66c-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="ac66c-113">Pokud je čas nejednoznačný, zavolejte <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda k načtení pole <xref:System.TimeSpan> objekty.</span><span class="sxs-lookup"><span data-stu-id="ac66c-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="ac66c-114">Každý prvek v poli obsahuje časový posun můžete namapovat nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="ac66c-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="ac66c-115">Umožní uživateli vybrat požadovaný posun.</span><span class="sxs-lookup"><span data-stu-id="ac66c-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="ac66c-116">Získáte odečtením posun vybraný uživatelem z místního času datum a čas UTC.</span><span class="sxs-lookup"><span data-stu-id="ac66c-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="ac66c-117">Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodu a nastavit UTC hodnota data a času na <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac66c-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="ac66c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac66c-118">Example</span></span>

<span data-ttu-id="ac66c-119">Následující příklad zobrazí výzvu k zadání datum a čas a pokud je nejednoznačný, umožňuje uživateli vybrat čas UTC, která mapuje nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="ac66c-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="ac66c-120">Základní příklad kódu používá pole <xref:System.TimeSpan> objekty pro označení možných posunů nejednoznačný čas od času UTC.</span><span class="sxs-lookup"><span data-stu-id="ac66c-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="ac66c-121">Tyto posuny jsou však pravděpodobně smysl pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="ac66c-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="ac66c-122">O vysvětlení význam posuny, kód také popisuje, zda posunutí představuje místní časové pásmo (běžný čas) nebo jeho letní čas.</span><span class="sxs-lookup"><span data-stu-id="ac66c-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="ac66c-123">Určuje kód, který čas je standardní a který čas je letní porovnáním posunu s hodnotou <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ac66c-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="ac66c-124">Tato vlastnost určuje rozdíl mezi UTC a časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ac66c-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="ac66c-125">V tomto příkladu jsou provedeny všechny odkazy na místní časové pásmo prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas zóny nikdy přiřazená proměnná objektu.</span><span class="sxs-lookup"><span data-stu-id="ac66c-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="ac66c-126">Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda by způsobila neplatnost objekty, které je přiřazeno místní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="ac66c-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ac66c-127">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ac66c-127">Compiling the code</span></span>

<span data-ttu-id="ac66c-128">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ac66c-128">This example requires:</span></span>

* <span data-ttu-id="ac66c-129">Aby byl přidán odkaz na System.Core.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="ac66c-129">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="ac66c-130">Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="ac66c-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac66c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac66c-131">See also</span></span>

<span data-ttu-id="ac66c-132">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postupy: řešení víceznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="ac66c-132">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md)</span></span>
