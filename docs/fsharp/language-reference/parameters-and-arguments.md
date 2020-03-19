---
title: Parametry a argumenty
description: Další informace o podpoře jazyka F# pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400195"
---
# <a name="parameters-and-arguments"></a>Parametry a argumenty

Toto téma popisuje jazykovou podporu pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem. Obsahuje informace o tom, jak předat odkaz emitovat a jak definovat a používat metody, které mohou mít proměnný počet argumentů.

## <a name="parameters-and-arguments"></a>Parametry a argumenty

Termín *parametr* se používá k popisu názvů pro hodnoty, které se očekává, že budou dodány. Termín *argument* se používá pro hodnoty uvedené pro každý parametr.

Parametry lze zadat v n-tice nebo curried formě nebo v nějaké kombinaci obou. Argumenty můžete předat pomocí explicitního názvu parametru. Parametry metod mohou být zadány jako volitelné a má výchozí hodnotu.

## <a name="parameter-patterns"></a>Vzorky parametrů

Parametry dodávané funkcím a metodám jsou obecně vzory oddělené mezerami. To znamená, že v zásadě některý ze vzorů popsaných v [match výrazy](match-expressions.md) lze použít v seznamu parametrů pro funkci nebo člena.

Metody obvykle používají n-tice formulář předávání argumentů. Tím se dosáhne jasnější výsledek z hlediska jiných jazyků .NET, protože n-tice formulář odpovídá způsobu, jakým jsou argumenty předány v metodách .NET.

Curried formulář se nejčastěji používá s `let` funkcemi vytvořenými pomocí vazeb.

Následující pseudokód ukazuje příklady řazené kolekce členů a curried argumenty.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Kombinované formuláře jsou možné, pokud některé argumenty jsou v řazených kolekcí členů a některé nejsou.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Jiné vzorky lze také použít v seznamech parametrů, ale pokud vzorek parametru neodpovídá všem možným vstupům, může být neúplná shoda za běhu. Výjimka `MatchFailureException` je generována, pokud hodnota argumentu neodpovídá vzorům zadaným v seznamu parametrů. Kompilátor vydá upozornění, pokud vzor parametru umožňuje neúplné shody. Alespoň jeden další vzor je běžně užitečné pro seznamy parametrů, a to je zástupný vzor. Vzor se zástupnými kódy v seznamu parametrů použijete, pokud chcete jednoduše ignorovat všechny zadané argumenty. Následující kód ilustruje použití zástupného vzoru v seznamu argumentů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Vzorek se zástupnými symboly může být užitečný vždy, když nepotřebujete předané argumenty, například v hlavním vstupním bodu programu, pokud vás nezajímají argumenty příkazového řádku, které jsou obvykle dodávány jako pole řetězců, jako v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Jiné vzory, které se někdy používají `as` v argumentech jsou vzor a identifikátor vzory spojené s discriminated sjednocení a aktivní vzory. Můžete použít jeden případ discriminated unie vzor takto.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Výstup je následující.

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Aktivní vzorky mohou být užitečné jako parametry, například při transformaci argumentu do požadovaného formátu, jako v následujícím příkladu:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

`as` Vzor můžete použít k uložení odpovídající hodnoty jako místní hodnoty, jak je znázorněno v následujícím řádku kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Jiný vzor, který se používá příležitostně je funkce, která ponechává poslední argument nepojmenovaný poskytnutím, jako tělo funkce, lambda výraz, který okamžitě provede porovnávání vzoru na implicitní argument. Příkladem je následující řádek kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Tento kód definuje funkci, která přebírá `true` obecný seznam a vrátí, pokud je seznam prázdný a `false` jinak. Použití těchto technik může ztížit čtení kódu.

V některých případě vzorky, které zahrnují neúplné shody jsou užitečné, například pokud víte, že seznamy v programu mají pouze tři prvky, můžete použít vzor, jako je následující v seznamu parametrů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Použití vzorů, které mají neúplné shody je nejlepší vyhrazena pro rychlé vytváření prototypů a další dočasná použití. Kompilátor vydá upozornění pro takový kód. Takové vzory nemohou pokrývat obecný případ všech možných vstupů, a proto nejsou vhodné pro komponentní api.

## <a name="named-arguments"></a>Pojmenované argumenty

Argumenty pro metody mohou být určeny podle pozice v seznamu argumentů oddělených čárkami nebo mohou být explicitně předány metodě zadáním názvu, následovaným rovnítkem a hodnotou, která má být předána. Pokud je zadán zadáním názvu, mohou se objevit v jiném pořadí, než které bylo použito v deklaraci.

Pojmenované argumenty mohou kód čitelnější a adaptabilnější pro určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.

Pojmenované argumenty jsou povoleny pouze `let`pro metody, nikoli pro vázané funkce, hodnoty funkcí nebo výrazy lambda.

Následující příklad kódu ukazuje použití pojmenovaných argumentů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Při volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí syntaxe podobné syntaxi pojmenované argumenty. Následující příklad ukazuje tuto syntaxi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Další informace naleznete v [tématu Konstruktory (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Volitelné parametry

Volitelný parametr metody můžete zadat pomocí otazníku před názvem parametru. Volitelné parametry jsou interpretovány jako typ možnosti F#, takže je můžete pravidelně dotazovat, `match` že `Some` `None`typy možností jsou dotazovány pomocí výrazu s a . Volitelné parametry jsou povoleny pouze na členy, `let` nikoli na funkce vytvořené pomocí vazby.

Existující volitelné hodnoty můžete předat metodě podle `?arg=None` `?arg=Some(3)` názvu `?arg=arg`parametru, například nebo nebo . To může být užitečné při vytváření metody, která předá volitelné argumenty jiné metodě.

Můžete také použít `defaultArg`funkci , která nastaví výchozí hodnotu volitelného argumentu. Funkce `defaultArg` přebírá volitelný parametr jako první argument a výchozí hodnotu jako druhý.

Následující příklad ilustruje použití volitelných parametrů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

Výstup je následující.

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

Pro účely Interop Jazyka C# a Visual Basic `[<Optional; DefaultParameterValue<(...)>]` můžete použít atributy v Jazyce F#, takže volající uvidí argument jako volitelné. To je ekvivalentní definování argumentu jako volitelné `MyMethod(int i = 3)`v c# jako v .

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Jako výchozí hodnotu parametru můžete také zadat nový objekt. `Foo` Člen může mít například `CancellationToken` volitelný jako vstup místo:

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

Hodnota uvedená jako `DefaultParameterValue` argument musí odpovídat typu parametru. Například následující není povoleno:

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

V tomto případě kompilátor generuje upozornění a bude ignorovat oba atributy úplně. Všimněte si, `null` že výchozí hodnota musí být typu anotována, protože jinak kompilátor `[<Optional; DefaultParameterValue(null:obj)>] o:obj`odvodí nesprávný typ, tj.

## <a name="passing-by-reference"></a>Předání odkazem

Předání hodnoty F# odkazem zahrnuje [byrefs](byrefs.md), které jsou spravované typy ukazatelů. Pokyny, pro který typ použít, jsou následující:

- Použijte, `inref<'T>` pokud potřebujete pouze číst ukazatel.
- Použijte, `outref<'T>` pokud potřebujete pouze zapisovat do ukazatele.
- Použijte, `byref<'T>` pokud potřebujete číst z a zapisovat do ukazatele.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

Vzhledem k tomu, že parametr je ukazatel a hodnota je proměnlivá, všechny změny hodnoty jsou zachovány po spuštění funkce.

Řazenou kolekce členů můžete použít `out` jako vrácenou hodnotu k uložení libovolných parametrů v metodách knihovny .NET. Alternativně můžete považovat `out` parametr jako `byref` parametr. Následující příklad kódu ilustruje oba způsoby.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Pole parametrů

V některých případě je nutné definovat funkci, která má libovolný počet parametrů heterogenního typu. Nebylo by praktické vytvořit všechny možné přetížené metody k účtu pro všechny typy, které by mohly být použity. Implementace .NET poskytují podporu pro tyto metody prostřednictvím funkce pole parametrů. Metoda, která má pole parametrů v jeho podpisu může být poskytnuta libovolný počet parametrů. Parametry jsou vloženy do pole. Typ prvků pole určuje typy parametrů, které mohou být předány funkci. Pokud definujete pole `System.Object` parametrů jako typ prvku, pak kód klienta může předat hodnoty libovolného typu.

V F# pole parametrů lze definovat pouze v metodách. Nelze je použít v samostatných funkcích nebo funkcích, které jsou definovány v modulech.

Pole parametrů definujete pomocí `ParamArray` atributu. Atribut `ParamArray` lze použít pouze na poslední parametr.

Následující kód ilustruje volání metody .NET, která přebírá pole parametrů, a definici typu v f#, která má metodu, která přebírá pole parametrů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Při spuštění v projektu je výstup předchozího kódu následující:

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Viz také

- [Členové](./members/index.md)
