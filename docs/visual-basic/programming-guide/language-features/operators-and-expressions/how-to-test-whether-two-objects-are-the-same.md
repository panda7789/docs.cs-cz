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
ms.openlocfilehash: dbb268175d197e7b931af45a98f3a273c593e5a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819106"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="6454b-102">Postupy: Otestujte, zda jsou oba objekty stejné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6454b-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="6454b-103">Pokud budete mít dvě proměnné, které odkazují na objekty, můžete použít buď `Is` nebo `IsNot` operátor nebo obojí, chcete-li zjistit, jestli se odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="6454b-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="6454b-104">K ověření, zda jsou dva objekty stejné</span><span class="sxs-lookup"><span data-stu-id="6454b-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="6454b-105">Použití [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) nebo [IsNot operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) se dvěma proměnnými jako operandy.</span><span class="sxs-lookup"><span data-stu-id="6454b-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="6454b-106">Můžete chtít provést určité akce v závislosti na tom, zda dva objekty odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="6454b-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="6454b-107">Předchozí příklad porovnává `c` proti aktivním ovládacím prvkem na formuláři `f`.</span><span class="sxs-lookup"><span data-stu-id="6454b-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="6454b-108">Pokud neexistuje žádná aktivní ovládací prvek, nebo pokud není ten ale není stejnou instanci ovládacího prvku jako `c`, pak bude `If` příkaz selže a postup vrátí bez dalšího zpracování.</span><span class="sxs-lookup"><span data-stu-id="6454b-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="6454b-109">Ať už používáte `Is` nebo `IsNot` je otázkou osobní usnadnění práce vás.</span><span class="sxs-lookup"><span data-stu-id="6454b-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="6454b-110">Jedna může být snadněji čtou než ten druhý v daném výrazu.</span><span class="sxs-lookup"><span data-stu-id="6454b-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6454b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6454b-111">See also</span></span>

- [<span data-ttu-id="6454b-112">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6454b-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
