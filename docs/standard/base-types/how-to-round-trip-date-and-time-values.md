---
title: 'Postupy: Hodnoty data a času round-trip'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 2e3a58ffe8332e0afec62461f6897d673e1da09f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132009"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="54158-102">Postupy: Hodnoty data a času round-trip</span><span class="sxs-lookup"><span data-stu-id="54158-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="54158-103">V mnoha aplikacích je hodnota data a času určena k jednoznačné identifikaci jednoho bodu v čase.</span><span class="sxs-lookup"><span data-stu-id="54158-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="54158-104">Toto téma ukazuje, jak <xref:System.DateTime> uložit <xref:System.DateTimeOffset> a obnovit hodnotu, hodnotu a hodnotu data a času s informacemi o časovém pásmu tak, aby obnovená hodnota identifikovala stejný čas jako uložená hodnota.</span><span class="sxs-lookup"><span data-stu-id="54158-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="54158-105">Chcete-li round-trip DateTime hodnotu</span><span class="sxs-lookup"><span data-stu-id="54158-105">To round-trip a DateTime value</span></span>

1. <span data-ttu-id="54158-106">Převeďte hodnotu na <xref:System.DateTime> její <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> řetězcovou reprezentaci voláním metody s specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="54158-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="54158-107">Uložte řetězcovou <xref:System.DateTime> reprezentaci hodnoty do souboru nebo ji předajte přes hranice procesu, domény aplikace nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="54158-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="54158-108">Načtěte řetězec, <xref:System.DateTime> který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="54158-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="54158-109">Volání <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody a <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> předat jako hodnotu parametru. `styles`</span><span class="sxs-lookup"><span data-stu-id="54158-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="54158-110">Následující příklad ukazuje, jak round-trip hodnotu. <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="54158-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="54158-111">Při zaoblení <xref:System.DateTime> hodnoty tato technika úspěšně zachová čas pro všechny místní a univerzální časy.</span><span class="sxs-lookup"><span data-stu-id="54158-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="54158-112">Pokud je například <xref:System.DateTime> místní hodnota uložena v systému v americkém tichomořském standardním časovém pásmu a obnovena v systému v centrálním časovém pásmu USA, bude obnovené datum a čas o dvě hodiny později než původní čas, což odráží časový rozdíl mezi oběma časovými pásmy.</span><span class="sxs-lookup"><span data-stu-id="54158-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="54158-113">Tato technika však nemusí být nutně přesná pro nespecifikované časy.</span><span class="sxs-lookup"><span data-stu-id="54158-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="54158-114">Všechny <xref:System.DateTime> hodnoty, <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified> jejichž vlastnost je považována za místní časy.</span><span class="sxs-lookup"><span data-stu-id="54158-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="54158-115">Pokud tomu tak není, <xref:System.DateTime> nebude úspěšně identifikovat správný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="54158-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="54158-116">Řešení pro toto omezení je pevně spárovat hodnotu data a času s jeho časové pásmo pro uložení a obnovení operace.</span><span class="sxs-lookup"><span data-stu-id="54158-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="54158-117">Chcete-li round-trip DateTimeOffset hodnotu</span><span class="sxs-lookup"><span data-stu-id="54158-117">To round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="54158-118">Převeďte hodnotu na <xref:System.DateTimeOffset> její <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> řetězcovou reprezentaci voláním metody s specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="54158-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="54158-119">Uložte řetězcovou <xref:System.DateTimeOffset> reprezentaci hodnoty do souboru nebo ji předajte přes hranice procesu, domény aplikace nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="54158-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="54158-120">Načtěte řetězec, <xref:System.DateTimeOffset> který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="54158-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="54158-121">Volání <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody a <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> předat jako hodnotu parametru. `styles`</span><span class="sxs-lookup"><span data-stu-id="54158-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="54158-122">Následující příklad ukazuje, jak round-trip hodnotu. <xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="54158-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="54158-123">Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jeden bod v čase.</span><span class="sxs-lookup"><span data-stu-id="54158-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="54158-124">Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody, nebo ji lze převést <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> na čas v určitém časovém pásmu voláním metody nebo.</span><span class="sxs-lookup"><span data-stu-id="54158-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="54158-125">Hlavní omezení této techniky je, že aritmetika data <xref:System.DateTimeOffset> a času, při provádění na hodnotu, která představuje čas v určitém časovém pásmu, nemusí vést k přesným výsledkům pro toto časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="54158-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="54158-126">Důvodem je, <xref:System.DateTimeOffset> že při vytvoření instance hodnoty je odpojena od svého časového pásma.</span><span class="sxs-lookup"><span data-stu-id="54158-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="54158-127">Proto pravidla úprav tohoto časového pásma již nelze použít při provádění výpočtů data a času.</span><span class="sxs-lookup"><span data-stu-id="54158-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="54158-128">Tento problém můžete vyřešit definováním vlastního typu, který obsahuje hodnotu data a času a doprovodné časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="54158-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="54158-129">Round-trip datum a čas hodnota s jeho časové pásmo</span><span class="sxs-lookup"><span data-stu-id="54158-129">To round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="54158-130">Definujte třídu nebo strukturu se dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="54158-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="54158-131">První pole je <xref:System.DateTime> buď <xref:System.DateTimeOffset> nebo objekt a druhý <xref:System.TimeZoneInfo> je objekt.</span><span class="sxs-lookup"><span data-stu-id="54158-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="54158-132">Následující příklad je jednoduchá verze takového typu.</span><span class="sxs-lookup"><span data-stu-id="54158-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="54158-133">Označte třídu atributem. <xref:System.SerializableAttribute></span><span class="sxs-lookup"><span data-stu-id="54158-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="54158-134">Serialize objektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="54158-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="54158-135">Obnovte objekt <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="54158-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="54158-136">Přetypovat (v jazyce C#) nebo převést (v jazyce Visual Basic) rekonstruovaný objekt na objekt příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="54158-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="54158-137">Následující příklad ukazuje, jak round-trip objekt, který ukládá informace o datu a čase a časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="54158-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="54158-138">Tato technika by měla vždy jednoznačně odrážet správný časový bod před uložením a obnovením i po něm za předpokladu, že implementace kombinovaného objektu data a času a časového pásma neumožňuje, aby se hodnota data nesynchronizovala s objektem hodnota časového pásma.</span><span class="sxs-lookup"><span data-stu-id="54158-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="54158-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="54158-139">Compiling the Code</span></span>

<span data-ttu-id="54158-140">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="54158-140">These examples require:</span></span>

- <span data-ttu-id="54158-141">Že následující obory názvů lze `using` importovat s `Imports` příkazy Jazyka C# nebo příkazy jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="54158-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="54158-142"><xref:System>(pouze C#).</span><span class="sxs-lookup"><span data-stu-id="54158-142"><xref:System> (C# only).</span></span>

  - <span data-ttu-id="54158-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54158-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="54158-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54158-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="54158-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54158-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="54158-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54158-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="54158-147">Každý příklad kódu, `DateInTimeZone` jiný než třída, by měl být zahrnut do třídy nebo `Main` modulu visual basic, zabalený v metodách a volán z metody.</span><span class="sxs-lookup"><span data-stu-id="54158-147">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="54158-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="54158-148">See also</span></span>

- [<span data-ttu-id="54158-149">Provádění operací formátování</span><span class="sxs-lookup"><span data-stu-id="54158-149">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
- [<span data-ttu-id="54158-150">Volba Mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="54158-150">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="54158-151">Standardní řetězce formátu data a času</span><span class="sxs-lookup"><span data-stu-id="54158-151">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
