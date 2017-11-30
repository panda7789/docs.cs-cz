---
title: "Postupy: Extrahování dne v týdnu z konkrétního data"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3accb01eb8c5edb8b3e245020b43c5a94a8bb4cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Postupy: Extrahování dne v týdnu z konkrétního data
Rozhraní .NET Framework usnadňuje určení pořadí dne v týdnu pro konkrétní datum a zobrazí se název lokalizované den v týdnu pro konkrétní datum. Výčtová hodnota určující, den v týdnu odpovídající konkrétní datum je k dispozici prostřednictvím <xref:System.DateTime.DayOfWeek%2A> nebo <xref:System.DateTimeOffset.DayOfWeek%2A> vlastnost. Načítání názvu den v týdnu je naopak operaci formátování, které lze provést pomocí volání metody pro formátování, jako je například hodnota data a času `ToString` metoda nebo <xref:System.String.Format%2A?displayProperty=nameWithType> metoda. Toto téma ukazuje, jak provést tyto operace formátování.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Extrahování číslo určující den v týdnu z konkrétního data  
  
1.  Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2.  Použití <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> vlastnosti načíst <xref:System.DayOfWeek> hodnotu, která označuje den v týdnu.  
  
3.  V případě potřeby přetypování (v C#) nebo převést (v jazyce Visual Basic) <xref:System.DayOfWeek> hodnotu na celé číslo.  
  
 Následující příklad zobrazí celé číslo představující den v týdnu konkrétní datum.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Extrahovat zkrácený název dne z konkrétního data  
  
1.  Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2.  Můžete rozbalit zkrácený název dne aktuální jazykové verze nebo konkrétní jazykové verze:  
  
    1.  Chcete-li extrahovat zkrácený název dne pro aktuální jazykovou verzi, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodu instance a předejte řetězec "ddd" jako `format` parametr. Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metoda.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  Chcete-li extrahovat zkrácený název dne pro konkrétní jazykové verze, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu instance. Předejte řetězec "ddd" jako `format` parametr. Buď předat <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který reprezentuje jazykovou verzi, jejíž název den v týdnu, můžete obnovit jako `provider` parametr. Následující kód ukazuje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí metody <xref:System.Globalization.CultureInfo> objekt, který reprezentuje fr-FR jazykovou verzi.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Chcete-li extrahovat název úplné den v týdnu z konkrétního data  
  
1.  Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2.  Můžete rozbalit úplné den v týdnu název aktuální jazykové verze nebo konkrétní jazykové verze:  
  
    1.  Chcete-li extrahovat úplný název pro aktuální jazykovou verzi, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodu instance a předejte řetězec "dddd" jako `format` parametr. Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metoda.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  Chcete-li extrahovat úplný název pro konkrétní jazykové verze, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu instance. Předejte řetězec "dddd" jako `format` parametr. Buď předat <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který reprezentuje jazykovou verzi, jejíž název den v týdnu, můžete obnovit jako `provider` parametr. Následující kód ukazuje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí metody <xref:System.Globalization.CultureInfo> objekt, který reprezentuje es-ES jazykovou verzi.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje volání <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> vlastnosti a <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> metody pro získání čísla, které představuje den v týdnu, zkrácený název dne a názvu úplné den v týdnu pro konkrétní datum.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Jednotlivé jazyky může poskytují funkce, která duplikuje nebo doplňují funkce poskytované službou [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Visual Basic například obsahuje dvě takové funkce:  
  
-   `Weekday`, která vrací číslo, které označuje den v týdnu určitého data. Považuje za pořadové číslo první den v týdnu na jednu, zatímco <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost považuje být nula.  
  
-   `WeekdayName`, která vrací název v týdnu v aktuální jazykovou verzi, která odpovídá na číslo určitý den v týdnu.  
  
 Následující příklad ukazuje použití Visual Basicu `Weekday` a `WeekdayName` funkce.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Můžete také použít hodnoty vrácené <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost načíst název den v týdnu určitého data. To vyžaduje pouze volání <xref:System.Enum.ToString%2A> metodu <xref:System.DayOfWeek> hodnoty vrácené vlastnost. Tento postup však neobsahuje název lokalizované den v týdnu pro aktuální jazykovou verzi, jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Viz také  
 [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Řetězce formátu standardní hodnoty data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Řetězce formátu vlastní hodnota data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
