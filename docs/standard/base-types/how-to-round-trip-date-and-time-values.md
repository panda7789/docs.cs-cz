---
title: 'Postupy: Hodnoty data a doby odezvy'
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
ms.openlocfilehash: 60483a6e29c65fc0c5803e8084053d53d9fc3c37
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290445"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="e91fb-102">Postupy: Hodnoty data a doby odezvy</span><span class="sxs-lookup"><span data-stu-id="e91fb-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="e91fb-103">V mnoha aplikacích je hodnota data a času určena k jednoznačné identifikaci určitého bodu v čase.</span><span class="sxs-lookup"><span data-stu-id="e91fb-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="e91fb-104">Tento článek ukazuje, jak uložit a obnovit <xref:System.DateTime> hodnotu, <xref:System.DateTimeOffset> hodnotu a hodnotu data a času s informacemi o časovém pásmu tak, aby obnovená hodnota označovala stejnou dobu jako uložená hodnota.</span><span class="sxs-lookup"><span data-stu-id="e91fb-104">This article shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="e91fb-105">Operace round-trip pro hodnotu DateTime</span><span class="sxs-lookup"><span data-stu-id="e91fb-105">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="e91fb-106">Převeďte <xref:System.DateTime> hodnotu na její řetězcovou reprezentaci voláním <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody se specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="e91fb-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="e91fb-107">Uložte řetězcovou reprezentaci <xref:System.DateTime> hodnoty do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.</span><span class="sxs-lookup"><span data-stu-id="e91fb-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="e91fb-108">Načte řetězec, který představuje <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e91fb-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="e91fb-109">Zavolejte <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodu a předejte ji <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="e91fb-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="e91fb-110">Následující příklad ukazuje, jak pomocí operace Round-Trip <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e91fb-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="e91fb-111">Při zaokrouhlení Trip <xref:System.DateTime> hodnoty Tato technika úspěšně zachovává čas pro všechny místní a univerzální časy.</span><span class="sxs-lookup"><span data-stu-id="e91fb-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="e91fb-112">Pokud je například místní <xref:System.DateTime> hodnota uložena v systému v oblasti USA (běžný čas) a je obnovena v systému v centrálním časovém pásmu USA – střed, obnovené datum a čas budou dvě hodiny později než původní čas, což odráží časový rozdíl mezi těmito dvěma časovými pásmy.</span><span class="sxs-lookup"><span data-stu-id="e91fb-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="e91fb-113">Tato technika ale není nutně přesná pro nespecifikovanou dobu.</span><span class="sxs-lookup"><span data-stu-id="e91fb-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="e91fb-114">Všechny <xref:System.DateTime> hodnoty, jejichž <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified> považována za místní časy.</span><span class="sxs-lookup"><span data-stu-id="e91fb-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="e91fb-115">Pokud se nejedná o místní čas, <xref:System.DateTime> nerozpozná úspěšně správný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="e91fb-115">If it's not a local time, the <xref:System.DateTime> doesn't successfully identify the correct point in time.</span></span> <span data-ttu-id="e91fb-116">Alternativním řešením pro toto omezení je, že je hodnota data a času pevně spojená s časovým pásmem pro operaci uložení a obnovení.</span><span class="sxs-lookup"><span data-stu-id="e91fb-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="e91fb-117">Operace round-trip pro hodnotu DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e91fb-117">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="e91fb-118">Převeďte <xref:System.DateTimeOffset> hodnotu na její řetězcovou reprezentaci voláním <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody se specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="e91fb-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="e91fb-119">Uložte řetězcovou reprezentaci <xref:System.DateTimeOffset> hodnoty do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.</span><span class="sxs-lookup"><span data-stu-id="e91fb-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="e91fb-120">Načte řetězec, který představuje <xref:System.DateTimeOffset> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e91fb-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="e91fb-121">Zavolejte <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodu a předejte ji <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="e91fb-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="e91fb-122">Následující příklad ukazuje, jak pomocí operace Round-Trip <xref:System.DateTimeOffset> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e91fb-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="e91fb-123">Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="e91fb-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="e91fb-124">Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody, nebo může být převedena na čas v konkrétním časovém pásmu voláním <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody nebo.</span><span class="sxs-lookup"><span data-stu-id="e91fb-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e91fb-125">Hlavními omezeními této techniky je, že aritmetické operace s hodnotami data a času, <xref:System.DateTimeOffset> které reprezentují čas v konkrétním časovém pásmu, nemusí pro toto časové pásmo poskytovat přesné výsledky.</span><span class="sxs-lookup"><span data-stu-id="e91fb-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="e91fb-126">To je způsobeno tím <xref:System.DateTimeOffset> , že při vytvoření instance dojde k jejich přidružení od svého časového pásma.</span><span class="sxs-lookup"><span data-stu-id="e91fb-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="e91fb-127">Proto pravidla úprav tohoto časového pásma již nelze použít při výpočtu data a času.</span><span class="sxs-lookup"><span data-stu-id="e91fb-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="e91fb-128">Tento problém můžete obejít tak, že definujete vlastní typ, který obsahuje hodnotu data a času a jeho doprovodné časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="e91fb-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="e91fb-129">Přenos hodnoty data a času pomocí časového pásma</span><span class="sxs-lookup"><span data-stu-id="e91fb-129">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="e91fb-130">Definujte třídu nebo strukturu se dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="e91fb-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="e91fb-131">První pole je buď <xref:System.DateTime> <xref:System.DateTimeOffset> objekt, nebo objekt a druhým je <xref:System.TimeZoneInfo> objekt.</span><span class="sxs-lookup"><span data-stu-id="e91fb-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="e91fb-132">Následující příklad je jednoduchá verze takového typu.</span><span class="sxs-lookup"><span data-stu-id="e91fb-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="e91fb-133">Označte třídu <xref:System.SerializableAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="e91fb-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="e91fb-134">Serializovat objekt pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e91fb-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="e91fb-135">Obnovte objekt pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e91fb-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="e91fb-136">Přetypování (v jazyce C#) nebo převést (v Visual Basic) deserializovaný objekt na objekt příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="e91fb-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="e91fb-137">Následující příklad ukazuje, jak operaci round-trip pro objekt, který ukládá časové pásmo i informace o datu a času.</span><span class="sxs-lookup"><span data-stu-id="e91fb-137">The following example illustrates how to round-trip an object that stores both time zone and date and time information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="e91fb-138">Tato technika by měla vždy jednoznačně odrážet správný bod před i po uložení a obnovení, za předpokladu, že implementace kombinovaného objektu data a času a časového pásma nepovoluje, aby byla hodnota data nesynchronizovaná s hodnotou časového pásma.</span><span class="sxs-lookup"><span data-stu-id="e91fb-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="e91fb-139">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="e91fb-139">Compile the code</span></span>

<span data-ttu-id="e91fb-140">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="e91fb-140">These examples require that:</span></span>

- <span data-ttu-id="e91fb-141">Následující obory názvů se importují pomocí `using` direktiv jazyka C# nebo `Imports` příkazů Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="e91fb-141">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="e91fb-142"><xref:System>(Pouze C#)</span><span class="sxs-lookup"><span data-stu-id="e91fb-142"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="e91fb-143">Každý příklad kódu, kromě `DateInTimeZone` třídy, je součástí třídy nebo Visual Basic modulu, zabalen do metod a volán z `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="e91fb-143">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="e91fb-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="e91fb-144">See also</span></span>

- [<span data-ttu-id="e91fb-145">Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="e91fb-145">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../datetime/choosing-between-datetime.md)
- [<span data-ttu-id="e91fb-146">Řetězce standardního formátu data a času</span><span class="sxs-lookup"><span data-stu-id="e91fb-146">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)
