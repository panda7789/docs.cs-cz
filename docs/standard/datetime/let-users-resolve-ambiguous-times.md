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
ms.openlocfilehash: ae6d16bda7a2cd6f2367129b737ec79d8193ebf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903783"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="0bb58-102">Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele</span><span class="sxs-lookup"><span data-stu-id="0bb58-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="0bb58-103">Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný univerzální čas (UTC).</span><span class="sxs-lookup"><span data-stu-id="0bb58-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="0bb58-104">K tomu dochází, když čas dojde k přenastavení zpět v čase, například při přechodu z časové pásmo letního času na jeho (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="0bb58-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="0bb58-105">Při zpracování nejednoznačný čas, můžete provést jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="0bb58-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="0bb58-106">Nejednoznačný čas je to položka data zadaná uživatelem,-li to můžete nechat pro uživatele, aby se vyřešit nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="0bb58-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="0bb58-107">Zkontrolujte předpoklady o způsobu, jakým času mapuje na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="0bb58-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="0bb58-108">Můžete například předpokládat, který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="0bb58-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="0bb58-109">Toto téma ukazuje, jak může uživatel vyřešit nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="0bb58-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="0bb58-110">Aby mohl uživatel vyřešit nejednoznačný čas</span><span class="sxs-lookup"><span data-stu-id="0bb58-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="0bb58-111">Získáte datum a čas zadaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0bb58-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="0bb58-112">Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodou ke zjištění, zda je nejednoznačný čas.</span><span class="sxs-lookup"><span data-stu-id="0bb58-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="0bb58-113">Pokud čas je nejednoznačný, zavolejte <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metody k načtení pole <xref:System.TimeSpan> objekty.</span><span class="sxs-lookup"><span data-stu-id="0bb58-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="0bb58-114">Každý prvek v poli obsahuje nejednoznačný čas můžete namapovat na časový posun.</span><span class="sxs-lookup"><span data-stu-id="0bb58-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="0bb58-115">Nechte uživatele, vyberte požadovanou posun.</span><span class="sxs-lookup"><span data-stu-id="0bb58-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="0bb58-116">Získáte tak, že se Posun vybrané uživatelem z místního času datum a čas UTC.</span><span class="sxs-lookup"><span data-stu-id="0bb58-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="0bb58-117">Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metody nastavte čas UTC data a času hodnoty <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0bb58-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="0bb58-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0bb58-118">Example</span></span>

<span data-ttu-id="0bb58-119">V následujícím příkladu se zobrazí výzva k zadání datum a čas a pokud je nejednoznačný a umožní uživateli vybrat, který mapuje nejednoznačný čas na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="0bb58-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="0bb58-120">Základní příklad kódu používá pole <xref:System.TimeSpan> objektech k určení možných posunů nejednoznačný čas od času UTC.</span><span class="sxs-lookup"><span data-stu-id="0bb58-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="0bb58-121">Tyto hodnoty posunu jsou však pravděpodobně srozumitelné pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="0bb58-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="0bb58-122">Pro objasnění významu posuny, kód rovněž uvedena, zda představuje posun místního časového pásma (běžný čas) nebo jeho letního času.</span><span class="sxs-lookup"><span data-stu-id="0bb58-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="0bb58-123">Kód určuje, kdy je standardní a kdy je letního času porovnáním posun s hodnotou <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0bb58-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="0bb58-124">Tato vlastnost určuje rozdíl mezi časem UTC a časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="0bb58-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="0bb58-125">V tomto příkladu jsou všechny odkazy na místní časové pásmo provedené prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas, zóna není nikdy přiřazeno do proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="0bb58-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="0bb58-126">Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda zruší platnost objektů přiřazené k místním časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="0bb58-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="0bb58-127">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="0bb58-127">Compiling the code</span></span>

<span data-ttu-id="0bb58-128">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0bb58-128">This example requires:</span></span>

* <span data-ttu-id="0bb58-129">Aby byl odkaz na System.Core.dll přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="0bb58-129">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="0bb58-130">Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="0bb58-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bb58-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bb58-131">See also</span></span>

- [<span data-ttu-id="0bb58-132">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="0bb58-132">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="0bb58-133">Postupy: Řešení nejednoznačných časových údajů</span><span class="sxs-lookup"><span data-stu-id="0bb58-133">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)
