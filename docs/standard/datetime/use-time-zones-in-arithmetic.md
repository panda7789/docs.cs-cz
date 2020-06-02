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
ms.openlocfilehash: af19145f7caa9dbe8630ae7593734769e98720d0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280917"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="7226b-102">Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů</span><span class="sxs-lookup"><span data-stu-id="7226b-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="7226b-103">Obvykle při provádění aritmetických operací s daty a časem <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnotami neodráží výsledek žádná pravidla upravující časová pásma.</span><span class="sxs-lookup"><span data-stu-id="7226b-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="7226b-104">To platí i v případě, že časové pásmo hodnoty data a času je jasně identifikovatelné (například když <xref:System.DateTime.Kind%2A> je vlastnost nastavena na hodnotu <xref:System.DateTimeKind.Local> ).</span><span class="sxs-lookup"><span data-stu-id="7226b-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="7226b-105">V tomto tématu se dozvíte, jak provádět aritmetické operace s hodnotami data a času, které patří do konkrétního časového pásma.</span><span class="sxs-lookup"><span data-stu-id="7226b-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="7226b-106">Výsledky aritmetických operací budou odrážet pravidla upravující časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="7226b-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="7226b-107">Použití pravidel úprav pro aritmetické operace s daty a časem</span><span class="sxs-lookup"><span data-stu-id="7226b-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="7226b-108">Implementujte některé metody, které budou úzce připojovat hodnotu data a času s časovým pásmem, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="7226b-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="7226b-109">Například deklarujete strukturu, která obsahuje hodnotu data a času a příslušné časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="7226b-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="7226b-110">Následující příklad používá tento přístup k propojení <xref:System.DateTime> hodnoty s časovým pásmem.</span><span class="sxs-lookup"><span data-stu-id="7226b-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="7226b-111">Převeďte čas na koordinovaný světový čas (UTC) voláním <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody nebo <xref:System.TimeZoneInfo.ConvertTime%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7226b-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="7226b-112">Proveďte aritmetickou operaci v čase UTC.</span><span class="sxs-lookup"><span data-stu-id="7226b-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="7226b-113">Převeďte čas z času UTC na původní přiřazené časové pásmo, a to voláním <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7226b-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="7226b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7226b-114">Example</span></span>

<span data-ttu-id="7226b-115">Následující příklad přidá dvě hodiny a třicet minut do 9. března 2008, v 1:30 dop.</span><span class="sxs-lookup"><span data-stu-id="7226b-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="7226b-116">Střední oblast (běžný čas)</span><span class="sxs-lookup"><span data-stu-id="7226b-116">Central Standard Time.</span></span> <span data-ttu-id="7226b-117">Přechod časového pásma na letní čas probíhá třicet minut později, v 2:00 ráno.</span><span class="sxs-lookup"><span data-stu-id="7226b-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="7226b-118">9. března 2008.</span><span class="sxs-lookup"><span data-stu-id="7226b-118">on March 9, 2008.</span></span> <span data-ttu-id="7226b-119">Vzhledem k tomu, že příklad následuje po čtyřech krocích uvedených v předchozí části, správně oznamuje výsledný čas jako 5:00 dop.</span><span class="sxs-lookup"><span data-stu-id="7226b-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="7226b-120">9. března 2008.</span><span class="sxs-lookup"><span data-stu-id="7226b-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="7226b-121"><xref:System.DateTime> <xref:System.DateTimeOffset> Z časového pásma, ke kterému by mohly patřit, i hodnoty a jsou odasociovány.</span><span class="sxs-lookup"><span data-stu-id="7226b-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="7226b-122">Chcete-li provádět aritmetické operace s datem a časem způsobem, který automaticky aplikuje pravidla pro úpravu časového pásma, časové pásmo, do kterého patří jakákoli hodnota data a času, musí být ihned identifikovatelné.</span><span class="sxs-lookup"><span data-stu-id="7226b-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="7226b-123">To znamená, že datum a čas a jeho přidružené časové pásmo musí být úzce spojeny.</span><span class="sxs-lookup"><span data-stu-id="7226b-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="7226b-124">To lze provést několika způsoby, mezi které patří následující:</span><span class="sxs-lookup"><span data-stu-id="7226b-124">There are several ways to do this, which include the following:</span></span>

- <span data-ttu-id="7226b-125">Předpokládejte, že všechny časy používané v aplikaci patří do konkrétního časového pásma.</span><span class="sxs-lookup"><span data-stu-id="7226b-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="7226b-126">I když je to v některých případech vhodné, nabízí tento přístup omezená flexibilitu a možnou omezené přenositelnost.</span><span class="sxs-lookup"><span data-stu-id="7226b-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

- <span data-ttu-id="7226b-127">Definujte typ, který pevně Couples datum a čas s přidruženým časovým pásmem zahrnutím jako polí typu.</span><span class="sxs-lookup"><span data-stu-id="7226b-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="7226b-128">Tento přístup se používá v příkladu kódu, který definuje strukturu pro uložení data a času a časového pásma do dvou polí členů.</span><span class="sxs-lookup"><span data-stu-id="7226b-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="7226b-129">Tento příklad ukazuje, jak provádět aritmetické operace s <xref:System.DateTime> hodnotami, takže pravidla úpravy časového pásma se aplikují na výsledek.</span><span class="sxs-lookup"><span data-stu-id="7226b-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="7226b-130">Hodnoty však <xref:System.DateTimeOffset> lze použít stejně snadno.</span><span class="sxs-lookup"><span data-stu-id="7226b-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="7226b-131">Následující příklad ukazuje, jak může být kód v původním příkladu přizpůsoben pro použití <xref:System.DateTimeOffset> namísto <xref:System.DateTime> hodnot.</span><span class="sxs-lookup"><span data-stu-id="7226b-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="7226b-132">Všimněte si, že pokud je toto sčítání provedeno na základě <xref:System.DateTimeOffset> hodnoty, aniž byste ji nejprve převedli na čas UTC, výsledek odráží správný bod v čase, ale jeho posun nereflektuje, že určené časové pásmo pro daný čas.</span><span class="sxs-lookup"><span data-stu-id="7226b-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="7226b-133">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="7226b-133">Compiling the code</span></span>

<span data-ttu-id="7226b-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7226b-134">This example requires:</span></span>

- <span data-ttu-id="7226b-135">Tento <xref:System> obor názvů se naimportuje pomocí `using` příkazu (vyžaduje se v kódu jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="7226b-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="7226b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="7226b-136">See also</span></span>

- [<span data-ttu-id="7226b-137">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="7226b-137">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="7226b-138">Provádění aritmetických operací s daty a časy</span><span class="sxs-lookup"><span data-stu-id="7226b-138">Performing arithmetic operations with dates and times</span></span>](performing-arithmetic-operations.md)
