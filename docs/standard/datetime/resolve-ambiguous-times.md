---
title: 'Postupy: řešení nejednoznačných časových údajů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb09b1f087e0a0f726d32d85e06cfb2a9ec741a8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863131"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="ff42b-102">Postupy: řešení nejednoznačných časových údajů</span><span class="sxs-lookup"><span data-stu-id="ff42b-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="ff42b-103">Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný univerzální čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="ff42b-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="ff42b-104">K tomu dochází, když čas dojde k přenastavení zpět v čase, například při přechodu z časové pásmo letního času na jeho (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ff42b-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="ff42b-105">Při zpracování nejednoznačný čas, můžete provést jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="ff42b-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="ff42b-106">Zkontrolujte předpoklady o způsobu, jakým času mapuje na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="ff42b-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="ff42b-107">Můžete například předpokládat, který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ff42b-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="ff42b-108">Nejednoznačný čas je to položka data zadaná uživatelem,-li to můžete nechat pro uživatele, aby se vyřešit nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="ff42b-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="ff42b-109">Toto téma ukazuje, jak vyřešit nejednoznačný čas za předpokladu, že představuje časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ff42b-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="ff42b-110">K namapování nejednoznačný čas na časové pásmo (běžný čas)</span><span class="sxs-lookup"><span data-stu-id="ff42b-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="ff42b-111">Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodou ke zjištění, zda je nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="ff42b-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="ff42b-112">Pokud čas je nejednoznačný, odečíst čas <xref:System.TimeSpan> vrácený časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ff42b-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="ff42b-113">Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metody nastavte čas UTC data a času hodnoty <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ff42b-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="ff42b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff42b-114">Example</span></span>

<span data-ttu-id="ff42b-115">Následující příklad ukazuje, jak převést nejednoznačný čas na čas UTC podle předpokladu, že představuje místní časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ff42b-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="ff42b-116">V příkladu se skládá z metodu s názvem `ResolveAmbiguousTime` , který určuje, zda <xref:System.DateTime> předaná hodnota je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="ff42b-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="ff42b-117">Pokud hodnota je nejednoznačný, metoda vrátí <xref:System.DateTime> hodnotu, která představuje odpovídající čas UTC.</span><span class="sxs-lookup"><span data-stu-id="ff42b-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="ff42b-118">Tato metoda obsluhuje tento převod tak, že se hodnota místní časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost z místního času.</span><span class="sxs-lookup"><span data-stu-id="ff42b-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="ff42b-119">Obvykle je zpracována nejednoznačný čas voláním <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metody k načtení pole <xref:System.TimeSpan> posuny objektů, které obsahují možná nejednoznačný čas UTC.</span><span class="sxs-lookup"><span data-stu-id="ff42b-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="ff42b-120">V tomto příkladu je však libovolného předpokladu, že by vždy nejednoznačný čas musí být mapováno na časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ff42b-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="ff42b-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A> Vlastnost vrací posun mezi UTC a časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="ff42b-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="ff42b-122">V tomto příkladu jsou všechny odkazy na místní časové pásmo provedené prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas, zóna není nikdy přiřazeno do proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="ff42b-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="ff42b-123">Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda zruší platnost objektů přiřazené k místním časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="ff42b-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ff42b-124">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="ff42b-124">Compiling the code</span></span>

<span data-ttu-id="ff42b-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ff42b-125">This example requires:</span></span>

* <span data-ttu-id="ff42b-126">Aby byl odkaz na System.Core.dll přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="ff42b-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="ff42b-127">Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="ff42b-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff42b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff42b-128">See also</span></span>

* [<span data-ttu-id="ff42b-129">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="ff42b-129">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="ff42b-130">Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele</span><span class="sxs-lookup"><span data-stu-id="ff42b-130">How to: Let users resolve ambiguous times</span></span>](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
