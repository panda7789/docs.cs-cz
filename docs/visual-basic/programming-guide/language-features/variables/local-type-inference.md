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
ms.openlocfilehash: f79ac70aecb5805a3a4a4fea8f7e7ccd3f8243fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351838"
---
# <a name="local-type-inference-visual-basic"></a>Odvození místního typu (Visual Basic)

Kompilátor Visual Basic používá *odvození typu* k určení datových typů místních proměnných deklarovaných bez klauzule `As`. Kompilátor odvodí typ proměnné z typu inicializačního výrazu. To umožňuje deklarovat proměnné bez explicitního oznámení typu, jak je znázorněno v následujícím příkladu. V důsledku deklarací jsou jako celé číslo `num1` i `num2` silného typu.

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> Pokud nechcete, aby `num2` v předchozím příkladu jako `Integer`, můžete zadat jiný typ pomocí deklarace, jako je `Dim num3 As Object = 3` nebo `Dim num4 As Double = 3`.

> [!NOTE]
> Odvození typu lze použít pouze pro nestatické lokální proměnné; nelze ji použít k určení typu polí třídy, vlastností nebo funkcí.

Odvození místního typu se vztahuje na úrovni procedury. Nedá se použít k deklaraci proměnných na úrovni modulu (v rámci třídy, struktury, modulu nebo rozhraní, ale ne v rámci procedury nebo bloku). Pokud `num2` v předchozím příkladu byly polem třídy namísto lokální proměnné v proceduře, by deklarace způsobila chybu s `Option Strict` na a mohla klasifikovat `num2` jako `Object` s `Option Strict` vypnuto. Podobně odvození místního typu se nevztahuje na proměnné na úrovni procedury deklarované jako `Static`.

## <a name="type-inference-vs-late-binding"></a>Odvození typu a pozdní vazba

Kód, který používá odvození typu, se podobá kódu, který závisí na pozdní vazbě. Nicméně odvození typu je místo toho, aby byla proměnná ponechána jako `Object`. Kompilátor používá inicializátor proměnné k určení typu proměnné v době kompilace pro vytvoření kódu na začátku vazby. V předchozím příkladu je `num2`jako `num1`typu `Integer`.

Chování proměnných s časnou vazbou se liší od proměnné s pozdní vazbou, pro které je typ znám pouze v době běhu. Znalost typu předčasné umožňuje kompilátoru identifikovat problémy před provedením, přidělit paměť přesně a provádět další optimalizace. Časná vazba také umožňuje Visual Basic integrované vývojové prostředí (IDE), které poskytuje nápovědu IntelliSense o členech objektu. Pro výkon je upřednostňována i počáteční vazba. Důvodem je, že všechna data uložená v proměnné s pozdní vazbou musí být zabalena jako typ `Object`a přístup k členům typu za běhu program zpomalí.

## <a name="examples"></a>Příklady

Odvození typu nastane, pokud je místní proměnná deklarována bez klauzule `As` a inicializovaná. Kompilátor používá typ přiřazené počáteční hodnoty jako typ proměnné. Například každý z následujících řádků kódu deklaruje proměnnou typu `String`.

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

Následující kód ukazuje dva ekvivalentní způsoby, jak vytvořit pole celých čísel.

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

Je vhodné použít odvození typu k určení typu řídicí proměnné smyčky. V následujícím kódu kompilátor odvodí, že `number` je `Integer`, protože `someNumbers2` z předchozího příkladu je pole celých čísel.

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

Odvození místního typu lze použít v příkazech `Using` pro vytvoření typu názvu prostředku, jak ukazuje následující příklad.

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

Typ proměnné lze také odvodit z vrácených hodnot funkcí, jak ukazuje následující příklad. `pList1` i `pList2` jsou pole procesů, protože `Process.GetProcesses` vrací pole procesů.

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a>Odvoditelné možnosti

`Option Infer` umožňuje určit, zda je místní odvozený typ povolen v určitém souboru. Chcete-li povolit nebo zablokovat možnost, zadejte na začátku souboru jeden z následujících příkazů.

`Option Infer On`

`Option Infer Off`

Pokud nezadáte hodnotu pro `Option Infer` v kódu, výchozí hodnota kompilátoru je `Option Infer On`.

Pokud je hodnota nastavená pro `Option Infer` v souboru v konfliktu s hodnotou nastavenou v integrovaném vývojovém prostředí (IDE) nebo na příkazovém řádku, má hodnota v souboru přednost.

Další informace naleznete v tématu [možnost odvození příkazu](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [Stránka kompilace, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

## <a name="see-also"></a>Viz také:

- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Statické a pozdní vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz For...Next](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [-optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
