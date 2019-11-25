---
title: Indexované vlastnosti
description: Přečtěte si o indexovaných vlastnostech v F#, které umožňují přístup k seřazeným datům typu pole.
ms.date: 11/04/2019
ms.openlocfilehash: f6cf3bfa737d2bf458e379594be5884696cee3e1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976600"
---
# <a name="indexed-properties"></a>Indexované vlastnosti

Při definování třídy, která je abstraktní nad seřazenými daty, může být někdy užitečná k poskytnutí indexovaného přístupu k těmto datům bez odhalení základní implementace. To se provádí s členem `Item`.

## <a name="syntax"></a>Syntaxe

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Poznámky

Formuláře předchozí syntaxe ukazují, jak definovat indexované vlastnosti, které mají jak `get`, tak `set` metoda, mají pouze `get` metodu nebo mají pouze `set` metodu. Lze také kombinovat jak syntaxi zobrazenou pouze pro příkaz Get, syntaxi zobrazenou pouze pro sadu a vytvořit vlastnost, která má obě metody Get a set. Tato druhá forma umožňuje umístit různé modifikátory a atributy dostupnosti do metod get a set.

Pomocí názvu `Item`kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost. *Výchozí indexovaná vlastnost* je vlastnost, ke které můžete přistupovat pomocí syntaxe typu pole v instanci objektu. Například pokud `o` je objekt typu, který definuje tuto vlastnost, `o.[index]` syntaxe se používá pro přístup k vlastnosti.

Syntaxe pro přístup k jiné než výchozí indexované vlastnosti je poskytnout název vlastnosti a indexu v závorkách, stejně jako regulární člen. Například pokud je vlastnost na `o` volána `Ordinal`, zapíšete `o.Ordinal(index)` pro přístup k ní.

Bez ohledu na to, který formulář použijete, byste měli vždy použít formulář curryfikované pro metodu set pro indexovanou vlastnost. Informace o funkcích curryfikované najdete v tématu [Functions](../functions/index.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje definici a použití výchozích a nevýchozích indexovaných vlastností, které mají metody Get a set.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Výstup

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Indexované vlastnosti s více hodnotami indexu

Indexované vlastnosti můžou mít víc než jednu hodnotu indexu. V takovém případě jsou hodnoty odděleny čárkami při použití vlastnosti. Metoda set v takové vlastnosti musí mít dva argumenty curryfikované, první z nich je řazená kolekce členů obsahující klíče a druhá z nich je hodnota, kterou chcete nastavit.

Následující kód demonstruje použití indexované vlastnosti s více hodnotami indexu.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member _.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
