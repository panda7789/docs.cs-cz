---
title: While...End While – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: d9eb8cb95d46e860aa127954d7b44e37991d4a13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391583"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="faf79-102">While...End While – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faf79-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="faf79-103">Spustí sérii příkazů, pokud je daná podmínka `True` .</span><span class="sxs-lookup"><span data-stu-id="faf79-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faf79-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="faf79-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="faf79-105">Parts</span></span>  
  
|<span data-ttu-id="faf79-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="faf79-106">Term</span></span>|<span data-ttu-id="faf79-107">Definice</span><span class="sxs-lookup"><span data-stu-id="faf79-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="faf79-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="faf79-108">Required.</span></span> <span data-ttu-id="faf79-109">`Boolean`vyjádření.</span><span class="sxs-lookup"><span data-stu-id="faf79-109">`Boolean` expression.</span></span> <span data-ttu-id="faf79-110">Pokud `condition` je `Nothing` , Visual Basic považuje za `False` .</span><span class="sxs-lookup"><span data-stu-id="faf79-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="faf79-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="faf79-111">Optional.</span></span> <span data-ttu-id="faf79-112">Jeden nebo více níže uvedených příkazů `While` , které jsou spouštěny pokaždé, když `condition` je `True` .</span><span class="sxs-lookup"><span data-stu-id="faf79-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="faf79-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="faf79-113">Optional.</span></span> <span data-ttu-id="faf79-114">Přenáší řízení na další iteraci `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="faf79-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="faf79-115">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="faf79-115">Optional.</span></span> <span data-ttu-id="faf79-116">Přenáší řízení z `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="faf79-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="faf79-117">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="faf79-117">Required.</span></span> <span data-ttu-id="faf79-118">Ukončí definici `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="faf79-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faf79-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="faf79-119">Remarks</span></span>  
 <span data-ttu-id="faf79-120">Strukturu použijte `While...End While` , pokud chcete opakovat sadu příkazů neurčitému počtu výskytů, dokud podmínka zůstane `True` .</span><span class="sxs-lookup"><span data-stu-id="faf79-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="faf79-121">Pokud potřebujete větší flexibilitu při testování podmínky nebo k tomu, pro který výsledek testujete, můžete preferovat do.. [. Příkaz LOOP](do-loop-statement.md)</span><span class="sxs-lookup"><span data-stu-id="faf79-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](do-loop-statement.md).</span></span> <span data-ttu-id="faf79-122">Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](for-next-statement.md) je obvykle lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="faf79-122">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="faf79-123">`While`Klíčové slovo se používá také v do [... Příkaz LOOP](do-loop-statement.md), [klauzule Skip While](../queries/skip-while-clause.md) a [klauzuli HAVING while](../queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="faf79-123">The `While` keyword is also used in the [Do...Loop Statement](do-loop-statement.md), the [Skip While Clause](../queries/skip-while-clause.md) and the [Take While Clause](../queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="faf79-124">Pokud `condition` je `True` , všechny `statements` spuštění až do chvíle, kdy se `End While` příkaz vyskytne.</span><span class="sxs-lookup"><span data-stu-id="faf79-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="faf79-125">Ovládací prvek se pak vrátí do `While` příkazu a `condition` znovu se vyhradí.</span><span class="sxs-lookup"><span data-stu-id="faf79-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="faf79-126">Pokud `condition` je stále `True` , proces se opakuje.</span><span class="sxs-lookup"><span data-stu-id="faf79-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="faf79-127">Pokud je `False` , řízení se předá příkazu, který následuje po `End While` příkazu.</span><span class="sxs-lookup"><span data-stu-id="faf79-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="faf79-128">`While`Příkaz vždy před spuštěním smyčky kontroluje podmínku.</span><span class="sxs-lookup"><span data-stu-id="faf79-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="faf79-129">Opakování pokračuje, i když podmínka zůstane `True` .</span><span class="sxs-lookup"><span data-stu-id="faf79-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="faf79-130">Pokud `condition` je `False` při prvním zadání smyčky, nebude spuštěna ani jednou.</span><span class="sxs-lookup"><span data-stu-id="faf79-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="faf79-131">`condition`Obvykle je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../data-types/boolean-data-type.md) ( `True` nebo `False` ).</span><span class="sxs-lookup"><span data-stu-id="faf79-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="faf79-132">Tento výraz může obsahovat hodnotu jiného datového typu, jako je například číselný typ, který byl převeden na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="faf79-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="faf79-133">Smyčky můžete vnořovat `While` vložením jedné smyčky do jiné.</span><span class="sxs-lookup"><span data-stu-id="faf79-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="faf79-134">Můžete také vnořit různé druhy řídicích struktur mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="faf79-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="faf79-135">Další informace najdete v tématu [vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="faf79-135">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="faf79-136">Ukončit během</span><span class="sxs-lookup"><span data-stu-id="faf79-136">Exit While</span></span>  
 <span data-ttu-id="faf79-137">Příkaz [Exit while](exit-statement.md) může poskytnout jiný způsob, jak ukončit `While` smyčku.</span><span class="sxs-lookup"><span data-stu-id="faf79-137">The [Exit While](exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="faf79-138">`Exit While`okamžitě přenese řízení na příkaz, který následuje po `End While` příkazu.</span><span class="sxs-lookup"><span data-stu-id="faf79-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="faf79-139">Obvykle se používá `Exit While` po vyhodnocení některé podmínky (například ve `If...Then...Else` struktuře).</span><span class="sxs-lookup"><span data-stu-id="faf79-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="faf79-140">Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="faf79-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="faf79-141">Můžete použít `Exit While` při testování podmínky, která by mohla způsobit *nekonečnou smyčku*, což je smyčka, která by mohla běžet velmi velkým nebo dokonce nekonečným počtem výskytů.</span><span class="sxs-lookup"><span data-stu-id="faf79-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="faf79-142">Pak můžete použít `Exit While` k řídicímu cyklu smyčky.</span><span class="sxs-lookup"><span data-stu-id="faf79-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="faf79-143">Libovolný počet příkazů můžete umístit `Exit While` kdekoli ve `While` smyčce.</span><span class="sxs-lookup"><span data-stu-id="faf79-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="faf79-144">Při použití v rámci vnořených `While` smyček `Exit While` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="faf79-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="faf79-145">`Continue While`Příkaz okamžitě převede řízení na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="faf79-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="faf79-146">Další informace najdete v tématu [příkaz Continue](continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="faf79-146">For more information, see [Continue Statement](continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf79-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="faf79-147">Example</span></span>  
 <span data-ttu-id="faf79-148">V následujícím příkladu jsou příkazy ve smyčce nadále spuštěny, dokud `index` je proměnná větší než 10.</span><span class="sxs-lookup"><span data-stu-id="faf79-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="faf79-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="faf79-149">Example</span></span>  
 <span data-ttu-id="faf79-150">Následující příklad ilustruje použití `Continue While` `Exit While` příkazů a.</span><span class="sxs-lookup"><span data-stu-id="faf79-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="faf79-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="faf79-151">Example</span></span>  
 <span data-ttu-id="faf79-152">Následující příklad přečte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="faf79-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="faf79-153"><xref:System.IO.File.OpenText%2A>Metoda otevře soubor a vrátí hodnotu <xref:System.IO.StreamReader> , která přečte znaky.</span><span class="sxs-lookup"><span data-stu-id="faf79-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="faf79-154">V `While` podmínce <xref:System.IO.StreamReader.Peek%2A> Metoda `StreamReader` Určuje, zda soubor obsahuje další znaky.</span><span class="sxs-lookup"><span data-stu-id="faf79-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="faf79-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="faf79-155">See also</span></span>

- [<span data-ttu-id="faf79-156">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="faf79-156">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="faf79-157">Do...Loop – příkaz</span><span class="sxs-lookup"><span data-stu-id="faf79-157">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="faf79-158">For...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="faf79-158">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="faf79-159">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="faf79-159">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="faf79-160">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="faf79-160">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="faf79-161">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="faf79-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="faf79-162">Continue – příkaz</span><span class="sxs-lookup"><span data-stu-id="faf79-162">Continue Statement</span></span>](continue-statement.md)
