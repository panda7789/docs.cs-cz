---
title: 'Postupy: Přerušení a kombinace příkazů v kódu (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 680084c39b90d4f664f48559fa21388ce192d999
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837708"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Postupy: Přerušení a kombinace příkazů v kódu (Visual Basic)
Při psaní kódu, může být čas od času vytvoření dlouhé příkazy, které vyžadují vodorovného posouvání v editoru kódu. I když to nemá vliv způsob, jak kód poběží, to ztěžuje pro vás nebo někdo jiný kód přečíst, jak je zobrazen na monitorování. V takovém případě zvažte rozdělení jeden dlouhý příkaz na několika řádcích.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Chcete rozdělit jeden příkaz na více řádků  
  
-   Použijte znak pro pokračování řádku, který je podtržítko (`_`), v okamžiku, kdy chcete řádek rozdělit. Podtržítka musí být bezprostředně předchází mezerou a ihned následovány znakem ukončení řádku (návrat).  
  
    > [!NOTE]
    >  V některých případech Pokud vynecháte znak pro pokračování řádku, kompilátor jazyka Visual Basic implicitně bude příkaz na další řádek kódu. Seznam prvky syntaxe, pro které je možné vynechat znak pro pokračování řádku naleznete v části "Implicitní pokračování řádku" v [příkazy](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     V následujícím příkladu příkaz rozdělená do čtyř řádků se ukončuje všechny znaky pokračování řádku, ale na posledním řádku.  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     Pomocí tohoto pořadí díky váš kód lépe čitelný, online i při tisku.  
  
     Znak pokračování řádku musí být poslední znak na řádku. Ho nemůže následovat s cokoli na stejném řádku.  
  
     Existují určitá omezení, kde můžete použít znak pokračování řádku. například nelze použít uprostřed název argumentu. Můžete přerušit seznam argumentů znakem pokračování řádku, ale jednotlivé názvy argumentů, musí zůstat beze změny.  
  
     Komentář nemůže pokračovat s použitím znak pro pokračování řádku. Kompilátor nebude zkontrolujte znaky v komentáři pro zvláštní význam. Více řádků komentáře, opakujte symbol komentáře (`'`) na každém řádku.  
  
 I když každý příkaz umístit na samostatný řádek je doporučená metoda, Visual Basic také umožňuje umístit více příkazů na stejném řádku.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Umístit více příkazů na stejném řádku  
  
-   Oddělení příkazů s dvojtečkou (`:`), jako v následujícím příkladu.  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
