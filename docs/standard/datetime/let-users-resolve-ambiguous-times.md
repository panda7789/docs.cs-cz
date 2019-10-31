---
title: 'Postupy: převod nejednoznačných časů uživatelů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122280"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="d84e7-102">Postupy: převod nejednoznačných časů uživatelů</span><span class="sxs-lookup"><span data-stu-id="d84e7-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="d84e7-103">Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="d84e7-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="d84e7-104">K tomu dochází, když se změní čas v čase, například během přechodu z letního času v časovém pásmu do standardního času.</span><span class="sxs-lookup"><span data-stu-id="d84e7-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="d84e7-105">Při zpracování dvojznačného času můžete provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="d84e7-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="d84e7-106">Pokud je nejednoznačným časem položka dat zadaná uživatelem, můžete ji ponechat uživateli, aby vyřešila nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="d84e7-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="d84e7-107">Zajistěte, aby se čas namapoval na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="d84e7-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="d84e7-108">Můžete například předpokládat, že nejednoznačná doba je vždy vyjádřena v časovém pásmu standardního času.</span><span class="sxs-lookup"><span data-stu-id="d84e7-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="d84e7-109">V tomto tématu se dozvíte, jak umožnit uživateli vyřešit nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="d84e7-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="d84e7-110">Aby uživatel mohl vyřešit nejednoznačný čas</span><span class="sxs-lookup"><span data-stu-id="d84e7-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="d84e7-111">Získá uživateli zadání data a času.</span><span class="sxs-lookup"><span data-stu-id="d84e7-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="d84e7-112">Voláním metody <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> určíte, zda je čas nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="d84e7-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="d84e7-113">Pokud je čas dvojznačný, zavolejte metodu <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pro načtení pole objektů <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="d84e7-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="d84e7-114">Každý prvek v poli obsahuje časový posun UTC, na který může být mapován dvojznačný čas.</span><span class="sxs-lookup"><span data-stu-id="d84e7-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="d84e7-115">Umožní uživateli vybrat požadovaný posun.</span><span class="sxs-lookup"><span data-stu-id="d84e7-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="d84e7-116">Získá datum a čas UTC odečtením posunu vybraného uživatelem od místního času.</span><span class="sxs-lookup"><span data-stu-id="d84e7-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="d84e7-117">Voláním metody `static` (`Shared` in Visual Basic .NET <xref:System.DateTime.SpecifyKind%2A>) nastavte vlastnost <xref:System.DateTime.Kind%2A> hodnoty data a času UTC na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d84e7-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="d84e7-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d84e7-118">Example</span></span>

<span data-ttu-id="d84e7-119">Následující příklad vyzve uživatele k zadání data a času a, pokud je dvojznačný, umožňuje uživateli vybrat čas UTC, ke kterému se nejednoznačná doba mapuje.</span><span class="sxs-lookup"><span data-stu-id="d84e7-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="d84e7-120">Jádro ukázkového kódu používá pole objektů <xref:System.TimeSpan> k označení možných posunů nejednoznačného času od času UTC.</span><span class="sxs-lookup"><span data-stu-id="d84e7-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="d84e7-121">Tyto posuny ale pravděpodobně nebudou smysluplné pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="d84e7-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="d84e7-122">Pro objasnění významu posunu kód také Poznamenejte, zda posun představuje standardní čas místního časového pásma nebo jeho letní čas.</span><span class="sxs-lookup"><span data-stu-id="d84e7-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="d84e7-123">Kód určuje, který čas je standardní a který čas je letní, porovnáním posunu s hodnotou vlastnosti <xref:System.TimeZoneInfo.BaseUtcOffset%2A>.</span><span class="sxs-lookup"><span data-stu-id="d84e7-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="d84e7-124">Tato vlastnost označuje rozdíl mezi časem UTC a standardním časem časového pásma.</span><span class="sxs-lookup"><span data-stu-id="d84e7-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="d84e7-125">V tomto příkladu jsou všechny odkazy na místní časové pásmo provedeny prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; místní časové pásmo není nikdy přiřazeno k objektové proměnné.</span><span class="sxs-lookup"><span data-stu-id="d84e7-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="d84e7-126">Toto je doporučený postup, protože volání metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> zruší platnost všech objektů, ke kterým je místní časové pásmo přiřazeno.</span><span class="sxs-lookup"><span data-stu-id="d84e7-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="d84e7-127">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="d84e7-127">Compiling the code</span></span>

<span data-ttu-id="d84e7-128">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d84e7-128">This example requires:</span></span>

- <span data-ttu-id="d84e7-129">Obor názvů <xref:System> lze importovat pomocí příkazu `using` (požadováno v C# kódu).</span><span class="sxs-lookup"><span data-stu-id="d84e7-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="d84e7-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d84e7-130">See also</span></span>

- [<span data-ttu-id="d84e7-131">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="d84e7-131">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="d84e7-132">Postupy: Řešení nejednoznačných časových údajů</span><span class="sxs-lookup"><span data-stu-id="d84e7-132">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)
