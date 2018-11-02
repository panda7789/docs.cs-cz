---
title: Rozlišovaná sjednocení (F#)
description: 'Další informace o použití F # rozlišovaná sjednocení.'
ms.date: 05/16/2016
ms.openlocfilehash: 06d6c154790f659c0c7ff73290357ab50a134362
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43788120"
---
# <a name="discriminated-unions"></a>Rozlišovaná sjednocení

Rozlišovaná sjednocení poskytují podporu pro hodnoty, které může být jedna z počty pojmenovaných případů, případně každý má jiné hodnoty a typy. Rozlišovaná sjednocení jsou užitečná pro heterogenní data; data, která mohou mít zvláštní případy, včetně platných a chybových případů; data, která se liší v typu z jedné instance do druhé; a jako alternativu pro malé hierarchie objektů. Navíc rekurzivně diskriminovaná sjednocení se používají ke znázornění stromových struktur dat.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Poznámky

Rozlišovaná sjednocení jsou podobná sjednocovacím typům v jiných jazycích, ale existují rozdíly. Jako s sjednocovacího typu v C++ nebo variantním typu v jazyce Visual Basic, data uložená v hodnotě nejsou pevná; To může být jedna z několika různých možností. Na rozdíl od sjednocení v těchto jazycích však každé možnosti dostane *identifikátor případu*. Identifikátory velikosti písmen jsou názvy pro různé typy hodnot, které by mohly být objekty tohoto typu; hodnoty jsou volitelné. Pokud hodnoty nejsou k dispozici, případ je ekvivalentní případu výčtu. Pokud existují hodnoty, každá hodnota může být buď samostatná hodnota ze zadaného typu nebo n-tice, která agreguje více polí stejných nebo různých typů. Jednotlivá pole můžete dát název, ale název je volitelný, i když jsou pojmenovány jiná pole v malých písmen.

Usnadnění pro rozlišovaná sjednocení výchozí hodnota je `public`.

Zvažte například následující deklaraci typu obrazce.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Předchozí kód deklaruje diskriminované sjednocení tvar, který může nabývat hodnot ve všech třech případech: obdélník, kruh a hranol. Každý případ má jinou sadu polí. Obdélník využívá dvě s názvem pole, oba typu `float`, které mají názvy šířka a délka. Případ kruh má pouze jedno pole s názvem, poloměr. Případ hranolu obsahuje tři pole dvě z které (šířka a výška) jsou pojmenované názvy polí. Nepojmenované pole jsou označovány jako anonymní pole.

Objekty je možné vytvořit zadáním hodnot pro pojmenované a anonymní pole podle následujících příkladů.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Tento kód ukazuje, že můžete použít buď pojmenovaná pole v inicializaci, nebo můžete spoléhat na pořadí polí v deklaraci a stačí zadat hodnoty pro každé pole zase. Volání konstruktoru pro `rect` v předcházejícím kódu používá pojmenovaná pole, ale volání konstruktoru pro `circ` používá řazení. Můžete kombinovat objednaná pole a pojmenovaná pole jako v konstrukci `prism`.

`option` Typ je jednoduchým diskriminovaným sjednocením v základní knihovně F #. `option` Typ je deklarován následujícím způsobem.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Předchozí kód, který určuje typ `Option` je diskriminovaným sjednocením, které má dva případy `Some` a `None`. `Some` Případ má přidruženou hodnotu, která se skládá z jednoho anonymní pole, jehož typ je vyjádřen parametrem typu `'a`. `None` Případ nemá přidruženou hodnotu. Proto `option` typ určuje obecný typ, který má buď hodnotu některého typu nebo žádnou hodnotu. Typ `Option` má také alias psaný malými písmeny `option`, to znamená informace, které se běžně používají.

Identifikátory velikosti písmen lze jako konstruktory diskriminovaného typu sjednocení. Například následující kód slouží k vytvoření hodnoty `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Identifikátory velikosti písmen se také používají ve vzorech porovnávání výrazů. Ve vzoru porovnávání výrazů jsou k dispozici identifikátory hodnot spojené s jednotlivými případy. Například v následujícím kódu `x` identifikátorem přiřazené hodnoty, který je přidružen `Some` případě `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Ve vzoru porovnávání výrazů můžete použít pojmenovaná pole k určení diskriminovaných sjednocených shod. Pro typ tvar, který byl deklarován dříve můžete použít pojmenovaná pole, jak ukazuje následující kód k extrahování hodnot polí.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Za normálních okolností lze identifikátory velikosti písmen použít bez jejich kvalifikace názvu unie. Pokud chcete, aby název, který má být vždy kvalifikovaným názvem sjednocení, můžete použít [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atributu na definici typu sjednocení.

### <a name="unwrapping-discriminated-unions"></a>Rozbalení rozlišovaná sjednocení

V Rozlišované sjednocení F # se často používají v doméně modelování pro obtékání jednoho typu. Je snadné získání základní hodnoty přes porovnávání vzorů také. Není nutné použít odpovídající výraz pro jeden případ:

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

Následující příklad ukazuje toto:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a>Rozlišovaná sjednocení – struktura

Od verze F # 4.1, může také představovat Rozlišované sjednocení jako struktury.  Používá se k tomu `[<Struct>]` atribut.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Protože jsou typy hodnot a typy odkazů nikoli, jsou doplňující aspekty, které jsou ve srovnání s odkazem na rozlišovaná sjednocení:

1. Tyto jsou zkopírovány jako typy hodnot a mít Sémantika typu hodnoty.
2. Definice rekurzivního typu nelze použít s multicase struct Discriminated Union.
3. Musíte zadat jedinečné názvy případu pro multicase struct Discriminated Union.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Použití rozlišovaných Unionů místo hierarchií objektu

Můžete často použít diskriminované sjednocení jako jednodušší alternativu k malé hierarchii objektu. Například následující diskriminované sjednocení může místo `Shape` základní třída, která obsahuje odvozené typy pro kruh, čtverec, a tak dále.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Místo toho virtuální metody pro výpočet plochy nebo obvodu, jako byste použili pro objektově orientované implementaci, můžete k výpočtu těchto množství porovnávání vzorce pro větvení příslušných vzorců. V následujícím příkladu se používají různé vzorce pro výpočet plochy v závislosti na tvaru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Výstup vypadá takto:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Použití rozlišovaných Unionů pro struktury dat stromu

Rozlišovaná sjednocení mohou být rekurzivní, což znamená, že samotné sjednocení mohou být součástí typů jednoho nebo více případů. Rekurzivní rozlišovaná sjednocení lze použít k vytvoření stromových struktur, které se používají pro modelování výrazů v programovacích jazycích. V následujícím kódu je rekurzivní diskriminované sjednocení použito k vytvoření struktury dat binárního stromu. Union se skládá ze dvou případech `Node`, což je uzel s celočíselnou hodnotou a levým a pravým podstromem, a `Tip`, který ukončí strom.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

V předchozím kódu `resultSumTree` má hodnotu 10. Následující obrázek znázorňuje stromovou strukturu `myTree`.

![Stromová struktura pro myTree](../media/TreeStructureDiagram.png)

Rozlišovaná sjednocení pracují dobře, pokud uzly ve stromu jsou heterogenní. V následujícím kódu, typ `Expression` představuje abstraktní strom syntaxe výrazu v jednoduchém programovacím jazyce, který podporuje sčítání a násobení čísel a proměnných. Některé sjednocovací případy nejsou rekurzivní a představují buď čísla (`Number`) nebo proměnné (`Variable`). Ostatní případy jsou rekurzivní a představují operace (`Add` a `Multiply`), kde jsou jako operandy také výrazy. `Evaluate` Funkce používá odpovídající výraz pro rekurzivní zpracování stromu syntaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Při spuštění tohoto kódu, hodnota `result` je 5.

## <a name="common-attributes"></a>Běžné atributy

Následující atributy se běžně zobrazují v rozlišovaných sjednoceních:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
