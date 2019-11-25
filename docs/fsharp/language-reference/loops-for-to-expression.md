---
title: 'Smyčky: Výraz for...to'
description: Podívejte se, F# jak pro... na výraz se používá k iterování ve smyčce přes rozsah hodnot proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283905"
---
# <a name="loops-forto-expression"></a>Smyčky: Výraz for...to

Výraz `for...to` slouží k iterování ve smyčce přes rozsah hodnot proměnné smyčky.

## <a name="syntax"></a>Syntaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Poznámky

Typ identifikátoru je odvozen od typu výrazů *zahájení* a *dokončení* . Typy pro tyto výrazy musí být 32 celých čísel.

I když technicky výraz, `for...to` je více podobně jako tradiční příkaz v imperativním programovacím jazyce. Návratový typ pro *tělo-výrazu* musí být `unit`. Následující příklady znázorňují různá použití výrazu `for...to`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Výstup předchozího kódu vypadá takto.

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky: výraz `for...in`](loops-for-in-expression.md)
- [Smyčky: výraz `while...do`](loops-while-do-expression.md)
