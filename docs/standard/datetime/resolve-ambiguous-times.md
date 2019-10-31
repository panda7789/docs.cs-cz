---
title: 'Postupy: řešení dvojznačných časů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 0b5b28c588237fb2f7f069aaef06f3f73d5268bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122251"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="1cb70-102">Postupy: řešení dvojznačných časů</span><span class="sxs-lookup"><span data-stu-id="1cb70-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="1cb70-103">Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="1cb70-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="1cb70-104">K tomu dochází, když se změní čas v čase, například během přechodu z letního času v časovém pásmu do standardního času.</span><span class="sxs-lookup"><span data-stu-id="1cb70-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="1cb70-105">Při zpracování dvojznačného času můžete provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="1cb70-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="1cb70-106">Zajistěte, aby se čas namapoval na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="1cb70-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="1cb70-107">Můžete například předpokládat, že nejednoznačná doba je vždy vyjádřena v časovém pásmu standardního času.</span><span class="sxs-lookup"><span data-stu-id="1cb70-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="1cb70-108">Pokud je nejednoznačným časem položka dat zadaná uživatelem, můžete ji ponechat uživateli, aby vyřešila nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="1cb70-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="1cb70-109">V tomto tématu se dozvíte, jak vyřešit dvojznačný čas za předpokladu, že představuje standardní čas časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1cb70-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="1cb70-110">Chcete-li namapovat nejednoznačný čas na běžný čas v časovém pásmu</span><span class="sxs-lookup"><span data-stu-id="1cb70-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="1cb70-111">Voláním metody <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> určíte, zda je čas nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="1cb70-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="1cb70-112">Pokud je čas dvojznačný, odečíst čas z objektu <xref:System.TimeSpan> vráceného vlastností <xref:System.TimeZoneInfo.BaseUtcOffset%2A> časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1cb70-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="1cb70-113">Voláním metody `static` (`Shared` in Visual Basic .NET <xref:System.DateTime.SpecifyKind%2A>) nastavte vlastnost <xref:System.DateTime.Kind%2A> hodnoty data a času UTC na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1cb70-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="1cb70-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cb70-114">Example</span></span>

<span data-ttu-id="1cb70-115">Následující příklad ukazuje, jak převést dvojznačný čas na čas UTC za předpokladu, že představuje standardní čas místního časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1cb70-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="1cb70-116">Příklad se skládá z metody s názvem `ResolveAmbiguousTime`, která určuje, zda <xref:System.DateTime> předaná hodnota je nejednoznačná.</span><span class="sxs-lookup"><span data-stu-id="1cb70-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="1cb70-117">Pokud je hodnota dvojznačná, metoda vrátí <xref:System.DateTime> hodnotu, která představuje odpovídající čas UTC.</span><span class="sxs-lookup"><span data-stu-id="1cb70-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="1cb70-118">Metoda zpracovává tento převod odečtením hodnoty vlastnosti <xref:System.TimeZoneInfo.BaseUtcOffset%2A> místního časového pásma z místního času.</span><span class="sxs-lookup"><span data-stu-id="1cb70-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="1cb70-119">Obvykle je nejednoznačná doba zpracována voláním metody <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pro načtení pole <xref:System.TimeSpan> objektů, které obsahují nejednoznačná časová posun UTC.</span><span class="sxs-lookup"><span data-stu-id="1cb70-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="1cb70-120">Tento příklad ale provede libovolný předpoklad, že nejednoznačný čas by měl být vždy namapován na standardní čas časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1cb70-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="1cb70-121">Vlastnost <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vrací posun mezi časem UTC a standardním časem časového pásma.</span><span class="sxs-lookup"><span data-stu-id="1cb70-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="1cb70-122">V tomto příkladu jsou všechny odkazy na místní časové pásmo provedeny prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; místní časové pásmo není nikdy přiřazeno k objektové proměnné.</span><span class="sxs-lookup"><span data-stu-id="1cb70-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="1cb70-123">Toto je doporučený postup, protože volání metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> zruší platnost všech objektů, ke kterým je místní časové pásmo přiřazeno.</span><span class="sxs-lookup"><span data-stu-id="1cb70-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1cb70-124">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="1cb70-124">Compiling the code</span></span>

<span data-ttu-id="1cb70-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1cb70-125">This example requires:</span></span>

- <span data-ttu-id="1cb70-126">Obor názvů <xref:System> lze importovat pomocí příkazu `using` (požadováno v C# kódu).</span><span class="sxs-lookup"><span data-stu-id="1cb70-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="1cb70-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1cb70-127">See also</span></span>

- [<span data-ttu-id="1cb70-128">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="1cb70-128">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="1cb70-129">Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele</span><span class="sxs-lookup"><span data-stu-id="1cb70-129">How to: Let users resolve ambiguous times</span></span>](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
