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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55bdf4cf589bd912dbfc85777542150696aaa436
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589775"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Postupy: Extrahování dne v týdnu z konkrétního data
Rozhraní .NET Framework umožňuje snadno určit pořadí dne v týdnu pro konkrétní datum a zobrazovaný název lokalizované den v týdnu pro konkrétní datum. Výčtová hodnota, která označuje den v týdnu odpovídající určitému datu je k dispozici <xref:System.DateTime.DayOfWeek%2A> nebo <xref:System.DateTimeOffset.DayOfWeek%2A> vlastnost. Naproti tomu načítání název dne v týdnu je operace formátování, které lze provést zavoláním metody pro formátování, jako jsou hodnoty data a času `ToString` metoda nebo <xref:System.String.Format%2A?displayProperty=nameWithType> metody. Toto téma ukazuje, jak provádět tyto operace formátování.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Extrahovat číslo udávající den v týdnu v určité datum  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Použití <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> vlastnost pro načtení <xref:System.DayOfWeek> hodnotu, která označuje den v týdnu.  
  
3. V případě potřeby přetypování (v jazyce C#) nebo převést (v jazyce Visual Basic) <xref:System.DayOfWeek> hodnotu na celé číslo.  
  
 Následující příklad zobrazuje celé číslo, které představuje den v týdnu k určitému datu.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Extrahovat zkrácený název dne v určité datum  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat zkrácený název dne aktuální jazykové verze nebo specifické jazykové verze:  
  
    1. Chcete-li extrahovat zkrácený název dne pro aktuální jazykovou verzi, zavolejte hodnoty data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instanci metody a předejte jako řetězec "ddd" `format` parametru. Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Chcete-li extrahovat zkrácený název dne pro konkrétní jazykovou verzi, zavolejte hodnoty data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu instance. Předejte jako řetězec "ddd" `format` parametru. Předat <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který představuje jazykovou verzi, jejíž název dne v týdnu, které chcete načíst jako `provider` parametru. Následující kód znázorňuje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí metody <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi fr-FR.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Extrahovat název úplné dne v týdnu v určité datum  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Můžete extrahovat úplné úplný název aktuální jazykové verze nebo specifické jazykové verze:  
  
    1. Chcete-li extrahovat název dne v týdnu pro aktuální jazykovou verzi, zavolejte hodnoty data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instanci metody a předejte jako řetězec "dddd" `format` parametru. Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Chcete-li extrahovat název dne v týdnu pro konkrétní jazykovou verzi, zavolejte hodnoty data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu instance. Předejte jako řetězec "dddd" `format` parametru. Předat <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který představuje jazykovou verzi, jejíž název dne v týdnu, které chcete načíst jako `provider` parametru. Následující kód znázorňuje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí metody <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, es-ES.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje volání <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> vlastnosti a <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> metody pro načtení číslo představující den v týdnu, zkrácený název dne a název úplné dne v týdnu pro konkrétní datum.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Jednotlivé jazyky Tyhle nástroje nabízejí funkce, která duplikuje nebo doplňuje funkce poskytované rozhraním .NET Framework. Například Visual Basic obsahuje dvou takových funkcí:  
  
- `Weekday`, který vrátí číslo, které označuje den v týdnu konkrétního data. Považuje pořadové číslo první den v týdnu se, že <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost považuje nula.  
  
- `WeekdayName`, který vrátí název v týdnu v aktuální jazykové verze, která odpovídá na konkrétní den v týdnu číslo.  
  
 Následující příklad ukazuje použití jazyka Visual Basic `Weekday` a `WeekdayName` funkce.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Můžete použít také hodnoty vrácené <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost pro načtení název dne v týdnu konkrétního data. To vyžaduje pouze volání <xref:System.Enum.ToString%2A> metodu <xref:System.DayOfWeek> hodnota vrácená vlastností. Tento postup však nevytváří den v týdnu lokalizovaný název pro aktuální jazykovou verzi, jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
