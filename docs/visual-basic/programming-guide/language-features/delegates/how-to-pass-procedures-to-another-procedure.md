---
title: 'Postupy: Předání procedur jiné proceduře'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 36f623068372614ae034a8a7b31bffb7496f98b1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410692"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Postupy: Předání procedur jiné proceduře v jazyce Visual Basic
Tento příklad ukazuje, jak použít delegáty k předání procedury jinému postupu.  
  
 Delegát je typ, který můžete použít jako jakýkoli jiný typ v Visual Basic. `AddressOf`Operátor vrací objekt delegáta při použití na název procedury.  
  
 Tento příklad má proceduru s parametrem delegáta, který může odkazovat na jiný postup získaný pomocí `AddressOf` operátoru.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Vytvořit delegáta a postupy pro porovnání  
  
1. Vytvořte delegáta s názvem `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Vytvořte proceduru s názvem `AddNumbers` s parametry a návratovou hodnotou, která odpovídá hodnotám `MathOperator` , aby se podpisy shodovaly.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Vytvořte proceduru s názvem `SubtractNumbers` , která odpovídá podpisu `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Vytvořte proceduru s názvem `DelegateTest` , která přijímá delegáta jako parametr.  
  
     Tento postup může přijmout odkaz na `AddNumbers` nebo `SubtractNumbers` , protože jeho signatury odpovídají `MathOperator` podpisu.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Vytvořte proceduru s názvem `Test` , která volá `DelegateTest` jednou s delegátem `AddNumbers` jako parametr a znovu s delegátem `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Při `Test` volání se nejprve zobrazí výsledek, `AddNumbers` který funguje na `5` a `3` , což je 8. Pak se zobrazí výsledek `SubtractNumbers` vyjednání `9` a `3` je 6.  
  
## <a name="see-also"></a>Viz také

- [Delegáti](index.md)
- [AddressOf – operátor](../../../language-reference/operators/addressof-operator.md)
- [Delegate – příkaz](../../../language-reference/statements/delegate-statement.md)
- [Postupy: Volání metody delegáta](how-to-invoke-a-delegate-method.md)
