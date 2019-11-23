---
title: Exit – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345942"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="21252-102">Exit – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21252-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="21252-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span><span class="sxs-lookup"><span data-stu-id="21252-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="21252-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21252-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="21252-105">Příkazy</span><span class="sxs-lookup"><span data-stu-id="21252-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="21252-106">Immediately exits the `Do` loop in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="21252-107">Execution continues with the statement following the `Loop` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="21252-108">`Exit Do` can be used only inside a `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="21252-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="21252-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span><span class="sxs-lookup"><span data-stu-id="21252-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="21252-110">Immediately exits the `For` loop in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="21252-111">Execution continues with the statement following the `Next` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="21252-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span><span class="sxs-lookup"><span data-stu-id="21252-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="21252-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span><span class="sxs-lookup"><span data-stu-id="21252-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="21252-114">Immediately exits the `Function` procedure in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="21252-115">Execution continues with the statement following the statement that called the `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="21252-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="21252-116">`Exit Function` can be used only inside a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="21252-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="21252-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="21252-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="21252-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="21252-119">Immediately exits the `Property` procedure in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="21252-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span><span class="sxs-lookup"><span data-stu-id="21252-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="21252-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="21252-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="21252-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="21252-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="21252-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="21252-125">Immediately exits the `Select Case` block in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="21252-126">Execution continues with the statement following the `End Select` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="21252-127">`Exit Select` can be used only inside a `Select Case` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="21252-128">Immediately exits the `Sub` procedure in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="21252-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="21252-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="21252-130">`Exit Sub` can be used only inside a `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="21252-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="21252-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="21252-132">Immediately exits the `Try` or `Catch` block in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="21252-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span><span class="sxs-lookup"><span data-stu-id="21252-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="21252-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="21252-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="21252-135">Immediately exits the `While` loop in which it appears.</span><span class="sxs-lookup"><span data-stu-id="21252-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="21252-136">Execution continues with the statement following the `End While` statement.</span><span class="sxs-lookup"><span data-stu-id="21252-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="21252-137">`Exit While` can be used only inside a `While` loop.</span><span class="sxs-lookup"><span data-stu-id="21252-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="21252-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span><span class="sxs-lookup"><span data-stu-id="21252-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="21252-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21252-139">Remarks</span></span>

<span data-ttu-id="21252-140">Do not confuse `Exit` statements with `End` statements.</span><span class="sxs-lookup"><span data-stu-id="21252-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="21252-141">`Exit` does not define the end of a statement.</span><span class="sxs-lookup"><span data-stu-id="21252-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="21252-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="21252-142">Example</span></span>

<span data-ttu-id="21252-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span><span class="sxs-lookup"><span data-stu-id="21252-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="21252-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span><span class="sxs-lookup"><span data-stu-id="21252-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="21252-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="21252-145">Example</span></span>

<span data-ttu-id="21252-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span><span class="sxs-lookup"><span data-stu-id="21252-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="21252-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="21252-147">Example</span></span>

<span data-ttu-id="21252-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span><span class="sxs-lookup"><span data-stu-id="21252-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="21252-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21252-149">See also</span></span>

- [<span data-ttu-id="21252-150">Příkaz Continue</span><span class="sxs-lookup"><span data-stu-id="21252-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="21252-151">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="21252-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="21252-152">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="21252-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="21252-153">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="21252-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="21252-154">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="21252-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="21252-155">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="21252-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="21252-156">Příkaz Return</span><span class="sxs-lookup"><span data-stu-id="21252-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="21252-157">Příkaz Stop</span><span class="sxs-lookup"><span data-stu-id="21252-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="21252-158">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="21252-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="21252-159">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="21252-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
