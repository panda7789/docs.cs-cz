---
title: Logické operátory (F#)
description: 'Další informace o logické operátory, které jsou k dispozici v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44364349"
---
# <a name="boolean-operators"></a>Logické operátory

Toto téma popisuje podporu pro logické operátory v jazyce F #.

## <a name="summary-of-boolean-operators"></a>Souhrnné informace o logické operátory

Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F #. Je jediným typem podporuje tyto operátory `bool` typu.

|Operátor|Popis|
|--------|-----------|
|`not`|Logická negace|
|<code>&#124;&#124;</code>|Logický OR|
|`&&`|Logická a|

Logické a a operátory provádějí nebo *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocení výrazu na pravé straně operátoru pouze v případě, že je potřeba určit celkový výsledek výrazu. Druhý výraz `&&` operátor je vyhodnocen pouze v případě, že první výraz je vyhodnocen jako `true`; druhý výraz `||` operátor je vyhodnocen pouze v případě, že první výraz je vyhodnocen jako `false`.

## <a name="see-also"></a>Viz také:

- [Bitové operátory](bitwise-operators.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Referenční dokumentace symbolů a operátorů](index.md)
