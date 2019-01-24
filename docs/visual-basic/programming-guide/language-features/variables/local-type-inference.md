---
title: Odvození místního typu (Visual Basic)
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
ms.openlocfilehash: f4edc879af9539a40269336bed97fe206920992a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706745"
---
# <a name="local-type-inference-visual-basic"></a>Odvození místního typu (Visual Basic)
Kompilátor jazyka Visual Basic používá *odvození typu* určit typy dat místní proměnné deklarované bez `As` klauzuli. Kompilátor odvodí typ proměnné z typu výrazu inicializace. To umožňuje deklarovat proměnné bez explicitně typu, s informacemi o tom, jak je znázorněno v následujícím příkladu. V důsledku deklarace obě `num1` a `num2` jsou silného typu jako celá čísla.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  Pokud nechcete, aby `num2` v předchozím příkladu na zadaný jako `Integer`, můžete určit jiný typ pomocí deklarací, jako `Dim num3 As Object = 3` nebo `Dim num4 As Double = 3`.  

> [!NOTE]
>  Odvození typu proměnné lze použít pouze pro nestatické lokální proměnné; nedá se použít k určení typu třídy pole, vlastnosti a funkce.
 
 Odvození místního typu se vztahuje na úrovni postup. Nelze použít pro deklarování proměnných na úrovni modulu (v rámci třídy, struktury, modul nebo rozhraní, ale není v rozsahu proceduru nebo blok). Pokud `num2` v předchozím příkladu se o pole třídy místo místní proměnné v postupu, deklarace by způsobila chybu s `Option Strict` a bude klasifikovat `num2` jako `Object` s `Option Strict` vypnout. Podobně, se nedá použít odvození místního typu k postupu úrovně proměnné deklarované jako `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Typ odvození vs. Pozdní vazby  
 Kód, že použití odvození typu vypadá podobně jako kód, který využívá pozdní vazby. Však odvození typu silnými typy proměnnou nenechávejte jako `Object`. Kompilátor používá k určení typu proměnné v době kompilace pro vytvoření kódu časné vazby proměnná inicializátor. V předchozím příkladu `num2`, třeba `num1`, je `Integer`.  
  
 Chování časné vazby proměnné se liší od proměnné s pozdní vazbou, pro které typ je znám pouze za běhu. Vědomí, že typ již v rané fázi umožňuje kompilátoru k identifikaci problémů před spuštěním, přesně přidělení paměti a provádět další optimalizace. Časná vazba umožňuje také integrovaného vývojového prostředí (IDE) k poskytnutí technologie IntelliSense nápovědy o členy objektu jazyka Visual Basic. Časná vazba je také upřednostněny výkonu. Důvodem je, že všechna data uložená v proměnné s pozdní vazbou, musí být zabalené jako typ `Object`, a přístup k členům typu za běhu programu pomalejší.  
  
## <a name="examples"></a>Příklady  
 Odvození typu vyvolá se v případě lokální proměnná je deklarovaná bez `As` klauzule a inicializován. Kompilátor používá jako typ proměnné typu počáteční hodnota. Například všechny následující řádky kódu deklaruje proměnnou typu `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 Následující kód ukazuje dva ekvivalentní způsoby, jak vytvořit pole celých čísel.  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 Je vhodné použít odvození typu k určení typu řídicí proměnná smyčky for. V následujícím kódu, kompilátor odvodí, které `number` je `Integer` protože `someNumbers2` z předchozího příkladu je pole celých čísel.  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 Odvození místního typu lze použít v `Using` příkazy k vytvoření typu název prostředku, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 Typ proměnné také jde odvodit z návratové hodnoty funkce, jak ukazuje následující příklad. Obě `pList1` a `pList2` jsou pole procesů, protože `Process.GetProcesses` vrátí celou řadu procesů.  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` Umožňuje určit, zda je povolena odvození místního typu v určitý soubor. Povolit nebo blokovat možnost, zadejte jeden z následujících příkazů na začátku souboru.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Pokud nezadáte hodnotu `Option Infer` ve vašem kódu, je výchozí nastavení kompilátoru `Option Infer On`. Pro projekty upgradovali z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] nebo starší, je výchozí nastavení kompilátoru `Option Infer Off`.  
  
 Je-li nastavena hodnota pro `Option Infer` v souboru konflikty s hodnotou nastavenou v integrovaném vývojovém prostředí nebo na příkazovém řádku, hodnota v souboru má prioritu.  
  
 Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Viz také:
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Statické a dynamické vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Příkaz For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz For...Next](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
