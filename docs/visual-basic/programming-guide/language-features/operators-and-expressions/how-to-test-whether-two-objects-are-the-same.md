---
title: 'Postupy: Test, zda jsou dva objekty stejné.'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343621"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Postupy: Test, zda jsou dva objekty stejné (Visual Basic).
Pokud máte dvě proměnné, které odkazují na objekty, můžete použít operátor `Is` nebo `IsNot` nebo obojí, chcete-li určit, zda odkazují na stejnou instanci.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Testování, zda jsou dva objekty stejné  
  
- Použijte [operátor is](../../../../visual-basic/language-reference/operators/is-operator.md) nebo [operátor IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) s těmito dvěma proměnnými jako operandy.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 V závislosti na tom, zda dva objekty odkazují na stejnou instanci, je vhodné provést určitou akci. Předchozí příklad porovná ovládací prvek `c` proti aktivnímu ovládacímu prvku ve formuláři `f`. Pokud neexistuje žádný aktivní ovládací prvek nebo pokud existuje, ale není to stejná instance ovládacího prvku jako `c`, příkaz `If` se nezdařil a procedura se vrátí bez dalšího zpracování.  
  
 Bez ohledu na to, jestli používáte `Is` nebo `IsNot`, je osobní pohodlí pro vás. Jednu z nich je možné snáze číst než druhá v daném výrazu.  
  
## <a name="see-also"></a>Viz také:

- [Operátory porovnávání v Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
