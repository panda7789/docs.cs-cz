---
title: Tabulka explicitních číselných převodů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 7363df3e4b2449924222745de409fd68349b93de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabulka explicitních číselných převodů (Referenční dokumentace jazyka C#)
Explicitní číselný převod se používá k jakékoli číselné typ převést na jiný číselný typ, pro kterou neexistuje žádný implicitní převod pomocí výraz přetypování. V následující tabulce jsou tyto převody.  
  
 Další informace o převody najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|From|Chcete-li|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` Nebo `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short`, nebo `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, nebo `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, nebo `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, nebo `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte`, nebo `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, nebo `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, nebo `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, nebo `double`|  
  
## <a name="remarks"></a>Poznámky  
  
-   Explicitní číselný převod může způsobit ztrátu přesnosti nebo výsledek v aktivační výjimky.  
  
-   Při převodu `decimal` integrální typ, tato hodnota se zaokrouhlí směrem k nule na nejbližší hodnotu integrálu. Pokud výsledná integrální hodnota je mimo rozsah cílového typu, <xref:System.OverflowException> je vyvolána výjimka.  
  
-   Při převodu z `double` nebo `float` integrální typ, hodnota je oříznuta. Pokud výsledná integrální hodnota je mimo rozsah hodnoty cílové, výsledek bude záviset na přetečení kontrola kontextu. V kontextu zaškrtnuté `OverflowException` je vyvolána v kontextu není zaškrtnuto, výsledkem je, hodnotu nespecifikované cílového typu.  
  
-   Při převodu `double` k `float`, `double` hodnota se zaokrouhlí na nejbližší `float` hodnotu. Pokud `double` hodnota je příliš malá nebo příliš velká na typ cílového, výsledkem bude nula nebo nekonečna.  
  
-   Při převodu `float` nebo `double` k `decimal`, zdrojové hodnoty jsou převedeny na `decimal` reprezentace a zaokrouhlí na nejbližší číslo po 28th desetinné místo v případě potřeby. V závislosti na hodnotě zdrojové hodnoty může dojít mezi následující výsledky:  
  
    -   Pokud je příliš malá, aby být reprezentován jako zdrojové hodnoty `decimal`, výsledek klesne na nulu.  
  
    -   Pokud je zdroj hodnota typu NaN (není číslo), infinity, nebo příliš velký a nelze je jako `decimal`, `OverflowException` je vyvolána výjimka.  
  
-   Při převodu `decimal` k `float` nebo `double`, `decimal` hodnota se zaokrouhlí na nejbližší `double` nebo `float` hodnotu.  
  
 Další informace o explicitní převod najdete v tématu explicitní v specifikace jazyka C#. Další informace o tom, jak získat přístup k o specifikace, najdete v části [specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [() – operátor](../../../csharp/language-reference/operators/invocation-operator.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
