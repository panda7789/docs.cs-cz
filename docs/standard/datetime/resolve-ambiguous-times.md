---
title: "Postupy: řešení víceznačných časových údajů"
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
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 251f1914b131c5deed194ad7f3fb068c1d9b27c5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="9b85f-102">Postupy: řešení víceznačných časových údajů</span><span class="sxs-lookup"><span data-stu-id="9b85f-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="9b85f-103">Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="9b85f-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="9b85f-104">K tomu dojde, při času hodin se upraví zpět v čase, například při přechodu z letního času časového pásma na jeho (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="9b85f-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="9b85f-105">Při zpracování nejednoznačný čas, můžete provést jednu z těchto možností:</span><span class="sxs-lookup"><span data-stu-id="9b85f-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="9b85f-106">Zkontrolujte předpoklady o tom, jak mapuje čas UTC.</span><span class="sxs-lookup"><span data-stu-id="9b85f-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="9b85f-107">Například předpokládejte, že který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="9b85f-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="9b85f-108">Pokud nejednoznačný čas položky data zadaná uživatelem, můžete je nechat uživateli, aby vyřešit nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="9b85f-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="9b85f-109">Toto téma ukazuje, jak vyřešit nejednoznačný čas za předpokladu, že představuje časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="9b85f-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="9b85f-110">Pro mapování nejednoznačný čas na časové pásmo (běžný čas)</span><span class="sxs-lookup"><span data-stu-id="9b85f-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="9b85f-111">Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metoda k určení, zda je čas nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="9b85f-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="9b85f-112">Pokud je čas nejednoznačný, odečtena čas z <xref:System.TimeSpan> objekt vrácený časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b85f-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="9b85f-113">Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodu a nastavit UTC hodnota data a času na <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b85f-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="9b85f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b85f-114">Example</span></span>

<span data-ttu-id="9b85f-115">Následující příklad ukazuje, jak převést nejednoznačný čas UTC podle předpokladu, že představuje místní časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="9b85f-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="9b85f-116">V příkladu se skládá z metodu s názvem `ResolveAmbiguousTime` který určuje, zda <xref:System.DateTime> hodnotu do ní předán je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="9b85f-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="9b85f-117">Pokud hodnota je nejednoznačné, vrátí metoda <xref:System.DateTime> hodnotu, která představuje odpovídající čas UTC.</span><span class="sxs-lookup"><span data-stu-id="9b85f-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="9b85f-118">Tato metoda obsluhuje tento převod odečtením hodnoty místní časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost z místního času.</span><span class="sxs-lookup"><span data-stu-id="9b85f-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="9b85f-119">Obvykle je nejednoznačný čas zpracováván voláním <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda k načtení pole <xref:System.TimeSpan> objekty, které obsahují nejednoznačný čas UTC možné posun.</span><span class="sxs-lookup"><span data-stu-id="9b85f-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="9b85f-120">V tomto příkladu však umožňuje libovolné předpoklad, že nejednoznačný čas musí být vždy mapována na časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="9b85f-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="9b85f-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A> Vlastnost vrací posun mezi ČASEM a časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="9b85f-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="9b85f-122">V tomto příkladu jsou provedeny všechny odkazy na místní časové pásmo prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas zóny nikdy přiřazená proměnná objektu.</span><span class="sxs-lookup"><span data-stu-id="9b85f-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="9b85f-123">Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda by způsobila neplatnost objekty, které je přiřazeno místní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="9b85f-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="9b85f-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9b85f-124">Compiling the code</span></span>

<span data-ttu-id="9b85f-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9b85f-125">This example requires:</span></span>

* <span data-ttu-id="9b85f-126">Aby byl přidán odkaz na System.Core.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="9b85f-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="9b85f-127">Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="9b85f-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b85f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b85f-128">See also</span></span>

<span data-ttu-id="9b85f-129">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postup: uživatelům řešení víceznačných časových údajů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="9b85f-129">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span></span>
