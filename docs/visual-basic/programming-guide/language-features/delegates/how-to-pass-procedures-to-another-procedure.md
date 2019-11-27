---
title: 'Postupy: Předání procedur jiným postupům'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 300489935ce54d78b989d09211a7f6ba95c2f514
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345251"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Postupy: Předání procedur jiné proceduře v jazyce Visual Basic
Tento příklad ukazuje, jak použít delegáty k předání procedury jinému postupu.  
  
 Delegát je typ, který můžete použít jako jakýkoli jiný typ v Visual Basic. Operátor `AddressOf` vrací objekt delegáta při použití na název procedury.  
  
 Tento příklad má proceduru s parametrem delegáta, který může odkazovat na jiný postup získaný pomocí operátoru `AddressOf`.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Vytvořit delegáta a postupy pro porovnání  
  
1. Vytvořte delegáta s názvem `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Vytvořte proceduru s názvem `AddNumbers` s parametry a návratovou hodnotou, která odpovídá hodnotám `MathOperator`, aby se podpisy shodovaly.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Vytvořte proceduru s názvem `SubtractNumbers` s podpisem, který odpovídá `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Vytvořte proceduru s názvem `DelegateTest`, která přebírá delegáta jako parametr.  
  
     Tento postup může přijmout odkaz na `AddNumbers` nebo `SubtractNumbers`, protože jejich signatury odpovídají signatuře `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Vytvořte proceduru s názvem `Test`, která volá `DelegateTest` jednou s delegátem pro `AddNumbers` jako parametr a znovu s delegátem pro `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Při volání `Test` se nejprve zobrazí výsledek `AddNumbers` působícího na `5` a `3`, což je 8. Pak se zobrazí výsledek `SubtractNumbers` jednající `9` a `3`, což je 6.  
  
## <a name="see-also"></a>Viz také:

- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Operátor AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Postupy: Volání metody delegáta](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
