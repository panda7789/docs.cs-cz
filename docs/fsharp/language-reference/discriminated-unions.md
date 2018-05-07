---
title: Rozlišovaná sjednocení (F#)
description: 'Další informace o použití F # rozlišované sjednocení.'
ms.date: 05/16/2016
ms.openlocfilehash: 7949fd1685ca128f19dd0d0d4aec7236169cd375
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="discriminated-unions"></a>Rozlišovaná sjednocení

Rozlišovaná sjednocení poskytuje podporu pro hodnoty, které může být jedna z číslo pojmenované případů, které by mohly mít každý s různými hodnotami a typy. Rozlišovaná sjednocení jsou užitečné pro heterogenní data; data, která může mít speciální případech, včetně platný a chybových případech; data, která se liší v typu z jedné instance a jako alternativu pro malé objekt hierarchie. Kromě toho rekurzivní rozlišované sjednocení se používají k vyjádření stromu datové struktury.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a>Poznámky
Rozlišovaná sjednocení jsou podobné typy union v jiných jazycích, ale jsou rozdíly. Jako s typu union v jazyce C++ nebo typu variant v jazyce Visual Basic odstraněny data uložená v hodnotě; může být jeden z několika různých možností. Na rozdíl od sjednocení v těchto dalších jazycích, ale každá z možných možností je uveden *případu identifikátor*. Case identifikátory jsou názvy pro různé druhy hodnoty, které by mohly být objekty tohoto typu; hodnoty jsou volitelné. Pokud nejsou zadány hodnoty, tak je ekvivalentní – případ výčtu. Pokud jsou v něm hodnoty, každá hodnota může být buď jednu hodnotu na zadaný typ nebo řazené kolekce členů, která agreguje více polí stejné nebo různých typů. Od F # 3.1 je jednotlivá pole zadejte název, ale název je volitelný, i když mají další pole v případě, že stejný název.

Zvažte například následující deklaraci typu tvaru.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Předchozí kód deklaruje rozlišovaná sjednocení tvar, který může mít hodnoty všech třech případech: obdélníku, kruh a modulu Prism. Každý případ má jinou sadu polí. Pole rámeček případ má dva s názvem, obě typu `float`, které mají názvy šířky a výšky. Kruh případě má pouze jedno pole s názvem, protokolu radius. Tento případ modulu Prism má tři pole dva které (šířky a výšky) jsou pojmenované pole. Nepojmenované pole jsou označovány jako anonymní pole.

Můžete vytvořit objekty tím, že poskytuje hodnoty pro pole pojmenované a anonymní podle následujících příkladů.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Tento kód ukazuje, že můžete použít buď pole s názvem při inicializaci, nebo můžete spoléhat na pořadí polí v deklaraci a stačí zadat hodnoty pro každé pole, pak. Volání konstruktoru pro `rect` v předchozí kód používá pole s názvem, ale volání konstruktoru pro `circ` používá řazení. Můžete kombinovat uspořádaného pole a s názvem pole, jako vytváření `prism`.

`option` Typ je jednoduchý rozlišovaná sjednocení v základní knihovny F #. `option` Typ je deklarován následujícím způsobem.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Předchozí kód určuje, že typ `Option` je rozlišovaná sjednocení, která má dva případy `Some` a `None`. `Some` Případ má přidružené hodnotu, která se skládá z jednoho anonymní pole, jejichž typ je reprezentována parametr typu `'a`. `None` Případ nemá žádné přidružené hodnoty. Proto `option` typ určuje obecného typu, který má buď hodnotu nějaký typ nebo žádná hodnota. Typ `Option` má také alias malá typ `option`, který je informace, které se běžně používá.

Case identifikátory slouží jako konstruktory rozlišovaná sjednocení typu. Například následující kód slouží k vytvoření hodnoty `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Case identifikátory používají taky ve výrazech porovnávání vzorů. Ve tvaru odpovídající výrazu jsou uvedené identifikátory pro hodnoty přidružené k jednotlivých případech. Například v následujícím kódu `x` je identifikátor zadána hodnota, která je přidružená `Some` případu z `option` typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Ve vzoru odpovídající výrazy můžete použít pole s názvem k určení rozlišovaná sjednocení odpovídá. Pro typ tvar, který byl předtím deklarován můžete použít pole s názvem, jak ukazuje následující kód k extrakci hodnoty polí.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Za normálních okolností případu identifikátory lze použít bez jejich kvalifikující s názvem sjednocení. Pokud chcete název, který má být vždy kvalifikovaný pomocí názvu sjednocení, můžete použít [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atribut definici typu union.

### <a name="unwrapping-discriminated-unions"></a>Rozbalení rozlišovaná sjednocení

V Rozlišované sjednocení F # se často používají v doméně modelování pro zabalení jednoho typu. Je snadno rozbalte základní hodnotu prostřednictvím také porovnávání vzorů. Nemusíte používat výrazu shody pro jeden případ:
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

## <a name="struct-discriminated-unions"></a>Rozlišované sjednocení – struktura

Od verze 4.1 F #, může také představovat Rozlišované sjednocení jako struktury.  To lze provést pomocí `[<Struct>]` atribut.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Protože jsou typy hodnot a není odkazové typy, jsou doplňující aspekty ve srovnání s odkazem na rozlišované sjednocení:

1. Že se zkopírují jako typy hodnot a mít Sémantika typu hodnoty.
2. Rekurzivní definici typu nelze použít s multicase struktury Discriminated Union.
3. Musíte zadat jedinečné názvy případu pro multicase struktury Discriminated Union.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Použití rozlišovaná sjednocení namísto objektu hierarchie
Rozlišovaná sjednocení můžete často použít jako jednodušší alternativa k hierarchie malé objektů. Například následující rozlišovaná sjednocení může místo `Shape` základní třídu, která má odvozených typů pro kruh, čtvercovou, a tak dále.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Virtuální metody k výpočtu oblasti nebo hraniční, jako je by použijte pro implementaci objektově orientované, můžete použít k výpočtu tyto počty porovnávání vzorů pro firemní pobočky na příslušné vzorce. V následujícím příkladu se používají různé vzorce k výpočtu oblasti, v závislosti na tvaru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Výstup vypadá takto:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Použití rozlišovaná sjednocení pro strom datové struktury
Rozlišovaná sjednocení může být rekurzivní, což znamená, že sjednocení samotné můžou být součástí typ jeden nebo více případů. Rekurzivní rozlišovaná sjednocení lze použít k vytvoření stromové struktury, které se používají k modelu výrazy v programovacích jazyků. V následujícím kódu rekurzivního rozlišované sjednocení se používá k vytvoření datová struktura binárního stromu. Sjednocení se skládá ze dvou případech `Node`, který je uzlem s celočíselnou hodnotu a levé a pravé podstromy a `Tip`, který ukončí stromu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

V předchozí kód `resultSumTree` má hodnotu 10. Následující obrázek znázorňuje stromové struktury pro `myTree`.

![Stromovou strukturu pro myTree](../media/TreeStructureDiagram.png)

Rozlišovaná sjednocení vhodný, pokud jsou heterogenní uzly ve stromu. V následujícím kódu, typ `Expression` představuje abstraktního syntaktického stromu výrazu v jednoduchý programovací jazyk, který podporuje přidání a násobení čísel a proměnné. Některé union případů nejsou rekurzivní a představují buď čísla (`Number`) nebo proměnné (`Variable`). Ostatních případech jsou rekurzivní a představují operací (`Add` a `Multiply`), kde jsou operandy také výrazy. `Evaluate` Funkce používá výrazu shody rekurzivně procesu stromu syntaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Při spuštění tohoto kódu, hodnota `result` je 5.

## <a name="common-attributes"></a>Běžné atributy

Následující atributy jsou běžně zobrazená v rozlišovaná sjednocení:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]` (F # 4.1 a vyšší)

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)
