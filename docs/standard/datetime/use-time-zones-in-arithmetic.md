---
title: 'Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d504aa9ad7d6e4084192a2434ac408e8fa7a041
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588537"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="9ab50-102">Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů</span><span class="sxs-lookup"><span data-stu-id="9ab50-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="9ab50-103">Obvykle při provádění datum a čas aritmetické pomocí <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnot, výsledek neodráží všechna pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="9ab50-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="9ab50-104">To platí i v případě, časovém pásmu z hodnoty data a času je jasně údaje (například když <xref:System.DateTime.Kind%2A> je nastavena na <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="9ab50-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="9ab50-105">Toto téma ukazuje, jak provádět aritmetické operace na hodnoty data a času, které patří do určitého časového pásma.</span><span class="sxs-lookup"><span data-stu-id="9ab50-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="9ab50-106">Výsledky aritmetické operace bude odrážet pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="9ab50-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="9ab50-107">Použít pravidla úpravy aritmetika data a času</span><span class="sxs-lookup"><span data-stu-id="9ab50-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="9ab50-108">Implementujte některé metody, které úzce párování hodnoty data a času s časovým pásmem, do které patří.</span><span class="sxs-lookup"><span data-stu-id="9ab50-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="9ab50-109">Například definice struktury, která obsahuje datum a čas a její časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="9ab50-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="9ab50-110">Následující příklad používá tento přístup k propojení <xref:System.DateTime> hodnotu s časovým pásmem.</span><span class="sxs-lookup"><span data-stu-id="9ab50-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="9ab50-111">Převod času na koordinovaný univerzální čas (UTC) pomocí volání buď <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metoda nebo <xref:System.TimeZoneInfo.ConvertTime%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9ab50-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="9ab50-112">Proveďte aritmetickou operaci na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="9ab50-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="9ab50-113">Převést čas od času UTC na časové pásmo přidružené původní čas voláním <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9ab50-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="9ab50-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ab50-114">Example</span></span>

<span data-ttu-id="9ab50-115">Následující příklad přidá dvě hodiny a 30 minut do 9. března 2008 v 1:30 hod</span><span class="sxs-lookup"><span data-stu-id="9ab50-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="9ab50-116">Střední (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="9ab50-116">Central Standard Time.</span></span> <span data-ttu-id="9ab50-117">Časové pásmo přechodu na letní čas dojde později, 30 minut ve 2:00:00</span><span class="sxs-lookup"><span data-stu-id="9ab50-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="9ab50-118">9. března, 2008.</span><span class="sxs-lookup"><span data-stu-id="9ab50-118">on March 9, 2008.</span></span> <span data-ttu-id="9ab50-119">Protože příklad následující čtyři kroky uvedené v předchozí části, správně hlásí ve výsledné dobu 5:00:00.</span><span class="sxs-lookup"><span data-stu-id="9ab50-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="9ab50-120">9. března, 2008.</span><span class="sxs-lookup"><span data-stu-id="9ab50-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="9ab50-121">Obě <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty nejsou přidruženy k libovolné časové pásmo, do kterého může patřit.</span><span class="sxs-lookup"><span data-stu-id="9ab50-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="9ab50-122">Pokud chcete provést tak, aby automaticky použije pravidla úpravy časového pásma aritmetika data a času, musí být časové pásmo, do které žádné datum a čas, hodnotu patří okamžitě identifikovatelné.</span><span class="sxs-lookup"><span data-stu-id="9ab50-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="9ab50-123">To znamená, že datum a čas a její přidružené časového pásma musí být úzce spojeny.</span><span class="sxs-lookup"><span data-stu-id="9ab50-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="9ab50-124">Existuje několik způsobů, jak to provést, mezi které patří následující:</span><span class="sxs-lookup"><span data-stu-id="9ab50-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="9ab50-125">Předpokládejme, že, která se použijí všechny časy v aplikaci patří konkrétní časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="9ab50-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="9ab50-126">I když v některých případech je vhodné, tento přístup nabízí omezené flexibilitu a přenositelnost může být omezená.</span><span class="sxs-lookup"><span data-stu-id="9ab50-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="9ab50-127">Definice typu, který úzce spojuje datum a čas s časovým pásmem jeho přidružené zahrnutím i jako pole typu.</span><span class="sxs-lookup"><span data-stu-id="9ab50-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="9ab50-128">Tento přístup se používá v příkladu kódu, který definuje strukturu ukládat data a času a časového pásma ve dvou polích člena.</span><span class="sxs-lookup"><span data-stu-id="9ab50-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="9ab50-129">Příklad ukazuje, jak k provádění aritmetických operací na <xref:System.DateTime> hodnoty tak, aby na výsledek jsou použita pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="9ab50-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="9ab50-130">Ale <xref:System.DateTimeOffset> hodnoty můžete použít stejně snadno.</span><span class="sxs-lookup"><span data-stu-id="9ab50-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="9ab50-131">Následující příklad ukazuje, jak může kód v původním příkladu je adaptovat k použití <xref:System.DateTimeOffset> místo <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9ab50-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="9ab50-132">Všimněte si, že pokud je toto přidání je jednoduše provedeno na <xref:System.DateTimeOffset> hodnoty bez nejprve převodu na čas UTC, výsledek odráží správného bodu v čase, ale její posun toto nereflektuje určeného časového pásma.</span><span class="sxs-lookup"><span data-stu-id="9ab50-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="9ab50-133">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="9ab50-133">Compiling the code</span></span>

<span data-ttu-id="9ab50-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9ab50-134">This example requires:</span></span>

* <span data-ttu-id="9ab50-135">Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="9ab50-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ab50-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ab50-136">See also</span></span>

- [<span data-ttu-id="9ab50-137">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="9ab50-137">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="9ab50-138">Provádění aritmetických operací s daty a časy</span><span class="sxs-lookup"><span data-stu-id="9ab50-138">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)
