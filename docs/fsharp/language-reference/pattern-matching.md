---
title: Porovnávání vzorů
description: Zjistěte, jak vzorky se používají v F# k porovnání dat pomocí logické struktury, jak rozložit data na základní části nebo extrahovat informace z dat.
ms.date: 05/16/2016
ms.openlocfilehash: bb6b41f6d15612e4a65abd4a3d5d7291d84a8f3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795457"
---
# <a name="pattern-matching"></a>Porovnávání vzorů

Vzorky jsou pravidla pro transformování vstupních dat. Používají se v průběhu F# jazyk k porovnání dat s logickou strukturou nebo strukturami, rozložení dat na základní části nebo extrahovat informace z dat různými způsoby.

## <a name="remarks"></a>Poznámky

Vzorky se používají v mnoha konstrukcích jazyka, jako `match` výrazu. Používají se při zpracování argumentů pro funkce v `let` vazeb, lambda výrazy a v obslužných rutinách výjimek spojených s `try...with` výrazu. Další informace najdete v tématu [odpovídající výrazy](match-expressions.md), [vazby let](functions/let-bindings.md), [výrazy Lambda: `fun` – Klíčové slovo](functions/lambda-expressions-the-fun-keyword.md), a [výjimky: `try...with` Výraz](exception-handling/the-try-with-expression.md).

Například v `match` výrazu, *vzor* co následuje symbol svislé čáry.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Každý vzorek se chová jako pravidlo pro transformování vstupu nějakým způsobem. V `match` výrazu, každý vzorek je zkoumán zjistit, jestli se vstupní data kompatibilní se vzorkem. Pokud se najde shoda, výsledkem spuštění výrazu. Pokud není nalezena shoda, je testováno další pravidlo vzorku. Volitelně při *podmínku* části je vysvětlen v [odpovídající výrazy](match-expressions.md).

Podporované vzory jsou uvedeny v následující tabulce. V době běhu vstup je testován oproti každému z následujících vzorů v uvedeném pořadí v tabulce a vzory se používají rekurzivně, od nejprve na poslední, jak se objeví ve vašem kódu a zleva doprava pro vzory na každém řádku.

|Název|Popis|Příklad|
|----|-----------|-------|
|Konstantní vzorek|Všechny číselné, znak, nebo textový literál, konstanta výčtu nebo definovaný identifikátor literálu|`1.0`, `"test"`, `30`, `Color.Red`|
|Vzor identifikátoru|Hodnota case diskriminované sjednocení, popisku výjimky nebo případ aktivního vzoru|`Some(x)`<br /><br />`Failure(msg)`|
|Variabilní vzor|*identifier*|`a`|
|`as` Vzor|*vzor* jako *identifikátor*|`(a, b) as tuple1`|
|NEBO vzor|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|Vzor AND|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Nevýhody vzoru|*identifikátor* :: *identifikátor seznamu*|`h :: t`|
|Vzor seznamu|[ *pattern_1*; ... ; *pattern_n* ]|`[ a; b; c ]`|
|Vzor pole|[&#124; *pattern_1*;.; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Vzor v závorce|( *vzor* )|`( a )`|
|Vzor řazené kolekce členů|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Vzor záznamu|{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Vzorec zástupných znaků|\_|`_`|
|Vzorek společně s anotací typu|*vzor* : *typu*|`a : int`|
|Testovací vzorek typu|:? *typ* [jako *identifikátor* ]|`:? System.DateTime as dt`|
|Vzor Null|null|`null`|

## <a name="constant-patterns"></a>Konstantní vzorky

Konstantní vzorky jsou číselné, znakové a řetězcové literály výčtu konstant (se zahrnutým názvem výčtu typu). A `match` výraz, který má pouze konstantní vzory, je možné porovnat s příkazy case v jiných jazycích. Vstup je porovnán s hodnotou literálu a vzor odpovídá, pokud jsou hodnoty stejné. Typ literálu musí být kompatibilní s typem vstupu.

Následující příklad ukazuje použití vzorů literálu a také používá vzory proměnné a vzor OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Dalším příkladem vzoru literálu je vzor založený na výčtu konstant. Při použití konstant výčtu, musíte zadat název typu výčtu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Vzorky identifikátoru

Pokud vzorek je řetězec znaků, který tvoří platný identifikátor, forma identifikátoru Určuje, jak je vzorek párován. Pokud identifikátor je delší než jeden znak a začíná velkým písmenem, kompilátor se pokusí spárovat se vzorkem identifikátoru. Identifikátor pro tento model může být hodnota označená jako literální atribut, případ diskriminovaného sjednocení, identifikátor výjimky nebo případ aktivního vzoru. Pokud není nalezen žádný odpovídající identifikátor, shoda se nezdaří a další pravidlo pro vzorek, vzorek proměnné, se porovná se vstupem.

Vzorky rozlišeného sjednocení mohou být jednoduše pojmenované případy nebo mají hodnotu či n-tici obsahující více hodnot. Pokud je hodnota, je nutné zadat identifikátor pro hodnotu. V případě řazené kolekce členů je nutné zadat vzor n-tice s identifikátor pro každý element n-tice nebo identifikátor s názvem pole pro jedno nebo více sjednocených polí. Podívejte se na příklady kódu v této části s příklady.

`option` Typ je diskriminovaným sjednocením, které má dva případy `Some` a `None`. Jeden případ (`Some`) má hodnotu, ale další (`None`) je pouze pojmenovaný případ. Proto `Some` musí mít proměnnou pro hodnotu spojenou s `Some` případu, ale `None` musí zobrazovat samostatně. V následujícím kódu, proměnná `var1` přiřazena hodnota získaná pomocí odpovídajícího `Some` případ.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

V následujícím příkladu `PersonName` diskriminované sjednocení obsahuje směs řetězců a znaků, které představují možné formy jména. Případy diskriminovaného sjednocení jsou `FirstOnly`, `LastOnly`, a `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Pro rozlišovaná sjednocení, které mají pojmenované názvy polí použijte znaménko rovná se (=) k získání hodnoty pojmenovaného pole. Zvažte například diskriminované sjednocení s deklarací, jako následující.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Můžete použít pojmenovaná pole ve výrazu odpovídajícímu vzorci následujícím způsobem.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Použití pojmenovaného pole je volitelné, protože v předchozím příkladu obě `Circle(r)` a `Circle(radius = r)` stejný efekt.

Pokud zadáte více polí, použijte středník (;) jako oddělovač.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Aktivní vzorky umožňují definovat složitější vlastní porovnávání vzorů. Další informace o aktivních vzorech naleznete v tématu [aktivní vzory](active-patterns.md).

Případ, ve kterém je identifikátor výjimkou se používá v porovnávání vzorů v kontextu obslužné rutiny výjimek. Informace o vzoru porovnávání ve zpracování výjimek naleznete v tématu [výjimky: `try...with` Výraz](exception-handling/the-try-with-expression.md).

## <a name="variable-patterns"></a>Vzorce proměnné

Variabilní vzor přiřadí hodnotu porovnávanou s názvem proměnné, který je k dispozici pro použití v prováděném výrazu vpravo od `->` symbol. Variabilní vzor odpovídá jakémukoliv vstupu, ale variabilní vzorky se často objevuje v rámci jiných vzorků, proto umožňuje složitější struktury, jako například záznamy a pole, které lze rozložit na proměnné.

Následující příklad ukazuje vzor proměnné v rámci vzoru n-tice.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>jako vzor

`as` Vzor je vzor, který má `as` připojena k němu klauzule. `as` Klauzule váže odpovídající hodnotu pro název, který lze použít ve výrazu spuštění `match` výrazu, nebo v případě, kdy se tento model používá v `let` vazby, přidání názvu jako vazby v místním rozsahu.

Následující příklad používá `as` vzor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>NEBO vzor

Vzor OR se používá, když vstupní data mohou odpovídat více vzorům a chcete provést ve výsledku stejný kód. Typy obou stran vzoru operátoru OR musí být kompatibilní.

Následující příklad demonstruje vzory OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>Vzor AND

Vzor AND vyžaduje, aby vstupu shoda dvou vzorků. Typy obou stran vzoru operátoru AND musí být kompatibilní.

Následující příklad je podobný `detectZeroTuple` ukazuje [vzor n-tice](https://msdn.microsoft.com/library/#tuple) dále v tomto tématu, ale zde jsou `var1` a `var2` získány jako hodnoty pomocí vzoru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Nevýhody vzoru

Vzorek nevýhod se používá rozložení seznamu na první prvek *head*a seznam, který obsahuje zbývající prvky *tail*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Vzor seznamu

Vzor seznamu umožňuje seznamů lze rozložit na počet prvků. Vzor seznamu sám může odpovídat pouze seznamům určitého počtu prvků.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Vzor pole

Vzor pole podobá vzoru seznamu a lze použít k rozložení polí určité délky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Vzor v závorce

Závorky mohou být seskupeny kolem vzorků k dosažení požadované asociativity. V následujícím příkladu jsou použity závorky pro řízení asociativity mezi vzorcem a nevýhody vzoru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Vzor řazené kolekce členů

Vzor řazené kolekce členů odpovídá formě řazené kolekce členů a umožňuje řazené kolekce členů, které lze rozložit na jeho základní prvky pomocí proměnných porovnání vzorce pro každou pozici v řazené kolekci členů.

Následující příklad ukazuje vzor n-tice a také používá vzor literálu, vzory proměnné a vzor zástupných znaků.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Vzor záznamu

Vzor záznamu slouží k rozložení záznamů pro extrahování hodnot polí. Vzor nemá odkaz na všechna pole záznamu; Vynechaná pole pouze nejsou součástí srovnávání a nejsou extrahována.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Vzorec zástupných znaků

Vzorec zástupných znaků je vyjádřen podtržítkem (`_`) znak a odpovídá jakémukoli zadání, stejně jako vzorec proměnné s tím rozdílem, že je vstup ignorován místo přiřazen proměnné. Vzorec zástupných znaků se často používá v rámci jiných vzorků jako zástupný symbol pro hodnoty, které nejsou potřeba ve výrazu vpravo od `->` symbol. Vzorec zástupných znaků se také často používá na konci seznamu vzorků tak, aby odpovídaly jakémukoli neodpovídajícímu vstupu. Vzorec zástupných znaků je znázorněna v mnoha příkladech kódu v tomto tématu. Viz předchozí kód pro jedním z příkladů.

## <a name="patterns-that-have-type-annotations"></a>Vzorky, které mají anotace typu

Vzorky mohou mít anotace typu. Ty se chovají stejně jako ostatní poznámky typu a příručka pro odvození stejně jako ostatní poznámky typu. Jsou vyžadovány závorky kolem anotace typu ve vzorcích. Následující kód popisuje vzor, který má anotaci typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Testovací vzorek typu

Vzor testovacího typu slouží k porovnání vstupu oproti typu. Pokud je vstupní typ pro vyhledání shody (nebo odvozeným typem) typem určeným ve vzorku, porovnávání úspěšné.

Následující příklad ukazuje vzor testu typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Vzor Null

Vzor null odpovídá hodnotě null, který může zobrazit při práci s typy, které umožňují hodnotu null. Vzory Null jsou často používány při spolupráci s kódu rozhraní .NET Framework. Návratová hodnota rozhraní API .NET může být například vstup do `match` výrazu. Můžete řídit tok programu na základě, zda je návratová hodnota null a také na jiných vlastnostech vrácené hodnoty. Vzor null můžete zabránit ostatních částí programu šíření hodnoty null.

Následující příklad používá vzor null a vzor proměnné.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Viz také:

- [Výrazy shody](match-expressions.md)
- [Aktivní vzory](active-patterns.md)
- [Referenční dokumentace jazyka F#](index.md)