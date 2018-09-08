---
title: 'Výrazy shody (F #)'
description: 'Zjistěte, jak výrazu porovnání F # poskytuje větvení ovládací prvek, který je založena na porovnávání výrazů sadu vzorů.'
ms.date: 04/19/2018
ms.openlocfilehash: e4cb82f20fe82bff562736557c2346562c557f59
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221841"
---
# <a name="match-expressions"></a>Výrazy shody

`match` Výraz poskytuje větvení ovládací prvek, který je založena na porovnávání výrazů sadu vzorů.

## <a name="syntax"></a>Syntaxe

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>Poznámky

Vzor odpovídající výrazy umožňují na základě porovnání výrazu testovací sadu vzorů komplexní větvení. V `match` výrazu, *výrazu testu* se porovná se každý vzorek, v důsledku, a když je nalezena shoda, odpovídající *výsledek výrazu* je vyhodnocen a je výsledná hodnota Vrátí jako hodnota výrazu match.

Porovnávání vzorů funkce je znázorněno v předchozí syntaxi je výraz lambda, který vzoru porovnávání je okamžitě na argumentu provedeno. Porovnávání vzorů funkce je znázorněno v předchozí syntaxi je ekvivalentní následujícímu zápisu.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Další informace o výrazech lambda naleznete v tématu [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md).

Možných shod je vstupní proměnná by měla zahrnovat celou sadu vzorů. Často, použijte vzor zástupných znaků (`_`) jako poslední vzorek tak, aby odpovídaly všechny dříve bezkonkurenční vstupní hodnoty.

Následující kód ukazuje několik způsobů jak, ve kterém `match` výraz je použit. Odkaz a příklady možných vzory, které lze použít, naleznete v tématu [porovnávání vzorů](pattern-matching.md).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Výrazy guard na vzory

Můžete použít `when` klauzule zadat další podmínku, která proměnná musí splňovat odpovídající vzorku. Tato klauzule se označuje jako *guard*. Následující výraz `when` – klíčové slovo není vyhodnocen, pokud není shoda vzoru přidružené k této guard.

Následující příklad ukazuje použití ochranného zařízení můžete určit číselný rozsah pro vzor proměnné. Všimněte si, že jsou více podmínek kombinovat pomocí logické operátory.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Mějte na paměti, protože hodnoty jiné než literály nelze použít ve vzoru, je nutné použít `when` klauzule, pokud máte k porovnání některá část vstup podle dokumentu hodnotu. To je ukázáno v následujícím kódu:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Všimněte si, že pokud vzor sjednocení se bude vztahovat ochranu, ochranného zařízení platí pro **všechny** vzorů, ne jenom poslední z nich. Mějme například následující kód, ochranného zařízení `when a > 12` platí jak `A a` a `B a`:

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)  
- [Aktivní vzory](active-patterns.md)  
- [Porovnávání vzorů](pattern-matching.md)  
