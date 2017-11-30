---
title: "Smyčky: Výraz for...to (F#)"
description: "V tématu Jak for. F #.. výrazu je použít k iteraci ve smyčce přes rozsah hodnot proměnné smyčky."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
[Referenční dokumentace jazyka F #](index.md)

[Smyčky: `for...in` výraz](loops-for-in-expression.md)

[Smyčky: `while...do` výraz](loops-while-do-expression.md)
