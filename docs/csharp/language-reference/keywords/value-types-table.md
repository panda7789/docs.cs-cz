---
title: Tabulka typů hodnot - C# odkaz
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 2e2897ff647140b58b3a1812e153a44a6fcdaef7
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859563"
---
# <a name="value-types-table-c-reference"></a>Tabulka typů hodnot (referenční dokumentace jazyka C#)

Následující tabulka ukazuje C# typů hodnot:

|Typ hodnoty|Kategorie|Typ přípony|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|`byte`|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)
|`decimal`|Numeric, [floating-point](../builtin-types/floating-point-numeric-types.md)|M nebo m|
|`double`|Numeric, [floating-point](../builtin-types/floating-point-numeric-types.md)|D nebo d|
|[enum](enum.md)|Výčet||
|`float`|Numeric, [floating-point](../builtin-types/floating-point-numeric-types.md)|F nebo f|
|`int`|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|`long`|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)|L nebo l|
|`sbyte`|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|`short`|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Struktury definované uživatelem||
|`uint`|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)|U nebo u|
|`ulong`|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, logická jednotka nebo logická jednotka|
|`ushort`|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||

## <a name="remarks"></a>Poznámky

Použijete příponou podle typu k určení typu číselný literál. Příklad:

```csharp
decimal a = 0.1M;
```

Pokud [celočíselný literál číselné](~/_csharplang/spec/lexical-structure.md#integer-literals) nemá žádné příponu má první z těchto typů, ve kterých může být reprezentována jeho hodnota: `int`, `uint`, `long`, `ulong`.

Pokud [reálné číselný literál](~/_csharplang/spec/lexical-structure.md#real-literals) nemá žádné příponu, je typu `double`.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Tabulka výchozích hodnot](default-values-table.md)
- [Typy hodnot](value-types.md)
- [Tabulka formátování číselných výsledků](formatting-numeric-results-table.md)
