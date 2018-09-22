---
title: 'Výrazy lambda: Klíčové slovo fun (F#)'
description: 'Další informace o použití F # "zábavu" – klíčové slovo k definování výraz lambda, který je anonymní funkce.'
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580743"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Výrazy lambda: Klíčové slovo fun (F#)

`fun` – Klíčové slovo se používá k definování výraz lambda, to znamená, anonymní funkce.

## <a name="syntax"></a>Syntaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Poznámky

*Seznam parametrů* se obvykle skládá z názvů a volitelně typy parametrů. Obecně platí *seznam parametrů* může skládat z jakékoli vzorky F #. Úplný seznam možných vzory, naleznete v tématu [porovnávání vzorů](../pattern-matching.md). Seznam platných parametrů zahrnují následující příklady.

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

*Výraz* tělo funkce posledního výrazu z nich generuje návratovou hodnotu. Příklady výrazů lambda platné patří:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Používání výrazů lambda

Výrazy lambda jsou zvláště užitečné, pokud chcete provádět operace v seznamu nebo z jiné kolekce a chcete se vyhnout nadbytečné práci spojené se definice funkce. Řada funkcí knihovny F # přebírají hodnoty funkce jako argumenty a může být zvláště praktické použití lambda výrazů v těchto případech. Následující kód platí pro prvky seznamu výraz lambda. V takovém případě anonymní funkce přičte 1 k každý prvek seznamu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
