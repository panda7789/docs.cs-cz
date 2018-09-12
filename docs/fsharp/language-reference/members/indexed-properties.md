---
title: Indexované vlastnosti (F#)
description: 'Další informace o F # indexované vlastnosti, které jsou vlastnosti, které poskytují přístup jako pole k datům seřazené.'
ms.date: 05/16/2016
ms.openlocfilehash: e56e4e2ea3f35df4c8ec46012357242cb6ce69f3
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511039"
---
# <a name="indexed-properties"></a>Indexované vlastnosti

*Indexované vlastnosti* jsou uspořádány ve vlastnosti, které poskytují přístup jako pole na data. Přišli v tři formuláře:

* `Item`
* `Ordinal`
* `Cardinal`

Člen F # musí mít název jedné z těchto tří názvů a zajistit tak přístup jako pole. `IndexerName` se používá k reprezentování některý z následujících tří možností:

## <a name="syntax"></a>Syntaxe

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Poznámky

Formy syntaxe předchozí ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metodu, mají `get` metoda pouze, nebo mít `set` pouze metody. Můžete také zkombinovat obojí tomu syntaxe uvedená jenom příkaz get a syntaxi pro sadu pouze a vytvoří vlastnost, která má get a set. Tento druhý formulář umožňuje umístit různou přístupností. modifikátorů a vlastností atributy na get a set metod.

Když *IndexerName* je `Item`, kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost. A *výchozí indexovanou vlastnost* vlastností, která může získat přístup pomocí syntaxe pro pole na instanci objektu. Například pokud `obj` je objekt typu, který definuje tato vlastnost syntaxe `obj.[index]` slouží k přístupu k vlastnosti.

Syntaxe pro přístup k nevýchozí indexované vlastnosti je název vlastnosti a index v závorkách. Například, pokud je vlastnost `Ordinal`, psaní `obj.Ordinal(index)` k němu přistupovat.

Bez ohledu na to, jaký tvar použijete, byste měli vždy používat curryfikované formulář pro `set` metoda indexované vlastnosti. Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje definice a používání výchozích a jiné než výchozí indexované vlastnosti, které mají get a set metod.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Výstup

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Indexované vlastnosti v případě více proměnných indexu

Indexované vlastnosti můžou mít více než jeden indexovaná proměnná. Proměnné v takovém případě jsou odděleny čárkami, pokud se vlastnost používá. Metoda set v těchto vlastností musí mít dva curryfikované argumenty, první z nich je řazená kolekce členů obsahující klíče a druhý z nich je hodnota nastavena.

Následující kód ukazuje použití indexovaná vlastnost s několika proměnnými indexu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
