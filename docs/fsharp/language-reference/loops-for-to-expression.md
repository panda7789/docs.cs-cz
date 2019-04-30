---
title: 'Smyčky: Výraz for...to'
description: V tématu Jak F# for... výraz se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 041e98fa4bcc140aa3cd699f6ed35bf52c8b4175
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904030"
---
# <a name="loops-forto-expression"></a>Smyčky: Výraz for...to

`for...to` Výrazu se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.

## <a name="syntax"></a>Syntaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Poznámky

Typ identifikátoru je odvozen z typu *start* a *Dokončit* výrazy. Typy pro tyto výrazy musí být 32bitová celá čísla.

I když technicky výraz `for...to` je více než tradiční výroky imperativní programovací jazyk. Návratový typ *výraz těla* musí být `unit`. Následující příklady znázorňují různé způsoby použití `for...to` výrazu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Výstup předchozího kódu vypadá takto.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky: `for...in` Výraz](loops-for-in-expression.md)
- [Smyčky: `while...do` Výraz](loops-while-do-expression.md)