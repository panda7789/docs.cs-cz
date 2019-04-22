---
title: Exit – příkaz (Visual Basic)
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
ms.openlocfilehash: 1f386694bd7425ee530b9305ab684b730f9b73c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832629"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="13216-102">Exit – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13216-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="13216-103">Ukončí proceduru nebo blok a okamžitě přenese ovládací prvek do příkazu za voláním procedury nebo definicí bloku.</span><span class="sxs-lookup"><span data-stu-id="13216-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13216-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13216-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="13216-105">Příkazy</span><span class="sxs-lookup"><span data-stu-id="13216-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="13216-106">Okamžitě ukončí `Do` smyčky v kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="13216-107">Provádění pokračuje pomocí následujícího příkazu `Loop` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="13216-108">`Exit Do` může být použit pouze uvnitř `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="13216-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="13216-109">Při použití v rámci vnořené `Do` smyčky, `Exit Do` ukončení vnitřní smyčky a přenese ovládací prvek na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="13216-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="13216-110">Okamžitě ukončí `For` smyčky v kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="13216-111">Provádění pokračuje pomocí následujícího příkazu `Next` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="13216-112">`Exit For` může být použit pouze uvnitř `For`... `Next` nebo `For Each`... `Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="13216-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="13216-113">Při použití v rámci vnořené `For` smyčky, `Exit For` ukončení vnitřní smyčky a přenese ovládací prvek na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="13216-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="13216-114">Okamžitě ukončí `Function` procedura, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="13216-115">Pokračuje s příkazu za příkazem, který volá se, `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="13216-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="13216-116">`Exit Function` může být použit pouze uvnitř `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="13216-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="13216-117">K určení návratovou hodnotu, můžete přiřadit hodnotu k názvu funkce na řádku před `Exit Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="13216-118">Pro přiřazení návratovou hodnotu a ukončení funkce v jednom příkazu, můžete místo toho použít [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="13216-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="13216-119">Okamžitě ukončí `Property` procedura, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="13216-120">Provádění pokračuje s příkazem, který volá `Property` procedury, to znamená, s příkazem požádat nebo nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13216-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="13216-121">`Exit Property` může být použit pouze uvnitř vlastnosti `Get` nebo `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="13216-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="13216-122">K určení návratovou hodnotu v `Get` postup, můžete přiřadit hodnotu k názvu funkce na řádku před `Exit Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="13216-123">K přiřazení návratovou hodnotu a ukončení `Get` postupu v jednom příkazu, můžete místo toho použít `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="13216-124">V `Set` postupu `Exit Property` je ekvivalentní příkazu `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="13216-125">Okamžitě ukončí `Select Case` blok, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="13216-126">Provádění pokračuje pomocí následujícího příkazu `End Select` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="13216-127">`Exit Select` může být použit pouze uvnitř `Select Case` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="13216-128">Okamžitě ukončí `Sub` procedura, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="13216-129">Pokračuje s příkazu za příkazem, který volá se, `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="13216-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="13216-130">`Exit Sub` může být použit pouze uvnitř `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="13216-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="13216-131">V `Sub` postupu `Exit Sub` je ekvivalentní příkazu `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="13216-132">Okamžitě ukončí `Try` nebo `Catch` blok, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="13216-133">Provádění pokračuje `Finally` blokovat, pokud existuje, nebo pomocí následujícího příkazu `End Try` příkaz jinak.</span><span class="sxs-lookup"><span data-stu-id="13216-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="13216-134">`Exit Try` může být použit pouze uvnitř `Try` nebo `Catch` bloku a ne uvnitř `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="13216-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="13216-135">Okamžitě ukončí `While` smyčky v kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="13216-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="13216-136">Provádění pokračuje pomocí následujícího příkazu `End While` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13216-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="13216-137">`Exit While` může být použit pouze uvnitř `While` smyčky.</span><span class="sxs-lookup"><span data-stu-id="13216-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="13216-138">Při použití v rámci vnořené `While` smyčky, `Exit While` předá řízení smyčky, která je jednu úroveň vnořeného nad smyčky kde `Exit While` dojde k.</span><span class="sxs-lookup"><span data-stu-id="13216-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13216-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13216-139">Remarks</span></span>  
 <span data-ttu-id="13216-140">Nezaměňujte `Exit` příkazy `End` příkazy.</span><span class="sxs-lookup"><span data-stu-id="13216-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="13216-141">`Exit` konec příkazu není definován.</span><span class="sxs-lookup"><span data-stu-id="13216-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13216-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="13216-142">Example</span></span>  
 <span data-ttu-id="13216-143">V následujícím příkladu podmínka smyčky zastaví smyčky při `index` proměnnou je větší než 100.</span><span class="sxs-lookup"><span data-stu-id="13216-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="13216-144">`If` Příkaz ve smyčce, ale způsobí, že `Exit Do` příkaz zastaví smyčky, pokud indexovaná proměnná je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="13216-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="13216-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="13216-145">Example</span></span>  
 <span data-ttu-id="13216-146">Následující příklad přiřadí název funkce návratová hodnota `myFunction`a potom použije `Exit Function` vrácení z funkce.</span><span class="sxs-lookup"><span data-stu-id="13216-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="13216-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="13216-147">Example</span></span>  
 <span data-ttu-id="13216-148">V následujícím příkladu [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) přiřazovat návratovou hodnotu a ukončení funkce.</span><span class="sxs-lookup"><span data-stu-id="13216-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="13216-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13216-149">See also</span></span>

- [<span data-ttu-id="13216-150">Příkaz Continue</span><span class="sxs-lookup"><span data-stu-id="13216-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
- [<span data-ttu-id="13216-151">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="13216-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="13216-152">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="13216-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
- [<span data-ttu-id="13216-153">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="13216-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="13216-154">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="13216-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="13216-155">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="13216-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="13216-156">Příkaz Return</span><span class="sxs-lookup"><span data-stu-id="13216-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="13216-157">Příkaz Stop</span><span class="sxs-lookup"><span data-stu-id="13216-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="13216-158">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="13216-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="13216-159">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="13216-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
