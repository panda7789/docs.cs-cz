---
title: Uvozovky kódu
description: 'Přečtěte si o uvozovkách kódu F #, funkce jazyka, která umožňuje vygenerovat a pracovat s výrazy kódu F # programově.'
ms.date: 05/16/2016
ms.openlocfilehash: bb5c03edd180c42667731bb90d7a1f624ed2e522
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855389"
---
# <a name="code-quotations"></a>Citace kódu

Tento článek popisuje *citace kódu*, funkci jazyka, která umožňuje vygenerovat a pracovat s výrazy kódu F # programově. Tato funkce umožňuje vygenerovat abstraktní strom syntaxe, který představuje kód jazyka F #. Abstraktní strom syntaxe lze následně procházet a zpracovávat podle potřeb vaší aplikace. Stromovou strukturu můžete například použít ke generování kódu F # nebo k vygenerování kódu v jiném jazyce.

> [!NOTE]
> Reference k rozhraní docs.microsoft.com API pro F # není dokončená. Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="quoted-expressions"></a>Výrazy v uvozovkách

*Výraz v uvozovkách* je výraz jazyka F # v kódu, který je oddělen takovým způsobem, že není zkompilován jako součást programu, ale je zkompilován do objektu, který představuje výraz jazyka f #. Citovaný výraz můžete označit jedním ze dvou způsobů: buď s typem informací, nebo bez informací o typu. Chcete-li zahrnout informace o typu, použijte symboly `<@` a `@>` k vymezení citovaného výrazu. Pokud nepotřebujete informace o typu, použijte symboly `<@@` a `@@>` . Následující kód ukazuje typové a netypové citace.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Procházení velkého stromu výrazů je rychlejší, Pokud nezahrnete informace o typu. Výsledný typ výrazu v uvozovkách se zadanými symboly je `Expr<'T>` , kde parametr typu má typ výrazu, který je určen algoritmem odvození typu kompilátorem jazyka F #. Použijete-li citace kódu bez informací o typu, je typ výrazu v uvozovkách výrazem neobecného [typu.](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65) K získání netypového objektu můžete zavolat [nezpracovaný](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) vlastnost na typované `Expr` třídě `Expr` .

Existuje celá řada statických metod, které umožňují generovat objekty výrazu jazyka F # programově ve `Expr` třídě bez použití výrazů v uvozovkách.

Všimněte si, že citace kódu musí zahrnovat úplný výraz. U `let` vazby například potřebujete jak definici vázaného názvu, tak i další výraz, který používá vazbu. V podrobné syntaxi je to výraz, který následuje za `in` klíčovým slovem. V nejvyšší úrovni modulu se jedná o jenom další výraz v modulu, ale v citace se explicitně vyžaduje.

Proto následující výraz není platný.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Následující výrazy jsou ale platné.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Chcete-li vyhodnotit citace F #, je nutné použít [vyhodnocovací filtr nabídek f #](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Poskytuje podporu pro vyhodnocování a provádění objektů výrazu jazyka F #.

## <a name="expr-type"></a>Typ výrazu

Instance `Expr` typu představuje výraz F #. Obecné i neobecné `Expr` typy jsou zdokumentovány v dokumentaci knihovny F #. Další informace najdete v tématu [obor názvů Microsoft. FSharp. quots](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) a [quots. expr](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Operátory spojování

Spojení umožňuje kombinovat citace literálového kódu s výrazy, které jste vytvořili programově nebo z jiné nabídky kódu. `%`Operátory a `%%` umožňují přidat objekt výrazu F # do nabídky kódu. Operátor můžete použít `%` k vložení typovaného objektu výrazu do typované citace; pomocí `%%` operátoru vložíte Netypový objekt výrazu do netypové citace. Oba operátory jsou unární operátory prefixu. Proto `expr` je-li výraz netypového typu `Expr` , je platný následující kód.

```fsharp
<@@ 1 + %%expr @@>
```

A pokud `expr` je typové citace typu `Expr<int>` , je následující kód platný.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ilustruje použití nabídek kódu k vložení kódu F # do objektu Expression a následné vytisknutí kódu F #, který představuje výraz. Funkce `println` je definována, která obsahuje rekurzivní funkci `print` , která zobrazuje objekt výrazu jazyka F # (typu `Expr` ) v popisném formátu. Existuje několik aktivních vzorů v modulech [Microsoft. FSharp. quotes. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) a [Microsoft. FSharp. quotes. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) , které lze použít k analýze objektů výrazů. Tento příklad nezahrnuje všechny možné vzory, které se mohou objevit ve výrazu jazyka F #. Libovolný nerozpoznaný vzor aktivuje shodu se zástupným vzorem ( `_` ) a je vykreslen pomocí `ToString` metody, která na `Expr` typu umožňuje, abyste věděli aktivní vzor, který chcete přidat do výrazu shody.

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

Můžete také použít tři aktivní vzory v [modulu ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) k procházení stromů výrazů s menším počtem aktivních vzorů. Tyto aktivní vzory mohou být užitečné, pokud chcete procházet stromovou strukturou, ale nepotřebujete všechny informace ve většině uzlů. Použijete-li tyto vzory, jakýkoli výraz F # odpovídá jednomu z následujících tří vzorů: je-li výraz proměnná, je-li výraz `ShapeVar` `ShapeLambda` výraz lambda, nebo `ShapeCombination` Pokud je výraz cokoli jiného. Pokud přecházíte do stromu výrazů pomocí aktivních vzorů, jako v předchozím příkladu kódu, musíte použít mnoho dalších vzorů pro zpracování všech možných typů výrazů F # a váš kód bude složitější. Další informace najdete v tématu [ExprShape. ShapeVar&#124;ShapeLambda&#124;ShapeCombination – aktivní vzor](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

Následující příklad kódu lze použít jako základ pro složitější procházení. V tomto kódu je vytvořen strom výrazu pro výraz, který zahrnuje volání funkce `add` . [SpecificCall –](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) aktivní vzor slouží ke zjištění libovolného volání `add` ve stromu výrazu. Tento aktivní vzor přiřadí argumenty volání `exprList` hodnoty. V tomto případě jsou k dispozici pouze dva, takže jsou vyvolány a funkce se zavolá rekurzivně na argumenty. Výsledky jsou vloženy do nabídky kódu, která představuje volání `mul` pomocí operátoru splice ( `%%` ). `println`Funkce z předchozího příkladu se používá k zobrazení výsledků.

Kód v ostatních větvích aktivních vzorů právě znovu vygeneruje stejný strom výrazů, takže jediná změna ve výsledném výrazu je změna z `add` na `mul` .

### <a name="code"></a>Kód

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Výstup

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
