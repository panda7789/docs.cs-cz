---
title: Rekurzivní procedury
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 646d4e29ed7a0b6367d4b35a7f8641bcf659e616
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352558"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="e121c-102">Rekurzivní procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e121c-102">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="e121c-103">A *recursive* procedure is one that calls itself.</span><span class="sxs-lookup"><span data-stu-id="e121c-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="e121c-104">In general, this is not the most effective way to write Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="e121c-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="e121c-105">The following procedure uses recursion to calculate the factorial of its original argument.</span><span class="sxs-lookup"><span data-stu-id="e121c-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="e121c-106">Considerations with Recursive Procedures</span><span class="sxs-lookup"><span data-stu-id="e121c-106">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="e121c-107">**Limiting Conditions**.</span><span class="sxs-lookup"><span data-stu-id="e121c-107">**Limiting Conditions**.</span></span> <span data-ttu-id="e121c-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span><span class="sxs-lookup"><span data-stu-id="e121c-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="e121c-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span><span class="sxs-lookup"><span data-stu-id="e121c-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="e121c-110">**Memory Usage**.</span><span class="sxs-lookup"><span data-stu-id="e121c-110">**Memory Usage**.</span></span> <span data-ttu-id="e121c-111">Your application has a limited amount of space for local variables.</span><span class="sxs-lookup"><span data-stu-id="e121c-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="e121c-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span><span class="sxs-lookup"><span data-stu-id="e121c-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="e121c-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span><span class="sxs-lookup"><span data-stu-id="e121c-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="e121c-114">**Efficiency**.</span><span class="sxs-lookup"><span data-stu-id="e121c-114">**Efficiency**.</span></span> <span data-ttu-id="e121c-115">You can almost always substitute a loop for recursion.</span><span class="sxs-lookup"><span data-stu-id="e121c-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="e121c-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span><span class="sxs-lookup"><span data-stu-id="e121c-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="e121c-117">Your performance can be much better without recursive calls.</span><span class="sxs-lookup"><span data-stu-id="e121c-117">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="e121c-118">**Mutual Recursion**.</span><span class="sxs-lookup"><span data-stu-id="e121c-118">**Mutual Recursion**.</span></span> <span data-ttu-id="e121c-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span><span class="sxs-lookup"><span data-stu-id="e121c-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="e121c-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span><span class="sxs-lookup"><span data-stu-id="e121c-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="e121c-121">**Calling with Parentheses**.</span><span class="sxs-lookup"><span data-stu-id="e121c-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="e121c-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span><span class="sxs-lookup"><span data-stu-id="e121c-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="e121c-123">Otherwise, the function name is taken as representing the return value of the function.</span><span class="sxs-lookup"><span data-stu-id="e121c-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="e121c-124">**Testing**.</span><span class="sxs-lookup"><span data-stu-id="e121c-124">**Testing**.</span></span> <span data-ttu-id="e121c-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span><span class="sxs-lookup"><span data-stu-id="e121c-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="e121c-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span><span class="sxs-lookup"><span data-stu-id="e121c-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="e121c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e121c-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="e121c-128">Procedury</span><span class="sxs-lookup"><span data-stu-id="e121c-128">Procedures</span></span>](index.md)
- [<span data-ttu-id="e121c-129">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="e121c-129">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="e121c-130">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="e121c-130">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="e121c-131">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e121c-131">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="e121c-132">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="e121c-132">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="e121c-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="e121c-133">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e121c-134">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="e121c-134">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="e121c-135">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="e121c-135">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="e121c-136">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="e121c-136">Loop Structures</span></span>](../control-flow/loop-structures.md)
