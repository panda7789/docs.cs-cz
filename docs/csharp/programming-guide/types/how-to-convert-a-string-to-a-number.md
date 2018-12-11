---
title: 'Postupy: Převod řetězce na číslo - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: a75d6dd5fdb74ca3cb6fe28db7415aeb478e2237
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243215"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Postupy: Převod řetězce na číslo (C# Průvodce programováním v)
Můžete převést [řetězec](../../../csharp/language-reference/keywords/string.md) na číslo pomocí metod v <xref:System.Convert> třídy nebo pomocí `TryParse` nalezena metoda u různých číselných typů (int, long, float, atd.).  
  
 Pokud máte řetězec, je o něco víc efektivní a jednoduchý volání `TryParse` – metoda (například [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)).  Použití <xref:System.Convert> metoda je užitečná více pro hlavní objekty, které implementují <xref:System.IConvertible>.  
  
 Můžete použít `Parse` nebo `TryParse` metody na číselný typ očekáváte, že řetězec obsahuje, jako <xref:System.Int32?displayProperty=nameWithType> typu.  <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Používá metoda <xref:System.Int32.Parse%2A> interně.  Pokud řetězec není v platném formátu `Parse` vyvolá výjimku, zatímco `TryParse` vrátí [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Příklad  
 `Parse` a `TryParse` metody ignorování prázdných znaků na začátku a na konci řetězce, ale všechny ostatní znaky musí být znaky, které tvoří příslušného číselného typu (int, long, ulong, float, decimal, atd.).  Žádné prázdné znaky. mezi znaky, které tvoří číslo způsobit chybu.  Například můžete použít `decimal.TryParse` analyzovat "10", "10.3", "10", ale tuto metodu nelze použít k analýze 10 z "10 X", "1 0" (Poznámka: místo), "10. 3" (Poznámka: místo), "10e1" (`float.TryParse` Tady můžete použít), a tak dále.  
  
 Následující příklady znázorňují úspěšné i neúspěšné volání `Parse` a `TryParse`.  
  
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
  
 Tento příklad příkladu volá <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> způsobů, jak převést vstupní [řetězec](../../../csharp/language-reference/keywords/string.md) do [int](../../../csharp/language-reference/keywords/int.md) . Kód zachytí dvě nejčastější výjimky, které mohou být vyvolány touto metodou, <xref:System.FormatException> a <xref:System.OverflowException>. Pokud lze číslo zvýšit bez přetečení umístění úložiště celého čísla, program přidá k výsledku hodnotu 1 a výstup vytiskne.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Viz také

- [Typy](../../../csharp/programming-guide/types/index.md)  
- [Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
- [Nástroj pro formátování rozhraní .NET framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
