---
title: Tabulka typů hodnot - C# odkaz
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 98829f30c2c25c0710cf3fe044359d3c7538fe76
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424043"
---
# <a name="value-types-table-c-reference"></a>Tabulka typů hodnot (referenční dokumentace jazyka C#)

Následující tabulka ukazuje C# typů hodnot:

|Typ hodnoty|Kategorie|Typ přípony|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|[byte](../builtin-types/integral-numeric-types.md)|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)
)||
|[decimal](decimal.md)|Numeric, [floating-point](floating-point-types-table.md)|M nebo m|
|[double](double.md)|Numeric, [floating-point](floating-point-types-table.md)|D nebo d|
|[enum](enum.md)|Výčet||
|[float](float.md)|Numeric, [floating-point](floating-point-types-table.md)|F nebo f|
|[int](../builtin-types/integral-numeric-types.md)|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|[long](../builtin-types/integral-numeric-types.md)|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)|L nebo l|
|[sbyte](../builtin-types/integral-numeric-types.md)|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|[short](../builtin-types/integral-numeric-types.md)|Podepsaný držitelem, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Struktury definované uživatelem||
|[uint](../builtin-types/integral-numeric-types.md)|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)|U nebo u|
|[ulong](../builtin-types/integral-numeric-types.md)|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, logická jednotka nebo logická jednotka|
|[ushort](../builtin-types/integral-numeric-types.md)|Bez znaménka, číselné hodnoty a [integrální](../builtin-types/integral-numeric-types.md)||

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
