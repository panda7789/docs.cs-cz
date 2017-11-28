---
title: "Odvození místního typu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d753d1fbdc60f70dcf0513d809f28a112243c111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="local-type-inference-visual-basic"></a>Odvození místního typu (Visual Basic)
Visual Basic – kompilátor používá *odvození typu* k určení datové typy lokální proměnné deklarované bez `As` klauzule. Kompilátor odvodí typ proměnné z typu inicializace výrazu. To umožňuje deklarujte proměnné bez explicitně typu, s informacemi o tom, jak je znázorněno v následujícím příkladu. V důsledku deklarace obě `num1` a `num2` jsou silného typu jako celá čísla.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  Pokud nechcete, aby `num2` v předchozím příkladu zadat jako `Integer`, můžete zadat jiný typ pomocí deklaraci jako `Dim num3 As Object = 3` nebo `Dim num4 As Double = 3`.  

> [!NOTE]
>  Odvození typu proměnné lze použít pouze pro místní proměnné nestatické; nedá se použít k určení typ pole třídy, vlastnosti a funkce.
 
 Odvození místního typu se vztahuje na úrovni postupu. Nelze se používá k deklaraci proměnné na úrovni modulu (v rámci třídy, struktury, modul nebo rozhraní ale není uvnitř procedury nebo bloku). Pokud `num2` v předchozím příkladu byly pole třídy místo místní proměnné v postupu, deklaraci by způsobilo chybu s `Option Strict` a by klasifikaci `num2` jako `Object` s `Option Strict` vypnout. Podobně odvození místního typu nelze použít na postup úrovně proměnných deklarovaných jako `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Zadejte odvození vs. Pozdní vazba  
 Odvození používá typu kódu vypadá takto: kód, který využívá pozdní vazbu. Ale odvození typu důrazně typy proměnnou místo ponechání jako `Object`. Kompilátor proměnná inicializátoru používá k určení typu proměnné v době kompilace k vytvoření časné vazby kódu. V předchozím příkladu `num2`, například `num1`, je zadán jako `Integer`.  
  
 Chování časné vazby proměnné se liší od pozdní vazbou proměnné, pro které je známý typ pouze za běhu. Zároveň budete vědět, že typ již v rané fázi umožňuje kompilátoru identifikaci problémů před spuštěním, přesněji přidělit paměť a provádět další optimalizace. Časná vazba taky umožňuje jazyka Visual Basic integrované vývojové prostředí (IDE) k poskytnutí nápovědy IntelliSense o členům v objektu. Časná vazba je také upřednostňuje výkonu. Důvodem je, že všechna data, které jsou uložené v proměnné pozdní vazbou musí být uzavřen jako typ `Object`, a přístup ke členům typu v době běhu programu pomalejší.  
  
## <a name="examples"></a>Příklady  
 Odvození typu nastane, když místní proměnné je deklarovaná bez `As` klauzule a inicializovat. Kompilátor používá typ přiřazené počáteční hodnoty jako typ proměnné. Například každý následující řádek kódu deklaruje proměnné typu `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 Následující kód ukazuje dva způsoby ekvivalentní vytvoření pole celých čísel.  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 Je vhodnější použít odvození typu určit typ řídicí proměnná smyčky. V následujícím kódu, který odvodí kompilátor `number` je `Integer` protože `someNumbers2` z předchozího příkladu je pole celých čísel.  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 Odvození místního typu mohou být používány `Using` příkazy k vytvoření je typ názvu prostředku, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 Typ proměnné lze také odvodit z návratové hodnoty funkce, jako následující příklad ukazuje. Obě `pList1` a `pList2` jsou pole procesů, protože `Process.GetProcesses` vrátí pole procesů.  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer –  
 `Option Infer`povoluje, který zadáte, jestli je povolené odvození místního typu v konkrétním souboru. Chcete-li povolit nebo blokovat možnost, zadejte jednu z následujících příkazů na začátku souboru.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Pokud nezadáte hodnotu `Option Infer` ve vašem kódu kompilátoru výchozí hodnota je `Option Infer On`. Pro projekty upgradovali z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] nebo starší, je výchozí nastavení kompilátoru `Option Infer Off`.  
  
 Pokud je hodnota nastavená pro `Option Infer` souboru konflikty s hodnotu nastavenou v prostředí IDE nebo na příkazovém řádku, v souboru hodnota má vyšší prioritu.  
  
 Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Viz také  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Statické a pozdní vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [Pro každou... Next – příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Pro... Next – příkaz](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [/ optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
