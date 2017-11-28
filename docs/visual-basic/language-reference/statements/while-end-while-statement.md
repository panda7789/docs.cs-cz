---
title: "While...End While – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f831f233eaa4f1c38d56f3a89bda9b0cf1bccaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="cc24a-102">While...End While – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc24a-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="cc24a-103">Spouští řadu příkazů, dokud danou podmínkou je `True`.</span><span class="sxs-lookup"><span data-stu-id="cc24a-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc24a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc24a-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="cc24a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="cc24a-105">Parts</span></span>  
  
|<span data-ttu-id="cc24a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="cc24a-106">Term</span></span>|<span data-ttu-id="cc24a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="cc24a-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="cc24a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cc24a-108">Required.</span></span> <span data-ttu-id="cc24a-109">`Boolean`výraz.</span><span class="sxs-lookup"><span data-stu-id="cc24a-109">`Boolean` expression.</span></span> <span data-ttu-id="cc24a-110">Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.</span><span class="sxs-lookup"><span data-stu-id="cc24a-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="cc24a-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cc24a-111">Optional.</span></span> <span data-ttu-id="cc24a-112">Jeden nebo více následujících příkazů `While`, která spustit pokaždé, když `condition` je `True`.</span><span class="sxs-lookup"><span data-stu-id="cc24a-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="cc24a-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cc24a-113">Optional.</span></span> <span data-ttu-id="cc24a-114">Přenosy ovládacího prvku do další iterace `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="cc24a-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="cc24a-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cc24a-115">Optional.</span></span> <span data-ttu-id="cc24a-116">Přenosy ovládacího prvku z `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="cc24a-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="cc24a-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cc24a-117">Required.</span></span> <span data-ttu-id="cc24a-118">Ukončí definice `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="cc24a-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc24a-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc24a-119">Remarks</span></span>  
 <span data-ttu-id="cc24a-120">Použití `While...End While` struktury, pokud chcete sadu příkazů na nekonečný počet dobu, opakujte, dokud zůstává podmínku `True`.</span><span class="sxs-lookup"><span data-stu-id="cc24a-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="cc24a-121">Pokud chcete větší flexibilitu s kde otestuje podmínku nebo co výsledný můžete otestovat pro možná budete chtít [provést... Cykly příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc24a-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="cc24a-122">Pokud chcete opakujte příkazy se stanoveným počtem dobu, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="cc24a-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc24a-123">`While` – Klíčové slovo je používán také [provést... Cykly příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While – klauzule](../../../visual-basic/language-reference/queries/skip-while-clause.md) a [Take While – klauzule](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cc24a-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="cc24a-124">Pokud `condition` je `True`, všechny z `statements` spuštění, dokud `End While` příkaz je zjistil.</span><span class="sxs-lookup"><span data-stu-id="cc24a-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="cc24a-125">Pak vrátí k řízení `While` příkaz, a `condition` je znovu zaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="cc24a-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="cc24a-126">Pokud `condition` stále `True`, tento proces se opakuje.</span><span class="sxs-lookup"><span data-stu-id="cc24a-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="cc24a-127">Pokud má `False`, řídit předává do příkazu, který odpovídá `End While` příkaz.</span><span class="sxs-lookup"><span data-stu-id="cc24a-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="cc24a-128">`While` Příkaz vždy kontroluje podmínku před spuštěním smyčky.</span><span class="sxs-lookup"><span data-stu-id="cc24a-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="cc24a-129">Ve smyčce bude pokračovat při současném zachování stavu `True`.</span><span class="sxs-lookup"><span data-stu-id="cc24a-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="cc24a-130">Pokud `condition` je `False` když poprvé vstoupíte smyčky, nefunguje i jednou.</span><span class="sxs-lookup"><span data-stu-id="cc24a-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="cc24a-131">`condition` Obvykle způsobují porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnocuje [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`).</span><span class="sxs-lookup"><span data-stu-id="cc24a-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="cc24a-132">Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselného typu, který byl převeden na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cc24a-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="cc24a-133">Lze vnořit `While` smyčky tím, že jeden smyčky v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="cc24a-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="cc24a-134">Můžete také vnořovat různé druhy řídicí struktury v rámci jednu na druhou.</span><span class="sxs-lookup"><span data-stu-id="cc24a-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="cc24a-135">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="cc24a-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="cc24a-136">Při ukončení</span><span class="sxs-lookup"><span data-stu-id="cc24a-136">Exit While</span></span>  
 <span data-ttu-id="cc24a-137">[Ukončete při](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz můžete zadat jiný způsob, jak ukončit `While` smyčky.</span><span class="sxs-lookup"><span data-stu-id="cc24a-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="cc24a-138">`Exit While`příkaz, který následuje okamžitě předá řízení `End While` příkaz.</span><span class="sxs-lookup"><span data-stu-id="cc24a-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="cc24a-139">Obvykle použijete `Exit While` po některé podmínka vyhodnocena (například v `If...Then...Else` struktura).</span><span class="sxs-lookup"><span data-stu-id="cc24a-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="cc24a-140">Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která umožňuje nepotřebné nebo dokonce znemožňují pokračujte iterace, třeba chybná hodnota nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="cc24a-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="cc24a-141">Můžete použít `Exit While` při testování pro podmínku, která by mohla způsobovat *nekonečná smyčka*, což je smyčku, který by mohl spustit i nekonečné nebo velmi velký počet časy.</span><span class="sxs-lookup"><span data-stu-id="cc24a-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="cc24a-142">Pak můžete použít `Exit While` abyste se vyhnuli smyčky.</span><span class="sxs-lookup"><span data-stu-id="cc24a-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="cc24a-143">Můžete umístit libovolný počet `Exit While` příkazy kdekoli v `While` smyčky.</span><span class="sxs-lookup"><span data-stu-id="cc24a-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="cc24a-144">Při použití uvnitř vnořené `While` smyčky, `Exit While` přenosy ovládacího prvku mimo nejvnitřnější smyčky a do další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="cc24a-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="cc24a-145">`Continue While` Příkaz okamžitě přenosy ovládacího prvku do další iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="cc24a-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="cc24a-146">Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc24a-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc24a-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc24a-147">Example</span></span>  
 <span data-ttu-id="cc24a-148">V následujícím příkladu, příkazy v smyčky dál běžet, dokud `index` proměnná je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="cc24a-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="cc24a-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc24a-149">Example</span></span>  
 <span data-ttu-id="cc24a-150">Následující příklad ukazuje použití `Continue While` a `Exit While` příkazy.</span><span class="sxs-lookup"><span data-stu-id="cc24a-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="cc24a-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc24a-151">Example</span></span>  
 <span data-ttu-id="cc24a-152">Následující příklad načte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="cc24a-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="cc24a-153"><xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky.</span><span class="sxs-lookup"><span data-stu-id="cc24a-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="cc24a-154">V `While` podmínky, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` Určuje, zda soubor obsahuje další znaky.</span><span class="sxs-lookup"><span data-stu-id="cc24a-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cc24a-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc24a-155">See Also</span></span>  
 [<span data-ttu-id="cc24a-156">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="cc24a-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="cc24a-157">Provést... Příkaz smyčky</span><span class="sxs-lookup"><span data-stu-id="cc24a-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="cc24a-158">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="cc24a-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="cc24a-159">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="cc24a-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="cc24a-160">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="cc24a-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="cc24a-161">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="cc24a-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="cc24a-162">Continue – příkaz</span><span class="sxs-lookup"><span data-stu-id="cc24a-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
