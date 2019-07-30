---
title: 'Smyčky: Výraz for...to'
description: Podívejte se, F# jak pro... na výraz se používá k iterování ve smyčce přes rozsah hodnot proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626622"
---
# <a name="loops-forto-expression"></a>Smyčky: Výraz for...to

`for...to` Výraz se používá k iterování smyčky v rámci rozsahu hodnot proměnné smyčky.

## <a name="syntax"></a>Syntaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Poznámky

Typ identifikátoru je odvozen od typu výrazů *zahájení* a *dokončení* . Typy pro tyto výrazy musí být 32 celých čísel.

I když je technicky výraz `for...to` , je více podobný jako tradiční příkaz v imperativním programovacím jazyce. Návratový typ pro *výraz body* musí být `unit`. Následující příklady znázorňují různá použití `for...to` výrazu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

Výstup předchozího kódu vypadá takto.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky `for...in`Vyjádření](loops-for-in-expression.md)
- [Smyčky `while...do`Vyjádření](loops-while-do-expression.md)
