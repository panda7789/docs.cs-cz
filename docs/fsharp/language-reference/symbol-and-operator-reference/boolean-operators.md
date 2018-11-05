---
title: Logické operátory (F#)
description: Další informace o logické operátory, které jsou k dispozici v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45638477"
---
# <a name="boolean-operators"></a>Logické operátory

Toto téma popisuje podporu pro logické operátory v jazyce F#.

## <a name="summary-of-boolean-operators"></a>Souhrnné informace o logické operátory

Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F#. Je jediným typem podporuje tyto operátory `bool` typu.

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
