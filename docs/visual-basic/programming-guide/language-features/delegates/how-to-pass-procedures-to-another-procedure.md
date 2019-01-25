---
title: 'Postupy: Předání procedur jiné proceduře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: cf5a8447cbedcd8071da98ac6763ff06eb608199
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506755"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="abe91-102">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abe91-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="abe91-103">Tento příklad ukazuje způsob použití delegátů k předání procedury jiné proceduře.</span><span class="sxs-lookup"><span data-stu-id="abe91-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="abe91-104">Delegát je typ, který můžete použít stejně jako jakýkoli jiný typ v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="abe91-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="abe91-105">`AddressOf` Operátor vrací objekt delegáta při použití pro název procedury.</span><span class="sxs-lookup"><span data-stu-id="abe91-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="abe91-106">V tomto příkladu má procedura se parametr delegáta, který může vytvořit odkaz na jiný postup získali díky `AddressOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="abe91-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="abe91-107">Vytvoření delegáta a odpovídající procedur</span><span class="sxs-lookup"><span data-stu-id="abe91-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="abe91-108">Vytvoření delegáta s názvem `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="abe91-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="abe91-109">Vytvořte proceduru s názvem `AddNumbers` s parametry a návratovou hodnotu, která odpovídají objektu `MathOperator`tak, aby se podpisy shodují.</span><span class="sxs-lookup"><span data-stu-id="abe91-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="abe91-110">Vytvořte proceduru s názvem `SubtractNumbers` s podpisem, který odpovídá `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="abe91-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="abe91-111">Vytvořte proceduru s názvem `DelegateTest` , která přebírá jako parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="abe91-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="abe91-112">Tento postup může přijmout odkaz na `AddNumbers` nebo `SubtractNumbers`, protože jejich podpisy shodují `MathOperator` podpis.</span><span class="sxs-lookup"><span data-stu-id="abe91-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="abe91-113">Vytvořte proceduru s názvem `Test` , která volá `DelegateTest` jednou pro delegáta pro `AddNumbers` jako parametr a znovu s delegátem pro `SubtractNumbers` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="abe91-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="abe91-114">Když `Test` je volána, nejprve zobrazí výsledek `AddNumbers` funguje na `5` a `3`, což je 8.</span><span class="sxs-lookup"><span data-stu-id="abe91-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="abe91-115">Potom výsledek `SubtractNumbers` jednající `9` a `3` se zobrazí, což je 6.</span><span class="sxs-lookup"><span data-stu-id="abe91-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe91-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abe91-116">See also</span></span>
- [<span data-ttu-id="abe91-117">Delegáti</span><span class="sxs-lookup"><span data-stu-id="abe91-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="abe91-118">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="abe91-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="abe91-119">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="abe91-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="abe91-120">Postupy: Volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="abe91-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
