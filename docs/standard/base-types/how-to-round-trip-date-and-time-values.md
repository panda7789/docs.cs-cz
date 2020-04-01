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
ms.openlocfilehash: 4fc38b6b852f8a7b8f268fd9e8624bdf350744c8
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523822"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Postupy: Hodnoty data a doby odezvy

V mnoha aplikacích je hodnota data a času určena k jednoznačné identifikaci jednoho bodu v čase. Toto téma ukazuje, jak <xref:System.DateTime> uložit <xref:System.DateTimeOffset> a obnovit hodnotu, hodnotu a hodnotu data a času s informacemi o časovém pásmu tak, aby obnovená hodnota identifikovala stejný čas jako uložená hodnota.

## <a name="round-trip-a-datetime-value"></a>Round-trip datetime hodnota

1. Převeďte hodnotu na <xref:System.DateTime> její <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> řetězcovou reprezentaci voláním metody s specifikátorem formátu "o".

2. Uložte řetězcovou <xref:System.DateTime> reprezentaci hodnoty do souboru nebo ji předajte přes hranice procesu, domény aplikace nebo počítače.

3. Načtěte řetězec, <xref:System.DateTime> který představuje hodnotu.

4. Volání <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody a <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> předat jako hodnotu parametru. `styles`

Následující příklad ukazuje, jak round-trip hodnotu. <xref:System.DateTime>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Při zaoblení <xref:System.DateTime> hodnoty tato technika úspěšně zachová čas pro všechny místní a univerzální časy. Pokud je například <xref:System.DateTime> místní hodnota uložena v systému v americkém tichomořském standardním časovém pásmu a obnovena v systému v centrálním časovém pásmu USA, bude obnovené datum a čas o dvě hodiny později než původní čas, což odráží časový rozdíl mezi oběma časovými pásmy. Tato technika však nemusí být nutně přesná pro nespecifikované časy. Všechny <xref:System.DateTime> hodnoty, <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified> jejichž vlastnost je považována za místní časy. Pokud tomu tak není, <xref:System.DateTime> nebude úspěšně identifikovat správný bod v čase. Řešení pro toto omezení je pevně spárovat hodnotu data a času s jeho časové pásmo pro uložení a obnovení operace.

## <a name="round-trip-a-datetimeoffset-value"></a>Round-trip a DateTimeOffset hodnota

1. Převeďte hodnotu na <xref:System.DateTimeOffset> její <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> řetězcovou reprezentaci voláním metody s specifikátorem formátu "o".

2. Uložte řetězcovou <xref:System.DateTimeOffset> reprezentaci hodnoty do souboru nebo ji předajte přes hranice procesu, domény aplikace nebo počítače.

3. Načtěte řetězec, <xref:System.DateTimeOffset> který představuje hodnotu.

4. Volání <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody a <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> předat jako hodnotu parametru. `styles`

Následující příklad ukazuje, jak round-trip hodnotu. <xref:System.DateTimeOffset>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jeden bod v čase. Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody, nebo ji lze převést <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> na čas v určitém časovém pásmu voláním metody nebo. Hlavní omezení této techniky je, že aritmetika data <xref:System.DateTimeOffset> a času, při provádění na hodnotu, která představuje čas v určitém časovém pásmu, nemusí vést k přesným výsledkům pro toto časové pásmo. Důvodem je, <xref:System.DateTimeOffset> že při vytvoření instance hodnoty je odpojena od svého časového pásma. Proto pravidla úprav tohoto časového pásma již nelze použít při provádění výpočtů data a času. Tento problém můžete vyřešit definováním vlastního typu, který obsahuje hodnotu data a času a doprovodné časové pásmo.

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a>Round-trip datum a čas hodnota s jeho časové pásmo

1. Definujte třídu nebo strukturu se dvěma poli. První pole je <xref:System.DateTime> buď <xref:System.DateTimeOffset> nebo objekt a druhý <xref:System.TimeZoneInfo> je objekt. Následující příklad je jednoduchá verze takového typu.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Označte třídu atributem. <xref:System.SerializableAttribute>

3. Serialize objektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> pomocí metody.

4. Obnovte objekt <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> pomocí metody.

5. Přetypovat (v jazyce C#) nebo převést (v jazyce Visual Basic) rekonstruovaný objekt na objekt příslušného typu.

Následující příklad ukazuje, jak round-trip objekt, který ukládá informace o datu a čase a časové pásmo.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Tato technika by měla vždy jednoznačně odrážet správný časový bod před a po uložení a obnovení za předpokladu, že implementace kombinovaného objektu data a času a časového pásma neumožňuje, aby se hodnota data nesynchronizovala s hodnotou časového pásma.

## <a name="compile-the-code"></a>Kompilace kódu

Tyto příklady vyžadují, aby:

- Následující obory názvů lze importovat pomocí direktiv jazyka C# `using` nebo příkazů jazyka Visual Basic: `Imports`

  - <xref:System>(pouze C#)

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- Každý příklad kódu, `DateInTimeZone` jiný než třída, být zahrnuty do třídy nebo modulu `Main` Visual Basic, zabalené v metodách a volány z metody.

## <a name="see-also"></a>Viz také

- [Volba Mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
