---
title: 'Postupy: Otestujte, zda jsou oba objekty stejné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: d13671f284863fa7bf56964c2b9b963c25e8ea52
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977445"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Postupy: Otestujte, zda jsou oba objekty stejné (Visual Basic)
Pokud budete mít dvě proměnné, které odkazují na objekty, můžete použít buď `Is` nebo `IsNot` operátor nebo obojí, chcete-li zjistit, jestli se odkazují na stejnou instanci.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>K ověření, zda jsou dva objekty stejné  
  
-   Použití [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) nebo [IsNot operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) se dvěma proměnnými jako operandy.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 Můžete chtít provést určité akce v závislosti na tom, zda dva objekty odkazují na stejnou instanci. Předchozí příklad porovnává `c` proti aktivním ovládacím prvkem na formuláři `f`. Pokud neexistuje žádná aktivní ovládací prvek, nebo pokud není ten ale není stejnou instanci ovládacího prvku jako `c`, pak bude `If` příkaz selže a postup vrátí bez dalšího zpracování.  
  
 Ať už používáte `Is` nebo `IsNot` je otázkou osobní usnadnění práce vás. Jedna může být snadněji čtou než ten druhý v daném výrazu.  
  
## <a name="see-also"></a>Viz také:
- [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
