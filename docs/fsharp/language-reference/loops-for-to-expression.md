---
title: 'Smyčky: Výraz for...to (F#)'
description: 'V tématu Jak for. F #.. výrazu je použít k iteraci ve smyčce přes rozsah hodnot proměnné smyčky.'
ms.date: 05/16/2016
ms.openlocfilehash: 841c7d557abc11e0253cb87ab8081cc77671b44b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563399"
---
# <a name="loops-forto-expression"></a>Smyčky: Výraz for...to

`for...to` Výraz se používá k iterace ve smyčce v rozsahu hodnot proměnné smyčky.


## <a name="syntax"></a>Syntaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Poznámky
Typ identifikátoru je odvozen z typu *spustit* a *Dokončit* výrazy. Typy pro tyto výrazy musí být 32bitová celá čísla.

I když technicky výraz `for...to` je více než tradiční příkaz v imperativní programovací jazyk. Návratový typ pro *textu výraz* musí být `unit`. Následující příklady ukazují použití různých `for...to` výraz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Výstup předchozího kódu vypadá takto.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Smyčky: `for...in` výraz](loops-for-in-expression.md)

[Smyčky: `while...do` výraz](loops-while-do-expression.md)
