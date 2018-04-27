---
title: 'Postupy: Předání procedur jiné proceduře v jazyce Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 30264e0480b603b21f8f71893af0fd742af40286
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="50f92-102">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50f92-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="50f92-103">Tento příklad ukazuje způsob použití delegátů k předání procedury jiné proceduře.</span><span class="sxs-lookup"><span data-stu-id="50f92-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="50f92-104">Delegát je typ, který můžete použít jako libovolný jiný typ v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="50f92-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="50f92-105">`AddressOf` Operátor vrátí objekt delegáta při použití název procedury.</span><span class="sxs-lookup"><span data-stu-id="50f92-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="50f92-106">V tomto příkladu má procedura se parametr delegáta, který může trvat odkaz na jinou proceduru, které byly získány `AddressOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="50f92-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="50f92-107">Vytvořit odpovídající postupů a delegování</span><span class="sxs-lookup"><span data-stu-id="50f92-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="50f92-108">Vytvoření delegáta s názvem `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="50f92-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="50f92-109">Vytvoření procedury s názvem `AddNumbers` s parametry a návratové hodnoty, které se shodují `MathOperator`tak, aby podpisů shodují.</span><span class="sxs-lookup"><span data-stu-id="50f92-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="50f92-110">Vytvoření procedury s názvem `SubtractNumbers` podpisem, který odpovídá `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="50f92-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="50f92-111">Vytvoření procedury s názvem `DelegateTest` , která má delegáta jako parametr.</span><span class="sxs-lookup"><span data-stu-id="50f92-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="50f92-112">Tento postup může přijmout odkaz na `AddNumbers` nebo `SubtractNumbers`, protože jejich podpisů shodují `MathOperator` podpis.</span><span class="sxs-lookup"><span data-stu-id="50f92-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="50f92-113">Vytvoření procedury s názvem `Test` , který volá `DelegateTest` jednou pro delegáta pro `AddNumbers` jako parametr a znovu s delegátem pro `SubtractNumbers` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="50f92-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="50f92-114">Když `Test` je volána, se nejprve zobrazí výsledek `AddNumbers` funguje na `5` a `3`, což je 8.</span><span class="sxs-lookup"><span data-stu-id="50f92-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="50f92-115">Potom výsledek `SubtractNumbers` funguje na `9` a `3` se zobrazí, což je 6.</span><span class="sxs-lookup"><span data-stu-id="50f92-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f92-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="50f92-116">See Also</span></span>  
 [<span data-ttu-id="50f92-117">Delegáti</span><span class="sxs-lookup"><span data-stu-id="50f92-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="50f92-118">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="50f92-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="50f92-119">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="50f92-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="50f92-120">Postupy: Volání metody delegáta</span><span class="sxs-lookup"><span data-stu-id="50f92-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
