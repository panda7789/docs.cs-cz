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
# <a name="how-to-round-trip-date-and-time-values"></a>Postupy: Hodnoty data a doby odezvy

V mnoha aplikacích je hodnota data a času určena k jednoznačné identifikaci určitého bodu v čase. Tento článek ukazuje, jak uložit a obnovit <xref:System.DateTime> hodnotu, <xref:System.DateTimeOffset> hodnotu a hodnotu data a času s informacemi o časovém pásmu tak, aby obnovená hodnota označovala stejnou dobu jako uložená hodnota.

## <a name="round-trip-a-datetime-value"></a>Operace round-trip pro hodnotu DateTime

1. Převeďte <xref:System.DateTime> hodnotu na její řetězcovou reprezentaci voláním <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody se specifikátorem formátu "o".

2. Uložte řetězcovou reprezentaci <xref:System.DateTime> hodnoty do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.

3. Načte řetězec, který představuje <xref:System.DateTime> hodnotu.

4. Zavolejte <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodu a předejte ji <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametru.

Následující příklad ukazuje, jak pomocí operace Round-Trip <xref:System.DateTime> hodnotu.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Při zaokrouhlení Trip <xref:System.DateTime> hodnoty Tato technika úspěšně zachovává čas pro všechny místní a univerzální časy. Pokud je například místní <xref:System.DateTime> hodnota uložena v systému v oblasti USA (běžný čas) a je obnovena v systému v centrálním časovém pásmu USA – střed, obnovené datum a čas budou dvě hodiny později než původní čas, což odráží časový rozdíl mezi těmito dvěma časovými pásmy. Tato technika ale není nutně přesná pro nespecifikovanou dobu. Všechny <xref:System.DateTime> hodnoty, jejichž <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified> považována za místní časy. Pokud se nejedná o místní čas, <xref:System.DateTime> nerozpozná úspěšně správný bod v čase. Alternativním řešením pro toto omezení je, že je hodnota data a času pevně spojená s časovým pásmem pro operaci uložení a obnovení.

## <a name="round-trip-a-datetimeoffset-value"></a>Operace round-trip pro hodnotu DateTimeOffset

1. Převeďte <xref:System.DateTimeOffset> hodnotu na její řetězcovou reprezentaci voláním <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody se specifikátorem formátu "o".

2. Uložte řetězcovou reprezentaci <xref:System.DateTimeOffset> hodnoty do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.

3. Načte řetězec, který představuje <xref:System.DateTimeOffset> hodnotu.

4. Zavolejte <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodu a předejte ji <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametru.

Následující příklad ukazuje, jak pomocí operace Round-Trip <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jediný bod v čase. Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody, nebo může být převedena na čas v konkrétním časovém pásmu voláním <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody nebo. Hlavními omezeními této techniky je, že aritmetické operace s hodnotami data a času, <xref:System.DateTimeOffset> které reprezentují čas v konkrétním časovém pásmu, nemusí pro toto časové pásmo poskytovat přesné výsledky. To je způsobeno tím <xref:System.DateTimeOffset> , že při vytvoření instance dojde k jejich přidružení od svého časového pásma. Proto pravidla úprav tohoto časového pásma již nelze použít při výpočtu data a času. Tento problém můžete obejít tak, že definujete vlastní typ, který obsahuje hodnotu data a času a jeho doprovodné časové pásmo.

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a>Přenos hodnoty data a času pomocí časového pásma

1. Definujte třídu nebo strukturu se dvěma poli. První pole je buď <xref:System.DateTime> <xref:System.DateTimeOffset> objekt, nebo objekt a druhým je <xref:System.TimeZoneInfo> objekt. Následující příklad je jednoduchá verze takového typu.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Označte třídu <xref:System.SerializableAttribute> atributem.

3. Serializovat objekt pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.

4. Obnovte objekt pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.

5. Přetypování (v jazyce C#) nebo převést (v Visual Basic) deserializovaný objekt na objekt příslušného typu.

Následující příklad ukazuje, jak operaci round-trip pro objekt, který ukládá časové pásmo i informace o datu a času.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Tato technika by měla vždy jednoznačně odrážet správný bod před i po uložení a obnovení, za předpokladu, že implementace kombinovaného objektu data a času a časového pásma nepovoluje, aby byla hodnota data nesynchronizovaná s hodnotou časového pásma.

## <a name="compile-the-code"></a>Kompilovat kód

Tyto příklady vyžadují:

- Následující obory názvů se importují pomocí `using` direktiv jazyka C# nebo `Imports` příkazů Visual Basic:

  - <xref:System>(Pouze C#)

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- Každý příklad kódu, kromě `DateInTimeZone` třídy, je součástí třídy nebo Visual Basic modulu, zabalen do metod a volán z `Main` metody.

## <a name="see-also"></a>Viz také

- [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../datetime/choosing-between-datetime.md)
- [Řetězce standardního formátu data a času](standard-date-and-time-format-strings.md)
