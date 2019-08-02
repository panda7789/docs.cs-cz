---
title: Uvozovky kódu
description: Seznamte F# se s citacemi kódu, funkcí jazyka, která umožňuje vygenerovat a pracovat F# s výrazy kódu programově.
ms.date: 05/16/2016
ms.openlocfilehash: c6ec0078c685a6452f49edd289b01491dd62e3db
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630414"
---
# <a name="code-quotations"></a>Uvozovky kódu

> [!NOTE]
> Odkaz na odkaz rozhraní API vás převezme na webu MSDN.  Reference k rozhraní docs.microsoft.com API není dokončená.

V tomto tématu jsou popsány *nabídky kódu*, funkce jazyka, která umožňuje vygenerovat a F# pracovat s výrazy kódu programově. Tato funkce umožňuje vygenerovat abstraktní strom syntaxe reprezentující F# kód. Abstraktní strom syntaxe lze následně procházet a zpracovávat podle potřeb vaší aplikace. Stromovou strukturu můžete například použít k vygenerování F# kódu nebo generování kódu v jiném jazyce.

## <a name="quoted-expressions"></a>Výrazy v uvozovkách

*Výraz* v uvozovkách je F# výraz v kódu, který je oddělen takovým způsobem, že není zkompilován jako součást programu, ale místo toho je zkompilován do objektu, který představuje F# výraz. Citovaný výraz můžete označit jedním ze dvou způsobů: buď s typem informací, nebo bez informací o typu. Chcete-li zahrnout informace o typu, použijte symboly `<@` a `@>` k vymezení citovaného výrazu. Pokud nepotřebujete informace o typu, použijte symboly `<@@` a. `@@>` Následující kód ukazuje typové a netypové citace.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Procházení velkého stromu výrazů je rychlejší, Pokud nezahrnete informace o typu. Výsledný typ výrazu v uvozovkách se zadanými symboly je `Expr<'T>`, kde parametr typu má typ výrazu, který je určen algoritmem odvození typu F# kompilátoru. Použijete-li citace kódu bez informací o typu, je typ výrazu v uvozovkách výrazem neobecného [typu.](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65) K získání netypového `Expr` objektu můžete zavolat nezpracovaný vlastnost na typované [](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) `Expr` třídě.

Existuje celá řada statických metod, které umožňují programově generovat F# objekty výrazu ve `Expr` třídě bez použití citovaných výrazů.

Všimněte si, že citace kódu musí zahrnovat úplný výraz. `let` U vazby například potřebujete jak definici vázaného názvu, tak i další výraz, který používá vazbu. V podrobné syntaxi je to výraz, který následuje za `in` klíčovým slovem. V nejvyšší úrovni modulu se jedná o jenom další výraz v modulu, ale v citace se explicitně vyžaduje.

Proto následující výraz není platný.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Následující výrazy jsou ale platné.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Chcete- F# li vyhodnotit citace, je nutné použít [ F# vyhodnocení citace](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Poskytuje podporu pro vyhodnocování a spouštění F# objektů výrazů.

## <a name="expr-type"></a>Typ výrazu

Instance `Expr` typu představuje F# výraz. Obecné i neobecné `Expr` typy jsou zdokumentovány v dokumentaci F# knihovny. Další informace najdete v tématu [obor názvů Microsoft. FSharp. quots](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) a [quots. expr](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Operátory spojování

Spojení umožňuje kombinovat citace literálového kódu s výrazy, které jste vytvořili programově nebo z jiné nabídky kódu. Operátory `%` a `%%` umožňují přidat objekt F# výrazu do nabídky kódu. `%` Operátor můžete použít k vložení typovaného objektu výrazu do typované citace; `%%` pomocí operátoru vložíte Netypový objekt výrazu do netypové citace. Oba operátory jsou unární operátory prefixu. Proto je `expr` -li výraz `Expr`netypového typu, je platný následující kód.

```fsharp
<@@ 1 + %%expr @@>
```

A pokud `expr` je typové citace typu `Expr<int>`, je následující kód platný.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ilustruje použití citace kódu pro vložení F# kódu do objektu Expression a následné vytisknutí F# kódu, který reprezentuje výraz. Funkce `println` je definována, která obsahuje rekurzivní funkci `print` , která zobrazuje objekt F# výrazu (typu `Expr`) v popisném formátu. Existuje několik aktivních vzorů v modulech [Microsoft. FSharp. quotes. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) a [Microsoft. FSharp. quotes. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) , které lze použít k analýze objektů výrazů. Tento příklad nezahrnuje všechny možné vzory, které se mohou objevit ve F# výrazu. Libovolný nerozpoznaný vzor aktivuje shodu se zástupným`_`vzorem () a je vykreslen `ToString` pomocí metody `Expr` , která na typu umožňuje, abyste věděli aktivní vzor, který chcete přidat do výrazu shody.

### <a name="code"></a>Kód

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Výstup

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Můžete také použít tři aktivní vzory v [modulu ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) k procházení stromů výrazů s menším počtem aktivních vzorů. Tyto aktivní vzory mohou být užitečné, pokud chcete procházet stromovou strukturou, ale nepotřebujete všechny informace ve většině uzlů. Použijete-li tyto vzory, F# libovolný výraz odpovídá jednomu z následujících tří vzorů `ShapeVar` : Pokud `ShapeLambda` je výraz výraz lambda, nebo `ShapeCombination` Pokud je výraz cokoli jiného. Pokud přecházíte do stromu výrazů pomocí aktivních vzorů, jako v předchozím příkladu kódu, musíte použít mnoho dalších vzorů pro zpracování všech možných F# typů výrazů a váš kód bude složitější. Další informace najdete v tématu [ExprShape. ShapeVar&#124;ShapeLambda&#124;ShapeCombination – – aktivní vzor](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Následující příklad kódu lze použít jako základ pro složitější procházení. V tomto kódu je vytvořen strom výrazu pro výraz, který zahrnuje volání `add`funkce. [SpecificCall –](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) aktivní vzor slouží ke zjištění libovolného volání `add` ve stromu výrazu. Tento aktivní vzor přiřadí argumenty volání `exprList` hodnoty. V tomto případě jsou k dispozici pouze dva, takže jsou vyvolány a funkce se zavolá rekurzivně na argumenty. Výsledky jsou vloženy do nabídky kódu, která představuje volání `mul` pomocí operátoru splice (`%%`). `println` Funkce z předchozího příkladu se používá k zobrazení výsledků.

Kód v ostatních větvích aktivních vzorů právě znovu vygeneruje stejný strom výrazů, takže jediná změna ve výsledném výrazu je změna z `add` na. `mul`

### <a name="code"></a>Kód

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Výstup

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
