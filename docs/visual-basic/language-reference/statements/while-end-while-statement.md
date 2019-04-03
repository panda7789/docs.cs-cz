---
title: While...End While – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843705"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="1e166-102">While...End While – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e166-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="1e166-103">Spustí řadu příkazů, dokud bude podmínka `True`.</span><span class="sxs-lookup"><span data-stu-id="1e166-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e166-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e166-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="1e166-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1e166-105">Parts</span></span>  
  
|<span data-ttu-id="1e166-106">Termín</span><span class="sxs-lookup"><span data-stu-id="1e166-106">Term</span></span>|<span data-ttu-id="1e166-107">Definice</span><span class="sxs-lookup"><span data-stu-id="1e166-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="1e166-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1e166-108">Required.</span></span> <span data-ttu-id="1e166-109">`Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="1e166-109">`Boolean` expression.</span></span> <span data-ttu-id="1e166-110">Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.</span><span class="sxs-lookup"><span data-stu-id="1e166-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="1e166-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1e166-111">Optional.</span></span> <span data-ttu-id="1e166-112">Jeden nebo více následujících příkazů `While`, která spustí při každém `condition` je `True`.</span><span class="sxs-lookup"><span data-stu-id="1e166-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="1e166-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1e166-113">Optional.</span></span> <span data-ttu-id="1e166-114">Předá řízení následující iteraci `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="1e166-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="1e166-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1e166-115">Optional.</span></span> <span data-ttu-id="1e166-116">Přenese ovládací prvek z celkového počtu `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="1e166-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="1e166-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1e166-117">Required.</span></span> <span data-ttu-id="1e166-118">Ukončí definici `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="1e166-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e166-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e166-119">Remarks</span></span>  
 <span data-ttu-id="1e166-120">Použití `While...End While` struktury, pokud chcete sadu příkazů na nekonečný počet dob, opakujte tak dlouho, dokud zůstává podmínku `True`.</span><span class="sxs-lookup"><span data-stu-id="1e166-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="1e166-121">Pokud chcete větší flexibilitu s kde otestuje podmínku nebo co výsledek, můžete ji otestovat pro můžete dát přednost [udělat... Smyčky příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e166-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="1e166-122">Pokud chcete do sady počtu opakování, opakujte příkazy [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle vhodnější použít.</span><span class="sxs-lookup"><span data-stu-id="1e166-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e166-123">`While` – Klíčové slovo se používá také v [udělat... Smyčky příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While – klauzule](../../../visual-basic/language-reference/queries/skip-while-clause.md) a [Take While – klauzule](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1e166-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="1e166-124">Pokud `condition` je `True`, všechny nástroje `statements` běhu až do `End While` příkaz dochází.</span><span class="sxs-lookup"><span data-stu-id="1e166-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="1e166-125">Ovládací prvek vrátí na `While` příkaz, a `condition` proběhne znovu.</span><span class="sxs-lookup"><span data-stu-id="1e166-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="1e166-126">Pokud `condition` je stále `True`, proces se opakuje.</span><span class="sxs-lookup"><span data-stu-id="1e166-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="1e166-127">Pokud má `False`, řízení se předá příkazu, který následuje `End While` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1e166-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="1e166-128">`While` Příkaz vždy zkontrolujte tuto podmínku před spuštěním smyčky.</span><span class="sxs-lookup"><span data-stu-id="1e166-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="1e166-129">Opakování ve smyčce bude pokračovat, když podmínka zůstane `True`.</span><span class="sxs-lookup"><span data-stu-id="1e166-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="1e166-130">Pokud `condition` je `False` při prvním zadání smyčky, nespustí ještě jednou.</span><span class="sxs-lookup"><span data-stu-id="1e166-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="1e166-131">`condition` Obvykle výsledkem porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnotí [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`).</span><span class="sxs-lookup"><span data-stu-id="1e166-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="1e166-132">Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselného typu, který byl převeden na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1e166-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="1e166-133">Je možné vnořovat `While` smyčky tak, že v jednom průchodu v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="1e166-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="1e166-134">Lze také vnořit různé druhy řídicích struktur v rámci mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="1e166-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="1e166-135">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="1e166-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="1e166-136">Při ukončení</span><span class="sxs-lookup"><span data-stu-id="1e166-136">Exit While</span></span>  
 <span data-ttu-id="1e166-137">[Ukončení při](../../../visual-basic/language-reference/statements/exit-statement.md) příkazu můžete zadat další způsob, jak ukončit `While` smyčky.</span><span class="sxs-lookup"><span data-stu-id="1e166-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="1e166-138">`Exit While` okamžitě přenese ovládací prvek na příkazu, který následuje `End While` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1e166-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="1e166-139">Obvykle použijete `Exit While` po vyhodnocení některé podmínky (třeba v `If...Then...Else` struktura).</span><span class="sxs-lookup"><span data-stu-id="1e166-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="1e166-140">Můžete chtít ukončení smyčky je-li zjistit podmínku, která umožňuje zbytečné nebo nemožné, chcete-li pokračovat, iterace, jako jsou chybné hodnotu nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="1e166-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="1e166-141">Můžete použít `Exit While` při testování pro podmínku, která by mohla způsobit, že *vznik nekonečné smyčky*, což je smyčku, která může běžet velmi velká, nebo dokonce nekonečné počet pokusů.</span><span class="sxs-lookup"><span data-stu-id="1e166-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="1e166-142">Pak můžete použít `Exit While` dostala mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="1e166-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="1e166-143">Umístíte libovolný počet `Exit While` příkazy kdekoli v `While` smyčky.</span><span class="sxs-lookup"><span data-stu-id="1e166-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="1e166-144">Při použití v rámci vnořené `While` smyčky, `Exit While` předává řízení mimo vnitřní smyčky a na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="1e166-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="1e166-145">`Continue While` Příkaz okamžitě předá řízení další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="1e166-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="1e166-146">Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e166-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e166-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e166-147">Example</span></span>  
 <span data-ttu-id="1e166-148">V následujícím příkladu se příkazy ve smyčce dál běžet až `index` proměnnou je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="1e166-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="1e166-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e166-149">Example</span></span>  
 <span data-ttu-id="1e166-150">Následující příklad ukazuje použití `Continue While` a `Exit While` příkazy.</span><span class="sxs-lookup"><span data-stu-id="1e166-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="1e166-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e166-151">Example</span></span>  
 <span data-ttu-id="1e166-152">Následující příklad načte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="1e166-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="1e166-153"><xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky.</span><span class="sxs-lookup"><span data-stu-id="1e166-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="1e166-154">V `While` podmínku, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` Určuje, zda soubor obsahuje další znaky.</span><span class="sxs-lookup"><span data-stu-id="1e166-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="1e166-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e166-155">See also</span></span>

- [<span data-ttu-id="1e166-156">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="1e166-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="1e166-157">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="1e166-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="1e166-158">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="1e166-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="1e166-159">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="1e166-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="1e166-160">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="1e166-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="1e166-161">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="1e166-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="1e166-162">Příkaz Continue</span><span class="sxs-lookup"><span data-stu-id="1e166-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
