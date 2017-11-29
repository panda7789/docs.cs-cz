---
title: "Postupy: Převedení řetězce na číslo (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3dc67bc2f25bba14df0e3ce6859bb8bc9094871c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Postupy: Převedení řetězce na číslo (Průvodce programováním v C#)
Můžete převést [řetězec](../../../csharp/language-reference/keywords/string.md) na číslo pomocí metody v <xref:System.Convert> třídy nebo pomocí `TryParse` nalezena metoda na různých číselnými typy (int, dlouhé, float, atd.).  
  
 Pokud máte řetězec, je něco víc efektivní a přímý k volání `TryParse` – metoda (například `int.TryParse("11")`).  Použití `Convert` je užitečnější pro obecné objekty, které implementují <xref:System.IConvertible>.  
  
 Můžete použít `Parse` nebo `TryParse` metody na číselný typ očekáváte, že obsahuje řetězec, například <xref:System.Int32?displayProperty=nameWithType> typu.  <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Používá metoda <xref:System.Int32.Parse%2A> interně.  Pokud řetězec není v platném formátu `Parse` vyvolá výjimku, zatímco `TryParse` vrátí [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Příklad  
 `Parse` a `TryParse` metody Ignorovat prázdné znaky na začátku a na konci řetězce, ale všechny ostatní znaky musí být znaky, které tvoří příslušného číselného typu (int, long, ulong, float, decimal, atd.).  Všechny prázdné znaky v rámci znaky, které vytvářejí číslo způsobit chybu.  Například můžete použít `decimal.TryParse` analyzovat "10", "10.3", "10", ale tuto metodu nelze použít k analýze 10 z "10 X", "1 0" (Poznámka místa), "10. 3" (Poznámka místa), "10e1" (`float.TryParse` zde funguje), a tak dále.  
  
 Následující příklady ukazují úspěšné i neúspěšné volání `Parse` a `TryParse`.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Příklad  
 Následující tabulka uvádí některé z metod z <xref:System.Convert> třídu, která můžete použít.  
  
|Číselný typ|Metoda|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 Tento příklad volá <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> způsobů, jak převést vstup [řetězec](../../../csharp/language-reference/keywords/string.md) k [int](../../../csharp/language-reference/keywords/int.md) . Kód zachytí dvě nejběžnější výjimky, které může být vyvolána touto metodou, <xref:System.FormatException> a <xref:System.OverflowException>. Pokud lze číslo zvýšit bez přetečení umístění úložiště celého čísla, program přidá k výsledku hodnotu 1 a výstup vytiskne.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Postupy: určení, zda řetězec reprezentuje číselnou hodnotu](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [Nástroj formátování rozhraní .NET framework 4](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
