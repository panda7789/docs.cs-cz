---
title: "Tabulka předdefinovaných typů (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9d1e4945526a862074e73e608185696328946be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="built-in-types-table-c-reference"></a>Tabulka předdefinovaných typů (Referenční dokumentace jazyka C#)
V následující tabulce jsou uvedeny klíčová slova pro vestavěné C# typy, které jsou aliasy předdefinovaných typů v <xref:System> oboru názvů.  
  
|Typ jazyka C#|Typ rozhraní .NET framework|  
|--------------|-------------------------|  
|[BOOL](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[bajtů](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[SByte –](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[Char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[Decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[Double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[plovoucí desetinná čárka](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[celá čísla](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[dlouhá](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong –](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[objekt](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[krátký](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort –](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[řetězec](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>Poznámky  
 Všechny typy v tabulce s výjimkou `object` a `string`, se označují jako jednoduché typy.  
  
 Jazyce C# typ klíčová slova a jejich aliasy jsou zaměnitelné. Můžou například deklarovat proměnná typu integer pomocí některé z následujících deklarace:  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Pokud chcete zobrazit skutečný typ pro jakýkoli typ C#, použijte metodu systému `GetType()`. Například následující příkaz zobrazí alias systému, který představuje typ `myVariable`:  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 Můžete také [typeof](../../../csharp/language-reference/keywords/typeof.md) operátor.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [Tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Tabulka formátování číselných výsledků](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamické](../../../csharp/language-reference/keywords/dynamic.md)  
 [Referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
