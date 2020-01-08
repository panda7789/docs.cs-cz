---
title: Formátování číselných výsledků tabulky C# – referenční informace
ms.custom: seodec18
description: Informace o C# standardních řetězcích číselného formátu
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 853faf481e546f2980d799d5daf50a14c608c052
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345474"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Tabulka formátování číselných výsledkůC# (referenční)

V následující tabulce jsou uvedeny podporované specifikátory formátu pro formátování číselných výsledků. Formátovaný výsledek v posledním sloupci odpovídá <xref:System.Globalization.CultureInfo>"en-US".

|Specifikátor formátu|Popis|Příklady|Výsledek|  
|----------------------|-----------------|--------------|------------|  
|C nebo c|Měna|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|\\$2,50<br /><br /> (\\$2,50)|  
|D nebo d|Desetinné číslo|`string s = $"{25:D5}";`|00025|  
|E nebo e|Exponenciální|`string s = $"{250000:E2}";`|2.50 e + 005|  
|F nebo f|Pevná desetinná čárka|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2,50<br /><br /> 3|  
|G nebo g|Obecné|`string s = $"{2.5:G}";`|2,5|  
|N nebo n|Čísla|`string s = $"{2500000:N}";`|2,500,000.00|  
|P nebo p|Procento|`string s = $"{0.25:P}";`|25,00 %|  
|R nebo r|Zpáteční převod|`string s = $"{2.5:R}";`|2,5|  
|X nebo x|Šestnáctková hodnota|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>Poznámky

Použijete specifikátor formátu pro vytvoření formátovacího řetězce. Formátovací řetězec má následující tvar: `Axx`, kde

- `A` je specifikátor formátu, který řídí typ formátování použité pro číselnou hodnotu.
- `xx` je specifikátor přesnosti, který má vliv na počet číslic ve formátovaných výstupech. Hodnota specifikátoru přesnosti rozsahu od 0 do 99.

Specifikátory desítkového formátu ("D" nebo "d") a šestnáctkové hodnoty ("X" nebo "x") jsou podporovány pouze pro integrální typy. Specifikátor formátu Round-Trip ("R" nebo "r") je podporován pouze pro typy <xref:System.Single>, <xref:System.Double>a <xref:System.Numerics.BigInteger>.

Standardní řetězce číselného formátu jsou podporovány v:

- Některá přetížení metody `ToString` pro všechny číselné typy. Můžete například zadejte řetězec číselného formátu do <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.

- [Funkce složeného formátování](../../../standard/base-types/composite-formatting.md).NET, která je podporována metodou <xref:System.String.Format%2A?displayProperty=nameWithType>, například.

- [Interpolované řetězce](../tokens/interpolated.md).

Další informace naleznete v tématu [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
- [Složené formátování](../../../standard/base-types/composite-formatting.md)
- [Interpolace řetězců](../tokens/interpolated.md)
- [string](../builtin-types/reference-types.md)
