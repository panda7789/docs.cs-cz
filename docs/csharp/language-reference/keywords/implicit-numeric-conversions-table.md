---
title: Tabulka implicitních číselných převodů - C# odkaz
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 98774a0f7ad86e43178c6d0216e29e7b4767f3f2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235251"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabulka implicitních číselných převodů (referenční dokumentace jazyka C#)

V následující tabulce jsou uvedeny předdefinované implicitní převody mezi číselnými typy .NET.
  
|From|Chcete-li|  
|----------|--------|  
|[sbyte](sbyte.md)|`short`, `int`, `long`, `float`, `double`, nebo `decimal`|  
|[byte](byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[short](short.md)|`int`, `long`, `float`, `double`, nebo `decimal`|  
|[ushort](ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[int](int.md)|`long`, `float`, `double`, nebo `decimal`|  
|[uint](uint.md)|`long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[long](long.md)|`float`, `double`, nebo `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[float](float.md)|`double`|  
|[ulong](ulong.md)|`float`, `double`, nebo `decimal`|  
  
## <a name="remarks"></a>Poznámky  

- Žádné [celočíselného typu](integral-types-table.md) implicitně převést na libovolný [s plovoucí desetinnou čárkou typu](floating-point-types-table.md).

- Přesnost, ale nikoli velikost může být ztraceno v převody z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.  
  
- Neexistují žádné implicitní převody na `char` typu.  
  
- Neexistují žádné implicitní převody mezi `float` a `double` typy a `decimal` typu.  
  
- Hodnota konstantní výraz typu `int` (například, Hodnota reprezentovaná celočíselný literál) lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud má v rozsahu cílového typu:

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Další informace o implicitních převodů, najdete v článku [implicitních převodů](~/_csharplang/spec/conversions.md#implicit-conversions) část [specifikace jazyka C#](../language-specification/index.md).
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Tabulka celočíselných typů](integral-types-table.md)
- [Tabulka typů s plovoucí desetinnou čárkou](floating-point-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
- [Přetypování a převody typu](../../programming-guide/types/casting-and-type-conversions.md)
