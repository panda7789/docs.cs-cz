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
ms.openlocfilehash: 3aa615dc7d7d1d49dce4897f8508b5210b364fc0
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635140"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="a006b-102">Postupy: Hodnoty data a doby odezvy</span><span class="sxs-lookup"><span data-stu-id="a006b-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="a006b-103">V mnoha aplikacích je hodnota data a času určena k jednoznačné identifikaci jednoho bodu v čase.</span><span class="sxs-lookup"><span data-stu-id="a006b-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="a006b-104">Tento článek ukazuje, jak <xref:System.DateTime> uložit a <xref:System.DateTimeOffset> obnovit hodnotu, hodnotu a hodnotu data a času s informacemi o časovém pásmu tak, aby obnovená hodnota identifikovala stejný čas jako uložená hodnota.</span><span class="sxs-lookup"><span data-stu-id="a006b-104">This article shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="a006b-105">Round-trip datetime hodnota</span><span class="sxs-lookup"><span data-stu-id="a006b-105">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="a006b-106">Převeďte hodnotu na <xref:System.DateTime> její <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> řetězcovou reprezentaci voláním metody s specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="a006b-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="a006b-107">Uložte řetězcovou <xref:System.DateTime> reprezentaci hodnoty do souboru nebo ji předajte přes hranice procesu, domény aplikace nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="a006b-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="a006b-108">Načtěte řetězec, <xref:System.DateTime> který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a006b-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="a006b-109">Volání <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody a <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> předat jako hodnotu parametru. `styles`</span><span class="sxs-lookup"><span data-stu-id="a006b-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="a006b-110">Následující příklad ukazuje, jak round-trip hodnotu. <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="a006b-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="a006b-111">Při zaoblení <xref:System.DateTime> hodnoty tato technika úspěšně zachová čas pro všechny místní a univerzální časy.</span><span class="sxs-lookup"><span data-stu-id="a006b-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="a006b-112">Pokud je například <xref:System.DateTime> místní hodnota uložena v systému v americkém tichomořském standardním časovém pásmu a obnovena v systému v centrálním časovém pásmu USA, bude obnovené datum a čas o dvě hodiny později než původní čas, což odráží časový rozdíl mezi oběma časovými pásmy.</span><span class="sxs-lookup"><span data-stu-id="a006b-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="a006b-113">Tato technika však nemusí být nutně přesná pro nespecifikované časy.</span><span class="sxs-lookup"><span data-stu-id="a006b-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="a006b-114">Všechny <xref:System.DateTime> hodnoty, <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified> jejichž vlastnost je považována za místní časy.</span><span class="sxs-lookup"><span data-stu-id="a006b-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="a006b-115">Pokud to není místní čas, <xref:System.DateTime> není úspěšně identifikovat správný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="a006b-115">If it's not a local time, the <xref:System.DateTime> doesn't successfully identify the correct point in time.</span></span> <span data-ttu-id="a006b-116">Řešení pro toto omezení je pevně spárovat hodnotu data a času s jeho časové pásmo pro uložení a obnovení operace.</span><span class="sxs-lookup"><span data-stu-id="a006b-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="a006b-117">Round-trip a DateTimeOffset hodnota</span><span class="sxs-lookup"><span data-stu-id="a006b-117">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="a006b-118">Převeďte hodnotu na <xref:System.DateTimeOffset> její <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> řetězcovou reprezentaci voláním metody s specifikátorem formátu "o".</span><span class="sxs-lookup"><span data-stu-id="a006b-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="a006b-119">Uložte řetězcovou <xref:System.DateTimeOffset> reprezentaci hodnoty do souboru nebo ji předajte přes hranice procesu, domény aplikace nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="a006b-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="a006b-120">Načtěte řetězec, <xref:System.DateTimeOffset> který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a006b-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="a006b-121">Volání <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody a <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> předat jako hodnotu parametru. `styles`</span><span class="sxs-lookup"><span data-stu-id="a006b-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="a006b-122">Následující příklad ukazuje, jak round-trip hodnotu. <xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="a006b-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="a006b-123">Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jeden bod v čase.</span><span class="sxs-lookup"><span data-stu-id="a006b-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="a006b-124">Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody, nebo ji lze převést <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> na čas v určitém časovém pásmu voláním metody nebo.</span><span class="sxs-lookup"><span data-stu-id="a006b-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a006b-125">Hlavní omezení této techniky je, že aritmetika data <xref:System.DateTimeOffset> a času, při provádění na hodnotu, která představuje čas v určitém časovém pásmu, nemusí vést k přesným výsledkům pro toto časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="a006b-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="a006b-126">Důvodem je, <xref:System.DateTimeOffset> že při vytvoření instance hodnoty je odpojena od svého časového pásma.</span><span class="sxs-lookup"><span data-stu-id="a006b-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="a006b-127">Proto pravidla úprav tohoto časového pásma již nelze použít při provádění výpočtů data a času.</span><span class="sxs-lookup"><span data-stu-id="a006b-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="a006b-128">Tento problém můžete vyřešit definováním vlastního typu, který obsahuje hodnotu data a času a doprovodné časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="a006b-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="a006b-129">Round-trip datum a čas hodnota s jeho časové pásmo</span><span class="sxs-lookup"><span data-stu-id="a006b-129">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="a006b-130">Definujte třídu nebo strukturu se dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="a006b-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="a006b-131">První pole je <xref:System.DateTime> buď <xref:System.DateTimeOffset> nebo objekt a druhý <xref:System.TimeZoneInfo> je objekt.</span><span class="sxs-lookup"><span data-stu-id="a006b-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="a006b-132">Následující příklad je jednoduchá verze takového typu.</span><span class="sxs-lookup"><span data-stu-id="a006b-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="a006b-133">Označte třídu atributem. <xref:System.SerializableAttribute></span><span class="sxs-lookup"><span data-stu-id="a006b-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="a006b-134">Serialize objektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="a006b-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="a006b-135">Obnovte objekt <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="a006b-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="a006b-136">Přetypovat (v jazyce C#) nebo převést (v jazyce Visual Basic) rekonstruovaný objekt na objekt příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="a006b-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="a006b-137">Následující příklad ukazuje, jak round-trip objekt, který ukládá časové pásmo a datum a čas informace.</span><span class="sxs-lookup"><span data-stu-id="a006b-137">The following example illustrates how to round-trip an object that stores both time zone and date and time information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="a006b-138">Tato technika by měla vždy jednoznačně odrážet správný časový bod před a po uložení a obnovení za předpokladu, že implementace kombinovaného objektu data a času a časového pásma neumožňuje, aby se hodnota data nesynchronizovala s hodnotou časového pásma.</span><span class="sxs-lookup"><span data-stu-id="a006b-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="a006b-139">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a006b-139">Compile the code</span></span>

<span data-ttu-id="a006b-140">Tyto příklady vyžadují, aby:</span><span class="sxs-lookup"><span data-stu-id="a006b-140">These examples require that:</span></span>

- <span data-ttu-id="a006b-141">Následující obory názvů lze importovat pomocí direktiv jazyka C# `using` nebo příkazů jazyka Visual Basic: `Imports`</span><span class="sxs-lookup"><span data-stu-id="a006b-141">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="a006b-142"><xref:System>(pouze C#)</span><span class="sxs-lookup"><span data-stu-id="a006b-142"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="a006b-143">Každý příklad kódu, `DateInTimeZone` jiný než třída, být zahrnuty do třídy nebo modulu `Main` Visual Basic, zabalené v metodách a volány z metody.</span><span class="sxs-lookup"><span data-stu-id="a006b-143">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="a006b-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="a006b-144">See also</span></span>

- [<span data-ttu-id="a006b-145">Volba Mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="a006b-145">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="a006b-146">Standardní řetězce formátu data a času</span><span class="sxs-lookup"><span data-stu-id="a006b-146">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
