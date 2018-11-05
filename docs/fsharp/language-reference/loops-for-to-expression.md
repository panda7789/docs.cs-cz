---
title: 'Smyčky: Výraz for...to (F#)'
description: Naleznete v tématu Jak F# for... výraz se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 8160fd30c4f3afe8bb6b58f468802ef1c0ef32ee
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43800466"
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
- [Smyčky: `for...in` výraz](loops-for-in-expression.md)
- [Smyčky: `while...do` výraz](loops-while-do-expression.md)
