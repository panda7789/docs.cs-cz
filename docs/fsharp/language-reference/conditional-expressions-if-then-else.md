---
title: 'Podmíněné výrazy: if... then... else'
description: Další informace o zápisu podmíněné výrazy F# provést různými větvemi kódu.
ms.date: 05/16/2016
ms.openlocfilehash: eade8c20c1b62a2e9a54700550d832798308f368
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766035"
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