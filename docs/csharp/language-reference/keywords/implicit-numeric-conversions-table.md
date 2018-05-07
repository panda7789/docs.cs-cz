---
title: Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 2d417a2020656f300de0517526742679388f262e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)
V následující tabulce jsou předdefinované implicitní číselné převody. Implicitní převody může dojít v mnoha situacích, včetně metoda vyvolání a přiřazení příkazy.  
  
|From|Chcete-li|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double`, nebo `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double`, nebo `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double`, nebo `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`, `double`, nebo `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double`, nebo `decimal`|  
  
## <a name="remarks"></a>Poznámky  
  
-   Přesnost, ale není rozsahem může dojít ke ztrátě, při převodu z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.  
  
-   Neexistují žádná implicitní převod `char` typu.  
  
-   Neexistují žádná implicitní převody mezi typy s plovoucí desetinnou čárkou a `decimal` typu.  
  
-   Konstantní výraz typu `int` lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud konstantní výraz hodnotu v rozsahu cílového typ.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
