---
title: "Podmíněné výrazy: if... then...else (F#)"
description: "Další informace o zápisu podmíněné výrazy v jazyce F # k provedení různých pobočkách kódu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 5823e46cd13053fcd31f94f2d79d1f7470ca5118
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2018
---
# <a name="conditional-expressions-ifthenelse"></a>Podmíněné výrazy: `if...then...else`

`if...then...else` Výraz spouští různé větví kódu a také vyhodnocuje na jinou hodnotu, v závislosti na logický výraz zadaný.


## <a name="syntax"></a>Syntaxe

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Poznámky
V předchozích syntaxi *expression1* se spustí v případě, že se vyhodnocuje logický výraz `true`, jinak hodnota *Výraz2* běží.

Na rozdíl od v dalších jazycích `if...then...else` konstrukce je výraz, nikoli příkaz. To znamená, že vyvolá hodnotu, která je hodnota poslední výrazu v větve, které provádí. Typy hodnot vytvořil v každé větve se musí shodovat. Pokud neexistuje žádné explicitní `else` větve, je její typ `unit`. Proto pokud typ `then` větve je žádný typ, než `unit`, musí být `else` firemní pobočky s stejné návratovým typem. Když řetězení `if...then...else` výrazy společně, můžete použít klíčové slovo `elif` místo `else if`; jsou ekvivalentní.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak používat `if...then...else` výraz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

