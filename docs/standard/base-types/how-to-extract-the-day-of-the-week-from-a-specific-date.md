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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084192"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Postupy: Extrahování dne v týdnu z konkrétního data
Rozhraní .NET Framework usnadňuje určení řadového dne v týdnu pro určité datum a zobrazení lokalizovaného názvu dne v týdnu pro určité datum. Výčet hodnota, která označuje den v týdnu odpovídající určité datum <xref:System.DateTime.DayOfWeek%2A> <xref:System.DateTimeOffset.DayOfWeek%2A> je k dispozici od nebo vlastnost. Naproti tomu načítání názvu dne v týdnu je operace formátování, kterou lze provést voláním metody formátování, `ToString` jako je <xref:System.String.Format%2A?displayProperty=nameWithType> například metoda hodnoty data a času nebo metoda. Toto téma ukazuje, jak tyto operace formátování provádět.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Extrahování čísla označující den v týdnu od určitého data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Pomocí <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnosti or <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> <xref:System.DayOfWeek> načtěte hodnotu, která označuje den v týdnu.  
  
3. V případě potřeby přetypujte (v jazyce C#) nebo převeďte <xref:System.DayOfWeek> (v jazyce Visual Basic) hodnotu na celé číslo.  
  
 Následující příklad zobrazuje celé číslo představující den v týdnu určitého data.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Extrahování zkráceného názvu dne v týdnu od určitého data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat zkrácený název dne v týdnu aktuální jazykové verze nebo určité jazykové verze:  
  
    1. Chcete-li extrahovat zkrácený název dne v týdnu pro aktuální <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> jazykovou verzi, zavolejte metodu nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodu instance hodnoty data a času a předejte jako `format` parametr řetězec "ddd". Následující příklad ilustruje volání <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Chcete-li extrahovat zkrácený název dne v týdnu pro konkrétní <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> jazykovou verzi, zavolejte metodu hodnoty data a času nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instancí. Předajte řetězec "ddd" jako `format` parametr. Předaj <xref:System.Globalization.CultureInfo> te <xref:System.Globalization.DateTimeFormatInfo> buď a nebo objekt, který představuje jazykovou verzi, jejíž název dne v týdnu `provider` chcete načíst jako parametr. Následující kód ilustruje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> metody pomocí <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi fr-FR.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Extrahování celého názvu dne v týdnu z určitého data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat úplný název dne v týdnu aktuální jazykové verze nebo konkrétní jazykové verze:  
  
    1. Chcete-li extrahovat název dne v týdnu pro <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> aktuální <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> jazykovou verzi, zavolejte metodu hodnoty `format` data a času nebo metodu instance a předejte jako parametr řetězec "dddd". Následující příklad ilustruje volání <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Chcete-li extrahovat název dne v týdnu pro <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> konkrétní <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> jazykovou verzi, zavolejte metodu hodnoty data a času nebo instancí. Předajte řetězec "dddd" jako `format` parametr. Předaj <xref:System.Globalization.CultureInfo> te <xref:System.Globalization.DateTimeFormatInfo> buď a nebo objekt, který představuje jazykovou verzi, jejíž název dne v týdnu `provider` chcete načíst jako parametr. Následující kód ilustruje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> metody pomocí <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi es es.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Příklad  
 Příklad ilustruje <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> volání vlastností <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> a <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> metody a pro načtení čísla, které představuje den v týdnu, zkrácený název dne v týdnu a úplný název dne v týdnu pro určité datum.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Jednotlivé jazyky mohou poskytovat funkce, které duplikují nebo doplňují funkce poskytované rozhraním .NET Framework. Například Visual Basic obsahuje dvě takové funkce:  
  
- `Weekday`, který vrátí číslo, které označuje den v týdnu určitého data. Hodnotu prvního dne v týdnu považuje za jeden, zatímco <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost ji považuje za nulovou.  
  
- `WeekdayName`, který vrátí název týdne v aktuální jazykové verzi, který odpovídá určitému číslu dne v týdnu.  
  
 Následující příklad ilustruje použití jazyka a `Weekday` `WeekdayName` funkce.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Můžete také použít hodnotu <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vrácenou vlastností k načtení názvu konkrétního data dne v týdnu. To vyžaduje pouze volání <xref:System.Enum.ToString%2A> metody <xref:System.DayOfWeek> na hodnotu vrácenou vlastností. Tato technika však nevytváří lokalizovaný název dne v týdnu pro aktuální jazykovou verzi, jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Viz také

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
