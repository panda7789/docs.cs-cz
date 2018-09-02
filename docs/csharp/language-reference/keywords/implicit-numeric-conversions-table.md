---
title: Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 4bbc6086dc5fd3838ef9361762c3068ca44efd0e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417593"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)
V následující tabulce jsou uvedeny předdefinované implicitních číselných převodů. Implicitní převod může dojít v mnoha situacích, včetně příkazů metody vyvolání a přiřazení.  
  
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
  
-   Přesnost, ale nikoli velikost může být ztraceno v převody z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.  
  
-   Neexistují žádné implicitní převody na `char` typu.  
  
-   Neexistují žádné implicitní převody mezi typy s plovoucí desetinnou čárkou a `decimal` typu.  
  
-   Konstantní výraz typu `int` lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud má konstantní výraz hodnotu v rozsahu cílového umístění Zadejte.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
