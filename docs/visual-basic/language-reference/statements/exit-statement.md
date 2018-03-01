---
title: "Exit – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="a0c03-102">Exit – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0c03-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="a0c03-103">Ukončí proceduru nebo bloku a předá řízení příkaz následující volání procedury nebo definici bloku.</span><span class="sxs-lookup"><span data-stu-id="a0c03-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0c03-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="a0c03-105">Příkazy</span><span class="sxs-lookup"><span data-stu-id="a0c03-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="a0c03-106">Okamžitě ukončí `Do` smyčky v zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="a0c03-107">Provádění pokračuje následující příkaz `Loop` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="a0c03-108">`Exit Do`dá se použít jenom uvnitř `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="a0c03-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="a0c03-109">Při použití uvnitř vnořené `Do` smyčky, `Exit Do` ukončí nejvnitřnější smyčky a předá řízení další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="a0c03-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="a0c03-110">Okamžitě ukončí `For` smyčky v zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="a0c03-111">Provádění pokračuje následující příkaz `Next` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="a0c03-112">`Exit For`dá se použít jenom uvnitř `For`... `Next` nebo `For Each`... `Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="a0c03-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="a0c03-113">Při použití uvnitř vnořené `For` smyčky, `Exit For` ukončí nejvnitřnější smyčky a předá řízení další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="a0c03-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="a0c03-114">Okamžitě ukončí `Function` postup, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="a0c03-115">Provádění pokračuje příkaz následující příkaz, který volá `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="a0c03-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="a0c03-116">`Exit Function`dá se použít jenom uvnitř `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="a0c03-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="a0c03-117">K určení návratovou hodnotu, lze přiřadit hodnotu na řádek před název funkce `Exit Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="a0c03-118">Pokud chcete přiřadit návratovou hodnotu a ukončete funkce v jednom příkazu, místo toho můžete [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a0c03-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="a0c03-119">Okamžitě ukončí `Property` postup, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="a0c03-120">Provádění pokračuje příkaz, který volá `Property` postup, který je s příkazem požaduje nebo nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0c03-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="a0c03-121">`Exit Property`dá se použít jenom uvnitř vlastnost `Get` nebo `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="a0c03-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="a0c03-122">K určení návratovou hodnotu v `Get` postup, můžete přiřadit hodnotu název funkce na řádku před `Exit Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="a0c03-123">K přiřazení návratovou hodnotu a ukončení `Get` postup v jednom příkazu, místo toho můžete `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="a0c03-124">V `Set` postupu `Exit Property` je ekvivalentní příkaz `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="a0c03-125">Okamžitě ukončí `Select Case` blok, ve kterém zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="a0c03-126">Provádění pokračuje následující příkaz `End Select` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="a0c03-127">`Exit Select`dá se použít jenom uvnitř `Select Case` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="a0c03-128">Okamžitě ukončí `Sub` postup, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="a0c03-129">Provádění pokračuje příkaz následující příkaz, který volá `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="a0c03-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="a0c03-130">`Exit Sub`dá se použít jenom uvnitř `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="a0c03-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="a0c03-131">V `Sub` postupu `Exit Sub` je ekvivalentní příkaz `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="a0c03-132">Okamžitě ukončí `Try` nebo `Catch` blok, ve kterém zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="a0c03-133">Provádění pokračuje `Finally` blokování, pokud existuje, nebo s následující příkaz `End Try` příkaz, jinak hodnota.</span><span class="sxs-lookup"><span data-stu-id="a0c03-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="a0c03-134">`Exit Try`dá se použít jenom uvnitř `Try` nebo `Catch` blok a není uvnitř `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="a0c03-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="a0c03-135">Okamžitě ukončí `While` smyčky v zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c03-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="a0c03-136">Provádění pokračuje následující příkaz `End While` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0c03-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="a0c03-137">`Exit While`dá se použít jenom uvnitř `While` smyčky.</span><span class="sxs-lookup"><span data-stu-id="a0c03-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="a0c03-138">Při použití uvnitř vnořené `While` smyčky, `Exit While` předá řízení smyčky, která je jednu úroveň vnořené nad smyčky kde `Exit While` dojde.</span><span class="sxs-lookup"><span data-stu-id="a0c03-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0c03-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0c03-139">Remarks</span></span>  
 <span data-ttu-id="a0c03-140">Nezaměňujte `Exit` příkazy s `End` příkazy.</span><span class="sxs-lookup"><span data-stu-id="a0c03-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="a0c03-141">`Exit`nedefinuje konec příkazu.</span><span class="sxs-lookup"><span data-stu-id="a0c03-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c03-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c03-142">Example</span></span>  
 <span data-ttu-id="a0c03-143">V následujícím příkladu smyčku zastaví smyčky při `index` proměnné je větší než 100.</span><span class="sxs-lookup"><span data-stu-id="a0c03-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="a0c03-144">`If` Příkaz ve smyčce, ale způsobuje `Exit Do` příkaz k zastavení smyčky do proměnné index je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="a0c03-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="a0c03-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c03-145">Example</span></span>  
 <span data-ttu-id="a0c03-146">Následující příklad přiřadí návratovou hodnotu pro název funkce `myFunction`a pak používá `Exit Function` vrátit z funkce.</span><span class="sxs-lookup"><span data-stu-id="a0c03-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a0c03-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c03-147">Example</span></span>  
 <span data-ttu-id="a0c03-148">Následující příklad používá [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) přiřadit návratovou hodnotu a ukončení funkce.</span><span class="sxs-lookup"><span data-stu-id="a0c03-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a0c03-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c03-149">See Also</span></span>  
 [<span data-ttu-id="a0c03-150">Continue – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [<span data-ttu-id="a0c03-151">Provést... Příkaz smyčky</span><span class="sxs-lookup"><span data-stu-id="a0c03-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="a0c03-152">End – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="a0c03-153">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="a0c03-154">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="a0c03-155">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="a0c03-156">Return – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="a0c03-157">Stop – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="a0c03-158">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="a0c03-159">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0c03-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
