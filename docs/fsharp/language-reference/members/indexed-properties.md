---
title: "Indexované vlastnosti (F#)"
description: "Další informace o F # indexované vlastnosti, které jsou vlastnosti, které poskytují přístup jako pole k datům seřazené."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f1266b8b-e2e3-4f49-9332-65c6d34dc0f3
ms.openlocfilehash: 78a09a70621e82f073346471e68ec826359641d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="indexed-properties"></a>Indexované vlastnosti

*Indexované vlastnosti* seřazeni vlastnosti, které poskytují přístup jako pole k data.


## <a name="syntax"></a>Syntaxe

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Poznámky
Tři formuláře předchozí syntaxe ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metoda, mají `get` metoda pouze nebo mít `set` pouze metoda. Můžete také kombinací obou syntaxi uvedenou jenom příkaz get a syntaxi pro sadu pouze a vytvořit vlastnost, která má get a set. Tento formulář pozdější umožňuje umístit get modifikátory různých dostupnosti a atributy a nastavit metody.

Když *PropertyName* je `Item`, kompilátor zpracovává vlastnost jako vlastnost Výchozí indexovat. A *Výchozí indexované vlastnosti* je vlastnost, která můžete přistupovat pomocí syntaxe pro pole na instanci objektu. Například pokud `obj` je objekt typu, který definuje tato vlastnost syntaxe `obj.[index]` se používá pro přístup k vlastnosti.

Syntaxe pro přístup k vlastnosti nevýchozí indexované je poskytnout název vlastnosti a index v závorkách. Například, pokud je vlastnost `Ordinal`, můžete psát `obj.Ordinal(index)` k přístupu.

Bez ohledu na to, jaký typ použijete, byste měli vždycky používat curryfikované formuláře pro `set` metoda indexované vlastnosti. Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje definice a použití výchozí a jiné než výchozí indexované vlastnosti, které mají get a nastavit metody.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Výstup

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Indexované vlastnosti s více Index proměnné
Indexované vlastnosti může mít více než jednu proměnnou index. V takovém případě proměnné jsou oddělené čárkami, pokud je vlastnost použita. Curryfikované dva argumenty, z nichž první řazené kolekce členů obsahující klíče a druhá které nastaví se hodnota musí mít metodu set v taková vlastnost.

Následující kód ukazuje použití indexované vlastnosti s více index proměnné.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a>Viz také
[Členy](index.md)
