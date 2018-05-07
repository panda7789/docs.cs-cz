---
title: Logické operátory (F#)
description: 'Další informace o logické operátory, které jsou k dispozici v programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="boolean-operators"></a>Logické operátory

Toto téma popisuje podporu logické operátory v jazyce F #.


## <a name="summary-of-boolean-operators"></a>Souhrn logické operátory
Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F #. Je jediným typem podporuje tyto operátory `bool` typu.

|Operátor|Popis|
|--------|-----------|
|`not`|Logická negace|
|<code>&#124;&#124;</code>|Logická hodnota nebo|
|`&&`|Logická hodnota a|

Logická hodnota a a nebo operátory provést *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocování výrazu na pravé straně operátoru jenom v případě, že je nutné určit celkový výsledek výrazu. Druhý výraz `&&` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `true`; druhý výraz `||` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `false`.

## <a name="see-also"></a>Viz také
[Bitové operátory](bitwise-operators.md)

[Aritmetické operátory](arithmetic-operators.md)

[Referenční dokumentace symbolů a operátorů](index.md)
