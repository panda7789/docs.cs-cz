---
title: Tabulka typů hodnot (referenční dokumentace jazyka C#)
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: bc7143b9f006af20b0bb91203d3093410d4ac0bf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418419"
---
# <a name="value-types-table-c-reference"></a>Tabulka typů hodnot (referenční dokumentace jazyka C#)

V následující tabulce jsou uvedeny typy hodnot C#.  
  
|Typ hodnoty|Kategorie|Typ přípony|  
|----------------|--------------|-----------------|  
|[bool](bool.md)|Boolean||  
|[byte](byte.md)|Bez znaménka, číselné hodnoty a [integrální](integral-types-table.md)||  
|[char](char.md)|Bez znaménka, číselné hodnoty a [integrální](integral-types-table.md)||  
|[decimal](decimal.md)|Číselné hodnoty a [s plovoucí desetinnou čárkou](floating-point-types-table.md)|M nebo m|  
|[double](double.md)|Číselné hodnoty a [s plovoucí desetinnou čárkou](floating-point-types-table.md)|D nebo d|  
|[enum](enum.md)|Výčet||  
|[float](float.md)|Číselné hodnoty a [s plovoucí desetinnou čárkou](floating-point-types-table.md)|F nebo f|  
|[int](int.md)|Podepsaný držitelem, číselné hodnoty a [integrální](integral-types-table.md)||  
|[long](long.md)|Podepsaný držitelem, číselné hodnoty a [integrální](integral-types-table.md)|L nebo l|  
|[sbyte](sbyte.md)|Podepsaný držitelem, číselné hodnoty a [integrální](integral-types-table.md)||  
|[short](short.md)|Podepsaný držitelem, číselné hodnoty a [integrální](integral-types-table.md)||  
|[struct](struct.md)|Struktury definované uživatelem||  
|[uint](uint.md)|Bez znaménka, číselné hodnoty a [integrální](integral-types-table.md)|U nebo u|  
|[ulong](ulong.md)|Bez znaménka, číselné hodnoty a [integrální](integral-types-table.md)|UL, Ul, uL, ul, LU, Lu, logická jednotka nebo logická jednotka|  
|[ushort](ushort.md)|Bez znaménka, číselné hodnoty a [integrální](integral-types-table.md)||  

## <a name="remarks"></a>Poznámky

Použijete příponou podle typu k určení typu číselný literál. Příklad:

```csharp
decimal a = 0.1M;
```

Pokud [celočíselný literál číselné](/dotnet/csharp/language-reference/language-specification/lexical-structure#integer-literals) nemá žádné příponu má první z těchto typů, ve kterých může být reprezentována jeho hodnota: `int`, `uint`, `long`, `ulong`.

Pokud [reálné číselný literál](/dotnet/csharp/language-reference/language-specification/lexical-structure#real-literals) nemá žádné příponu, je typu `double`.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Referenční tabulky pro typy](reference-tables-for-types.md)
- [Tabulka výchozích hodnot](default-values-table.md)
- [Typy hodnot](value-types.md)
- [Tabulka formátování číselných výsledků](formatting-numeric-results-table.md)
