---
title: "Postupy: Test, zda jsou dva objekty stejné (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="54017-102">Postupy: Test, zda jsou dva objekty stejné (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="54017-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="54017-103">Pokud máte dvě proměnné, které odkazují na objekty, můžete použít buď `Is` nebo `IsNot` operátor nebo obojí, chcete-li zjistit, zda odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="54017-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="54017-104">K ověření, zda jsou oba objekty stejné</span><span class="sxs-lookup"><span data-stu-id="54017-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="54017-105">Použití [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) nebo [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) s dvě proměnné, které jako operandy.</span><span class="sxs-lookup"><span data-stu-id="54017-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="54017-106">Můžete chtít určité akci v závislosti na tom, zda dva objekty odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="54017-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="54017-107">Předchozí příklad porovnává `c` proti aktivní ovládací prvek na formuláři `f`.</span><span class="sxs-lookup"><span data-stu-id="54017-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="54017-108">Pokud neexistuje žádné aktivní ovládací prvek, nebo pokud je jedna, ale není na stejnou instanci ovládacího prvku jako `c`, pak se `If` příkaz selže a postup vrátí bez dalšího zpracování.</span><span class="sxs-lookup"><span data-stu-id="54017-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="54017-109">Ať už používáte `Is` nebo `IsNot` je řádu osobní užitečný pro vás.</span><span class="sxs-lookup"><span data-stu-id="54017-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="54017-110">Jedním může být snadněji číst než jiné v daném výrazu.</span><span class="sxs-lookup"><span data-stu-id="54017-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54017-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="54017-111">See Also</span></span>  
 [<span data-ttu-id="54017-112">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54017-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
