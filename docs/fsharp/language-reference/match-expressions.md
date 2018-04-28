---
title: 'Výrazy shody (F #)'
description: 'Zjistěte, jak výrazu shody F # poskytuje větvení ovládací prvek, který je založena na porovnávání výrazu sadu vzory.'
author: cartermp
ms.author: phcart
ms.date: 04/19/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f6930f782384464f0d44b205ea77cbaf43898213
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="match-expressions"></a>Výrazy shody

`match` Výraz poskytuje větvení ovládací prvek, který je založena na porovnávání výrazu sadu vzory.

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

Výrazy odpovídající vzor umožňují komplexní vytvoření větve na základě porovnání výraz testovací sadu vzory. V `match` výrazu *testovací výraz* se porovná se každý vzor zapnout, a pokud je nalezena shoda, odpovídající *výsledek výrazu* vyhodnotí a výsledná hodnota je Vrátí hodnotu výrazu shody.

Funkce uvedené v předchozí syntaxe pro porovnávání je v které vzor odpovídající provádí okamžitě v argumentu výrazu lambda. Funkce uvedené v předchozí syntaxe pro porovnávání je stejná jako následující.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Další informace o výrazy lambda najdete v tématu [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md).

Celou sadu vzory by mělo zahrnovat všechny možné shody vstupní proměnné. Často používají vzorec zástupný znak (`_`) jako poslední vzorek tak, aby odpovídaly všechny dříve neodpovídající vstupní hodnoty.

Následující kód ukazuje některé způsoby, ve kterém `match` použit výraz. Odkaz a příklady možných vzorů, které lze použít, najdete v části [porovnávání vzorů](pattern-matching.md).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Chrání vzory

Můžete použít `when` klauzule zadejte další podmínky, které proměnnou, musí vyhovovat tak, aby odpovídaly vzor. Tato klauzule odkazuje jako *ochrana*. Následující výraz `when` – klíčové slovo, nebude hodnocen pouze tehdy, pokud shoda se se vzorem přidružené k této ochrana.

Následující příklad ukazuje použití ochranu k určení číselný rozsah pro proměnné vzor. Všimněte si, že více podmínek jsou spojeny použitím logické operátory.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Všimněte si, že vzhledem k tomu, že hodnoty než literály nelze použít ve vzoru, musíte použít `when` klauzule, pokud máte k porovnání některé části vstup pro hodnotu. To je ukázáno v následujícím kódu:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Všimněte si, že když union vzor je předmětem ochranu, ochranného zařízení aplikuje na **všechny** schémat, ne jenom tu poslední. Například následující kód, ochranného zařízení uděleno `when a > 12` platí pro obě `A a` a `B a`:

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

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka F#](index.md)  
[Aktivní vzory](active-patterns.md)  
[Porovnávání vzorů](pattern-matching.md)  
