---
title: Bitové operátory (F#)
description: 'Další informace o bitové operátory, které jsou k dispozici v programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: bc653ae7ff6dd6bc2c269aaba344f073df1fb708
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565324"
---
# <a name="bitwise-operators"></a>Bitové operátory

Toto téma popisuje bitové operátory, které jsou k dispozici v jazyce F #.

## <a name="summary-of-bitwise-operators"></a>Souhrn bitové operátory
Následující tabulka popisuje bitové operátory, které jsou podporovány pro nezabalený integrální typy v jazyce F #.

|Operátor|Poznámky|
|--------|-----|
|`&&&`|Bitový operátor AND. BITS ve výsledku mít hodnotu 1, pokud odpovídající bity v obou operandy zdroje jsou 1.|
|<code>&#124;&#124;&#124;</code>|Bitový operátor OR. Služba BITS ve výsledku mít hodnotu 1, pokud buď odpovídající bitů ve zdroji jsou operandy 1.|
|`^^^`|Bitový exkluzivní operátor OR. BITS ve výsledku mít hodnotu 1, pokud bitů operandy zdroje mají nerovné hodnoty.|
|`~~~`|Operátor bitovou negaci. Toto je unární operátor a vytváří výsledek, ve kterém všechny 0 bitů operand zdroje se převedou na 1 bits a všechny 1 bits se převedou na 0 bits.|
|`<<<`|Bitový operátor posunutí doleva. Výsledkem je, že první operand s bity zapuštěno podle počtu bitů Druhý operand doleva. Nejsou BITS přesunout mimo nejvýznamnějších pozice otočen do nejméně významný pozici. Nejméně významný bits se vyplní nul. Typ druhý argument je `int32`.|
|`>>>`|Bitový operátor posunutí doprava. Výsledkem je první operand s bity zapuštěno právo podle počtu bitů Druhý operand. Nejsou BITS přesunout mimo nejméně významný pozice otočen do nejvýznamnějších pozici. Pro typy bez znaménka se vyplní nejvýznamnějších bity s nulami. Pro typy signed se s těmi, které vyplní nejvýznamnějších bits. Typ druhý argument je `int32`.|

Bitové operátory můžete použít následující typy: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, a `unativeint`.

## <a name="see-also"></a>Viz také
[Referenční dokumentace symbolů a operátorů](index.md)

[Aritmetické operátory](arithmetic-operators.md)

[Logické operátory](boolean-operators.md)

