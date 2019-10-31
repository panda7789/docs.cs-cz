---
title: 'Postupy: Extrahování dne v týdnu z konkrétního data'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET Framework], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET Framework], day of week
- Weekday function
- day of week [.NET Framework]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET Framework], day of week
- formatting [.NET Framework], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
ms.openlocfilehash: 771bd0276310eecb534fb80836faadb1a8aa10bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084192"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Postupy: Extrahování dne v týdnu z konkrétního data
.NET Framework usnadňuje určení pořadového čísla dne v týdnu pro konkrétní datum a zobrazení lokalizovaného názvu dne v týdnu pro konkrétní datum. Hodnota výčtu, která určuje den v týdnu odpovídající konkrétnímu datu, je k dispozici z vlastnosti <xref:System.DateTime.DayOfWeek%2A> nebo <xref:System.DateTimeOffset.DayOfWeek%2A>. Naproti tomu, že načtení názvu dne v týdnu je operace formátování, kterou lze provést voláním metody formátování, jako je například metoda `ToString` hodnoty data a času nebo metoda <xref:System.String.Format%2A?displayProperty=nameWithType>. V tomto tématu se dozvíte, jak provést tyto operace formátování.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Extrakce čísla určujícího den v týdnu od konkrétního data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Vlastnost <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> můžete použít k načtení <xref:System.DayOfWeek> hodnoty, která označuje den v týdnu.  
  
3. V případě potřeby přetypování ( C#in) nebo převeďte (v Visual Basic) hodnotu <xref:System.DayOfWeek> na celé číslo.  
  
 Následující příklad zobrazuje celé číslo, které představuje den v týdnu určitého data.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Extrakce zkráceného názvu dne v týdnu z konkrétního data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat zkrácený název dne v týdnu aktuální jazykové verze nebo konkrétní jazykové verze:  
  
    1. Chcete-li extrahovat zkrácený název dne v týdnu pro aktuální jazykovou verzi, zavolejte metodu hodnoty data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance a předejte řetězec "ddd" jako parametr `format`. Následující příklad ilustruje volání metody <xref:System.DateTime.ToString%28System.String%29>.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Chcete-li extrahovat zkrácený název dne v týdnu pro konkrétní jazykovou verzi, zavolejte metodu hodnoty data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance. Předejte řetězec "ddd" jako parametr `format`. Předejte buď <xref:System.Globalization.CultureInfo>, nebo objekt <xref:System.Globalization.DateTimeFormatInfo>, který představuje jazykovou verzi, jejíž název dne v týdnu chcete načíst jako parametr `provider`. Následující kód ilustruje volání metody <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí objektu <xref:System.Globalization.CultureInfo>, který představuje jazykovou verzi fr-FR.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Extrakce úplného názvu dne v týdnu z konkrétního data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat úplný název dne v týdnu aktuální jazykové verze nebo konkrétní jazykové verze:  
  
    1. Chcete-li extrahovat název dne v týdnu pro aktuální jazykovou verzi, zavolejte metodu <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance hodnoty data a času a předejte řetězec "dddd" jako parametr `format`. Následující příklad ilustruje volání metody <xref:System.DateTime.ToString%28System.String%29>.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Chcete-li extrahovat název dne v týdnu pro konkrétní jazykovou verzi, zavolejte metodu hodnoty data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance. Předejte řetězec "dddd" jako parametr `format`. Předejte buď <xref:System.Globalization.CultureInfo>, nebo objekt <xref:System.Globalization.DateTimeFormatInfo>, který představuje jazykovou verzi, jejíž název dne v týdnu chcete načíst jako parametr `provider`. Následující kód ilustruje volání metody <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí objektu <xref:System.Globalization.CultureInfo>, který představuje jazykovou verzi ES-ES.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Příklad  
 Příklad znázorňuje volání vlastností <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> a metody <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> k načtení čísla, které představuje den v týdnu, zkrácený název dne v týdnu a úplný název dne v týdnu pro konkrétní datum.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Jednotlivé jazyky mohou poskytovat funkce, které duplikují nebo doplňují funkce poskytované .NET Framework. Například Visual Basic obsahuje dvě takové funkce:  
  
- `Weekday`, která vrací číslo, které označuje den v týdnu určitého data. Považuje pořadové číslo prvního dne v týdnu za jeden, zatímco vlastnost <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> považuje hodnotu za nulu.  
  
- `WeekdayName`, která vrací název týdne v aktuální jazykové verzi, který odpovídá konkrétnímu číslu dne v týdnu.  
  
 Následující příklad znázorňuje použití Visual Basic `Weekday` a `WeekdayName` funkce.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Hodnotu vrácenou vlastností <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> můžete použít také k načtení názvu dne v týdnu určitého data. To vyžaduje pouze volání metody <xref:System.Enum.ToString%2A> na hodnotě <xref:System.DayOfWeek> vrácené vlastností. Nicméně tato technika nevytvoří lokalizovaný název dne v týdnu pro aktuální jazykovou verzi, jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
