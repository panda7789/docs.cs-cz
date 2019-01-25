---
title: Do...Loop – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 8c965dc89794654127e4b872c6aebf55c8902468
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525145"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="09502-102">Do...Loop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09502-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="09502-103">Opakuje blok příkazů při `Boolean` podmínka je `True` nebo dokud se podmínka nestane `True`.</span><span class="sxs-lookup"><span data-stu-id="09502-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09502-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09502-104">Syntax</span></span>  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="09502-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="09502-105">Parts</span></span>  
  
|<span data-ttu-id="09502-106">Termín</span><span class="sxs-lookup"><span data-stu-id="09502-106">Term</span></span>|<span data-ttu-id="09502-107">Definice</span><span class="sxs-lookup"><span data-stu-id="09502-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="09502-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="09502-108">Required.</span></span> <span data-ttu-id="09502-109">Spustí definici `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="09502-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="09502-110">Vyžaduje se, pokud `Until` se používá.</span><span class="sxs-lookup"><span data-stu-id="09502-110">Required unless `Until` is used.</span></span> <span data-ttu-id="09502-111">Opakování cyklu až do `condition` je `False`.</span><span class="sxs-lookup"><span data-stu-id="09502-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="09502-112">Vyžaduje se, pokud `While` se používá.</span><span class="sxs-lookup"><span data-stu-id="09502-112">Required unless `While` is used.</span></span> <span data-ttu-id="09502-113">Opakování cyklu až do `condition` je `True`.</span><span class="sxs-lookup"><span data-stu-id="09502-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="09502-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="09502-114">Optional.</span></span> <span data-ttu-id="09502-115">`Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="09502-115">`Boolean` expression.</span></span> <span data-ttu-id="09502-116">Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.</span><span class="sxs-lookup"><span data-stu-id="09502-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="09502-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="09502-117">Optional.</span></span> <span data-ttu-id="09502-118">Jeden nebo více příkazů, které se opakují při nebo dokud, `condition` je `True`.</span><span class="sxs-lookup"><span data-stu-id="09502-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="09502-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="09502-119">Optional.</span></span> <span data-ttu-id="09502-120">Předá řízení následující iteraci `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="09502-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="09502-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="09502-121">Optional.</span></span> <span data-ttu-id="09502-122">Přenese ovládací prvek z celkového počtu `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="09502-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="09502-123">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="09502-123">Required.</span></span> <span data-ttu-id="09502-124">Ukončí definici `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="09502-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09502-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09502-125">Remarks</span></span>  
 <span data-ttu-id="09502-126">Použití `Do...Loop` struktury, pokud má být opakován sadu příkazů na nekonečný počet dob, dokud není splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="09502-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="09502-127">Pokud chcete do sady počtu opakování, opakujte příkazy [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle vhodnější použít.</span><span class="sxs-lookup"><span data-stu-id="09502-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="09502-128">Můžete použít buď `While` nebo `Until` k určení `condition`, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="09502-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="09502-129">Můžete otestovat `condition` pouze jednou, na začátku nebo konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="09502-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="09502-130">Pokud testujete `condition` na začátek smyčky (v `Do` příkaz), smyčka nemusí spouštět ještě jednou.</span><span class="sxs-lookup"><span data-stu-id="09502-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="09502-131">Pokud otestujete na konci smyčky (v `Loop` příkaz), vždycky cyklu aspoň jednou.</span><span class="sxs-lookup"><span data-stu-id="09502-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="09502-132">Podmínka obvykle výsledkem porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnotí [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`).</span><span class="sxs-lookup"><span data-stu-id="09502-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="09502-133">To zahrnuje hodnoty jiné datové typy, jako je například číselné typy, které se převedly tak `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="09502-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="09502-134">Je možné vnořovat `Do` smyčky vložením v jednom průchodu v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="09502-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="09502-135">Lze také vnořit různé druhy řídicích struktur v sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="09502-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="09502-136">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="09502-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09502-137">`Do...Loop` Struktury poskytuje větší flexibilitu než [během... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md) vzhledem k tomu, že umožňuje rozhodnout, jestli se má ukončit smyčky při `condition` přestává být `True` nebo když se nejprve stane `True`.</span><span class="sxs-lookup"><span data-stu-id="09502-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="09502-138">K otestování také umožňuje `condition` na začátku nebo konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="09502-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="09502-139">Ukončit</span><span class="sxs-lookup"><span data-stu-id="09502-139">Exit Do</span></span>  
 <span data-ttu-id="09502-140">[Ukončit proveďte](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz může poskytnout alternativní způsob ukončení `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="09502-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="09502-141">`Exit Do` okamžitě přenese řízení příkazu následujícímu `Loop` příkazu.</span><span class="sxs-lookup"><span data-stu-id="09502-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="09502-142">`Exit Do` Po vyhodnocení některé podmínky, například se často používá `If...Then...Else` struktury.</span><span class="sxs-lookup"><span data-stu-id="09502-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="09502-143">Můžete chtít ukončení smyčky je-li zjistit podmínku, která umožňuje zbytečné nebo nemožné, chcete-li pokračovat, iterace, jako jsou chybné hodnotu nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="09502-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="09502-144">Jedno použití `Exit Do` je testovací podmínku, která by mohla způsobit, že *vznik nekonečné smyčky*, což je smyčku, která může běžet velká, nebo dokonce neomezený počet pokusů.</span><span class="sxs-lookup"><span data-stu-id="09502-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="09502-145">Můžete použít `Exit Do` dostala mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="09502-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="09502-146">Může obsahovat libovolný počet `Exit Do` příkazy kdekoli v `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="09502-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="09502-147">Při použití v rámci vnořené `Do` smyčky, `Exit Do` předává řízení mimo vnitřní smyčky a na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="09502-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09502-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="09502-148">Example</span></span>  
 <span data-ttu-id="09502-149">V následujícím příkladu se příkazy ve smyčce dál běžet až `index` proměnnou je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="09502-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="09502-150">`Until` Klauzule je na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="09502-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="09502-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="09502-151">Example</span></span>  
 <span data-ttu-id="09502-152">Následující příklad používá `While` klauzule místo `Until` klauzule a `condition` je testován na začátek smyčky místo na konci.</span><span class="sxs-lookup"><span data-stu-id="09502-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="09502-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="09502-153">Example</span></span>  
 <span data-ttu-id="09502-154">V následujícím příkladu `condition` smyčky se zastaví při `index` proměnnou je větší než 100.</span><span class="sxs-lookup"><span data-stu-id="09502-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="09502-155">`If` Příkaz ve smyčce, ale způsobí, že `Exit Do` příkaz zastaví smyčky, pokud indexovaná proměnná je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="09502-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="09502-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="09502-156">Example</span></span>  
 <span data-ttu-id="09502-157">Následující příklad načte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="09502-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="09502-158"><xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky.</span><span class="sxs-lookup"><span data-stu-id="09502-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="09502-159">V `Do...Loop` podmínku, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` Určuje, zda jsou mezi dalšími znaky.</span><span class="sxs-lookup"><span data-stu-id="09502-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="09502-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09502-160">See also</span></span>
- [<span data-ttu-id="09502-161">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="09502-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="09502-162">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="09502-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="09502-163">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="09502-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="09502-164">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="09502-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="09502-165">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="09502-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="09502-166">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="09502-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
