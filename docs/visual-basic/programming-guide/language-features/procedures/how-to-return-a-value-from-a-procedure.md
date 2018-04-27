---
title: 'Postupy: Vrácení hodnoty z procedury (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: affcb25951a6647604286bc91dcaec8898fe2e30
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="2f2bc-102">Postupy: Vrácení hodnoty z procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f2bc-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="2f2bc-103">A `Function` postup vrátí hodnotu volání kódu, buď spuštěním `Return` příkaz nebo zjištění `Exit Function` nebo `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="2f2bc-104">Chcete-li vrátit hodnotu pomocí příkaz Return</span><span class="sxs-lookup"><span data-stu-id="2f2bc-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="2f2bc-105">PUT `Return` příkaz v okamžiku, kdy dokončení úlohy postup.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="2f2bc-106">Postupujte podle `Return` – klíčové slovo s výrazem, jehož výsledkem je hodnota, kterou chcete vrátit volání kódu.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="2f2bc-107">Můžete mít více než jednu `Return` příkaz v stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="2f2bc-108">Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku práva a vrátí ji do volající kód.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     <span data-ttu-id="2f2bc-109">Následující příklad ukazuje typické volání `hypotenuse`, která ukládá vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="2f2bc-110">Vrácení hodnoty pomocí ukončení funkce nebo funkce End</span><span class="sxs-lookup"><span data-stu-id="2f2bc-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="2f2bc-111">Nejméně jedno místo v `Function` postupu, přiřazení a hodnota, která má název procedury.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="2f2bc-112">Při spuštění `Exit Function` nebo `End Function` příkazu jazyka Visual Basic, vrátí hodnotu naposledy přiřazen název procedury.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="2f2bc-113">Můžete mít více než jednu `Exit Function` příkaz v stejným způsobem a můžete kombinovat `Return` a `Exit Function` příkazy v stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="2f2bc-114">Může mít jen jeden `End Function` příkaz v `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="2f2bc-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="2f2bc-115">Další informace a příklady naleznete v tématu "Vrátí hodnotu" v [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2f2bc-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2bc-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f2bc-116">See Also</span></span>  
 [<span data-ttu-id="2f2bc-117">Procedury</span><span class="sxs-lookup"><span data-stu-id="2f2bc-117">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="2f2bc-118">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="2f2bc-118">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="2f2bc-119">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2f2bc-119">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="2f2bc-120">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="2f2bc-120">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="2f2bc-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="2f2bc-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="2f2bc-122">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="2f2bc-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="2f2bc-123">Příkaz Return</span><span class="sxs-lookup"><span data-stu-id="2f2bc-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="2f2bc-124">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="2f2bc-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="2f2bc-125">Postupy. Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="2f2bc-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
