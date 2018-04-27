---
title: 'Postupy: Přerušení a kombinace příkazů v kódu (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06702cdc9073065a418b17d198dbb43be4aefca1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Postupy: Přerušení a kombinace příkazů v kódu (Visual Basic)
Při psaní kódu, můžete vytvořit v některých případech zdlouhavé příkazy, které vyžadují vodorovného posouvání v editoru kódu. I když to nemá vliv způsob kód běží, je ztížíte pro vy ani nikdo jiný číst kód, jak se objevuje v monitorování. V takovém případě byste měli zvážit, rozdělení jeden dlouhý příkaz na několika řádcích.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Chcete-li rozdělit jeden příkaz na více řádků  
  
-   Použít znak pokračování řádku, který je podtržítko (`_`), v okamžiku, kdy chcete řádek ukončit. Podtržítko musí být bezprostředně před mezerou a bezprostředně následované ukončení řádku (návrat na začátek).  
  
    > [!NOTE]
    >  V některých případech Pokud vynecháte znak pokračování řádku Visual Basic – kompilátor implicitně bude příkaz na dalším řádku kódu. Seznam prvků syntaxe, pro které je možné vynechat znak pokračování řádku najdete v tématu "Implicitní pokračování řádku" v [příkazy](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     V následujícím příkladu je příkaz rozdělená do čtyř řádky s znaky pokračování řádku ukončení všech ale poslední řádek.  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     Pomocí tohoto pořadí usnadňuje kódu čtení, online i když vytisknout.  
  
     Znak pokračování řádku musí být poslední znak na řádek. Nelze ho sledovat s cokoliv jiného na stejném řádku.  
  
     Existují některá omezení, kde můžete použít znak pokračování řádku; například nelze použít uprostřed název argumentu. Seznam argumentů s znak pokračování řádku je možné přerušit, ale jednotlivé názvy argumenty, které musí zůstat beze změn.  
  
     Komentář nemůže pokračovat s použitím znak pokračování řádku. Kompilátor není zkontrolujte znaků v komentáři pro zvláštní význam. Pro více řádků komentář, opakujte symbol komentáře (`'`) na každém řádku.  
  
 I když každý příkaz umístění na samostatném řádku je doporučená metoda, Visual Basic také umožňuje umístit více příkazů na stejném řádku.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Umístit více příkazů na stejné přímce.  
  
-   Příkazy oddělte čárkou (`:`), jako v následujícím příkladu.  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
