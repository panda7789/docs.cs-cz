---
title: 'Postupy: Extrahování dne v týdnu z konkrétního data'
description: Zjistěte, jak určit pořadové číslo dne v týdnu pro určité datum v .NET. Přečtěte si, jak zobrazit lokalizovaný název dne v týdnu pro konkrétní datum.
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
ms.openlocfilehash: fa0eb6c36b88594543d08680af104b5408c295f9
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662612"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Postupy: Extrahování dne v týdnu z konkrétního data
.NET Framework usnadňuje určení pořadového čísla dne v týdnu pro konkrétní datum a zobrazení lokalizovaného názvu dne v týdnu pro konkrétní datum. Hodnota výčtu, která určuje den v týdnu odpovídající konkrétnímu datu, je k dispozici z <xref:System.DateTime.DayOfWeek%2A> <xref:System.DateTimeOffset.DayOfWeek%2A> vlastnosti nebo. Naproti tomu, že načtení názvu dne v týdnu je operace formátování, kterou lze provést voláním metody formátování, jako je například metoda hodnoty data a času `ToString` nebo <xref:System.String.Format%2A?displayProperty=nameWithType> metoda. V tomto tématu se dozvíte, jak provést tyto operace formátování.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Extrakce čísla určujícího den v týdnu od konkrétního data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Pomocí <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnosti nebo <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> načtěte <xref:System.DayOfWeek> hodnotu, která označuje den v týdnu.  
  
3. V případě potřeby přetypování (v jazyce C#) nebo převést (v Visual Basic) <xref:System.DayOfWeek> hodnotu na celé číslo.  
  
 Následující příklad zobrazuje celé číslo, které představuje den v týdnu určitého data.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Extrakce zkráceného názvu dne v týdnu z konkrétního data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat zkrácený název dne v týdnu aktuální jazykové verze nebo konkrétní jazykové verze:  
  
    1. Chcete-li extrahovat zkrácený název dne v týdnu pro aktuální jazykovou verzi, zavolejte metodu hodnoty data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instanci a předejte řetězec "ddd" jako `format` parametr. Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Chcete-li extrahovat zkrácený název dne v týdnu pro konkrétní jazykovou verzi, zavolejte metodu hodnoty data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody instance. Předá řetězec "ddd" jako `format` parametr. Předejte buď <xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> objekt, který představuje jazykovou verzi, jejíž název dne v týdnu chcete načíst jako `provider` parametr. Následující kód ilustruje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> metody pomocí <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi FR-fr.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Extrakce úplného názvu dne v týdnu z konkrétního data  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat úplný název dne v týdnu aktuální jazykové verze nebo konkrétní jazykové verze:  
  
    1. Chcete-li extrahovat název dne v týdnu pro aktuální jazykovou verzi, zavolejte metodu hodnoty data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instanci a předejte řetězec "dddd" jako `format` parametr. Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Chcete-li extrahovat název dne v týdnu pro konkrétní jazykovou verzi, zavolejte metodu hodnoty data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody instance. Předat řetězec "dddd" jako `format` parametr. Předejte buď <xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> objekt, který představuje jazykovou verzi, jejíž název dne v týdnu chcete načíst jako `provider` parametr. Následující kód ilustruje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> metody pomocí <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi ES-ES.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Příklad  
 Příklad znázorňuje volání <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> vlastností a a <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metody a <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> k načtení čísla, které představuje den v týdnu, zkrácený název dne v týdnu a úplný název dne v týdnu pro konkrétní datum.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Jednotlivé jazyky mohou poskytovat funkce, které duplikují nebo doplňují funkce poskytované .NET Framework. Například Visual Basic obsahuje dvě takové funkce:  
  
- `Weekday`Vrátí číslo, které označuje den v týdnu určitého data. Považuje pořadové číslo prvního dne v týdnu za jeden, zatímco <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost považuje hodnotu za nulu.  
  
- `WeekdayName`, který vrací název týdne v aktuální jazykové verzi, který odpovídá konkrétnímu číslu dne v týdnu.  
  
 Následující příklad ilustruje použití Visual Basic `Weekday` a `WeekdayName` funkcí.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Hodnotu vrácenou vlastností můžete použít také <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> k načtení názvu dne v týdnu určitého data. To vyžaduje pouze volání <xref:System.Enum.ToString%2A> metody na <xref:System.DayOfWeek> hodnotu vrácenou vlastností. Nicméně tato technika nevytvoří lokalizovaný název dne v týdnu pro aktuální jazykovou verzi, jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]

## <a name="see-also"></a>Viz také

- [Řetězce standardního formátu data a času](standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](custom-date-and-time-format-strings.md)
