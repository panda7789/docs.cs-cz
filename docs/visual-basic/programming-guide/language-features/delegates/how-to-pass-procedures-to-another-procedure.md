---
title: 'Postupy: Předání procedur jiné proceduře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: e9e6165414db00e7d7182e204d86d23debfbf4f6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967734"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Postupy: Předání procedur jiné proceduře v jazyce Visual Basic
Tento příklad ukazuje způsob použití delegátů k předání procedury jiné proceduře.  
  
 Delegát je typ, který můžete použít stejně jako jakýkoli jiný typ v jazyce Visual Basic. `AddressOf` Operátor vrací objekt delegáta při použití pro název procedury.  
  
 V tomto příkladu má procedura se parametr delegáta, který může vytvořit odkaz na jiný postup získali díky `AddressOf` operátor.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Vytvoření delegáta a odpovídající procedur  
  
1.  Vytvoření delegáta s názvem `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2.  Vytvořte proceduru s názvem `AddNumbers` s parametry a návratovou hodnotu, která odpovídají objektu `MathOperator`tak, aby se podpisy shodují.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3.  Vytvořte proceduru s názvem `SubtractNumbers` s podpisem, který odpovídá `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4.  Vytvořte proceduru s názvem `DelegateTest` , která přebírá jako parametr delegáta.  
  
     Tento postup může přijmout odkaz na `AddNumbers` nebo `SubtractNumbers`, protože jejich podpisy shodují `MathOperator` podpis.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5.  Vytvořte proceduru s názvem `Test` , která volá `DelegateTest` jednou pro delegáta pro `AddNumbers` jako parametr a znovu s delegátem pro `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Když `Test` je volána, nejprve zobrazí výsledek `AddNumbers` funguje na `5` a `3`, což je 8. Potom výsledek `SubtractNumbers` jednající `9` a `3` se zobrazí, což je 6.  
  
## <a name="see-also"></a>Viz také:
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Operátor AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Postupy: Volání metody delegáta](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
