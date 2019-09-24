---
title: Parametry a argumenty
description: Přečtěte F# si o jazykové podpoře pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem.
ms.date: 05/16/2016
ms.openlocfilehash: e8094ffbc55870b5de75acb740aa2736ec6590a5
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216822"
---
# <a name="parameters-and-arguments"></a>Parametry a argumenty

Toto téma popisuje jazykovou podporu pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem. Obsahuje informace o tom, jak předat odkaz, a jak definovat a používat metody, které mohou převzít proměnný počet argumentů.

## <a name="parameters-and-arguments"></a>Parametry a argumenty

*Parametr* Term slouží k popisu názvů pro hodnoty, které mají být dodány. Termínový *argument* se používá pro hodnoty zadané pro každý parametr.

Parametry lze zadat v řazené kolekci členů nebo ve formě curryfikované nebo v některé kombinaci dvou. Argumenty můžete předat pomocí explicitního názvu parametru. Parametry metod lze zadat jako nepovinné a předávat výchozí hodnotu.

## <a name="parameter-patterns"></a>Vzory parametrů

Parametry, které jsou zadány pro funkce a metody, jsou obecně vzory oddělené mezerami. To znamená, že v zásadě lze kterýkoli ze vzorů popsaných ve [výrazech shody](match-expressions.md) použít v seznamu parametrů pro funkci nebo člena.

Metody obvykle používají formulář řazené kolekce členů s předáváním argumentů. Výsledkem je jasný výsledek z perspektivy dalších jazyků .NET, protože formulář řazené kolekce členů odpovídá způsobu předání argumentů do metod .NET.

Formulář curryfikované se nejčastěji používá s funkcemi vytvořenými pomocí `let` vazeb.

Následující pseudokódu ukazuje příklady řazené kolekce členů a argumentů curryfikované.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Kombinované formuláře jsou možné, pokud jsou některé argumenty v řazené kolekci členů a některé nejsou.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Další vzory lze také použít v seznamech parametrů, ale pokud vzor parametru neodpovídá všem možným vstupům, může být v době běhu neúplná shoda. Výjimka `MatchFailureException` je vygenerována, pokud hodnota argumentu neodpovídá vzorům uvedeným v seznamu parametrů. Kompilátor vydá upozornění, když vzor parametru umožňuje neúplné shody. Minimálně jeden další vzor je běžně užitečný pro seznamy parametrů a je to vzor zástupného znaku. Vzor zástupného znaku v seznamu parametrů použijete, když jednoduše chcete ignorovat všechny argumenty, které jsou dodány. Následující kód ilustruje použití zástupného vzoru v seznamu argumentů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Vzor zástupných znaků může být užitečný kdykoli, když nepotřebujete předávat argumenty, jako je například v hlavním vstupním bodě do programu, pokud se nechcete zajímat o argumenty příkazového řádku, které jsou obvykle dodávány jako pole řetězců, jak je uvedeno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Další vzory, které jsou někdy používány v argumentech `as` , jsou vzor a vzory identifikátorů přidružené k rozlišeným sjednocením a aktivním vzorům. Můžete použít vzor sjednocení s jedním případem, jak je znázorněno níže.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

Výstup je následující.

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Aktivní vzory mohou být užitečné jako parametry, například při transformaci argumentu do požadovaného formátu, jako v následujícím příkladu:

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Můžete použít `as` vzor k uložení odpovídající hodnoty jako místní hodnoty, jak je znázorněno v následujícím řádku kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Jiný model, který je používán občas, je funkce, která opustí poslední argument bez názvu uvedením, jako tělo funkce, výraz lambda, který okamžitě provede porovnávání vzorů implicitního argumentu. Příkladem je následující řádek kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Tento kód definuje funkci, která přijímá obecný seznam a vrátí `true` , pokud je seznam prázdný, a `false` jinak. Použití takových technik může ztížit čtení kódu.

Modely, které zahrnují neúplné shody, jsou užitečné, například pokud víte, že seznamy v programu mají pouze tři prvky, můžete použít vzor podobný následujícímu v seznamu parametrů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

Používání vzorů, které mají neúplné shody, je nejlépe vyhrazené pro rychlé vytváření prototypů a další dočasné účely. Kompilátor vydá upozornění pro takový kód. Takové vzory nemůžou pokrývat obecný případ všech možných vstupů, takže nejsou vhodné pro rozhraní API komponent.

## <a name="named-arguments"></a>Pojmenované argumenty

Argumenty pro metody lze zadat podle pozice v seznamu argumentů oddělených čárkou nebo je lze předat metodě explicitně zadáním názvu, následovaným rovnítkem a hodnotou, která má být předána. Pokud je zadáno zadáním názvu, mohou se zobrazit v jiném pořadí, než je použito v deklaraci.

Pojmenované argumenty mohou zvýšit čitelnost kódu a můžou být přizpůsobitelné na určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.

Pojmenované argumenty jsou povoleny pouze pro metody, nikoli pro `let`funkce vázané na funkce, hodnoty funkcí nebo výrazy lambda.

Následující příklad kódu ukazuje použití pojmenovaných argumentů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

V volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí syntaxe podobné syntaxi pojmenovaných argumentů. Následující příklad ukazuje tuto syntaxi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Další informace naleznete v tématu [konstruktory (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Volitelné parametry

Můžete zadat volitelný parametr pro metodu pomocí otazníku před názvem parametru. Volitelné parametry jsou interpretovány jako F# typ možnosti, takže je lze dotazovat běžným způsobem, jakým jsou dotazovány typy možností, pomocí `match` výrazu s `Some` a `None`. Volitelné parametry jsou povoleny pouze u členů, nikoli u funkcí vytvořených pomocí `let` vazeb.

Můžete předat existující volitelné hodnoty metodě podle názvu parametru, například `?arg=None` nebo `?arg=Some(3)` nebo `?arg=arg`. To může být užitečné při vytváření metody, která předá volitelné argumenty jiné metodě.

Můžete také použít funkci `defaultArg`, která nastaví výchozí hodnotu volitelného argumentu. `defaultArg` Funkce přebírá volitelný parametr jako první argument a výchozí hodnotu jako sekundu.

Následující příklad ilustruje použití nepovinných parametrů.

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

Pro účely C# a Visual Basic spolupráci můžete použít atributy `[<Optional; DefaultParameterValue<(...)>]` v F#, aby volající jako volitelnou viděli argument. To je ekvivalentní k definování argumentu jako volitelné v C# nástroji jako `MyMethod(int i = 3)`v.

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Můžete také zadat nový objekt jako výchozí hodnotu parametru. `Foo` Člen by například mohl mít jako vstup volitelné `CancellationToken` místo:

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

Hodnota zadaná jako argument `DefaultParameterValue` musí odpovídat typu parametru. Například následující nejsou povoleny:

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

V tomto případě kompilátor vygeneruje upozornění a bude zcela ignorovat oba atributy. Všimněte si, že výchozí `null` hodnota musí být typu s poznámkami, jinak kompilátor odvodí nesprávný typ, tj. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`

## <a name="passing-by-reference"></a>Předávání odkazem

Předání F# hodnoty odkazem zahrnuje [byrefs](byrefs.md), které jsou spravované typy ukazatelů. Pokyny pro typ, který se má použít, jsou následující:

- Použijte `inref<'T>` , pokud potřebujete jen číst ukazatel.
- Použijte `outref<'T>` , pokud potřebujete zapisovat jenom na ukazatel.
- Použijte `byref<'T>` , pokud potřebujete číst a zapisovat do ukazatele.

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

Vzhledem k tomu, že parametr je ukazatel a hodnota je proměnlivá, všechny změny hodnoty se uchovávají po spuštění funkce.

Můžete použít řazenou kolekci členů jako návratovou hodnotu pro uložení `out` parametrů v metodách knihovny .NET. Alternativně můžete `out` parametr zakládat `byref` jako parametr. Následující příklad kódu ukazuje oba způsoby.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Pole parametrů

V některých případech je nutné definovat funkci, která přebírá libovolný počet parametrů heterogenního typu. Nebylo by praktické vytvořit všechny možné přetížené metody pro všechny typy, které by mohly být použity. Implementace rozhraní .NET poskytují podporu pro tyto metody prostřednictvím funkce pole parametrů. Metoda, která přebírá pole parametrů v jeho podpisu, může být poskytnuta s libovolným počtem parametrů. Parametry jsou vloženy do pole. Typ prvků pole určuje typy parametrů, které mohou být předány do funkce. Definujete-li pole `System.Object` parametrů jako typ prvku, může kód klienta předat hodnoty libovolného typu.

V F#nástroji lze pole parametrů definovat pouze v metodách. Nelze je použít v samostatných funkcích nebo funkcích, které jsou definovány v modulech.

Pole parametrů definujete pomocí `ParamArray` atributu. `ParamArray` Atribut lze použít pouze pro poslední parametr.

Následující kód ilustruje volání metody .NET, která přijímá pole parametrů a definice typu v F# , který má metodu, která přijímá pole parametrů.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Při spuštění v projektu je výstupem předchozího kódu následující:

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

- [Členové](./members/index.md)
