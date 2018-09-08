---
title: 'Podmíněné výrazy: if... then...else (F#)'
description: 'Další informace o zápisu podmíněné výrazy v jazyce F # ke spuštění různými větvemi kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177598"
---
# <a name="conditional-expressions-ifthenelse"></a>Podmíněné výrazy: `if...then...else`

`if...then...else` Výraz spouští různými větvemi kódu a také vyhodnotí na jinou hodnotu v závislosti na logický výraz zadaný.

## <a name="syntax"></a>Syntaxe

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *expression1* spustí, když logický výraz je vyhodnocen jako `true`; v opačném případě *expression2* běží.

Na rozdíl od v jiných jazycích `if...then...else` konstruktor je výraz, ne příkaz. To znamená, že vytvoří hodnotu, což je hodnota posledního výrazu ve větvi, který se spustí. Typy hodnot v jednotlivých větví se musí shodovat. Pokud neexistuje žádné explicitní `else` větev, jeho typ je `unit`. Proto pokud typ `then` větev je libovolného typu jiného než `unit`, musí existovat `else` větev s vracet hodnotu stejného typu. Při zřetězení `if...then...else` výrazů společně, můžete použít klíčové slovo `elif` místo `else if`; jsou ekvivalentní.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `if...then...else` výrazu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
