---
title: Výrazy shody
description: Přečtěte si F# , jak výraz shody poskytuje řízení větvení, které je založené na porovnání výrazu se sadou vzorů.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627610"
---
# <a name="match-expressions"></a>Výrazy shody

`match` Výraz poskytuje řízení větvení, které je založeno na porovnání výrazu se sadou vzorů.

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

Výrazy vyhovující vzorům umožňují složitou větev na základě porovnání testovacího výrazu se sadou vzorů. Ve výrazu je *výraz testu* porovnán s každým vzorem a když je nalezena shoda, je vyhodnocen odpovídající *výraz Result* a výsledná hodnota je vrácena jako hodnota výrazu Match. `match`

Funkce porovnávání vzorů zobrazená v předchozí syntaxi je výraz lambda, ve kterém se porovnávání vzorů provádí okamžitě na argumentu. Funkce porovnávání vzorů zobrazená v předchozí syntaxi je ekvivalentní následujícímu.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Další informace o výrazech lambda naleznete v [tématu lambda Expressions: `fun` Klíčové slovo](./functions/lambda-expressions-the-fun-keyword.md).

Celá sada vzorů by měla pokrývat všechny možné shody vstupní proměnné. Často se používá jako poslední vzorek zástupný znak`_`(), který porovnává všechny dříve neshodné vstupní hodnoty.

Následující kód ilustruje některé způsoby `match` použití výrazu. Odkaz a příklady všech možných vzorů, které lze použít, naleznete v tématu [porovnávání vzorů](pattern-matching.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Guard na vzorcích

`when` Klauzuli můžete použít k určení další podmínky, kterou musí proměnná splňovat, aby odpovídala vzoru. Taková klauzule se označuje jako *Guard*. Výraz následující `when` za klíčovým slovem není vyhodnocen, pokud není provedeno porovnávání vzoru přidruženého k tomuto Guard.

Následující příklad ilustruje použití Guard k určení číselného rozsahu pro vzorec proměnné. Všimněte si, že několik podmínek je kombinováno pomocí logických operátorů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Všimněte si, že vzhledem k tomu, že jiné hodnoty než literály nelze použít ve vzoru, `when` je nutné použít klauzuli, pokud je nutné porovnat část vstupu s hodnotou. Zobrazuje se v následujícím kódu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Všimněte si, že když je vzor sjednocení kryt ochranou, vztahuje se ochrana na **všechny** vzory, nikoli jenom na poslední z nich. Například s ohledem na následující kód platí, že Guard `when a > 12` platí pro `B a`i `A a` :

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
