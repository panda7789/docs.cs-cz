---
title: Rozlišovaná sjednocení
description: Naučte se používat f# discriminated sjednocení.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400216"
---
# <a name="discriminated-unions"></a>Rozlišovaná sjednocení

Discriminated sjednocení poskytují podporu pro hodnoty, které mohou být jedním z několika pojmenovaných případů, případně každý s různými hodnotami a typy. Diskriminované sjednocení jsou užitečné pro heterogenní data; údaje, které mohou mít zvláštní případy, včetně platných a chybových případů; data, která se v jednotlivých instanci liší typem; a jako alternativu pro malé hierarchie objektů. Kromě toho rekurzivní discriminated sjednocení se používají k reprezentaci stromové datové struktury.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Poznámky

Discriminated sjednocení jsou podobné typy sjednocení v jiných jazycích, ale existují rozdíly. Stejně jako u typu sjednocení v jazyce C++ nebo typu varianty v jazyce Visual Basic nejsou data uložená v hodnotě pevná; může to být jedna z několika odlišných možností. Na rozdíl od sjednocení v těchto jiných jazycích je však každé z možných možností přidělen *identifikátor případu*. Identifikátory případu jsou názvy pro různé možné typy hodnot, které by mohly být objekty tohoto typu; hodnoty jsou volitelné. Pokud hodnoty nejsou k dispozici, případ je ekvivalentní případu výčtu. Pokud jsou k dispozici hodnoty, každá hodnota může být buď jednu hodnotu zadaného typu nebo řazené kolekce členů, která agreguje více polí stejnénebo různé typy. Jednotlivé pole můžete pojmenovat, ale název je volitelný, i když jsou pojmenována jiná pole ve stejném případě.

Usnadnění pro discriminated odbory `public`výchozí nastavení .

Zvažte například následující deklaraci typu Shape.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Předchozí kód deklaruje discriminated union Shape, který může mít hodnoty libovolného ze tří případů: Rectangle, Circle a Prism. Každý případ má jinou sadu polí. Rectangle případ má dvě pojmenovaná `float`pole, oba typu , které mají názvy šířku a délku. Případ Kruh má jen jedno pojmenované pole, poloměr. Případ Hranol má tři pole, z nichž dvě (šířka a výška) jsou pojmenována pole. Nepojmenovaná pole jsou označována jako anonymní pole.

Objekty vytvoříte zadáním hodnot pro pojmenovaná a anonymní pole podle následujících příkladů.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Tento kód ukazuje, že můžete buď použít pojmenovaná pole v inicializaci, nebo se můžete spolehnout na pořadí polí v deklaraci a pouze zadat hodnoty pro každé pole v pořadí. Volání konstruktoru `rect` v předchozím kódu používá pojmenovaná pole, `circ` ale volání konstruktoru používá řazení. Můžete kombinovat uspořádaná pole a pojmenovaná `prism`pole, jako při výstavbě .

Typ `option` je jednoduché discriminated unie v knihovně jádra F#. Typ `option` je deklarován následujícím způsobem.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Předchozí kód určuje, že `Option` typ je discriminated unie, `Some` `None`která má dva případy a . Případ `Some` má přidruženou hodnotu, která se skládá z jednoho `'a`anonymního pole, jehož typ je reprezentován parametrem typu . Případ `None` nemá žádnou přidruženou hodnotu. `option` Typ tedy určuje obecný typ, který má buď hodnotu nějakého typu, nebo žádnou hodnotu. Typ `Option` má také alias typu `option`s nižšími písmeny , který se běžněji používá.

Identifikátory případu lze použít jako konstruktory pro discriminated union typu. Například následující kód se používá k `option` vytvoření hodnot typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Identifikátory případu se také používají ve výrazech porovnávání vzorů. Ve výrazu porovnávání vzorů jsou k dispozici identifikátory pro hodnoty přidružené k jednotlivým případům. Například v následujícím kódu `x` je identifikátor daný hodnotu, `Some` která je `option` spojena s případem typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Ve výrazech porovnávání vzorů můžete použít pojmenovaná pole k určení diskriminovaných shod sjednocení. Pro typ obrazec, který byl deklarován dříve, můžete použít pojmenovaná pole jako následující kód ukazuje extrahovat hodnoty polí.

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

Identifikátory případů lze obvykle použít, aniž by byly kvalifikovány názvem unie. Pokud chcete, aby byl název vždy kvalifikován názvem unie, můžete použít atribut [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) na definici typu sjednocení.

### <a name="unwrapping-discriminated-unions"></a>Rozbalení discriminated sjednocení

V F# Discriminated Unions se často používají v modelování domény pro obtékání jednoho typu. Je snadné extrahovat základní hodnotu pomocí porovnávání vzorů. Není nutné použít výraz shody pro jeden případ:

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

Následující příklad ukazuje toto:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Porovnávání vzorů je také povoleno přímo v parametrech funkce, takže můžete rozbalit jeden případ:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Strukturovat discriminated odbory

Můžete také zastupovat discriminated sjednocení jako struktury.  To se provádí `[<Struct>]` s atributem.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Vzhledem k tomu, že se jedná o typy hodnot a nikoli o typy odkazů, existují další důležité informace ve srovnání s odkazem discriminated sjednocení:

1. Jsou zkopírovány jako typy hodnot a mají sémantiku typu hodnota.
2. Nelze použít definici rekurzivního typu s víceřádkovou strukturou Discriminated Union.
3. Je nutné zadat jedinečné názvy případů pro vícecase strukturované sjednocení.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Použití diskriminovaných sjednocení namísto hierarchií objektů

Často můžete použít discriminated unie jako jednodušší alternativu k hierarchii malýobjekt. Například následující discriminated unie by mohla `Shape` být použita namísto základní třídy, která má odvozené typy pro kruh, čtverec a tak dále.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Namísto virtuální metody pro výpočet oblasti nebo obvodu, jako byste použili v objektově orientované implementaci, můžete použít porovnávání vzorů do větvení na příslušné vzorce pro výpočet těchto množství. V následujícím příkladu se k výpočtu oblasti používají různé vzorce v závislosti na tvaru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Výstup je následující:

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Použití diskriminovaných sjednocení pro stromové datové struktury

Diskriminované sjednocení může být rekurzivní, což znamená, že unie sama může být zahrnuta do typu jednoho nebo více případů. Rekurzivní discriminated sjednocení lze použít k vytvoření stromové struktury, které se používají k modelování výrazů v programovacích jazycích. V následujícím kódu rekurzivní discriminated unie se používá k vytvoření struktury dat binární strom. Unie se skládá ze `Node`dvou případů , což je uzel s celou hodnotou a `Tip`levými a pravými podstromy a , který ukončí strom.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

V předchozím kódu `resultSumTree` má hodnotu 10. Následující obrázek znázorňuje `myTree`stromovou strukturu pro .

![Diagram, který ukazuje stromovou strukturu pro myTree.](../media/discriminated-unions/tree-structure-mytree.png)

Discriminated sjednocení fungují dobře, pokud uzly ve stromu jsou heterogenní. V následujícím kódu typ `Expression` představuje abstraktní syntaktický strom výrazu v jednoduchém programovacím jazyce, který podporuje sčítání a násobení čísel a proměnných. Některé případy sjednocení nejsou rekurzivní a představují`Number`buď čísla (`Variable`) nebo proměnné ( ). Jiné případy jsou rekurzivní a`Add` představují `Multiply`operace ( a ), kde operandy jsou také výrazy. Funkce `Evaluate` používá výraz shody k rekurzivnímu zpracování stromu syntaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Při spuštění tohoto kódu `result` je hodnota 5.

## <a name="members"></a>Členové

Je možné definovat členy na diskriminované odbory. Následující příklad ukazuje, jak definovat vlastnost a implementovat rozhraní:

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a>Běžné atributy

Následující atributy jsou běžně vidět v diskriminované sjednocení:

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>Viz také

- [Referenční příručka jazyka F#](index.md)
