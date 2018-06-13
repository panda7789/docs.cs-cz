---
title: 'Postupy: Test, zda jsou dva objekty stejné (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 005c91e6f4ec556a7e1bf255b47c8276a5d3d185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647602"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Postupy: Test, zda jsou dva objekty stejné (Visual Basic).
Pokud máte dvě proměnné, které odkazují na objekty, můžete použít buď `Is` nebo `IsNot` operátor nebo obojí, chcete-li zjistit, zda odkazují na stejnou instanci.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>K ověření, zda jsou oba objekty stejné  
  
-   Použití [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) nebo [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) s dvě proměnné, které jako operandy.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Můžete chtít určité akci v závislosti na tom, zda dva objekty odkazují na stejnou instanci. Předchozí příklad porovnává `c` proti aktivní ovládací prvek na formuláři `f`. Pokud neexistuje žádné aktivní ovládací prvek, nebo pokud je jedna, ale není na stejnou instanci ovládacího prvku jako `c`, pak se `If` příkaz selže a postup vrátí bez dalšího zpracování.  
  
 Ať už používáte `Is` nebo `IsNot` je řádu osobní užitečný pro vás. Jedním může být snadněji číst než jiné v daném výrazu.  
  
## <a name="see-also"></a>Viz také  
 [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
