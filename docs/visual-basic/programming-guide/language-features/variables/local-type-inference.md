---
title: Odvození místního typu
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 3979396d32aa5d3b853aa087d43f70d5987e510b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410396"
---
# <a name="local-type-inference-visual-basic"></a>Odvození místního typu (Visual Basic)

Kompilátor Visual Basic používá *odvození typu* k určení datových typů místních proměnných deklarovaných bez `As` klauzule. Kompilátor odvodí typ proměnné z typu inicializačního výrazu. To umožňuje deklarovat proměnné bez explicitního oznámení typu, jak je znázorněno v následujícím příkladu. V důsledku deklarací `num1` jsou oba a `num2` silně typované jako celá čísla.

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> Pokud nechcete `num2` , aby byl v předchozím příkladu zadán jako `Integer` , lze zadat jiný typ pomocí deklarace jako `Dim num3 As Object = 3` nebo `Dim num4 As Double = 3` .

> [!NOTE]
> Odvození typu lze použít pouze pro nestatické lokální proměnné; nelze ji použít k určení typu polí třídy, vlastností nebo funkcí.

Odvození místního typu se vztahuje na úrovni procedury. Nedá se použít k deklaraci proměnných na úrovni modulu (v rámci třídy, struktury, modulu nebo rozhraní, ale ne v rámci procedury nebo bloku). Pokud `num2` byl v předchozím příkladu pole třídy namísto lokální proměnné v proceduře, deklarace by způsobila chybu `Option Strict` na v a měla by klasifikovat `num2` jako `Object` `Option Strict` off. Podobně odvození místního typu se nevztahuje na proměnné na úrovni procedury deklarované jako `Static` .

## <a name="type-inference-vs-late-binding"></a>Odvození typu a pozdní vazba

Kód, který používá odvození typu, se podobá kódu, který závisí na pozdní vazbě. Nicméně odvození typu je místo toho, aby je proměnná zanechala jako `Object` . Kompilátor používá inicializátor proměnné k určení typu proměnné v době kompilace pro vytvoření kódu na začátku vazby. V předchozím příkladu, například `num2` `num1` , je jako typ zadán `Integer` .

Chování proměnných s časnou vazbou se liší od proměnné s pozdní vazbou, pro které je typ znám pouze v době běhu. Znalost typu předčasné umožňuje kompilátoru identifikovat problémy před provedením, přidělit paměť přesně a provádět další optimalizace. Časná vazba také umožňuje Visual Basic integrované vývojové prostředí (IDE), které poskytuje nápovědu IntelliSense o členech objektu. Pro výkon je upřednostňována i počáteční vazba. Důvodem je, že všechna data uložená v proměnné s pozdní vazbou musí být zabalena jako typ `Object` a přístup k členům typu za běhu program zpomalí.

## <a name="examples"></a>Příklady

Odvození typu nastane, pokud je místní proměnná deklarována bez `As` klauzule a inicializovaná. Kompilátor používá typ přiřazené počáteční hodnoty jako typ proměnné. Například každý z následujících řádků kódu deklaruje proměnnou typu `String` .

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

Následující kód ukazuje dva ekvivalentní způsoby, jak vytvořit pole celých čísel.

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

Je vhodné použít odvození typu k určení typu řídicí proměnné smyčky. V následujícím kódu kompilátor odvodí, že v `number` `Integer` `someNumbers2` předchozím příkladu je pole celých čísel.

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

Odvození místního typu lze použít v `Using` příkazech k vytvoření typu názvu prostředku, jak ukazuje následující příklad.

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

Typ proměnné lze také odvodit z vrácených hodnot funkcí, jak ukazuje následující příklad. `pList1`A `pList2` jsou pole procesů, protože `Process.GetProcesses` vrací pole procesů.

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a>Odvoditelné možnosti

`Option Infer`umožňuje určit, zda bude odvození místního typu povoleno v určitém souboru. Chcete-li povolit nebo zablokovat možnost, zadejte na začátku souboru jeden z následujících příkazů.

`Option Infer On`

`Option Infer Off`

Pokud nezadáte hodnotu pro `Option Infer` v kódu, je výchozí kompilátor `Option Infer On` .

Pokud je hodnota nastavená `Option Infer` v souboru v konfliktu s hodnotou nastavenou v integrovaném vývojovém prostředí (IDE) nebo na příkazovém řádku, má hodnota v souboru přednost.

Další informace naleznete v tématu [možnost odvození příkazu](../../../language-reference/statements/option-infer-statement.md) a [Stránka kompilace, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

## <a name="see-also"></a>Viz také

- [Anonymní typy](../objects-and-classes/anonymous-types.md)
- [Počáteční a pozdní vazba](../early-late-binding/index.md)
- [For Each...Next – příkaz](../../../language-reference/statements/for-each-next-statement.md)
- [For...Next – příkaz](../../../language-reference/statements/for-next-statement.md)
- [Option Infer – příkaz](../../../language-reference/statements/option-infer-statement.md)
- [-optioninfer](../../../reference/command-line-compiler/optioninfer.md)
- [Představení technologie LINQ v jazyce Visual Basic](../linq/introduction-to-linq.md)
