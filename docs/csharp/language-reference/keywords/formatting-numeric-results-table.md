---
title: Tabulka formátování číselných výsledků (referenční dokumentace jazyka C#)
description: Další informace o řetězcích standardního číselného formátu jazyka C#
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 6f1cb5b49139cf9661e678cfc0ecc884a2749622
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863699"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Tabulka formátování číselných výsledků (referenční dokumentace jazyka C#)

Následující tabulka uvádí podporované specifikátorů pro formátování číselných výsledků. Formátovaný výsledek v posledním sloupci odpovídá "en US" <xref:System.Globalization.CultureInfo>.

|Specifikátor formátu|Popis|Příklady|Výsledek|  
|----------------------|-----------------|--------------|------------|  
|C nebo c|Měna|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|$2.50<br /><br /> ($2.50)|  
|D nebo d|Desetinné číslo|`string s = $"{25:D5}";`|00025|  
|E nebo e|Exponenciální|`string s = $"{250000:E2}";`|2.50E + 005|  
|F nebo f|Pevná desetinná čárka|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2.50<br /><br /> 3|  
|G nebo g|Obecné|`string s = $"{2.5:G}";`|2.5|  
|N nebo n|Číselné|`string s = $"{2500000:N}";`|2,500,000.00|  
|P nebo p|Procento|`string s = $"{0.25:P}";`|% 25,00|  
|R nebo r|Zpáteční převod|`string s = $"{2.5:R}";`|2.5|  
|X nebo x|Šestnáctková hodnota|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|DM<br /><br /> FFFF|  

## <a name="remarks"></a>Poznámky

Použití specifikátoru formátu pro vytvoření řetězce formátu. Formátovací řetězec má následující formát: `Axx`, kde

- `A` je specifikátor formátu, který určuje typ formátování použité pro číselné hodnoty.
- `xx` je specifikátor přesnosti, který ovlivňuje počet číslic v formátovaný výstup. Hodnota rozsahy specifikátor přesnosti od 0 do 99.

Desetinné číslo ("D" nebo "d") a šestnáctková ("X" nebo "x") formátu specifikátory jsou podporována pouze pro integrální typy. Operace round-trip specifikátor formátu ("R" nebo "r") je podporován pouze pro <xref:System.Single>, <xref:System.Double>, a <xref:System.Numerics.BigInteger> typy.

Řetězce standardního číselného formátu jsou podporovány:

- Některá přetížení `ToString` metoda všechny číselné typy. Například můžete zadat číselný formátovací řetězec <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.

- .NET [funkci složeného formátování](../../../standard/base-types/composite-formatting.md), která je podporována <xref:System.String.Format%2A?displayProperty=nameWithType> metody, například.

- [Interpolované řetězce](../tokens/interpolated.md).

Další informace najdete v tématu [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Referenční tabulky pro typy](reference-tables-for-types.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
- [Složené formátování](../../../standard/base-types/composite-formatting.md)
- [Interpolace řetězců](../tokens/interpolated.md)
- [string](string.md)
