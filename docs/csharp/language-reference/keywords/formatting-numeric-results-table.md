---
title: "Tabulka formátování číselných výsledků (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce14d5124ffdf030701ae0fc769278da51f86cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="formatting-numeric-results-table-c-reference"></a>Tabulka formátování číselných výsledků (Referenční dokumentace jazyka C#)
Můžete formátování číselných výsledků pomocí <xref:System.String.Format%2A?displayProperty=nameWithType> metoda, nebo pomocí <xref:System.Console.Write%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodu, která volá `String.Format`. Formát zadané pomocí řetězce formátu. Následující tabulka obsahuje podporované standardní formát řetězce. Řetězec formátu má následující podobu: `Axx`, kde `A` je specifikátor formátu a `xx` je specifikátor přesnosti. Specifikátor formátu řídí typ formátování aplikované na číselnou hodnotu a specifikátor přesnosti určuje počet platných číslic nebo desetinných míst formátovaný výstupu. Hodnota může být v rozmezí specifikátor přesnosti od 0 do 99.  
  
 Další informace o standardní a vlastní formátování řetězce najdete v tématu [typy formátování](../../../standard/base-types/formatting-types.md). Další informace o `String.Format` metodu, najdete v části <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
|Specifikace formátu|Popis|Příklady|Výstup|  
|----------------------|-----------------|--------------|------------|  
|C nebo c|Měna|Console.Write ("{0}",: c 2.5);<br /><br /> Console.Write ("{0}",: c čísla -2,5);|$2.50<br /><br /> ($2.50)|  
|D nebo d|Desetinné číslo|Console.Write ("{0:D5}", 25);|00025|  
|E nebo e|Scientific|Console.Write ("{0:E}", částku 250 000 jedné);|2.500000E + 005|  
|F nebo f|Pevná desetinná čárka|Console.Write ("{0: F2}", 25);<br /><br /> Console.Write ("{0: F0}", 25);|25.00<br /><br /> 25|  
|G nebo g|Obecné|Console.Write ("{0: g}", 2.5);|2.5|  
|N nebo n|Číslo|Console.Write ("{0: n}", 2500000);|2,500,000.00|  
|X nebo x|Šestnáctková hodnota|Console.Write ("{0: x}", 250);<br /><br /> Console.Write ("{0: x}", 0xffff);|DM<br /><br /> FFFF|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Standardní řetězce formátu čísla](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [řetězec](../../../csharp/language-reference/keywords/string.md)
