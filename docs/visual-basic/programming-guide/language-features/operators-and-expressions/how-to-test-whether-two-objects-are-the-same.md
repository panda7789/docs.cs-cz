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
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="9d7ea-102">Postupy: Test, zda jsou dva objekty stejné (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9d7ea-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="9d7ea-103">Pokud máte dvě proměnné, které odkazují na objekty, můžete použít operátor `Is` nebo `IsNot` nebo obojí, chcete-li určit, zda odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="9d7ea-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="9d7ea-104">Testování, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="9d7ea-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="9d7ea-105">Použijte [operátor is](../../../../visual-basic/language-reference/operators/is-operator.md) nebo [operátor IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) s těmito dvěma proměnnými jako operandy.</span><span class="sxs-lookup"><span data-stu-id="9d7ea-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="9d7ea-106">V závislosti na tom, zda dva objekty odkazují na stejnou instanci, je vhodné provést určitou akci.</span><span class="sxs-lookup"><span data-stu-id="9d7ea-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="9d7ea-107">Předchozí příklad porovná ovládací prvek `c` proti aktivnímu ovládacímu prvku ve formuláři `f`.</span><span class="sxs-lookup"><span data-stu-id="9d7ea-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="9d7ea-108">Pokud neexistuje žádný aktivní ovládací prvek nebo pokud existuje, ale není to stejná instance ovládacího prvku jako `c`, příkaz `If` se nezdařil a procedura se vrátí bez dalšího zpracování.</span><span class="sxs-lookup"><span data-stu-id="9d7ea-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="9d7ea-109">Bez ohledu na to, jestli používáte `Is` nebo `IsNot`, je osobní pohodlí pro vás.</span><span class="sxs-lookup"><span data-stu-id="9d7ea-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="9d7ea-110">Jednu z nich je možné snáze číst než druhá v daném výrazu.</span><span class="sxs-lookup"><span data-stu-id="9d7ea-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7ea-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d7ea-111">See also</span></span>

- [<span data-ttu-id="9d7ea-112">Operátory porovnávání v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d7ea-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
