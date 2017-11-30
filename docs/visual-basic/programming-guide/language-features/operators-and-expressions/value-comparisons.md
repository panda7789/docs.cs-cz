---
title: "Porovnání hodnot (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c11f12bbaf261c0853e96802f03322c5e7fdc706
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-comparisons-visual-basic"></a>Porovnání hodnot (Visual Basic)
Operátory porovnání lze použít k vytvoření výrazy, které porovnávají hodnoty proměnných číselná. Tyto výrazy vrátit `Boolean` hodnota založená na tom, zda je výsledkem porovnávání PRAVDA nebo NEPRAVDA. Příklady takových výraz.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 První vyhodnocen jako `True`, protože je větší než 26 45. V druhém příkladu se vyhodnocuje `False`, protože 26 není větší než 45.  
  
 Numerické výrazy tímto způsobem, můžete porovnat. Sami výrazy, které můžete porovnat může být složité výrazy, jako v následujícím příkladu.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Předchozí složitý výraz obsahuje literály, proměnné a volání funkce. Výrazy na obou stranách operátoru porovnání vyhodnocují a výsledné hodnoty jsou potom porovná pomocí `>=` operátor porovnání. Pokud hodnota výraz na levé straně je větší než nebo rovna hodnotě výrazu na pravé straně, celý výraz vyhodnocen jako `True`, jinak se vyhodnotí jako `False`.  
  
 Výrazy, které porovnat hodnoty se obvykle používají v `If...Then` konstrukce, jako v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 `=` Přihlášení je operátor porovnání a také operátor přiřazení. Když se použije jako operátor porovnání, vyhodnotí, zda hodnota na levé straně je stejná jako hodnota na pravé straně, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 Můžete také použít výraz porovnání kdekoli `Boolean` hodnota je potřebné, například jako v `If`, `While`, `Loop`, nebo `ElseIf` prohlášení, nebo při přiřazování nebo předáním hodnoty do `Boolean` proměnné. V následujícím příkladu je přiřazená hodnoty vrácené výraz pro porovnání `Boolean` proměnné.  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Logické výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Operátory a výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Postupy: výpočet numerických hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
