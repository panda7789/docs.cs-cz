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
ms.openlocfilehash: 516505ccacfd2a8a5c275b0de033e1316fa06d3a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661346"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabulka implicitních číselných převodů (referenční dokumentace jazyka C#)

V následující tabulce jsou uvedeny předdefinované implicitní převody mezi číselnými typy .NET.
  
|From|Chcete-li|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double`, nebo `decimal`|  
|[byte](../builtin-types/integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[short](../builtin-types/integral-numeric-types.md)|`int`, `long`, `float`, `double`, nebo `decimal`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[int](../builtin-types/integral-numeric-types.md)|`long`, `float`, `double`, nebo `decimal`|  
|[uint](../builtin-types/integral-numeric-types.md)|`long`, `ulong`, `float`, `double`, nebo `decimal`|  
|[long](../builtin-types/integral-numeric-types.md)|`float`, `double`, nebo `decimal`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`float`, `double`, nebo `decimal`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`double`|  
  
## <a name="remarks"></a>Poznámky  

- Žádné [celočíselného typu](../builtin-types/integral-numeric-types.md) implicitně převést na libovolný [s plovoucí desetinnou čárkou typu](../builtin-types/floating-point-numeric-types.md).

- Přesnost, ale nikoli velikost může být ztraceno v převody z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.  
  
- Neexistují žádné implicitní převody na `char`, `byte`, a `sbyte` typy.  

- Neexistují žádné implicitní převody z `double` a `decimal` typy.
  
- Neexistují žádné implicitní převody mezi `decimal` typ a `float` nebo `double` typy.  
  
- Hodnota konstantní výraz typu `int` (například, Hodnota reprezentovaná celočíselný literál) lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud má v rozsahu cílového typu:

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Další informace o implicitních převodů, najdete v článku [implicitních převodů](~/_csharplang/spec/conversions.md#implicit-conversions) část [specifikace jazyka C#](../language-specification/index.md).
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Celočíselné typy](../builtin-types/integral-numeric-types.md)
- [Tabulka typů s plovoucí desetinnou čárkou](../builtin-types/floating-point-numeric-types.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
- [Přetypování a převody typu](../../programming-guide/types/casting-and-type-conversions.md)
