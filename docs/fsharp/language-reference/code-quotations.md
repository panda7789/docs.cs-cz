---
title: Uvozovky kódu
description: Další informace o F# uvozovky kódu, funkce jazyka, která umožňuje generovat a pracovat s F# kódu výrazy prostřednictvím kódu programu.
ms.date: 05/16/2016
ms.openlocfilehash: 464df5e3fafa683c93fd5fb6e94d24c229903491
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642005"
---
# <a name="code-quotations"></a>Uvozovky kódu

> [!NOTE]
> Odkaz rozhraní API se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

Toto téma popisuje *nabídky kódu*, jazyk funkce, která vám umožní vytvořit a pracovat s F# kódu výrazy prostřednictvím kódu programu. Tato funkce umožňuje vygenerovat strom abstraktní syntaxe představující F# kódu. Strom abstraktní syntaxe můžete potom Procházet a zpracovávat podle potřeb svojí aplikace. Například tree můžete použít ke generování F# kódu nebo generování kódu v nějakém jiném jazyce.

## <a name="quoted-expressions"></a>Výrazy v uvozovkách

A *citovaný výraz* je F# výraz ve vašem kódu, který je oddělen tak, že není zkompilován jako součást vašich programů, ale místo toho je objekt, který představuje zkompilován F# výraz. Můžete označit citovaný výraz v jednom ze dvou způsobů: buď s informací o typu, nebo bez informace o typu. Pokud chcete zahrnout informace o typu, použijte symboly `<@` a `@>` pro vymezení výraz v uvozovkách. Pokud nepotřebujete informace o typu, použijte symboly `<@@` a `@@>`. Následující kód ukazuje typové a netypové citace.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Procházení stromu velké výrazu je rychlejší, pokud neobsahují informace o typu. Výsledný typ výrazu v uvozovkách s typem symbolů je `Expr<'T>`, kde parametr typu má typ výrazu podle F# algoritmus odvození typu kompilátoru. Při použití uvozovky kódu bez informací o typu je typ výrazu v uvozovkách neobecný typ [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Můžete volat [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) vlastnosti zadaného objektu `Expr` třídy získat netypové `Expr` objektu.

Existuje řada různých statických metod, které umožňují generování F# výraz objekty programově v `Expr` třídy bez použití v uvozovkách výrazy.

Všimněte si, že typového kódu musí obsahovat úplný výraz. Pro `let` vazby, například musíte definice názvu vazby a další výraz, který používá vazba. V podrobné syntaxi, to je výraz, který následuje `in` – klíčové slovo. Na nejvyšší úrovni v modulu to je jenom další výraz v modulu, ale v citaci, je explicitně vyžaduje.

Proto následující výraz není platný.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Ale tyto výrazy jsou platné.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Pokud chcete použít uvozovky kódu, je nutné přidat deklarace importu (pomocí `open` – klíčové slovo), která otevře [Microsoft.fsharp.quotations –](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) oboru názvů.

F# PowerPack poskytuje podporu pro testování a provádění F# objekty výrazů.

## <a name="expr-type"></a>Výraz typu

Instance `Expr` zadejte představuje F# výrazu. Obecné a neobecné `Expr` typy jsou dokumentovány v článku F# dokumentaci ke knihovně. Další informace najdete v tématu [Microsoft.fsharp.quotations – Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) a [quotations.Expr – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Operátory spojení

Spojení umožňují kombinovat uvozovky literálu kódu s výrazy, které jste vytvořili prostřednictvím kódu programu nebo z jiného typového kódu. `%` a `%%` operátory umožňují snadno přidat F# výraz objektu do typového kódu. Můžete použít `%` operátor vložení zadaný výraz objektu do typu nabídky; můžete použít `%%` operátor vložení objektu netypové výraz do netypové nabídky. Oba operátory jsou unární operátory prefix. Proto pokud `expr` je netypové výraz typu `Expr`, následující kód je platný.

```fsharp
<@@ 1 + %%expr @@>
```

A pokud `expr` je typovaná nabídku typu `Expr<int>`, následující kód je platný.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje použití uvozovky kódu vložit F# kódu do výrazu objektu a poté vytiskněte F# kód, který představuje výraz. Funkce `println` je definován, který obsahuje rekurzivní funkci `print` , který zobrazí F# objekt výrazu (typu `Expr`) ve formátu popisný. Existuje několik aktivní vzory v [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) a [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) moduly, které lze použít k analýze objekty výrazů. V tomto příkladu neobsahuje všechny možné vzorky, které se může objevit F# výrazu. Některé nebyl rozpoznán vzor aktivuje shody pro vzor zástupných znaků (`_`) a je vykreslen pomocí `ToString` metoda, který na `Expr` zadejte vás informuje, – aktivní vzor pro přidání do výrazu match.

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

Můžete také použít tři aktivní vzory v [exprshape – modul](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) k procházení stromů výrazů s menším počtem aktivní vzory. Tyto vzory aktivní může být užitečné, když chcete procházení stromu, ale není nutné všechny informace ve většině uzlů. Když použijete tyto vzory všechny F# výraz odpovídá jednomu z následujících tří vzorů: `ShapeVar` Pokud má výraz hodnotu proměnné, `ShapeLambda` Pokud je výraz lambda výraz nebo `ShapeCombination` Pokud má výraz hodnotu cokoli jiného. Pokud procházení stromu výrazů s využitím aktivní vzory stejně jako v předcházejícím příkladu, budete muset použít mnoho další postupy pro zpracování všech možných F# typy výrazů a váš kód bude složitější. Další informace najdete v tématu [ExprShape.ShapeVar&#124;shapelambda –&#124;shapecombination – aktivní vzor](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Následující příklad kódu lze použít jako základ pro složitější procházení. V tomto kódu se vytvoří strom výrazu pro výraz, který zahrnuje volání funkce, `add`. [Specificcall –](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) – aktivní vzor slouží ke zjištění voláním `add` ve stromu výrazu. Tato – aktivní vzor přiřadí argumenty volání `exprList` hodnotu. V tomto případě existují jenom dvě, tak tyto se berou navýšení kapacity a je zavolána funkce rekurzivně na argumenty. Výsledky jsou vloženy do kódu nabídky, která reprezentuje volání `mul` použití operátoru spojení (`%%`). `println` Funkce z předchozího příkladu se používá k zobrazení výsledků.

Kódu v jiných větvích – aktivní vzor jenom znovu vygeneruje stejný strom výrazu, tak jenom změnu v hodnotě výsledný výraz je změna z `add` k `mul`.

### <a name="code"></a>Kód

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Výstup

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
