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
ms.openlocfilehash: b215225dbc2d8c0d2bdfe2206e5d4a4f1faa6d0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403418"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Postupy: Test, zda jsou dva objekty stejné (Visual Basic).
Pokud máte dvě proměnné, které odkazují na objekty, můžete použít `Is` `IsNot` operátor OR nebo obojí k určení, zda odkazují na stejnou instanci.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Testování, zda jsou dva objekty stejné  
  
- Použijte [operátor is](../../../language-reference/operators/is-operator.md) nebo [operátor IsNot](../../../language-reference/operators/isnot-operator.md) s těmito dvěma proměnnými jako operandy.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 V závislosti na tom, zda dva objekty odkazují na stejnou instanci, je vhodné provést určitou akci. Předchozí příklad porovnává kontrolu `c` s aktivním ovládacím prvkem na formuláři `f` . Pokud neexistuje žádný aktivní ovládací prvek nebo pokud existuje, ale není to stejná instance ovládacího prvku jako `c` , `If` příkaz se nezdařil a procedura se vrátí bez dalšího zpracování.  
  
 Ať už používáte, `Is` nebo `IsNot` je to pro vás osobní pohodlí. Jednu z nich je možné snáze číst než druhá v daném výrazu.  
  
## <a name="see-also"></a>Viz také

- [Operátory porovnání v jazyce Visual Basic](comparison-operators.md)
