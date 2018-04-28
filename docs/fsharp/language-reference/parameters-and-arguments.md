---
title: Parametry a argumenty (F#)
description: 'Další informace o F # jazyková podpora pro definování parametry a předání argumentů do funkce, metod a vlastností.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e146ec4e877bb89f10e2f3daad2d8356c29fa81f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="parameters-and-arguments"></a>Parametry a argumenty

Toto téma popisuje jazyková podpora pro definování parametry a předání argumentů do funkce, metod a vlastností. Obsahuje informace o tom, k předání odkazem a definování a používání metody, které může provádět proměnný počet argumentů.


## <a name="parameters-and-arguments"></a>Parametry a argumenty
Termín *parametr* se používá k popisu názvy hodnot, které se očekává, že je nutné zadat. Termín *argument* se používá pro hodnoty poskytnuté pro jednotlivé parametry.

Parametry lze v řazené kolekce členů nebo curryfikované formuláře nebo v některé kombinaci obojího. Argumenty můžete předat pomocí názvu objektu explicitní parametr. Parametry metody můžete zadat jako volitelné a zadané výchozí hodnotu.


## <a name="parameter-patterns"></a>Parametr vzory
Parametry zadané pro funkce a metody jsou obecně vzory oddělené mezerami. To znamená, že v zásadě některé vzory popsané v [výrazy shody](match-expressions.md) lze použít v seznamu parametrů pro funkci nebo člen.

Metody obvykle formulář řazené kolekce členů předávání argumentů. Toto dosahuje výsledku jasnější z perspektivy jinými jazyky rozhraní .NET, protože formuláře řazené kolekce členů odpovídá způsob, jakým jsou argumenty předané metod rozhraní .NET.

Curryfikované formuláře se nejčastěji používá s funkcemi, které jsou vytvořeny pomocí `let` vazby.

Následující pseudokódu zobrazuje příklady řazené kolekce členů a curryfikované argumenty.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Kombinovaná formuláře je možné, pokud jsou některé argumenty v řazené kolekce členů a některé nejsou.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Jiných vzorů můžete použít i v seznamy parametrů, ale pokud vzor parametr neodpovídá všechny možné vstupy, může být neúplné shoda v době běhu. Výjimka `MatchFailureException` se vygeneruje, když je hodnota argumentu neodpovídá vzory uvedený v seznamu parametrů. Vydá výstrahu, pokud parametr vzor umožňuje pro neúplné odpovídá. Alespoň jeden další vzor je často užitečné pro seznamy parametrů a který je zástupný znak – vzor. Použít zástupný znak – vzor v seznamu parametrů. Pokud chcete jednoduše ignorovat všechny argumenty, které jsou zadány. Následující kód ukazuje použití vzoru zástupný znak v seznam argumentů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Zástupný znak – vzor může být užitečné vždy, když není nutné argumentů předaných v, například v hlavní vstupní bod programu, pokud si nejste zájem o argumenty příkazového řádku, které jsou obvykle poskytovány jako pole řetězců, jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Další vzory, které se někdy používají v argumentech `as` vzor a vzory identifikátor přidružené rozlišovaná sjednocení a aktivní vzorky. Můžete použít případě jedním rozlišovaná sjednocení – vzor následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Výstup je následující.

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Aktivní vzorky může být užitečné jako parametry, například při transformaci argumentu na požadovaný formát, jako v následujícím příkladu:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Můžete použít `as` vzor ukládání odpovídající hodnotu jako hodnotu místní, jak je znázorněno na následujícím řádku kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Jiné vzor, který se používá příležitostně je funkce, která zůstane poslední argument nepojmenované tím, že poskytuje jako text funkce, která okamžitě provede vzor shody implicitní argument výrazu lambda. Příkladem je následující řádek kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Tento kód definuje funkci, která přebírá seznam obecné a vrátí `true` Pokud je seznam prázdný, a `false` jinak. Použití těchto postupů můžete nastavit kód obtížněji čitelný.

V některých případech vzorů, které se týkají neúplné odpovídá jsou užitečné, například pokud jste si jisti, že seznamy v programu mají jenom tři prvky, můžete použít připomínat následující v seznamu parametrů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Použití vzorů, které obsahuje neúplné odpovídající se nejlépe hodí pro rychlé při vytváření prototypu a dalších dočasné používá. Kompilátor vydá upozornění pro takový kód. Tyto vzory nelze zahrnují obecné malá všechny možné vstupy a proto nejsou vhodné pro součást rozhraní API.

## <a name="named-arguments"></a>Pojmenované argumenty
Argumenty pro metody lze zadat podle pozice v seznamu odděleném čárkami argument, nebo je můžete předat metodě explicitně tím, že poskytuje název, za nímž následuje znak rovná a hodnota, která má být předán. -Li zadána, poskytnutím názvu, se objeví v jiném pořadí, ze kterého v deklaraci.

Pojmenované argumenty můžete provést kód srozumitelnější a další přizpůsobitelné určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.

Pojmenované argumenty jsou povoleny pouze pro metody, ne pro `let`-vázána funkce, funkce hodnoty nebo výrazy lambda.

Následující příklad kódu ukazuje použití pojmenovaných argumentech.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Ve volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí pomocí syntaxe podobná pojmenované argumenty. Následující příklad ukazuje tuto syntaxi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Další informace najdete v tématu [konstruktory (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Volitelné parametry
Můžete zadat volitelný parametr pro metodu pomocí otazník před název parametru. Volitelné parametry jsou interpretovány jako typ F # možnost, můžete zadávat dotazy běžným způsobem, že se dotaz typy možností, pomocí `match` výraz s `Some` a `None`. Volitelné parametry jsou povoleny pouze u členů, nikoli na funkce, které jsou vytvořeny pomocí `let` vazby.

Můžete použít také funkci `defaultArg`, který nastaví výchozí hodnota je za volitelným argumentem. `defaultArg` Funkce přebírá volitelný parametr jako první argument a výchozí hodnotu jako druhý.

Následující příklad ukazuje použití volitelné parametry.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Výstup je následující.

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Předávání odkazem
F # podporuje `byref` – klíčové slovo, které určuje, že je parametr předaný odkazem. To znamená, že po spuštění funkce se zachovají všechny změny na hodnotu. Hodnoty poskytnuté `byref` parametr musí být měnitelný. Alternativně můžete předat referenční buňky příslušného typu.

Předání odkazem v jazycích .NET vyvinuly jako způsob, jak z funkce vrátí více než jednu hodnotu. V F # můžete vrátit řazené kolekce členů pro tento účel, nebo použít buňku proměnlivé odkazové jako parametr. `byref` Parametr je poskytován interoperability s knihovnami .NET.

Následující příklady ilustrují použití `byref` – klíčové slovo. Všimněte si, že použijete-li odkaz na buňku jako parametr, musíte vytvořit odkaz na buňku jako hodnotu s názvem a použít je jako parametr, nejen přidat `ref` operátor, jak je znázorněno v prvním volání `Increment` v následujícím kódu. Vzhledem k tomu, že vytváření odkaz na buňku vytvoří kopii základní hodnoty, první volání právě zvýší dočasnou hodnotou.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

Řazené kolekce členů jako návratová hodnota můžete použít k uložení žádné `out` parametry v metod knihovny .NET. Alternativně lze považovat `out` parametr jako `byref` parametr. Následující příklad kódu ukazuje obou směrech.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Pole parametrů
Někdy je nutné definovat funkci, která přebírá libovolný počet parametrů heterogenní typu. Nebude potřeba vytvořit všechny možné přetížené metody pro účet pro všechny typy, které by mohly být použity. Implementace rozhraní .NET poskytuje podporu pro tyto metody prostřednictvím funkce parametr pole. Metoda, která přebírá parametr pole podpis lze zadat s libovolný počet parametrů. Parametry jsou vloženy do pole. Typ elementů pole určuje typy parametrů, které lze předat funkce. Pokud definujete pole parametrů s `System.Object` jako typ elementu, pak kód klienta můžete předat hodnoty libovolného typu.

V jazyce F # můžete pole parametrů definována pouze v metodách. Nelze použít v samostatné funkce nebo funkce, které jsou definovány v modulech.

Pole parametrů se definují pomocí `ParamArray` atribut. `ParamArray` Atribut lze použít pouze na poslední parametr.

Následující kód ukazuje, jak volání metody rozhraní .NET, která použije parametr pole a definici typu v F #, která se má metoda, která přebírá parametr pole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Při spuštění v projektu, výstup předchozí kód je následující:

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Viz také
[Členové](members/index.md)
