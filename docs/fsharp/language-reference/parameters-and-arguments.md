---
title: Parametry a argumenty (F#)
description: 'Další informace o podpora jazyka F # pro definování parametrů a předávání argumentů do funkce, metody a vlastnosti.'
ms.date: 05/16/2016
ms.openlocfilehash: a1e2a70ca560bbb09d2cd10f47485cbe5c5e029d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131973"
---
# <a name="parameters-and-arguments"></a>Parametry a argumenty

Toto téma popisuje podporu jazyka pro definování parametrů a předávání argumentů do funkce, metody a vlastnosti. Obsahuje informace o předávání pomocí odkazu a k definování a použití metod, které mohou provádět proměnný počet argumentů.

## <a name="parameters-and-arguments"></a>Parametry a argumenty

Termín *parametr* se používá k popisu názvy pro hodnoty, které se očekává, že @username. Termín *argument* se používá pro hodnoty poskytnuté pro každý parametr.

Parametry můžete zadat v n-tici nebo curryfikované formuláře, nebo určitou kombinaci obou. Pomocí názvu explicitní parametr můžete předat argumenty. Parametry metod můžete zadaný jako volitelný a zadaný výchozí hodnotu.

## <a name="parameter-patterns"></a>Vzory parametrů

Parametry zadané funkce a metody jsou obecně vzory oddělené mezerami. To znamená, že v zásadě, všechny tyto vzory se dají podle [odpovídající výrazy](match-expressions.md) lze použít v seznamu parametrů funkce nebo člen.

Metody obvykle používají formě řazené kolekce členů předávání argumentů. Toto dosahuje jasnější výsledek z hlediska jinými jazyky rozhraní .NET, protože odpovídá formě řazené kolekce členů způsob, jakým jsou argumenty předávány v metod rozhraní .NET.

Curryfikované formuláře se nejčastěji používá s funkcemi, které jsou vytvářeny instalační sadou `let` vazby.

Následujícím pseudokódu ukazuje příklady řazené kolekce členů a curryfikované argumenty.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Kombinované formuláře je možné, pokud některé argumenty jsou v řazených kolekcí členů a některé nejsou.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Další způsoby lze také v seznamech parametrů, ale pokud vzor parametru se neshoduje s všech vstupů je to možné, může být nekompletní shoda v době běhu. Výjimka `MatchFailureException` se vygeneruje, když hodnota argumentu není odpovídající vzorům uvedeným v seznamu parametrů. Kompilátor vyvolá upozornění, pokud parametr vzoru umožňuje pro úplné shody. Alespoň jeden další vzorek je často užitečné pro seznamy parametrů a, který je vzor zástupných znaků. Vzorec zástupných znaků v seznamu parametrů. použijte chcete jednoduše ignorovat všechny argumenty, které jsou dodávány. Následující kód ukazuje použití zástupných v seznam argumentů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Vzorec zástupných znaků může být užitečné pokaždé, když není nutné předaných argumentech, například hlavní vstupní bod programu, když vás nezajímají argumentů příkazového řádku, které jsou obvykle dodávány jako pole řetězců, stejně jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Další způsoby, které se občas používají v argumenty jsou `as` vzoru a vzorky identifikátoru přidružené rozlišovaná sjednocení a aktivní vzory. Rozlišovaná sjednocení vzor jedním případem můžete následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Výstup je následující.

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Aktivní vzory může být užitečné jako parametry, například při transformaci argumentu do požadovaného formátu, jako v následujícím příkladu:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Můžete použít `as` vzor ukládání odpovídající hodnotu jako místní hodnoty, jak je znázorněno v následující řádek kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Jiný model, který se používá čas od času je funkce, které se zasílají posledním argumentem nepojmenované poskytnutím jako tělo funkce, výraz lambda, který se okamžitě provede porovnávání na implicitní argument. Příkladem je následující řádek kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Tento kód definuje funkci, která přebírá seznam obecných a vrací `true` Pokud je seznam prázdný, a `false` jinak. Použití těchto metod může ztížit kód ke čtení.

V některých případech způsoby, které se týkají neúplné shody jsou užitečné, například pokud víte, že seznamy v aplikaci mají pouze tři prvky, můžete použít model následujícím postupem v seznamu parametrů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Použití vzorů, které obsahuje neúplné odpovídající se nejlépe hodí pro rychlé vytváření prototypů a jiné dočasné účely. Kompilátor vygeneruje upozornění pro takového kódu. Tyto vzory pokrýt obecné velikost všech vstupů je to možné a proto nejsou vhodné pro komponentu rozhraní API.

## <a name="named-arguments"></a>Pojmenované argumenty

Argumenty pro metody je možné zadat tak pozice v seznamu oddělovači argumentů nebo je můžete předat metodě explicitně zadáním názvu, za nímž následuje rovnítko a hodnota, která má být předán v. -Li zadán zadáním názvu, můžete zobrazit v jiném pořadí z použitého v deklaraci.

Pojmenované argumenty můžete provést kód lépe čitelný a další přizpůsobitelné určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.

Pojmenované argumenty jsou povoleny pouze pro metody, ne pro `let`-vázaná funkce, funkce hodnoty nebo výrazy lambda.

Následující příklad kódu ukazuje použití pojmenované argumenty.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Ve volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí syntaxe podobné pojmenované argumenty. Následující příklad ukazuje tuto syntaxi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Další informace najdete v tématu [konstruktory (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Volitelné parametry

Můžete zadat volitelný parametr pro metodu s použitím otazník před název parametru. Volitelné parametry jsou interpretovány jako typ možnost jazyka F #, proto dotazování těchto běžným způsobem, že typy možností jsou dotazovat, pomocí `match` výraz s `Some` a `None`. Volitelné parametry jsou povolené jenom na členy, nikoli na funkce, které jsou vytvářeny instalační sadou `let` vazby.

Můžete použít také funkci `defaultArg`, která nastaví výchozí hodnota je nepovinný argument. `defaultArg` Funkce přebírá volitelný parametr jako první argument a výchozí hodnotu jako druhý.

Následující příklad ukazuje použití nepovinných parametrů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Výstup je následující.

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Předávání odkazem.

Předávání odkazem na hodnotu F # zahrnuje [ByRef](byrefs.md), které jsou typy spravovaného ukazatele. Pokyny, který typ použít vypadá takto:

* Použití `inref<'T>` potřebujete pouze ke čtení ukazatel.
* Použití `outref<'T>` Pokud potřebujete napsat k ukazateli.
* Použití `byref<'T>` Pokud budete potřebovat číst z a zapisovat do ukazatele.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

Protože parametru je ukazatel a hodnota je proměnlivá, všechny změny hodnoty se uchovávají po spuštění funkce.

Řazené kolekce členů jako návratovou hodnotu můžete použít k ukládání žádné `out` parametrů metod knihovny .NET. Alternativně lze považovat `out` parametrem jako `byref` parametru. Následující příklad kódu znázorňuje oba způsoby.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Pole parametrů

Někdy je potřeba definovat funkci, která přijímá libovolný počet parametrů typu heterogenní. Nemusí být praktické k vytvoření všech možných přetížených metod pro všechny typy, které by bylo možné použít. Implementace .NET poskytují podporu pro tyto metody prostřednictvím pole funkce parametr. Metodu, která přebírá parametr pole v jeho podpisu může zobrazovat libovolný počet parametrů. Parametry jsou vloženy do pole. Typ prvků pole určuje typy parametrů, které může být předán funkci. Při definování pole parametrů s `System.Object` jako typ elementu, pak klient může kód předat hodnoty libovolného typu.

V jazyce F # je pole parametrů definovat pouze v metodách. Nelze je použít v samostatné funkce nebo funkce, které jsou definovány v modulech.

Definování pole parametrů s použitím `ParamArray` atribut. `ParamArray` Atribut lze použít pouze pro poslední parametr.

Následující kód ukazuje obě volání metody rozhraní .NET, která přijímá pole parametrů a definice typu v jazyce F #, která obsahuje metodu, která přebírá parametr pole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Při spuštění v projektu, výstup předchozího kódu vypadá takto:

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Viz také:

- [Členové](members/index.md)
