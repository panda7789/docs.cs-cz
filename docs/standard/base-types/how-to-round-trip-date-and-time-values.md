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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132009"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="ecec4-102">Postupy: Hodnoty data a času round-trip</span><span class="sxs-lookup"><span data-stu-id="ecec4-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="ecec4-103">V mnoha aplikacích je hodnota data a času určena k jednoznačné identifikaci určitého bodu v čase.</span><span class="sxs-lookup"><span data-stu-id="ecec4-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="ecec4-104">V tomto tématu se dozvíte, jak uložit a obnovit <xref:System.DateTime> hodnotu, hodnotu <xref:System.DateTimeOffset> a hodnotu data a času s informacemi o časovém pásmu tak, aby obnovená hodnota označovala stejnou dobu jako uložená hodnota.</span><span class="sxs-lookup"><span data-stu-id="ecec4-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="ecec4-105">Postup při přenosu hodnoty DateTime</span><span class="sxs-lookup"><span data-stu-id="ecec4-105">To round-trip a DateTime value</span></span>

1. <span data-ttu-id="ecec4-106">Převeďte hodnotu <xref:System.DateTime> na její řetězcové vyjádření voláním metody <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> se specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="ecec4-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="ecec4-107">Uložte řetězcovou reprezentaci hodnoty <xref:System.DateTime> do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.</span><span class="sxs-lookup"><span data-stu-id="ecec4-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="ecec4-108">Načte řetězec, který představuje hodnotu <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="ecec4-109">Zavolejte metodu <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> a předejte <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu parametru `styles`.</span><span class="sxs-lookup"><span data-stu-id="ecec4-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="ecec4-110">Následující příklad ukazuje, jak se má odcyklovat <xref:System.DateTime> hodnota.</span><span class="sxs-lookup"><span data-stu-id="ecec4-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="ecec4-111">Když se zaokrouhlí Trip hodnota <xref:System.DateTime>, tato technika úspěšně zachovává čas pro všechny místní a univerzální časy.</span><span class="sxs-lookup"><span data-stu-id="ecec4-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="ecec4-112">Pokud je například hodnota místního <xref:System.DateTime> uložena v systému v oblasti USA (běžný tichomořské čas) a je obnovena v systému v centrálním časovém pásmu USA – střed, obnovené datum a čas budou dvě hodiny později než původní čas. , který odráží časový rozdíl mezi dvěma časovými pásmy.</span><span class="sxs-lookup"><span data-stu-id="ecec4-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="ecec4-113">Tato technika ale není nutně přesná pro nespecifikovanou dobu.</span><span class="sxs-lookup"><span data-stu-id="ecec4-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="ecec4-114">Všechny hodnoty <xref:System.DateTime>, jejichž vlastnost <xref:System.DateTime.Kind%2A> je <xref:System.DateTimeKind.Unspecified>, se považují za místní časy.</span><span class="sxs-lookup"><span data-stu-id="ecec4-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="ecec4-115">Pokud se nejedná o tento případ, <xref:System.DateTime> nebude správně identifikovat správný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="ecec4-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="ecec4-116">Alternativním řešením pro toto omezení je, že je hodnota data a času pevně spojená s časovým pásmem pro operaci uložení a obnovení.</span><span class="sxs-lookup"><span data-stu-id="ecec4-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="ecec4-117">Postup při operaci round-trip pro hodnotu DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ecec4-117">To round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="ecec4-118">Převeďte hodnotu <xref:System.DateTimeOffset> na její řetězcové vyjádření voláním metody <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> se specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="ecec4-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="ecec4-119">Uložte řetězcovou reprezentaci hodnoty <xref:System.DateTimeOffset> do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.</span><span class="sxs-lookup"><span data-stu-id="ecec4-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="ecec4-120">Načte řetězec, který představuje hodnotu <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="ecec4-121">Zavolejte metodu <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> a předejte <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu parametru `styles`.</span><span class="sxs-lookup"><span data-stu-id="ecec4-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="ecec4-122">Následující příklad ukazuje, jak se má odcyklovat <xref:System.DateTimeOffset> hodnota.</span><span class="sxs-lookup"><span data-stu-id="ecec4-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="ecec4-123">Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="ecec4-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="ecec4-124">Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním metody <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>, nebo může být převedena na čas v konkrétním časovém pásmu voláním metody <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> nebo <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ecec4-125">Hlavními omezeními této techniky je, že aritmetické operace s hodnotami data a času, pokud se provádí na <xref:System.DateTimeOffset> hodnotě, která představuje čas v konkrétním časovém pásmu, nemusí pro toto časové pásmo poskytovat přesné výsledky.</span><span class="sxs-lookup"><span data-stu-id="ecec4-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="ecec4-126">Důvodem je to, že když se vytvoří instance <xref:System.DateTimeOffset>, odčlení se jeho časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="ecec4-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="ecec4-127">Proto pravidla úprav tohoto časového pásma již nelze použít při výpočtu data a času.</span><span class="sxs-lookup"><span data-stu-id="ecec4-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="ecec4-128">Tento problém můžete obejít tak, že definujete vlastní typ, který obsahuje hodnotu data a času a jeho doprovodné časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="ecec4-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="ecec4-129">Postup při přenosu hodnoty data a času v časovém pásmu</span><span class="sxs-lookup"><span data-stu-id="ecec4-129">To round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="ecec4-130">Definujte třídu nebo strukturu se dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="ecec4-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="ecec4-131">První pole je buď <xref:System.DateTime>, nebo objekt <xref:System.DateTimeOffset> a druhý je objekt <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="ecec4-132">Následující příklad je jednoduchá verze takového typu.</span><span class="sxs-lookup"><span data-stu-id="ecec4-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="ecec4-133">Označte třídu atributem <xref:System.SerializableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="ecec4-134">Serializovat objekt pomocí metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="ecec4-135">Obnovte objekt pomocí metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="ecec4-136">Přetypování ( C#in) nebo převést (v Visual Basic) deserializovaný objekt na objekt příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="ecec4-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="ecec4-137">Následující příklad ukazuje, jak operaci round-trip pro objekt, který ukládá informace o datu a čase i informace o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="ecec4-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="ecec4-138">Tato technika by měla vždy jednoznačně odrážet správný bod před i po uložení a obnovení, za předpokladu, že implementace kombinovaného objektu data a času a časového pásma neumožňuje, aby hodnota data nebyla synchronizovaná s hodnota časového pásma.</span><span class="sxs-lookup"><span data-stu-id="ecec4-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ecec4-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ecec4-139">Compiling the Code</span></span>

<span data-ttu-id="ecec4-140">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="ecec4-140">These examples require:</span></span>

- <span data-ttu-id="ecec4-141">Následující obory názvů se importují s C# příkazy `using` nebo Visual Basic `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="ecec4-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="ecec4-142"><xref:System> (C# pouze).</span><span class="sxs-lookup"><span data-stu-id="ecec4-142"><xref:System> (C# only).</span></span>

  - <span data-ttu-id="ecec4-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="ecec4-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="ecec4-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="ecec4-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ecec4-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="ecec4-147">Každý příklad kódu, kromě `DateInTimeZone` třídy, by měl být součástí třídy nebo Visual Basic modulu, zabalen do metod a volán z metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="ecec4-147">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecec4-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecec4-148">See also</span></span>

- [<span data-ttu-id="ecec4-149">Provádění operací formátování</span><span class="sxs-lookup"><span data-stu-id="ecec4-149">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
- [<span data-ttu-id="ecec4-150">Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="ecec4-150">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="ecec4-151">Standardní řetězce formátu data a času</span><span class="sxs-lookup"><span data-stu-id="ecec4-151">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
