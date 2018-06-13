---
title: 'Postupy: používání časových pásem datum a čas aritmetické'
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
ms.openlocfilehash: 9f9d326750cdef96be1aa6055d46b4ac08ec7a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574579"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="2ba54-102">Postupy: používání časových pásem datum a čas aritmetické</span><span class="sxs-lookup"><span data-stu-id="2ba54-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="2ba54-103">Normálně, když provést datum a čas aritmetické pomocí <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnoty, výsledek nezohledňuje všechna pravidla pro úpravu časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="2ba54-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="2ba54-104">To platí i v případě, na časové pásmo hodnoty data a času je jasně identifikovatelné (například když <xref:System.DateTime.Kind%2A> je nastavena na <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="2ba54-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="2ba54-105">Toto téma ukazuje, jak provádět aritmetické operace na hodnoty data a času, které patří do určitého časového pásma.</span><span class="sxs-lookup"><span data-stu-id="2ba54-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="2ba54-106">Výsledky aritmetické operace bude odrážet pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="2ba54-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="2ba54-107">Chcete-li použít pravidla úpravy datum a čas aritmetické</span><span class="sxs-lookup"><span data-stu-id="2ba54-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="2ba54-108">Implementujte některé metody úzce spojovacích hodnota data a času s časovým pásmem, do které patří.</span><span class="sxs-lookup"><span data-stu-id="2ba54-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="2ba54-109">Například deklarujte strukturu, která obsahuje datum a čas hodnota a její časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="2ba54-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="2ba54-110">Následující příklad používá tento přístup k propojení <xref:System.DateTime> hodnotu s časovým pásmem.</span><span class="sxs-lookup"><span data-stu-id="2ba54-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="2ba54-111">Převést čas koordinovaný světový čas (UTC) voláním buď <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metoda nebo <xref:System.TimeZoneInfo.ConvertTime%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2ba54-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="2ba54-112">Provádění aritmetických operací na čas UTC.</span><span class="sxs-lookup"><span data-stu-id="2ba54-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="2ba54-113">Převést čas od času UTC na původní čas přidružené časové pásmo voláním <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="2ba54-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="2ba54-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ba54-114">Example</span></span>

<span data-ttu-id="2ba54-115">Následující příklad přidá dvě hodiny a 30 minut do 9. března 2008 v 1:30 hodin</span><span class="sxs-lookup"><span data-stu-id="2ba54-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="2ba54-116">Centrální běžný čas.</span><span class="sxs-lookup"><span data-stu-id="2ba54-116">Central Standard Time.</span></span> <span data-ttu-id="2ba54-117">Časové pásmo přechodu na letní čas dojde později, 30 minut ve 2:00</span><span class="sxs-lookup"><span data-stu-id="2ba54-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="2ba54-118">9. března 2008.</span><span class="sxs-lookup"><span data-stu-id="2ba54-118">on March 9, 2008.</span></span> <span data-ttu-id="2ba54-119">Vzhledem k tomu, že v příkladu zahrnuje čtyři kroky uvedené v předchozí části, správně hlásí výsledný čas jako 05:00.</span><span class="sxs-lookup"><span data-stu-id="2ba54-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="2ba54-120">9. března 2008.</span><span class="sxs-lookup"><span data-stu-id="2ba54-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="2ba54-121">Obě <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty nejsou přidruženy k žádné časové pásmo, ke kterému můžou patřit.</span><span class="sxs-lookup"><span data-stu-id="2ba54-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="2ba54-122">Pokud chcete provést datum a čas aritmetické způsobem, který automaticky použije pravidla úpravy časového pásma, musí být časové pásmo, které žádné datum a čas patří hodnota okamžitě identifikovatelné.</span><span class="sxs-lookup"><span data-stu-id="2ba54-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="2ba54-123">To znamená, že datum a čas a jeho přidružené časové pásmo musí být úzce párované.</span><span class="sxs-lookup"><span data-stu-id="2ba54-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="2ba54-124">Existuje několik způsobů, jak to provést, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="2ba54-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="2ba54-125">Předpokládejme, že všechny časy použité v aplikaci patří do určitého časového pásma.</span><span class="sxs-lookup"><span data-stu-id="2ba54-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="2ba54-126">I když je vhodné v některých případech, tento postup nabízí omezenou flexibilitu a případně i omezenou přenositelnost.</span><span class="sxs-lookup"><span data-stu-id="2ba54-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="2ba54-127">Zadejte typ, který spojuje úzce datum a čas s jeho přidružené časové pásmo zahrnutím i pole typu.</span><span class="sxs-lookup"><span data-stu-id="2ba54-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="2ba54-128">Tento postup se používá v příkladu kódu, který definuje strukturu pro uložení datum a čas a časové pásmo ve dvou polích člen.</span><span class="sxs-lookup"><span data-stu-id="2ba54-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="2ba54-129">Příklad ukazuje, jak provádět aritmetické operace na <xref:System.DateTime> hodnoty tak, aby na výsledek použita pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="2ba54-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="2ba54-130">Ale <xref:System.DateTimeOffset> hodnoty lze použít stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="2ba54-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="2ba54-131">Následující příklad ilustruje, jak může být přizpůsobena použít kód v původní ukázce <xref:System.DateTimeOffset> místo <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2ba54-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="2ba54-132">Všimněte si, že Pokud Přidání provádí jednoduše na <xref:System.DateTimeOffset> hodnotu bez první převodu na čas UTC, výsledek odráží konkrétní bod v čase, ale její posun toto nereflektuje určené časového pásma.</span><span class="sxs-lookup"><span data-stu-id="2ba54-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2ba54-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2ba54-133">Compiling the code</span></span>

<span data-ttu-id="2ba54-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2ba54-134">This example requires:</span></span>

* <span data-ttu-id="2ba54-135">Aby byl přidán odkaz na System.Core.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="2ba54-135">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="2ba54-136">Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="2ba54-136">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ba54-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ba54-137">See also</span></span>

<span data-ttu-id="2ba54-138">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md)</span><span class="sxs-lookup"><span data-stu-id="2ba54-138">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)</span></span>
