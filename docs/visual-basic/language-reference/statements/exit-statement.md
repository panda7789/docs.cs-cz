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
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="2edf5-102">Exit – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2edf5-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="2edf5-103">Ukončí proceduru nebo blok a okamžitě přenese řízení do příkazu za voláním procedury nebo definicí bloku.</span><span class="sxs-lookup"><span data-stu-id="2edf5-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="2edf5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2edf5-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="2edf5-105">Příkazy</span><span class="sxs-lookup"><span data-stu-id="2edf5-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="2edf5-106">Okamžitě ukončí `Do` smyčku, ve které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="2edf5-107">Provádění pokračuje s příkazem za příkazem `Loop`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="2edf5-108">`Exit Do` lze použít pouze uvnitř smyčky `Do`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="2edf5-109">Při použití ve vnořených cyklech `Do` `Exit Do` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="2edf5-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="2edf5-110">Okamžitě ukončí `For` smyčku, ve které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="2edf5-111">Provádění pokračuje s příkazem za příkazem `Next`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="2edf5-112">`Exit For` lze použít pouze uvnitř `For`...`Next` nebo `For Each`...`Next` smyčka.</span><span class="sxs-lookup"><span data-stu-id="2edf5-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="2edf5-113">Při použití ve vnořených cyklech `For` `Exit For` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="2edf5-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="2edf5-114">Okamžitě ukončí `Function` postup, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="2edf5-115">Provádění pokračuje příkazem po příkazu, který se nazývá `Function` procedura.</span><span class="sxs-lookup"><span data-stu-id="2edf5-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="2edf5-116">`Exit Function` lze použít pouze v rámci `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="2edf5-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="2edf5-117">Chcete-li zadat návratovou hodnotu, můžete hodnotu přiřadit názvu funkce na řádku před příkazem `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="2edf5-118">Chcete-li přiřadit návratovou hodnotu a ukončit funkci v jednom příkazu, můžete místo toho použít [příkaz return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2edf5-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="2edf5-119">Okamžitě ukončí `Property` postup, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="2edf5-120">Provádění pokračuje s příkazem, který se nazývá `Property` procedura, to znamená s příkazem požadujícím nebo nastavením hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2edf5-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="2edf5-121">`Exit Property` lze použít pouze uvnitř vlastnosti `Get` nebo `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="2edf5-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="2edf5-122">Chcete-li zadat návratovou hodnotu v `Get` proceduře, lze hodnotu přiřadit názvu funkce na řádku před příkazem `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="2edf5-123">Chcete-li přiřadit návratovou hodnotu a ukončit `Get` procedura v jednom příkazu, můžete místo toho použít příkaz `Return`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="2edf5-124">V `Set` proceduře je příkaz `Exit Property` ekvivalentní příkazu `Return`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="2edf5-125">Okamžitě ukončí `Select Case` blok, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="2edf5-126">Provádění pokračuje s příkazem za příkazem `End Select`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="2edf5-127">`Exit Select` lze použít pouze uvnitř příkazu `Select Case`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="2edf5-128">Okamžitě ukončí `Sub` postup, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="2edf5-129">Provádění pokračuje příkazem po příkazu, který se nazývá `Sub` procedura.</span><span class="sxs-lookup"><span data-stu-id="2edf5-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="2edf5-130">`Exit Sub` lze použít pouze v rámci `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="2edf5-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="2edf5-131">V `Sub` proceduře je příkaz `Exit Sub` ekvivalentní příkazu `Return`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="2edf5-132">Okamžitě ukončí `Try` nebo `Catch` blok, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="2edf5-133">Provádění pokračuje s blokem `Finally`, pokud existuje, nebo s příkazem, který následuje za příkazem `End Try` jinak.</span><span class="sxs-lookup"><span data-stu-id="2edf5-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="2edf5-134">`Exit Try` lze použít pouze uvnitř bloku `Try` nebo `Catch` a nikoli uvnitř `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="2edf5-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="2edf5-135">Okamžitě ukončí `While` smyčku, ve které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="2edf5-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="2edf5-136">Provádění pokračuje s příkazem za příkazem `End While`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="2edf5-137">`Exit While` lze použít pouze uvnitř smyčky `While`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="2edf5-138">Při použití ve vnořených cyklech `While` `Exit While` přenáší řízení na smyčku, která je jednou vnořenou úrovní nad smyčkou, kde `Exit While` nastane.</span><span class="sxs-lookup"><span data-stu-id="2edf5-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="2edf5-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2edf5-139">Remarks</span></span>

<span data-ttu-id="2edf5-140">Nepleťte si `Exit` příkazy s příkazy `End`.</span><span class="sxs-lookup"><span data-stu-id="2edf5-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="2edf5-141">`Exit` nedefinuje konec příkazu.</span><span class="sxs-lookup"><span data-stu-id="2edf5-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="2edf5-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="2edf5-142">Example</span></span>

<span data-ttu-id="2edf5-143">V následujícím příkladu podmínka smyčky zastaví smyčku, když je proměnná `index` větší než 100.</span><span class="sxs-lookup"><span data-stu-id="2edf5-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="2edf5-144">Příkaz `If` ve smyčce ale způsobí, že příkaz `Exit Do` zastaví smyčku v případě, že je proměnná indexu větší než 10.</span><span class="sxs-lookup"><span data-stu-id="2edf5-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="2edf5-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="2edf5-145">Example</span></span>

<span data-ttu-id="2edf5-146">Následující příklad přiřadí návratovou hodnotu k názvu funkce `myFunction`a poté používá `Exit Function` k návratu z funkce:</span><span class="sxs-lookup"><span data-stu-id="2edf5-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="2edf5-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="2edf5-147">Example</span></span>

<span data-ttu-id="2edf5-148">Následující příklad používá [příkaz return](return-statement.md) k přiřazení návratové hodnoty a ukončení funkce:</span><span class="sxs-lookup"><span data-stu-id="2edf5-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="2edf5-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2edf5-149">See also</span></span>

- [<span data-ttu-id="2edf5-150">Příkaz Continue</span><span class="sxs-lookup"><span data-stu-id="2edf5-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="2edf5-151">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="2edf5-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="2edf5-152">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="2edf5-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="2edf5-153">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="2edf5-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="2edf5-154">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="2edf5-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="2edf5-155">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="2edf5-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="2edf5-156">Příkaz Return</span><span class="sxs-lookup"><span data-stu-id="2edf5-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="2edf5-157">Příkaz Stop</span><span class="sxs-lookup"><span data-stu-id="2edf5-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="2edf5-158">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="2edf5-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="2edf5-159">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="2edf5-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
