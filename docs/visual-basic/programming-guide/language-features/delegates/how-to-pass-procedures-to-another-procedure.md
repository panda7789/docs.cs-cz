---
title: 'Postupy: Předání procedur jiné proceduře v jazyce Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 30264e0480b603b21f8f71893af0fd742af40286
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Postupy: Předání procedur jiné proceduře v jazyce Visual Basic
Tento příklad ukazuje způsob použití delegátů k předání procedury jiné proceduře.  
  
 Delegát je typ, který můžete použít jako libovolný jiný typ v jazyce Visual Basic. `AddressOf` Operátor vrátí objekt delegáta při použití název procedury.  
  
 V tomto příkladu má procedura se parametr delegáta, který může trvat odkaz na jinou proceduru, které byly získány `AddressOf` operátor.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Vytvořit odpovídající postupů a delegování  
  
1.  Vytvoření delegáta s názvem `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Vytvoření procedury s názvem `AddNumbers` s parametry a návratové hodnoty, které se shodují `MathOperator`tak, aby podpisů shodují.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Vytvoření procedury s názvem `SubtractNumbers` podpisem, který odpovídá `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Vytvoření procedury s názvem `DelegateTest` , která má delegáta jako parametr.  
  
     Tento postup může přijmout odkaz na `AddNumbers` nebo `SubtractNumbers`, protože jejich podpisů shodují `MathOperator` podpis.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Vytvoření procedury s názvem `Test` , který volá `DelegateTest` jednou pro delegáta pro `AddNumbers` jako parametr a znovu s delegátem pro `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Když `Test` je volána, se nejprve zobrazí výsledek `AddNumbers` funguje na `5` a `3`, což je 8. Potom výsledek `SubtractNumbers` funguje na `9` a `3` se zobrazí, což je 6.  
  
## <a name="see-also"></a>Viz také  
 [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Operátor AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Postupy: Volání metody delegáta](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
