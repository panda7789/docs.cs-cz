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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b16d135449cad8ed489a8a3e21db326be0fae0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129057"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Postupy: Hodnoty data a času round-trip
V mnoha aplikacích hodnoty data a času slouží k jednoznačné identifikaci jediný bod v čase. Toto téma ukazuje, jak uložit a obnovit <xref:System.DateTime> hodnotu, <xref:System.DateTimeOffset> hodnotu a hodnotu data a času s časem zóna informace tak, aby se obnovená hodnota identifikuje ve stejnou dobu jako uloženou hodnotu.  
  
### <a name="to-round-trip-a-datetime-value"></a>Operace round-trip pro hodnoty data a času  
  
1.  Převést <xref:System.DateTime> hodnotu na řetězcové vyjádření pomocí volání <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metoda se specifikátorem formátu "o".  
  
2.  Uložit řetězcovou reprezentaci <xref:System.DateTime> hodnoty do souboru nebo ji předejte proces, aplikační domény nebo počítač hranice.  
  
3.  Načíst řetězec, který představuje <xref:System.DateTime> hodnotu.  
  
4.  Volání <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> a předáte <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametru.  
  
 Následující příklad ukazuje, jak zpátečního převodu <xref:System.DateTime> hodnotu.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Když verzemi <xref:System.DateTime> hodnota, tento postup úspěšně zachová čas potřebný pro celou dobu místního a univerzálního. Například, pokud místní <xref:System.DateTime> hodnota je uložena v rámci systému v USA Tichomořském časovém pásmu a obnovení v rámci systému v USA Centrální standardního časového pásma, obnovené datum a čas, bude později než původní čas, která odráží časový rozdíl mezi dvěma časových pásem dvě hodiny. Tento postup však není nutně přesné pro tento parametr zadán časy. Všechny <xref:System.DateTime> hodnoty, jejichž <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Unspecified> zacházeno, jako kdyby byly místní čas. Pokud to není případ, <xref:System.DateTime> nebude úspěšně identifikovat správného bodu v čase. Alternativním řešením pro toto omezení je úzce spojte hodnoty data a času s časovým pásmem pro uložení a obnovení.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Operace round-trip pro hodnoty DateTimeOffset  
  
1.  Převést <xref:System.DateTimeOffset> hodnotu na řetězcové vyjádření pomocí volání <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metoda se specifikátorem formátu "o".  
  
2.  Uložit řetězcovou reprezentaci <xref:System.DateTimeOffset> hodnoty do souboru nebo ji předejte proces, aplikační domény nebo počítač hranice.  
  
3.  Načíst řetězec, který představuje <xref:System.DateTimeOffset> hodnotu.  
  
4.  Volání <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> a předáte <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametru.  
  
 Následující příklad ukazuje, jak zpátečního převodu <xref:System.DateTimeOffset> hodnotu.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jediný bod v čase. Hodnota pak může být převedena na koordinovaný univerzální čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody nebo ji lze převést na čas v určitém časovém pásmu voláním <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> nebo <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda. Hlavním omezením této techniky je toto datum a čas aritmetický, provést u <xref:System.DateTimeOffset> hodnotu, která představuje čas v určitém časovém pásmu, nemusí poskytovat přesné výsledky pro toto časové pásmo. Důvodem je, že když <xref:System.DateTimeOffset> je vytvořena instance hodnoty, je oddělen od svého časového pásma. Proto se pravidla úpravy časového pásma už lze při provádění výpočtů datum a čas. Tento problém můžete vyřešit tak, že definujete vlastní typ, který obsahuje datum a čas a jeho související časové pásmo.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Operace round-trip pro hodnoty data a času s časovým pásmem  
  
1.  Definujte třídu nebo strukturu s dvě pole. První pole je buď <xref:System.DateTime> nebo <xref:System.DateTimeOffset> objekt a druhá je <xref:System.TimeZoneInfo> objektu. V následujícím příkladu je jednoduchá verze takového typu.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Označte třídu <xref:System.SerializableAttribute> atribut.  
  
3.  Serializace pomocí objektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.  
  
4.  Obnovit objekt pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.  
  
5.  Přetypování (v jazyce C#) nebo (v jazyce Visual Basic) deserializovaný objekt převést na objekt příslušného typu.  
  
 Následující příklad ukazuje, jak zpátečního převodu objektu, který ukládá informace data a času a časového pásma.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Tento postup by měl vždy odrážet správný bod čas i před a po jeho uložení a obnovení, zadaný, že implementace objektu kombinované data a času a časového pásma nepovoluje hodnotu data se synchronizované s Hodnota časové pásmo.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tyto příklady vyžadují:  
  
-   Aby následující obory názvů je importovat s C# `using` příkazy nebo Visual Basic `Imports` příkazy:  
  
    -   <xref:System> (C# pouze).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   Odkaz na System.Core.dll.  
  
-   Každý příklad kódu, než `DateInTimeZone` třídy, by měl součástí třídy nebo modulu jazyka Visual Basic, zabalené v metodách a volat z `Main` metody.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
