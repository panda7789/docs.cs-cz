---
title: Logické operátory
description: Další informace o logické operátory, které jsou k dispozici v F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612735"
---
# <a name="boolean-operators"></a>Logické operátory

Toto téma popisuje podporu pro logické operátory ve F# jazyka.

## <a name="summary-of-boolean-operators"></a>Souhrnné informace o logické operátory

Následující tabulka shrnuje logické operátory, které jsou k dispozici v F# jazyka. Je jediným typem podporuje tyto operátory `bool` typu.

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