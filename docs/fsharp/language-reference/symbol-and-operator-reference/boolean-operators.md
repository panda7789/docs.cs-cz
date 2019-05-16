---
title: Logické operátory
description: Další informace o logické operátory, které jsou k dispozici v F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: ad4bdd1121389f7e280647dbe0c4d0098ffb17df
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641903"
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
