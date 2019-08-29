---
title: 'Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf97f1a08c6df13ce639466fc07472926c63987f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106625"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="79aa3-102">Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele</span><span class="sxs-lookup"><span data-stu-id="79aa3-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="79aa3-103">Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="79aa3-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="79aa3-104">K tomu dochází, když se změní čas v čase, například během přechodu z letního času v časovém pásmu do standardního času.</span><span class="sxs-lookup"><span data-stu-id="79aa3-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="79aa3-105">Při zpracování dvojznačného času můžete provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="79aa3-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="79aa3-106">Pokud je nejednoznačným časem položka dat zadaná uživatelem, můžete ji ponechat uživateli, aby vyřešila nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="79aa3-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="79aa3-107">Zajistěte, aby se čas namapoval na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="79aa3-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="79aa3-108">Můžete například předpokládat, že nejednoznačná doba je vždy vyjádřena v časovém pásmu standardního času.</span><span class="sxs-lookup"><span data-stu-id="79aa3-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="79aa3-109">V tomto tématu se dozvíte, jak umožnit uživateli vyřešit nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="79aa3-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="79aa3-110">Aby uživatel mohl vyřešit nejednoznačný čas</span><span class="sxs-lookup"><span data-stu-id="79aa3-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="79aa3-111">Získá uživateli zadání data a času.</span><span class="sxs-lookup"><span data-stu-id="79aa3-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="79aa3-112"><xref:System.TimeZoneInfo.IsAmbiguousTime%2A> Zavolejte metodu pro zjištění, zda je čas nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="79aa3-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="79aa3-113">Pokud je čas dvojznačný, zavolejte <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodu pro načtení <xref:System.TimeSpan> pole objektů.</span><span class="sxs-lookup"><span data-stu-id="79aa3-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="79aa3-114">Každý prvek v poli obsahuje časový posun UTC, na který může být mapován dvojznačný čas.</span><span class="sxs-lookup"><span data-stu-id="79aa3-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="79aa3-115">Umožní uživateli vybrat požadovaný posun.</span><span class="sxs-lookup"><span data-stu-id="79aa3-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="79aa3-116">Získá datum a čas UTC odečtením posunu vybraného uživatelem od místního času.</span><span class="sxs-lookup"><span data-stu-id="79aa3-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="79aa3-117"><xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> <xref:System.DateTime.Kind%2A> Zavolejte metodu`Shared` (in Visual Basic .NET), chcete-li nastavit vlastnost hodnoty data a času UTC na hodnotu. `static`</span><span class="sxs-lookup"><span data-stu-id="79aa3-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="79aa3-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="79aa3-118">Example</span></span>

<span data-ttu-id="79aa3-119">Následující příklad vyzve uživatele k zadání data a času a, pokud je dvojznačný, umožňuje uživateli vybrat čas UTC, ke kterému se nejednoznačná doba mapuje.</span><span class="sxs-lookup"><span data-stu-id="79aa3-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="79aa3-120">Jádro ukázkového kódu používá pole <xref:System.TimeSpan> objektů k označení možných posunů nejednoznačného času od času UTC.</span><span class="sxs-lookup"><span data-stu-id="79aa3-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="79aa3-121">Tyto posuny ale pravděpodobně nebudou smysluplné pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="79aa3-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="79aa3-122">Pro objasnění významu posunu kód také Poznamenejte, zda posun představuje standardní čas místního časového pásma nebo jeho letní čas.</span><span class="sxs-lookup"><span data-stu-id="79aa3-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="79aa3-123">Kód určuje, který čas je standardní a který čas je letní, porovnáním posunu s hodnotou <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="79aa3-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="79aa3-124">Tato vlastnost označuje rozdíl mezi časem UTC a standardním časem časového pásma.</span><span class="sxs-lookup"><span data-stu-id="79aa3-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="79aa3-125">V tomto příkladu jsou všechny odkazy na místní časové pásmo provedeny prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti; místní časové pásmo není nikdy přiřazeno k objektové proměnné.</span><span class="sxs-lookup"><span data-stu-id="79aa3-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="79aa3-126">Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody zruší platnost všech objektů, které jsou přiřazeny k místnímu časovému pásmu.</span><span class="sxs-lookup"><span data-stu-id="79aa3-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="79aa3-127">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="79aa3-127">Compiling the code</span></span>

<span data-ttu-id="79aa3-128">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="79aa3-128">This example requires:</span></span>

- <span data-ttu-id="79aa3-129">Tento obor názvů se naimportuje `using` pomocí příkazu (vyžaduje C# se v kódu). <xref:System></span><span class="sxs-lookup"><span data-stu-id="79aa3-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="79aa3-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79aa3-130">See also</span></span>

- [<span data-ttu-id="79aa3-131">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="79aa3-131">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="79aa3-132">Postupy: Vyřešit dvojznačné časy</span><span class="sxs-lookup"><span data-stu-id="79aa3-132">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)
