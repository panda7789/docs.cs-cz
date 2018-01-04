---
title: "Postupy: Hodnoty data a času round-trip"
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
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68667369e1c7541313a166a1066e1ad9d69b6b71
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a>Postupy: Hodnoty data a času round-trip
V mnoha aplikacích hodnota data a času je určený pro jednoznačnou identifikaci jediný bod v čase. Toto téma ukazuje, jak k uložení a obnovení <xref:System.DateTime> hodnotu, <xref:System.DateTimeOffset> hodnota a datum a čas hodnotu s časem zónu informace tak, aby obnovená hodnota identifikuje ve stejnou dobu jako uložena hodnota.  
  
### <a name="to-round-trip-a-datetime-value"></a>Operace round-trip pro hodnoty data a času  
  
1.  Převést <xref:System.DateTime> hodnotu na řetězcovou reprezentaci voláním <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metoda s specifikátor formátu "o".  
  
2.  Uložte řetězcovou reprezentaci <xref:System.DateTime> hodnoty do souboru, nebo ji předejte procesu, aplikační domény nebo počítač hranici.  
  
3.  Načíst řetězec, který představuje <xref:System.DateTime> hodnotu.  
  
4.  Volání <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metoda a předejte jí <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametr.  
  
 Následující příklad ukazuje, jak k odezvě <xref:System.DateTime> hodnotu.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Když odezvy <xref:System.DateTime> hodnotu, tato technika úspěšně zachová čas pro všechny místního a univerzálního časy. Například, pokud místní <xref:System.DateTime> hodnota je uložena v systému v USA Tichomořském časovém pásmu a obnovení systému v USA Střed standardního časového pásma, obnovené datum a čas bude později než původní čas, což odráží časový rozdíl mezi dvěma časových pásem dvě hodiny. Tento postup však není nutně přesný pro neurčené časy. Všechny <xref:System.DateTime> hodnoty, jehož <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified> jsou zpracovány jako v případě, že jsou místních časů. Pokud to tak není, <xref:System.DateTime> nebude úspěšně identifikovat správný bod v čase. Alternativní řešení pro toto omezení je úzce spojte hodnota data a času s časovým pásmem pro uložení a operaci obnovení.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Operace round-trip pro hodnotu DateTimeOffset  
  
1.  Převést <xref:System.DateTimeOffset> hodnotu na řetězcovou reprezentaci voláním <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metoda s specifikátor formátu "o".  
  
2.  Uložte řetězcovou reprezentaci <xref:System.DateTimeOffset> hodnoty do souboru, nebo ji předejte procesu, aplikační domény nebo počítač hranici.  
  
3.  Načíst řetězec, který představuje <xref:System.DateTimeOffset> hodnotu.  
  
4.  Volání <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metoda a předejte jí <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametr.  
  
 Následující příklad ukazuje, jak k odezvě <xref:System.DateTimeOffset> hodnotu.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jediný bod v čase. Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda, nebo může být převeden na čas v určitém časovém pásmu voláním <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> nebo <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda. Hlavním omezením Tato technika je datum a čas aritmetické operace, při provádění v <xref:System.DateTimeOffset> hodnotu, která reprezentuje čas v určitém časovém pásmu, nemusí poskytovat přesné výsledky pro toto časové pásmo. Důvodem je, že když <xref:System.DateTimeOffset> vytváření instance hodnoty, je časovému pásmu, jeho. Proto pravidla úpravy časového pásma můžete už použijí při provádění výpočtů datum a čas. Tento problém můžete vyřešit definováním vlastního typu, který obsahuje datum a čas hodnota a jejich příslušná časová pásma.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Operace round-trip pro hodnoty data a času s časovým pásmem  
  
1.  Definujte třídu nebo strukturu se dvěma poli. První pole je buď <xref:System.DateTime> nebo <xref:System.DateTimeOffset> objekt a druhá je <xref:System.TimeZoneInfo> objektu. V následujícím příkladu je jednoduchý verze takového typu.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Označte třídu <xref:System.SerializableAttribute> atribut.  
  
3.  Serializovat objekt pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metoda.  
  
4.  Obnovení pomocí objektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metoda.  
  
5.  Přetypování (v C#) nebo převést (v jazyce Visual Basic) deserializovaný objekt na objekt příslušného typu.  
  
 Následující příklad ilustruje, jak k odezvě na objekt, který ukládá informace o datu a času a časového pásma.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Tento postup by měl vždy odrážet bod správný čas i před a po jeho uložení a obnovení, zadaný, implementace objektu kombinované datum a čas a časové pásmo nepovoluje hodnoty date se synchronizované s Hodnota časového pásma.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tyto příklady vyžadují:  
  
-   Že následujících oborů názvů naimportovat pomocí C# `using` příkazy nebo [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` příkazy:  
  
    -   <xref:System>(C# pouze).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   Odkaz na System.Core.dll.  
  
-   Každý příklad kódu, než `DateInTimeZone` třídy, by měl zahrnuté ve třídě nebo modulu Visual Basic, uzavřen do metod a volání z `Main` metoda.  
  
## <a name="see-also"></a>Viz také  
 [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
