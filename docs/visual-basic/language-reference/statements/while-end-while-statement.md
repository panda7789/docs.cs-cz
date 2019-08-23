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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965815"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="9c035-102">While...End While – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c035-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="9c035-103">Spustí sérii příkazů, pokud je `True`daná podmínka.</span><span class="sxs-lookup"><span data-stu-id="9c035-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c035-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c035-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="9c035-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9c035-105">Parts</span></span>  
  
|<span data-ttu-id="9c035-106">Termín</span><span class="sxs-lookup"><span data-stu-id="9c035-106">Term</span></span>|<span data-ttu-id="9c035-107">Definice</span><span class="sxs-lookup"><span data-stu-id="9c035-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="9c035-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9c035-108">Required.</span></span> <span data-ttu-id="9c035-109">`Boolean`vyjádření.</span><span class="sxs-lookup"><span data-stu-id="9c035-109">`Boolean` expression.</span></span> <span data-ttu-id="9c035-110">Pokud `condition` `False`je `Nothing`, Visual Basic považuje za.</span><span class="sxs-lookup"><span data-stu-id="9c035-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="9c035-111">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="9c035-111">Optional.</span></span> <span data-ttu-id="9c035-112">Jeden nebo více níže uvedených `While`příkazů, které jsou spouštěny `True`pokaždé, když `condition` je.</span><span class="sxs-lookup"><span data-stu-id="9c035-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="9c035-113">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="9c035-113">Optional.</span></span> <span data-ttu-id="9c035-114">Přenáší řízení na další iteraci `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="9c035-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="9c035-115">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="9c035-115">Optional.</span></span> <span data-ttu-id="9c035-116">Přenáší řízení `While` z bloku.</span><span class="sxs-lookup"><span data-stu-id="9c035-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="9c035-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9c035-117">Required.</span></span> <span data-ttu-id="9c035-118">Ukončí definici `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="9c035-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c035-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c035-119">Remarks</span></span>  
 <span data-ttu-id="9c035-120">Strukturu použijte, pokud chcete opakovat sadu příkazů neurčitému počtu výskytů, dokud podmínka zůstane `True`. `While...End While`</span><span class="sxs-lookup"><span data-stu-id="9c035-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="9c035-121">Pokud potřebujete větší flexibilitu při testování podmínky nebo k tomu, pro který výsledek testujete, můžete preferovat do.. [. Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9c035-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="9c035-122">Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="9c035-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c035-123">`While` Klíčové slovo se používá také v do [... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md), [klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) a [klauzuli HAVING while](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9c035-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="9c035-124">Pokud `condition` je `True`, `End While` všechny `statements` spuštění až do chvíle, kdy se příkaz vyskytne.</span><span class="sxs-lookup"><span data-stu-id="9c035-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="9c035-125">Ovládací prvek se pak vrátí `While` do příkazu a `condition` znovu se vyhradí.</span><span class="sxs-lookup"><span data-stu-id="9c035-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="9c035-126">Pokud `condition` je stále `True`, proces se opakuje.</span><span class="sxs-lookup"><span data-stu-id="9c035-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="9c035-127">Pokud je `End While` , řízení se předá příkazu, který následuje po příkazu. `False`</span><span class="sxs-lookup"><span data-stu-id="9c035-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="9c035-128">`While` Příkaz vždy před spuštěním smyčky kontroluje podmínku.</span><span class="sxs-lookup"><span data-stu-id="9c035-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="9c035-129">Opakování pokračuje, i když podmínka zůstane `True`.</span><span class="sxs-lookup"><span data-stu-id="9c035-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="9c035-130">Pokud `condition` je`False` při prvním zadání smyčky, nebude spuštěna ani jednou.</span><span class="sxs-lookup"><span data-stu-id="9c035-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="9c035-131">Obvykle `condition` je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` nebo `False`).</span><span class="sxs-lookup"><span data-stu-id="9c035-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="9c035-132">Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselný typ, který byl převeden na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="9c035-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="9c035-133">Smyčky můžete vnořovat `While` vložením jedné smyčky do jiné.</span><span class="sxs-lookup"><span data-stu-id="9c035-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="9c035-134">Můžete také vnořit různé druhy řídicích struktur mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="9c035-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="9c035-135">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="9c035-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="9c035-136">Ukončit během</span><span class="sxs-lookup"><span data-stu-id="9c035-136">Exit While</span></span>  
 <span data-ttu-id="9c035-137">Příkaz [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) může poskytnout jiný způsob, jak ukončit `While` smyčku.</span><span class="sxs-lookup"><span data-stu-id="9c035-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="9c035-138">`Exit While`okamžitě přenese řízení na příkaz, který následuje `End While` po příkazu.</span><span class="sxs-lookup"><span data-stu-id="9c035-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="9c035-139">Obvykle se používá `Exit While` po vyhodnocení některé podmínky (například `If...Then...Else` ve struktuře).</span><span class="sxs-lookup"><span data-stu-id="9c035-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="9c035-140">Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="9c035-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="9c035-141">Můžete použít `Exit While` při testování podmínky, která by mohla způsobit nekonečnou *smyčku*, což je smyčka, která by mohla běžet velmi velkým nebo dokonce nekonečným počtem výskytů.</span><span class="sxs-lookup"><span data-stu-id="9c035-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="9c035-142">Pak můžete použít `Exit While` k řídicímu cyklu smyčky.</span><span class="sxs-lookup"><span data-stu-id="9c035-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="9c035-143">Libovolný počet `Exit While` příkazů můžete umístit kdekoli `While` ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="9c035-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="9c035-144">Při použití v rámci `While` vnořených smyček `Exit While` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="9c035-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="9c035-145">`Continue While` Příkaz okamžitě převede řízení na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="9c035-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="9c035-146">Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9c035-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c035-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c035-147">Example</span></span>  
 <span data-ttu-id="9c035-148">V následujícím příkladu jsou příkazy ve smyčce nadále spuštěny, `index` dokud je proměnná větší než 10.</span><span class="sxs-lookup"><span data-stu-id="9c035-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="9c035-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c035-149">Example</span></span>  
 <span data-ttu-id="9c035-150">Následující příklad ilustruje použití `Continue While` příkazů a. `Exit While`</span><span class="sxs-lookup"><span data-stu-id="9c035-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="9c035-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c035-151">Example</span></span>  
 <span data-ttu-id="9c035-152">Následující příklad přečte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="9c035-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="9c035-153">Metoda otevře soubor a <xref:System.IO.StreamReader> vrátí hodnotu, která přečte znaky. <xref:System.IO.File.OpenText%2A></span><span class="sxs-lookup"><span data-stu-id="9c035-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="9c035-154">V podmínce <xref:System.IO.StreamReader.Peek%2A> Metoda`StreamReader` určuje, zda soubor obsahuje další znaky. `While`</span><span class="sxs-lookup"><span data-stu-id="9c035-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="9c035-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c035-155">See also</span></span>

- [<span data-ttu-id="9c035-156">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="9c035-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="9c035-157">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="9c035-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="9c035-158">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="9c035-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="9c035-159">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="9c035-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="9c035-160">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="9c035-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="9c035-161">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="9c035-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="9c035-162">Příkaz Continue</span><span class="sxs-lookup"><span data-stu-id="9c035-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
