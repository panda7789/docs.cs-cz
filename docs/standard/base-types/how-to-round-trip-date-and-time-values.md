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
# <a name="how-to-round-trip-date-and-time-values"></a>Postupy: Hodnoty data a času round-trip

V mnoha aplikacích je hodnota data a času určena k jednoznačné identifikaci určitého bodu v čase. V tomto tématu se dozvíte, jak uložit a obnovit <xref:System.DateTime> hodnotu, hodnotu <xref:System.DateTimeOffset> a hodnotu data a času s informacemi o časovém pásmu tak, aby obnovená hodnota označovala stejnou dobu jako uložená hodnota.

### <a name="to-round-trip-a-datetime-value"></a>Postup při přenosu hodnoty DateTime

1. Převeďte hodnotu <xref:System.DateTime> na její řetězcové vyjádření voláním metody <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> se specifikátorem formátu "o".

2. Uložte řetězcovou reprezentaci hodnoty <xref:System.DateTime> do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.

3. Načte řetězec, který představuje hodnotu <xref:System.DateTime>.

4. Zavolejte metodu <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> a předejte <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu parametru `styles`.

Následující příklad ukazuje, jak se má odcyklovat <xref:System.DateTime> hodnota.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Když se zaokrouhlí Trip hodnota <xref:System.DateTime>, tato technika úspěšně zachovává čas pro všechny místní a univerzální časy. Pokud je například hodnota místního <xref:System.DateTime> uložena v systému v oblasti USA (běžný tichomořské čas) a je obnovena v systému v centrálním časovém pásmu USA – střed, obnovené datum a čas budou dvě hodiny později než původní čas. , který odráží časový rozdíl mezi dvěma časovými pásmy. Tato technika ale není nutně přesná pro nespecifikovanou dobu. Všechny hodnoty <xref:System.DateTime>, jejichž vlastnost <xref:System.DateTime.Kind%2A> je <xref:System.DateTimeKind.Unspecified>, se považují za místní časy. Pokud se nejedná o tento případ, <xref:System.DateTime> nebude správně identifikovat správný bod v čase. Alternativním řešením pro toto omezení je, že je hodnota data a času pevně spojená s časovým pásmem pro operaci uložení a obnovení.

### <a name="to-round-trip-a-datetimeoffset-value"></a>Postup při operaci round-trip pro hodnotu DateTimeOffset

1. Převeďte hodnotu <xref:System.DateTimeOffset> na její řetězcové vyjádření voláním metody <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> se specifikátorem formátu "o".

2. Uložte řetězcovou reprezentaci hodnoty <xref:System.DateTimeOffset> do souboru nebo ji předejte v rámci procesu, domény aplikace nebo hranice počítače.

3. Načte řetězec, který představuje hodnotu <xref:System.DateTimeOffset>.

4. Zavolejte metodu <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> a předejte <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu parametru `styles`.

Následující příklad ukazuje, jak se má odcyklovat <xref:System.DateTimeOffset> hodnota.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jediný bod v čase. Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním metody <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>, nebo může být převedena na čas v konkrétním časovém pásmu voláním metody <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> nebo <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>. Hlavními omezeními této techniky je, že aritmetické operace s hodnotami data a času, pokud se provádí na <xref:System.DateTimeOffset> hodnotě, která představuje čas v konkrétním časovém pásmu, nemusí pro toto časové pásmo poskytovat přesné výsledky. Důvodem je to, že když se vytvoří instance <xref:System.DateTimeOffset>, odčlení se jeho časové pásmo. Proto pravidla úprav tohoto časového pásma již nelze použít při výpočtu data a času. Tento problém můžete obejít tak, že definujete vlastní typ, který obsahuje hodnotu data a času a jeho doprovodné časové pásmo.

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Postup při přenosu hodnoty data a času v časovém pásmu

1. Definujte třídu nebo strukturu se dvěma poli. První pole je buď <xref:System.DateTime>, nebo objekt <xref:System.DateTimeOffset> a druhý je objekt <xref:System.TimeZoneInfo>. Následující příklad je jednoduchá verze takového typu.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Označte třídu atributem <xref:System.SerializableAttribute>.

3. Serializovat objekt pomocí metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.

4. Obnovte objekt pomocí metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.

5. Přetypování ( C#in) nebo převést (v Visual Basic) deserializovaný objekt na objekt příslušného typu.

Následující příklad ukazuje, jak operaci round-trip pro objekt, který ukládá informace o datu a čase i informace o časovém pásmu.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Tato technika by měla vždy jednoznačně odrážet správný bod před i po uložení a obnovení, za předpokladu, že implementace kombinovaného objektu data a času a časového pásma neumožňuje, aby hodnota data nebyla synchronizovaná s hodnota časového pásma.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tyto příklady vyžadují:

- Následující obory názvů se importují s C# příkazy `using` nebo Visual Basic `Imports` příkazy:

  - <xref:System> (C# pouze).

  - <xref:System.Globalization?displayProperty=nameWithType>.

  - <xref:System.IO?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.

- Každý příklad kódu, kromě `DateInTimeZone` třídy, by měl být součástí třídy nebo Visual Basic modulu, zabalen do metod a volán z metody `Main`.

## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
