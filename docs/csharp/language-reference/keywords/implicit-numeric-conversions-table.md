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
ms.openlocfilehash: 9c3efe1dbea355e8bc00ef44e08efcc9d0e0bdca
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424169"
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
|[float](float.md)|`double`|  
  
## <a name="remarks"></a>Poznámky  

- Žádné [celočíselného typu](../builtin-types/integral-numeric-types.md) implicitně převést na libovolný [s plovoucí desetinnou čárkou typu](floating-point-types-table.md).

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
- [Tabulka typů s plovoucí desetinnou čárkou](floating-point-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
- [Přetypování a převody typu](../../programming-guide/types/casting-and-type-conversions.md)
