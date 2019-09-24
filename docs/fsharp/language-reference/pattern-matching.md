---
title: Porovnávání vzorů
description: Naučte se, jak se F# používají vzory pro porovnání dat s logickými strukturami, rozložení dat na části prvků nebo extrakce informací z dat.
ms.date: 05/16/2016
ms.openlocfilehash: 0e14fa00103742bbf5f054f8c04a7669ed767e63
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216797"
---
# <a name="pattern-matching"></a>Porovnávání vzorů

Vzory jsou pravidla pro transformaci vstupních dat. Používají se v celém F# jazyce k porovnání dat s logickou strukturou nebo strukturami, rozložení dat na části prvků nebo extrakce informací z dat různými způsoby.

## <a name="remarks"></a>Poznámky

Vzory se používají v mnoha konstrukcích jazyka, jako je `match` například výraz. Používají se při zpracovávání argumentů pro funkce v `let` Bindings, lambda výrazech a v obslužných rutinách výjimek přidružených `try...with` k výrazu. Další informace naleznete v tématu [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [lambda Expressions: Klíčové slovo](./functions/lambda-expressions-the-fun-keyword.md) a[výjimky: `fun` `try...with` Výraz.](./exception-handling/the-try-with-expression.md)

Například ve `match` výrazu je *vzor* následujícím způsobem jako symbol kanálu.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Každý vzor funguje jako pravidlo pro transformaci vstupu nějakým způsobem. `match` Ve výrazu je každý vzor zkontrolován a je možné zjistit, zda jsou vstupní data kompatibilní se vzorem. Pokud je nalezena shoda, je proveden výsledek výrazu. Pokud se shoda nenajde, otestuje se další pravidlo vzoru. Volitelná část when *podmínky* je vysvětlena ve [výrazech shody](match-expressions.md).

V následující tabulce jsou uvedeny podporované vzory. V době spuštění je vstup testován proti každému z následujících vzorů v pořadí uvedeném v tabulce a vzory jsou aplikovány rekurzivně, od první až po zobrazení ve vašem kódu a zleva doprava pro vzorce na každém řádku.

|Name|Popis|Příklad|
|----|-----------|-------|
|Konstantní vzorek|Jakýkoli numerický, znakový nebo řetězcový literál, konstanta výčtu nebo definovaný identifikátor literálu|`1.0`, `"test"`, `30`, `Color.Red`|
|Vzor identifikátoru|Hodnota případu rozlišeného sjednocení, popisek výjimky nebo aktivní vzor případu|`Some(x)`<br /><br />`Failure(msg)`|
|Vzorec proměnné|*RID*|`a`|
|`as`vzorku|*vzor* jako *identifikátor*|`(a, b) as tuple1`|
|NEBO vzor|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|AND – vzor|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Model nevýhody|*identifikátor* :: *list-Identifier*|`h :: t`|
|Vzor seznamu|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Vzor pole|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Vzor v závorce|( *vzor* )|`( a )`|
|Vzor řazené kolekce členů|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Vzor záznamu|{ *identifier1* = *pattern_1*;...; *identifier_n*  =  *pattern_n* }|`{ Name = name; }`|
|Vzor zástupných znaků|\_|`_`|
|Vzor spolu s anotací typu|*vzor* : *typ*|`a : int`|
|Vzorek testu typu|:? *typ* [as *identifikátor* ]|`:? System.DateTime as dt`|
|Vzor null|null|`null`|

## <a name="constant-patterns"></a>Konstantní vzorce

Konstantní vzorce jsou číselné, znakové a řetězcové literály, výčty výčtu (včetně názvu typu výčtu). `match` Výraz, který má pouze konstantní vzorce, lze porovnat s příkazem Case v jiných jazycích. Vstup je porovnán s hodnotou literálu a vzor se shoduje, pokud jsou hodnoty stejné. Typ literálu musí být kompatibilní s typem vstupu.

Následující příklad ukazuje použití vzorů literálu a také používá vzorec proměnné a vzor nebo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Dalším příkladem literálního vzoru je vzor založený na konstantách výčtu. Pokud používáte konstanty výčtu, je nutné zadat název typu výčtu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Vzory identifikátorů

Je-li vzor řetězcem znaků, které tvoří platný identifikátor, forma identifikátoru určuje, jak odpovídá vzor. Pokud je identifikátor delší než jeden znak a začíná velkým znakem, kompilátor se pokusí provést shodu se vzorem identifikátoru. Identifikátor pro tento vzor může být hodnota označená atributem literálu, případem rozlišeného sjednocení, identifikátorem výjimky nebo aktivním vzorem případu. Pokud není nalezen žádný odpovídající identifikátor, shoda se nezdařila a další pravidlo vzoru, proměnná vzor, je porovnána se vstupem.

Vzorce rozlišených sjednocení mohou být jednoduché pojmenované případy nebo mohou mít hodnotu nebo řazené kolekce členů obsahující více hodnot. Pokud je hodnota, je nutné zadat identifikátor hodnoty. V případě řazené kolekce členů je nutné dodat vzor řazené kolekce členů s identifikátorem pro každý prvek řazené kolekce členů nebo identifikátor s názvem pole pro jedno nebo více pojmenovaných polí Union. Příklady najdete v příkladech kódu v této části.

Typ je rozlišené sjednocení, které má dva `Some` případy a `None`. `option` Jeden případ (`Some`) má hodnotu, ale druhý (`None`) je pouze pojmenovaný případ. Proto musí mít proměnnou pro hodnotu přidruženou `Some` k případu, ale `None` musí být uvedena samostatně. `Some` V následujícím kódu je proměnná `var1` udělena hodnotě, která je získána spárováním `Some` s případem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

V následujícím příkladu `PersonName` obsahuje rozlišené sjednocení kombinaci řetězců a znaků, které reprezentují možné formy názvů. Případy rozlišeného sjednocení jsou `FirstOnly`, `LastOnly`a `FirstLast`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Pro rozlišené sjednocení, která mají pojmenovaná pole, použijte znaménko rovná se (=) k extrakci hodnoty pojmenovaného pole. Zvažte například rozlišené sjednocení s deklarací, jako je následující.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Pojmenovaná pole ve výrazu pro porovnávání se vzorci můžete použít následujícím způsobem.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Použití pojmenovaného pole je volitelné, takže v předchozím příkladu má obojí `Circle(r)` a `Circle(radius = r)` má stejný účinek.

Pokud zadáte více polí, použijte středník (;) jako oddělovač.

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Aktivní vzory umožňují definovat komplexnější vlastní porovnávání vzorů. Další informace o aktivních vzorech najdete v tématu [aktivní vzory](active-patterns.md).

Případ, ve kterém je identifikátor výjimkou, se používá v porovnávání vzorů v kontextu obslužných rutin výjimek. Informace o porovnávání vzorů při zpracování výjimek naleznete v [tématu výjimky: `try...with` Výraz.](./exception-handling/the-try-with-expression.md)

## <a name="variable-patterns"></a>Vzorce proměnných

Vzorec proměnné přiřadí hodnotu, která odpovídá názvu proměnné, který je pak k dispozici pro použití ve výrazu spuštění napravo od `->` symbolu. Proměnlivý vzorek se shoduje se všemi vstupy, ale vzory proměnných se často zobrazují v rámci jiných vzorů, čímž je umožněno rozložit komplexnější struktury, jako jsou například řazené kolekce členů a pole, aby byly rozložené do proměnných

Následující příklad ukazuje vzor proměnné v rámci vzoru řazené kolekce členů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>jako vzor

Vzor je vzor, ke kterému `as` je připojena klauzule. `as` Klauzule váže odpovídající hodnotu k názvu, který lze použít ve výrazu `match` provedení výrazu, nebo v případě, že je tento `let` vzor použit ve vazbě, je název přidán jako vazba do místního oboru. `as`

Následující příklad používá `as` vzor.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>NEBO vzor

Vzor nebo se používá, pokud vstupní data mohou odpovídat více vzorům a chcete spustit stejný kód jako výsledek. Typy obou stran vzoru OR musí být kompatibilní.

Následující příklad znázorňuje vzor nebo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>AND – vzor

Vzor a vyžaduje, aby vstup odpovídal dvěma vzorům. Typy obou stran vzoru a musí být kompatibilní.

Následující příklad je podobný jako `detectZeroTuple` v části [vzor řazené kolekce členů](https://msdn.microsoft.com/library/#tuple) dále v tomto tématu `var1` , ale tady a `var2` se získává jako hodnoty pomocí vzoru a.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Model nevýhody

Vzorec nevýhody slouží k rozloží seznamu do prvního prvku, *záhlaví*a seznamu, který obsahuje zbývající prvky, *konec*.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Vzor seznamu

Vzor seznamu umožňuje rozložit seznamy na několik prvků. Samotný vzor seznamu může odpovídat pouze seznamům určitého počtu prvků.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Vzor pole

Vzor pole se podobá vzoru seznamu a lze jej použít k rozložení polí určité délky.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Vzor v závorce

Závorky lze seskupit kolem vzorů, abyste dosáhli požadovaného asociativita. V následujícím příkladu jsou použity kulaté závorky k řízení asociativita mezi vzorem a a modelem nevýhody.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Vzor řazené kolekce členů

Vzor řazené kolekce členů odpovídá vstupu ve formuláři řazené kolekce členů a umožňuje rozdělit řazené kolekce členů pomocí proměnných pro porovnávání vzorů pro každou pozici v řazené kolekci členů.

Následující příklad znázorňuje vzor řazené kolekce členů a také používá vzory literálů, vzorce proměnných a vzor zástupného znaku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Vzor záznamu

Vzor záznamu slouží k rozbalování záznamů pro extrakci hodnot polí. Vzor nemusí odkazovat na všechna pole záznamu; všechna vynechaná pole se nepodílejí na shodě a nejsou extrahována.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Vzor zástupných znaků

Vzor zástupných znaků je reprezentován znakem podtržítka (`_`) a odpovídá jakémukoli vstupu, stejně jako variabilní vzorek, s tím rozdílem, že vstup je zahozen namísto přiřazení proměnné. Vzor zástupných znaků se často používá v jiných vzorcích jako zástupný symbol pro hodnoty, které nejsou nutné ve výrazu napravo `->` od symbolu. Vzor zástupných znaků se také často používá na konci seznamu vzorů, aby odpovídal jakémukoli neodpovídajícímu vstupu. Vzor zástupných znaků je znázorněn v mnoha příkladech kódu v tomto tématu. Viz předchozí kód pro jeden příklad.

## <a name="patterns-that-have-type-annotations"></a>Vzory, které mají anotace typu

Vzory mohou mít anotace typu. Chovají se podobně jako jiné anotace typu a odvozené vodítko jako jiné anotace typu. Pro anotace typu ve vzorcích jsou vyžadovány kulaté závorky. Následující kód ukazuje vzor, který má anotaci typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Vzorek testu typu

Vzor testu typu se používá pro porovnání vstupu proti typu. Pokud je vstupní typ shodný s typem (nebo odvozeného typu) typu zadaného ve vzorku, shoda se zdaří.

Následující příklad ukazuje vzorek testu typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Vzor null

Vzor null odpovídá hodnotě null, která se může zobrazit při práci s typy, které povolují hodnotu null. Vzory null jsou často používány při spolupráci s .NET Framework kódem. Například návratová hodnota rozhraní .NET API může být vstupní `match` hodnotou výrazu. Můžete řídit tok programu na základě toho, zda vrácená hodnota je null, a také na dalších charakteristikách vrácené hodnoty. Pomocí vzoru null můžete zabránit šíření hodnot null do zbytku programu.

Následující příklad používá vzory null a variabilní vzorek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Viz také:

- [Výrazy shody](match-expressions.md)
- [Aktivní vzory](active-patterns.md)
- [Referenční dokumentace jazyka F#](index.md)
