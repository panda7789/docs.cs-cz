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
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="88df2-102">Postupy: Test, zda jsou dva objekty stejné (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="88df2-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="88df2-103">Pokud máte dvě proměnné, které odkazují na objekty, můžete použít `Is` `IsNot` operátor OR nebo obojí k určení, zda odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="88df2-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="88df2-104">Testování, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="88df2-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="88df2-105">Použijte [operátor is](../../../language-reference/operators/is-operator.md) nebo [operátor IsNot](../../../language-reference/operators/isnot-operator.md) s těmito dvěma proměnnými jako operandy.</span><span class="sxs-lookup"><span data-stu-id="88df2-105">Use the [Is Operator](../../../language-reference/operators/is-operator.md) or the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="88df2-106">V závislosti na tom, zda dva objekty odkazují na stejnou instanci, je vhodné provést určitou akci.</span><span class="sxs-lookup"><span data-stu-id="88df2-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="88df2-107">Předchozí příklad porovnává kontrolu `c` s aktivním ovládacím prvkem na formuláři `f` .</span><span class="sxs-lookup"><span data-stu-id="88df2-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="88df2-108">Pokud neexistuje žádný aktivní ovládací prvek nebo pokud existuje, ale není to stejná instance ovládacího prvku jako `c` , `If` příkaz se nezdařil a procedura se vrátí bez dalšího zpracování.</span><span class="sxs-lookup"><span data-stu-id="88df2-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="88df2-109">Ať už používáte, `Is` nebo `IsNot` je to pro vás osobní pohodlí.</span><span class="sxs-lookup"><span data-stu-id="88df2-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="88df2-110">Jednu z nich je možné snáze číst než druhá v daném výrazu.</span><span class="sxs-lookup"><span data-stu-id="88df2-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88df2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="88df2-111">See also</span></span>

- [<span data-ttu-id="88df2-112">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88df2-112">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
