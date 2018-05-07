---
title: Uvozovky kódu (F#)
description: 'Další informace o F # uvozovky kódu, funkce jazyka, která umožňuje generovat a pracovat s výrazy kódu F # prostřednictvím kódu programu.'
ms.date: 05/16/2016
ms.openlocfilehash: a6fab0364cadef1f45276267a59c694140b24a9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="code-quotations"></a>Uvozovky kódu

> [!NOTE]
Rozhraní API použití odkazu přejdete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Toto téma popisuje *code uvozovky*, funkce jazyka, která umožňuje generovat a pracovat s výrazy kódu F # prostřednictvím kódu programu. Tato funkce umožňuje vygenerovat abstraktního syntaktického stromové struktury, která představuje F # – kód. Abstraktního syntaktického stromu můžete pak provázán a zpracovat podle potřeb vaší aplikace. Například můžete stromu ke generování kódu F # nebo generování kódu v některých dalších jazyků.


## <a name="quoted-expressions"></a>Uvozovkách výrazy
A *výrazu v uvozovkách* je výraz F # ve vašem kódu, která je oddělená tak, že není kompilována jako součást vašeho programu, ale místo toho se zkompiluje do objekt, který představuje výraz F #. Můžete označit výraz uvozovkách v jednom ze dvou způsobů: buď s informací o typu nebo bez informací o typu. Pokud chcete zahrnout informace o typu, můžete použít symboly `<@` a `@>` pro vymezení je výraz v uvozovkách. Pokud nepotřebujete informace o typu, můžete použít symboly `<@@` a `@@>`. Následující kód ukazuje typové a bez typu uvozovky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Procházení strom velké výrazu je vyšší, pokud nebudou obsahovat informace o typu. Výsledný typ výraz s typem symboly v uvozovkách je `Expr<'T>`, kde parametr typu má typ výrazu určeného algoritmus odvození typu kompilátoru F #. Když použijete uvozovky kódu bez informací o typu, je typ výrazu uvozovkách neobecný typ [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Můžete volat [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) vlastnost u zadaného objektu `Expr` třída získat netypové `Expr` objektu.

Existuje mnoho různých statických metod, které vám umožní generovat F # výraz objekty prostřednictvím kódu programu v `Expr` třída bez použití v uvozovkách výrazy.

Všimněte si, že kód uvozovek musí obsahovat úplný výraz. Pro `let` vazby, například musíte definice vázané název a další výraz, který používá vazby. V podrobná syntaxe, jedná se o výraz, který následuje `in` – klíčové slovo. Na nejvyšší úrovni v modulu jedná se jenom další výraz v modulu, ale v uvozovky, se výslovně vyžaduje.

Následující výraz proto není platný.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ale těchto výrazů jsou platné.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Chcete-li použít uvozovky kódu, je nutné přidat deklarace importu (pomocí `open` – klíčové slovo), otevře se [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) oboru názvů.

F # PowerPack poskytuje podporu pro vyhodnocení a provádění výrazu objekty F #.


## <a name="expr-type"></a>Výraz typu
Instance `Expr` typ představuje výraz F #. Obecná i neobecnou `Expr` typy jsou popsané v dokumentaci knihovny F #. Další informace najdete v tématu [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) a [quotations.Expr – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).


## <a name="splicing-operators"></a>Splétání operátory
Splétání umožňuje zkombinovat uvozovky literálu kódu s výrazy, které jste vytvořili prostřednictvím kódu programu, nebo z jiného uvozovky kódu. `%` a `%%` operátory umožňují do uvozovek kód přidejte objekt výraz F #. Můžete použít `%` operátor vložení objekt typu výrazu do typu uvozovek; můžete použít `%%` operátor vložení objektu bez typu výraz do bez typu nabídky. Unární operátory předpony jsou obě operátory. Proto pokud `expr` je netypové výrazu typu `Expr`, následující kód je platný.

```fsharp
<@@ 1 + %%expr @@>
```

A pokud `expr` je typu uvozovek typu `Expr<int>`, následující kód je platný.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis
Následující příklad ukazuje použití uvozovky kódu F # – kód vložena objekt výraz a pak postupně kód F #, který představuje výraz. Funkce `println` je definována obsahující rekurzivní funkce `print` který zobrazí objekt výraz F # (typu `Expr`) ve formátu popisný. Existuje několik aktivní vzorky v [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) a [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) moduly, které lze použít k analýze výraz objekty. Tento příklad nezahrnuje všechny možné vzorů, které se může objevit ve výrazu F #. Všechny nerozpoznané vzor aktivuje shoda se zástupnými znaky vzorem (`_`) a je vykreslen pomocí `ToString` metoda, která, na `Expr` typ, umožňuje znáte aktivní vzor pro přidání do vaší výrazu shody.


### <a name="code"></a>Kód
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a>Výstup

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis
Můžete také tři aktivní vzorky v [exprshape – modul](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) procházení stromů výrazů s méně aktivní vzorky. Tyto vzory aktivní může být užitečné, když chcete procházení stromu, ale není nutné všechny informace ve většině uzlů. Použijete-li tyto vzory, jakýkoli výraz F # odpovídá jednomu z následujících tří vzorů: `ShapeVar` li výraz proměnnou, `ShapeLambda` li výraz výraz lambda nebo `ShapeCombination` Pokud je výraz jiný. Pokud jste pomocí aktivní vzorky jako v předchozím příkladu kódu procházejí strom výrazu, budete muset použít mnoho další vzory pro zpracování všech možných typů F # výraz a váš kód bude složitější. Další informace najdete v tématu [ExprShape.ShapeVar&#124;shapelambda –&#124;shapecombination – aktivní vzor](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Následující příklad kódu můžete použít jako základ pro složitější traversals. V tomto kódu strom výrazu se vytvoří pro výraz, který zahrnuje volání funkce `add`. [Specificcall –](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) – aktivní vzor slouží ke zjištění všech volání `add` ve stromové struktuře výraz. Tato – aktivní vzor přiřadí argumenty volání `exprList` hodnotu. V takovém případě jsou uvedeny pouze dvě, tak, aby tyto jsou vyžádat a funkce se volá rekurzivní na argumenty. Výsledky jsou vloženy do uvozovek kód, který představuje volání `mul` pomocí operátoru uživatele programu splice (`%%`). `println` Funkce z předchozího příkladu se používá k zobrazení výsledků.

Kód v jiných – aktivní vzor větví právě regeneruje stejném stromu pro výraz, tak, aby pouze změnu v hodnotě výsledný výraz změnu z `add` k `mul`.


### <a name="code"></a>Kód
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a>Výstup

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

