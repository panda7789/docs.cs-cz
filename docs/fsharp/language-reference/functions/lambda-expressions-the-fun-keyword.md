---
title: 'Výrazy lambda: Klíčové slovo fun'
description: Naučte se používat F# klíčové slovo fun k definování výrazu lambda, který je anonymní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630660"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Výrazy lambda: Klíčové slovo Fun (F#)

`fun` Klíčové slovo slouží k definování výrazu lambda, tedy anonymní funkce.

## <a name="syntax"></a>Syntaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Poznámky

*Seznam parametrů* se obvykle skládá z názvů a volitelně typů parametrů. Obecně platí, že *seznam parametrů* se může skládat z libovolného F# vzoru. Úplný seznam možných vzorů naleznete v tématu [porovnávání vzorů](../pattern-matching.md). K seznamům platných parametrů patří následující příklady.

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

*Výraz* je tělo funkce, poslední výraz, který generuje návratovou hodnotu. Příklady platných výrazů lambda jsou následující:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Používání výrazů lambda

Výrazy lambda jsou obzvláště užitečné, pokud chcete provádět operace na seznamu nebo jiné kolekci a chcete se vyhnout nadbytečné práci s definováním funkce. Mnoho F# funkcí knihovny přijímá hodnoty funkcí jako argumenty a v těchto případech může být obzvláště užitečná pro použití výrazu lambda. Následující kód použije výraz lambda na prvky seznamu. V tomto případě anonymní funkce přidá 1 do každého prvku seznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
