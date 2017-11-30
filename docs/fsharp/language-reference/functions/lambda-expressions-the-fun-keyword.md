---
title: "Výrazy lambda: Klíčové slovo fun (F#)"
description: "Naučte se používat k definování výrazu lambda, což je anonymní funkce klíčového} zábavu\"F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Výrazy lambda: Klíčové slovo fun (F#)

`fun` – Klíčové slovo se používá k definování výrazu lambda, který je anonymní funkce.


## <a name="syntax"></a>Syntaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Poznámky
*Seznam parametrů* se obvykle skládá z názvy a volitelně typy parametrů. Obecně platí *seznam parametrů* může být složený z jakékoli vzory F #. Úplný seznam možných vzory, najdete v části [porovnávání vzorů](../pattern-matching.md). Seznam platné parametry patří následující příklady.

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

*Výraz* tělo funkce, poslední výraz, který generuje návratovou hodnotu. Příklady výrazů lambda platný zahrnují následující:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a>Používání výrazů lambda
Lambda – výrazy jsou zvláště užitečné, pokud chcete provádět operace v seznamu nebo jiné kolekci a chcete vyhnout další práci definice funkce. Mnoho funkcí knihovny F # trvat hodnoty funkce jako argumenty, a může být obzvláště vhodnější pomocí výrazu lambda v těchto případech. Následující kód vztahuje k elementům seznamu výrazu lambda. V takovém případě anonymní funkce přidá 1 každý element seznamu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a>Viz také
[Funkce](index.md)
