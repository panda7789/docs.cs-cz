---
title: Indexované vlastnosti
description: Další informace o indexované vlastnosti v F#, které umožňují pro přístup jako pole k datům seřazené.
ms.date: 10/17/2018
ms.openlocfilehash: 7fc8f46e029255c6ed985a43b92c8f7c2908c428
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489487"
---
# <a name="indexed-properties"></a>Indexované vlastnosti

Při definování třídy, který získává přes seřazených dat, může být někdy užitečné poskytnout indexovaný přístup k těmto datům bez vystavení se základní implementací. Používá se k tomu `Item` člena.

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

Formy syntaxe předchozí ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metodu, mají `get` metoda pouze, nebo mít `set` pouze metody. Můžete také zkombinovat obojí tomu syntaxe uvedená jenom příkaz get a syntaxi pro sadu pouze a vytvoří vlastnost, která má get a set. Tento druhý formulář umožňuje umístit různou přístupností. modifikátorů a vlastností atributy na get a set metod.

Pomocí názvu `Item`, kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost. A *výchozí indexovanou vlastnost* vlastností, která může získat přístup pomocí syntaxe pro pole na instanci objektu. Například pokud `o` je objekt typu, který definuje tato vlastnost syntaxe `o.[index]` slouží k přístupu k vlastnosti.

Syntaxe pro přístup k jiné než výchozí indexovaná vlastnost je k poskytnutí názvu vlastnosti a index v závorkách, stejně jako běžný člen. Například pokud vlastnost `o` nazývá `Ordinal`, psaní `o.Ordinal(index)` k němu přistupovat.

Bez ohledu na to, jaký tvar používáte měli byste použít vždy curryfikované formuláře pro metodu set indexované vlastnosti. Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje definice a používání výchozích a jiné než výchozí indexované vlastnosti, které mají get a set metod.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Výstup

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Indexované vlastnosti s více hodnotami indexu

Indexované vlastnosti můžou mít více než jedna hodnota indexu. V takovém případě hodnoty jsou oddělené čárkami, když se vlastnost používá. Metoda set v těchto vlastností musí mít dva curryfikované argumenty, první z nich řazené kolekce členů obsahující klíče a druhá z nich hodnota k nastavení.

Následující kód ukazuje použití indexovaná vlastnost s více hodnotami indexu.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
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
