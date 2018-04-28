---
title: Porovnávání vzorů (F#)
description: 'Zjistěte, jak se používají vzory v jazyce F # k porovnání dat pomocí logické struktury, rozloží data na základní části nebo extrahovat informace z dat.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 31a5b321e5daecdc3add9a205d60b63b2c00ccd2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="pattern-matching"></a>Porovnávání vzorů

Vzory jsou pravidla pro transformaci vstupní data. Používají se v průběhu jazyk F # k porovnání data pomocí logické struktury nebo struktury, rozloží data na základní části nebo extrahovat informace z dat různými způsoby.


## <a name="remarks"></a>Poznámky
Vzorky se používají v mnoha jazykové konstrukty, jako `match` výraz. Se používají při zpracování argumenty pro funkce v `let` vazby, výrazů lambda a v obslužné rutiny výjimek, které jsou přidružené k `try...with` výraz. Další informace najdete v tématu [výrazy shody](match-expressions.md), [let – vazby](functions/let-bindings.md), [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md), a [výjimkami: `try...with` Výraz](exception-handling/the-try-with-expression.md).

Například v `match` výrazu *vzor* je co následuje symbol kanálu.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Každý vzor funguje jako pravidlo pro transformaci vstup nějakým způsobem. V `match` výrazu, každý vzor je ověřuje, pak pokud vstupní data je kompatibilní s vzoru. Pokud je nalezena shoda, se spustí výsledek výrazu. Pokud není nalezena shoda, je otestovat další vzor pravidel. Volitelné při *podmínku* části je vysvětlen v [výrazy shody](match-expressions.md).

V následující tabulce jsou uvedeny podporované vzory. V době běhu vstup je testován vůči každé z následujících vzory v uvedeném v tabulce pořadí a vzory jsou rekurzivně, z první poslední jak se objeví ve vašem kódu a zleva doprava pro vzory na každém řádku.

|Název|Popis|Příklad|
|----|-----------|-------|
|Konstantní vzor|Jakékoli číselné, znak, nebo řetězcový literál, konstanta výčtu nebo identifikátor definovaný literálu|`1.0`, `"test"`, `30`, `Color.Red`|
|Identifikátor – vzor|Hodnota case rozlišovaná sjednocení, popisek výjimky nebo s případem – aktivní vzor|`Some(x)`<br /><br />`Failure(msg)`|
|Proměnná – vzor|*Identifikátor*|`a`|
|`as` vzor|*vzor* jako *identifikátor*|`(a, b) as tuple1`|
|NEBO vzor|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|A vzor|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Cons vzor|*identifikátor* :: *seznamu identifikátorů*|`h :: t`|
|Seznam – vzor|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Pole – vzor|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Závorky – vzor|( *vzor* )|`( a )`|
|Vzor řazené kolekce členů|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Záznam – vzor|{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Zástupný znak – vzor|_|`_`|
|Vzor společně s anotaci typu|*vzor* : *typu*|`a : int`|
|Typ testu vzor|:? *typ* [jako *identifikátor* ]|`:? System.DateTime as dt`|
|Null – vzor|null|`null`|

## <a name="constant-patterns"></a>Konstantní vzory
Konstantní vzorky se číselný znak a textové literály konstanty výčtu (s názvem typu výčtu zahrnuté). A `match` výraz, který má pouze konstantní vzory lze porovnat s hodnotou pro příkaz case v dalších jazycích. Vstup se porovná s literálovou hodnotou a vzor odpovídá, pokud jsou hodnoty stejné. Typ literál musí být kompatibilní s typem vstupu.

Následující příklad ukazuje použití literálu vzory a také používá proměnné vzor a nebo vzor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Další příklad literálu vzor je vzor, podle konstanty výčtu. Při použití konstanty výčtu, musíte zadat název typu výčtu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Identifikátor vzory
Pokud vzor je řetězec znaků, která tvoří platný identifikátor, formu identifikátor určuje, jak je shodují se vzorem. Pokud identifikátor je delší než jeden znak a začíná velké písmeno, kompilátor se pokouší provést odpovídající vzor identifikátoru. Identifikátor pro tento vzor může být hodnota označené jako atribut literálu, rozlišovaná – případ typu union, výjimka identifikátoru nebo případ – aktivní vzor. Pokud se nenajde žádný odpovídající identifikátor, shoda se nezdaří a další vzor pravidel, proměnná – vzor, je ve srovnání s vstupu.

Rozlišovaná sjednocení vzory může být jednoduchý s názvem případech nebo můžou mít hodnotu nebo řazené kolekce členů obsahující více hodnot. Pokud je hodnota, je nutné zadat identifikátor pro hodnotu. V případě řazené kolekce členů je nutné zadat vzorek řazené kolekce členů s identifikátorem pro každý prvek řazenou kolekci členů nebo identifikátor jiný název pro jednu nebo více s názvem union pole. Příklady kódu v této části Příklady.

`option` Typ je rozlišovaná sjednocení, která má dva případy `Some` a `None`. Jeden případ (`Some`) má hodnotu, ale druhá (`None`) je právě pojmenované případu. Proto `Some` musí mít proměnnou pro hodnotu přidruženou `Some` případu, ale `None` musí být samostatně. V následujícím kódu, proměnná `var1` je zadána hodnota, která se získávají pomocí odpovídajících k `Some` případu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

V následujícím příkladu `PersonName` rozlišovaná sjednocení obsahuje směs řetězce a znaky, které představují možné formy názvy. V případech rozlišovaná sjednocení jsou `FirstOnly`, `LastOnly`, a `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Pro rozlišovaná sjednocení, které mají pojmenované pole použijete k získání hodnoty z pole s názvem symbolem rovná se (=). Představte si třeba rozlišovaná sjednocení s deklaraci podobně jako tento.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Pole s názvem ve výrazu odpovídající vzor můžete použít následujícím způsobem.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

Použití s názvem pole je volitelné, takže v předchozím příkladu obě `Circle(r)` a `Circle(radius = r)` mají stejný účinek.

Pokud zadáte více polí, použijte středník (;) jako oddělovač.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Aktivní vzorky umožňují definovat složitější odpovídající vlastní vzorek. Další informace o aktivní vzorky najdete v tématu [aktivní vzorky](active-patterns.md).

Případ, ve kterém je identifikátor výjimku se používá v porovnávání se v kontextu obslužné rutiny výjimek. Informace o porovnávání se ve zpracování výjimek najdete v tématu [výjimkami: `try...with` výraz](exception-handling/the-try-with-expression.md).


## <a name="variable-patterns"></a>Proměnné vzory
Hodnota se namapovat na název proměnné, která je pak k dispozici pro použití ve výrazu provádění napravo od přiřadí proměnné vzor `->` symbol. Žádný vstup odpovídá proměnné vzor samostatně, ale proměnné vzory často se v rámci jiné vzory, proto povolení složitější struktury například řazených kolekcí členů a aby rozložit na proměnné pole.

Následující příklad ukazuje, proměnná – vzor v rámci vzor řazené kolekce členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>As – vzor
`as` Vzor je vzor, který má `as` klauzule, přidá se k němu. `as` Klauzule váže odpovídající hodnotu pro název, který lze použít ve výrazu provádění `match` výrazu, nebo v případě, kdy se tento vzor používá v `let` vazby, název je přidán jako vazbu na místní obor.

Následující příklad používá `as` vzor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>NEBO vzor
Vzor nebo se používá, pokud vstupní data může odpovídat více vzorů, a chcete provést v důsledku stejný kód. Typy obou stranách vzoru nebo musí být kompatibilní.

Následující příklad ukazuje nebo vzor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>A vzor
Vzor a vyžaduje, aby vstupní shodovala dva vzory. Typy obou stranách tohoto vzoru a musí být kompatibilní.

V následujícím příkladu je stejná jako `detectZeroTuple` ukazuje [řazené kolekce členů vzor](https://msdn.microsoft.com/library/#tuple) části později v tomto tématu, ale zde obě `var1` a `var2` zjištěny jako hodnoty pomocí vzoru a.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Cons vzor
Vzor cons se používá k rozložit na první prvek seznamu *head*a seznam obsahující zbývající elementy, *tail*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Seznam – vzor
Vzor seznamu umožňuje seznamy musí rozložit na počet elementů. Vzor seznamu sám může odpovídat pouze seznam konkrétní počet elementů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Pole – vzor
Vzor pole vypadá takto: seznam – vzor a slouží k rozložit pole konkrétní délku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Závorky – vzor
Závorky lze seskupovat kolem vzory k dosažení požadované asociativnost. V následujícím příkladu kulaté závorky slouží k řízení asociativnost mezi a vzor a vzor nevýhody.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Vzor řazené kolekce členů
Řazené kolekce členů vzor odpovídá vstup ve formuláři řazené kolekce členů a umožňuje řazené kolekce členů musí rozložit na jeho základní prvky pomocí proměnných pro každý pozice v řazené kolekci členů porovnávání vzorů.

Následující příklad ukazuje vzoru řazené kolekce členů a také používá literálu vzory, proměnné vzorce a zástupný znak – vzor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Záznam – vzor
Vzor záznam se používá k rozložit záznamy k extrakci hodnoty polí. Chcete-li všechna pole záznamu; nemá vzoru všechna pole vynechání právě neúčastnit odpovídající a nejsou rozbalené.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Zástupný znak – vzor
Zástupný znak – vzor je reprezentována podtržítko (`_`) znak a odpovídá žádný vstup, stejně jako proměnné vzor, s tím rozdílem, že vstup se zahodí místo přiřazený k proměnné. Zástupný znak – vzor se často používá v rámci jiných vzorů jako zástupný symbol pro hodnoty, které nejsou potřebné ve výrazu napravo `->` symbol. Zástupný znak – vzor slouží také často na konci seznam vzorů tak, aby odpovídaly jakékoli neodpovídající vstup. Zástupný znak – vzor je znázorněn v mnoha příklady kódu v tomto tématu. Viz předchozí kód pro jedním z příkladů.


## <a name="patterns-that-have-type-annotations"></a>Vzorce, které mají typ poznámky
Vzory může mít typ poznámek. Tyto chovají jako dalších typů poznámek a Průvodce odvození jako dalších typ poznámek. Kolem typ poznámky v vzory jsou vyžadovány závorky. Následující kód ukazuje vzor, který má anotaci typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Typ testu vzor
Typ testu vzor slouží k přiřazování vstup podle typu. Pokud vstupní typ je shoda pro (nebo odvozené typ) s typem zadaným ve vzoru shody úspěšné.

Následující příklad ukazuje typ testovací vzorek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Null – vzor
Null vzor odpovídá hodnotu null, která se může zobrazit při práci s typy, které umožňují hodnotu null. Null vzorů se často používají při interoperabilitě se službou kódu rozhraní .NET Framework. Návratová hodnota rozhraní API .NET může být například vstup `match` výraz. Můžete řídit tok programu na základě, zda je návratovou hodnotu null a také na dalších vlastností vrácené hodnoty. Null vzor můžete zabránit s ostatními vašeho programu při šíření hodnoty null.

Následující příklad používá vzoru hodnotu null a proměnná – vzor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Viz také
[Výrazy shody](match-expressions.md)

[Aktivní vzory](active-patterns.md)

[Referenční dokumentace jazyka F#](index.md)
