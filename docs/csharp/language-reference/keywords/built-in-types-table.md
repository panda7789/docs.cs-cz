---
title: Tabulka předdefinovaných typů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 120347e5bff7f0d6c7120af0cb250936ca39ea16
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="built-in-types-table-c-reference"></a>Tabulka předdefinovaných typů (Referenční dokumentace jazyka C#)
V následující tabulce jsou uvedeny klíčová slova pro vestavěné C# typy, které jsou aliasy předdefinovaných typů v <xref:System> oboru názvů.  
  
|Typ jazyka C#|Typ rozhraní .NET framework|  
|--------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>Poznámky  
 Všechny typy v tabulce s výjimkou `object` a `string`, se označují jako jednoduché typy.  
  
 Jazyce C# typ klíčová slova a jejich aliasy jsou zaměnitelné. Můžou například deklarovat proměnná typu integer pomocí některé z následujících deklarace:  
  
```csharp  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Pokud chcete zobrazit skutečný typ pro jakýkoli typ C#, použijte metodu systému `GetType()`. Například následující příkaz zobrazí alias systému, který představuje typ `myVariable`:  
  
```csharp  
Console.WriteLine(myVariable.GetType());  
```  
  
 Můžete také [typeof](../../../csharp/language-reference/keywords/typeof.md) operátor.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [Tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Tabulka formátování číselných výsledků](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
