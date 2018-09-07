---
title: Bitové operátory (F#)
description: 'Další informace o bitové operátory, které jsou k dispozici v programovacím jazyce F #.'
ms.date: 07/20/2018
ms.openlocfilehash: ed76fcf5f9c569a2f288cf260e99dc29fd65ef3b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44077821"
---
# <a name="bitwise-operators"></a>Bitové operátory

Toto téma popisuje bitové operátory, které jsou k dispozici v jazyce F #.

## <a name="summary-of-bitwise-operators"></a>Souhrnné informace o bitové operátory

Následující tabulka popisuje bitové operátory, které jsou podporovány pro bez unboxingu integrální typy v jazyce F #.

|Operátor|Poznámky|
|--------|-----|
|`&&&`|Bitový operátor AND. Bitů ve výsledku mít hodnotu 1 a pouze v případě odpovídající bitů v obou zdrojové operandy jsou od 1.|
|<code>&#124;&#124;&#124;</code>|Bitový operátor OR. Bitů ve výsledku mít hodnotu 1, pokud odpovídající bitů ve zdroji operandy jsou od 1.|
|`^^^`|Bitový exkluzivní operátor OR. Bitů ve výsledku mít hodnotu 1 a pouze v případě bitů v zdrojové operandy mají nerovnost hodnoty.|
|`~~~`|Operátor bitová negace. Toto je unární operátor a vytváří výsledek, ve kterém všechny bity 0 v operandu zdroje jsou převedeny na bitů s hodnotou 1 a všechny bity 1 budou převedeny na 0 bitů.|
|`<<<`|Bitový operátor posunutí doleva. Výsledkem je, že prvního operandu s bity posunuty vlevo o počet bitů ve druhém operandu. Posunuly pozice nejvýznamnější bity nejsou do nejméně významnou pozice otočen. Nejméně významná bity jsou doplněny nulami. Typ druhého argumentu je `int32`.|
|`>>>`|Bitový operátor posunu vpravo. Výsledkem je první operand se bitů doprava o počet bitů ve druhém operandu. Posunuly pozice nejméně významných bitů nejsou do nejvýznamnější pozice otočen. U typů bez znaménka nejvýznamnější bity jsou doplněny nulami. U typů se zápornými hodnotami se znaménkem nejvýznamnější bity jsou doplněny těmi. Typ druhého argumentu je `int32`.|

Následující typy je možné s bitové operátory: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, a `unativeint`.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace symbolů a operátorů](index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Logické operátory](boolean-operators.md)
