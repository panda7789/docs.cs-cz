---
title: 'Podmíněné výrazy: if... pak... ostatních'
description: Naučte se psát podmíněné výrazy v F# pro spouštění různých větví kódu.
ms.date: 05/16/2016
ms.openlocfilehash: d9763f37cd9170c42e968282b54a3ce925e92591
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083023"
---
# <a name="conditional-expressions-ifthenelse"></a>Podmíněné výrazy:`if...then...else`

`if...then...else` Výraz spustí různé větve kódu a také se vyhodnotí na jinou hodnotu v závislosti na daném logickém výrazu.

## <a name="syntax"></a>Syntaxe

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je *Výraz1* spuštěna při vyhodnocování logického výrazu. v `true`opačném případě je možné spustit *Výraz2* .

Na `if...then...else` rozdíl od jiných jazyků konstrukce je výraz, nikoli příkaz. To znamená, že vytvoří hodnotu, což je hodnota posledního výrazu ve větvi, která se spustí. Typy hodnot vytvořených v každé větvi se musí shodovat. Pokud není k dispozici `else` žádná explicitní větev, je `unit`její typ. Proto pokud je typ `then` větve libovolný typ jiný než `unit` `else` , musí existovat větev se stejným návratovým typem. Při zřetězení `if...then...else` výrazů můžete místo `else if`použít klíčové slovo `elif` , které je ekvivalentní.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `if...then...else` výraz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```console
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
