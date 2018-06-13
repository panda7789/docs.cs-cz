---
title: Tabulka formátování číselných výsledků (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: cc215971d63a0ee61eb25ac45834a81fbbc50b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216909"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Tabulka formátování číselných výsledků (Referenční dokumentace jazyka C#)
Můžete formátování číselných výsledků pomocí <xref:System.String.Format%2A?displayProperty=nameWithType> metoda, až <xref:System.Console.Write%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody, které volání `String.Format`, nebo pomocí [řetězec interpolace](../tokens/interpolated.md). Formát zadané pomocí řetězce formátu. Následující tabulka obsahuje podporované standardní formát řetězce. Řetězec formátu má následující podobu: `Axx`, kde `A` je specifikátor formátu a `xx` je specifikátor přesnosti. Specifikátor formátu řídí typ formátování aplikované na číselnou hodnotu a specifikátor přesnosti určuje počet platných číslic nebo desetinných míst formátovaný výstupu. Hodnota může být v rozmezí specifikátor přesnosti od 0 do 99.  
  
 Další informace o standardní a vlastní formátování řetězce najdete v tématu [typy formátování](../../../standard/base-types/formatting-types.md).
  
|Specifikace formátu|Popis|Příklady|Výstup|  
|----------------------|-----------------|--------------|------------|  
|C nebo c|Měna|Console.Write ("{0:C}", 2.5);<br /><br /> Console.Write ("{0:C}", čísla -2,5);|$2.50<br /><br /> ($2.50)|  
|D nebo d|Desetinné číslo|Console.Write ("{0:D5}", 25);|00025|  
|E nebo e|Scientific|Console.Write ("{0:E}", 250000);|2.500000E + 005|  
|F nebo f|Pevná desetinná čárka|Console.Write ("{0:F2}", 25);<br /><br /> Console.Write ("{0:F0}", 25);|25.00<br /><br /> 25|  
|G nebo g|Obecné|Console.Write ("{0:G}", 2.5);|2.5|  
|N nebo n|Číslo|Console.Write ("{0:N}", 2500000);|2,500,000.00|  
|X nebo x|Šestnáctková hodnota|Console.Write ("{0:X}", 250);<br /><br /> Console.Write ("{0:X}", 0xffff);|DM<br /><br /> FFFF|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [string](../../../csharp/language-reference/keywords/string.md)
