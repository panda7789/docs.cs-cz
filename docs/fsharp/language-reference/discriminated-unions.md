---
title: Rozlišovaná sjednocení
description: 'Naučte se používat rozlišené sjednocení F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 3f8ac656bd00b1022b2b13ee1be7ca5c98f68db5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812130"
---
# <a name="discriminated-unions"></a>Rozlišovaná sjednocení

Rozlišené sjednocení poskytují podporu pro hodnoty, které mohou být jedním z mnoha pojmenovaných případů, případně každý s různými hodnotami a typy. Rozlišené sjednocení jsou užitečné pro heterogenní data; data, která mohou mít zvláštní případy, včetně platných a chybových případů; data, která se liší v typu z jedné instance do druhé; a jako alternativu pro malé hierarchie objektů. Kromě toho rekurzivní rozlišené sjednocení slouží k reprezentaci stromových struktur dat.

## <a name="syntax"></a>Syntax

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Poznámky

Rozlišené sjednocení jsou podobné typům sjednocení v jiných jazycích, ale existují rozdíly. Stejně jako u typu sjednocení v jazyce C++ nebo typu variant v Visual Basic nejsou data uložená v hodnotě pevná; může to být jedna z několika různých možností. Na rozdíl od sjednocení v těchto jiných jazycích ale každá z možných možností má za následek *identifikátor případu*. Identifikátory případů jsou názvy různých možných typů hodnot, které mohou být objekty tohoto typu. hodnoty jsou volitelné. Pokud hodnoty nejsou k dispozici, je případ ekvivalentní s případem výčtu. Pokud jsou zadány hodnoty, každá hodnota může být buď jediná hodnota zadaného typu, nebo řazená kolekce členů, která agreguje více polí stejného nebo různých typů. Individuálnímu poli můžete zadat název, ale název je nepovinný, i když se pojmenují další pole ve stejném případě.

Přístupnost pro rozlišené sjednocení je ve výchozím nastavení `public` .

Zvažte například následující deklaraci typu tvaru.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Předchozí kód deklaruje nerozlišený obrazec sjednocení, který může mít hodnoty některého ze tří případů: Rectangle, Circle a Prism. Každý případ má jinou sadu polí. V případě obdélníku jsou k dispozici dvě pojmenovaná pole, obě typu, jejichž `float` názvy mají šířku a délku. KRUHOVÁ velikost má pouze jedno pojmenované pole, poloměr. PRISM případ obsahuje tři pole, z nichž dva mají (šířka a výška) pojmenovaná pole. Nepojmenovaná pole se nazývají anonymní pole.

Sestavíte objekty zadáním hodnot pro pojmenované a anonymní pole podle následujících příkladů.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Tento kód ukazuje, že můžete buď použít pojmenovaná pole v inicializaci, nebo můžete spoléhat na řazení polí v deklaraci a zadat pouze hodnoty pro každé pole. Volání konstruktoru `rect` v předchozím kódu používá pojmenovaná pole, ale volání konstruktoru `circ` používá řazení. Můžete kombinovat uspořádaná pole a pojmenovaná pole, jako v konstrukci `prism` .

`option`Typ je jednoduché rozlišené sjednocení v knihovně F # Core. `option`Typ je deklarován následujícím způsobem.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Předchozí kód určuje, že typ `Option` je rozlišené sjednocení, které má dva případy `Some` a `None` . `Some`Případ má přidruženou hodnotu, která se skládá z jednoho anonymního pole, jehož typ je reprezentován parametrem typu `'a` . K `None` případu není přidružena žádná hodnota. Proto `option` Typ určuje obecný typ, který má buď hodnotu nějakého typu, nebo žádnou hodnotu. Typ `Option` má také alias typu malý malý typ, `option` který se častěji používá.

Identifikátory případu lze použít jako konstruktory pro rozlišený typ sjednocení. Například následující kód se používá k vytvoření hodnot `option` typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Identifikátory Case se používají také ve výrazech pro porovnávání vzorů. Ve výrazu pro porovnávání vzorů jsou identifikátory k dispozici pro hodnoty přidružené k jednotlivým případům. Například v následujícím kódu `x` je identifikátor přiřazený k hodnotě, která je spojena s `Some` případem `option` typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Ve výrazech porovnávání se vzorci můžete použít pojmenovaná pole k určení shod rozlišených sjednocení. Pro typ obrazce, který byl dřív deklarovaný, můžete použít pojmenovaná pole, jak ukazuje následující kód k extrakci hodnot polí.

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

V normálním případě lze identifikátory případu použít bez kvalifikovaného názvu sjednocení. Pokud chcete, aby byl název vždy kvalifikován s názvem sjednocení, můžete použít atribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) na definici typu sjednocení.

### <a name="unwrapping-discriminated-unions"></a>Rozbalení rozlišených sjednocení

V jazyce F # rozlišených sjednoceních se často používají v modelovacích doménách pro zabalení jednoho typu. Základní hodnotu lze snadno extrahovat také pomocí porovnávání vzorů. Výraz shody nemusíte používat pro jeden případ:

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

Porovnávání vzorů je také povoleno přímo v parametrech funkcí, takže můžete rozbalit jeden případ:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Struktury rozlišených sjednocení

Můžete také znázornit rozlišené sjednocení jako struktury.  To se provádí s `[<Struct>]` atributem.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Vzhledem k tomu, že se jedná o typy hodnot a typy odkazů, existují další požadavky v porovnání s referenčními sjednoceními:

1. Jsou zkopírovány jako typy hodnot a mají sémantiku typu hodnoty.
2. Nemůžete použít definici rekurzivního typu s neomezeným sjednocením struktury s více případy.
3. Je nutné zadat jedinečné názvy případů pro rozlišené sjednocení ve více případech.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Použití rozlišených sjednocení místo hierarchií objektů

Můžete často použít rozlišené sjednocení jako jednodušší alternativu k malé hierarchii objektů. Například následující rozlišené sjednocení lze použít místo `Shape` základní třídy, která má odvozené typy pro kruh, čtverce a tak dále.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Místo virtuální metody pro výpočet oblasti nebo hraničního prostředí, stejně jako při použití v objektově orientované implementaci, můžete použít porovnávání vzorů pro větvení s vhodnými vzorci k výpočtu těchto množství. V následujícím příkladu jsou pro výpočet oblasti použity různé vzorce v závislosti na tvaru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Výstup je následující:

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Použití rozlišených sjednocení pro struktury dat stromu

Rozlišené sjednocení mohou být rekurzivní, což znamená, že samotné sjednocení lze zahrnout do typu jednoho nebo více případů. Rekurzivní rozlišené sjednocení lze použít k vytvoření stromové struktury, které se používají k modelování výrazů v programovacích jazycích. V následujícím kódu se rekurzivní rozlišené sjednocení používá k vytvoření binární struktury dat stromu. Sjednocení se skládá ze dvou případů, `Node` který je uzel s celočíselnou hodnotou, levým a pravým podstromem a `Tip` , který ukončí strom.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

V předchozím kódu `resultSumTree` má hodnotu 10. Následující ilustrace znázorňuje stromovou strukturu pro `myTree` .

![Diagram, který zobrazuje stromovou strukturu pro myTree.](../media/discriminated-unions/tree-structure-mytree.png)

Rozlišené sjednocení dobře fungují, pokud jsou uzly ve stromové struktuře heterogenní. V následujícím kódu typ `Expression` představuje abstraktní strom syntaxe výrazu v jednoduchém programovacím jazyce, který podporuje sčítání a násobení čísel a proměnných. Některé případy sjednocení nejsou rekurzivní a představují buď čísla ( `Number` ) nebo proměnné ( `Variable` ). Jiné případy jsou rekurzivní a představují operace ( `Add` a `Multiply` ), kde operandy jsou také výrazy. `Evaluate`Funkce používá výraz shody k rekurzivnímu zpracování stromu syntaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Při spuštění tohoto kódu `result` je hodnota 5.

## <a name="members"></a>Členové

Je možné definovat členy v rozlišených sjednoceních. Následující příklad ukazuje, jak definovat vlastnost a implementovat rozhraní:

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

## <a name="common-attributes"></a>Společné atributy

Následující atributy se běžně zobrazují v rozlišených sjednoceních:

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
