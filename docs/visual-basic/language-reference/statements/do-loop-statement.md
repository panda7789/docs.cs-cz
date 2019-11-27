---
title: Do...Loop – příkaz
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
ms.openlocfilehash: 9384cbb355189be448fa4b8d274721b4a7ca6a20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351258"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="82135-102">Do...Loop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82135-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="82135-103">Opakuje blok příkazů, dokud je podmínka `Boolean` `True` nebo dokud podmínka nebude `True`.</span><span class="sxs-lookup"><span data-stu-id="82135-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82135-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82135-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="82135-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="82135-105">Parts</span></span>  
  
|<span data-ttu-id="82135-106">Termín</span><span class="sxs-lookup"><span data-stu-id="82135-106">Term</span></span>|<span data-ttu-id="82135-107">Definice</span><span class="sxs-lookup"><span data-stu-id="82135-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="82135-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="82135-108">Required.</span></span> <span data-ttu-id="82135-109">Spustí definici smyčky `Do`.</span><span class="sxs-lookup"><span data-stu-id="82135-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="82135-110">Povinné, pokud se nepoužívá `Until`.</span><span class="sxs-lookup"><span data-stu-id="82135-110">Required unless `Until` is used.</span></span> <span data-ttu-id="82135-111">Opakujte smyčku, dokud není `False``condition`.</span><span class="sxs-lookup"><span data-stu-id="82135-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="82135-112">Povinné, pokud se nepoužívá `While`.</span><span class="sxs-lookup"><span data-stu-id="82135-112">Required unless `While` is used.</span></span> <span data-ttu-id="82135-113">Opakujte smyčku, dokud není `True``condition`.</span><span class="sxs-lookup"><span data-stu-id="82135-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="82135-114">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="82135-114">Optional.</span></span> <span data-ttu-id="82135-115">výraz `Boolean`</span><span class="sxs-lookup"><span data-stu-id="82135-115">`Boolean` expression.</span></span> <span data-ttu-id="82135-116">Pokud je `condition` `Nothing`, Visual Basic považuje za `False`.</span><span class="sxs-lookup"><span data-stu-id="82135-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="82135-117">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="82135-117">Optional.</span></span> <span data-ttu-id="82135-118">Jeden nebo více příkazů, které se opakují, nebo dokud `condition` `True`.</span><span class="sxs-lookup"><span data-stu-id="82135-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="82135-119">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="82135-119">Optional.</span></span> <span data-ttu-id="82135-120">Přenese řízení na další iteraci `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="82135-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="82135-121">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="82135-121">Optional.</span></span> <span data-ttu-id="82135-122">Přenáší řízení ze smyčky `Do`.</span><span class="sxs-lookup"><span data-stu-id="82135-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="82135-123">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="82135-123">Required.</span></span> <span data-ttu-id="82135-124">Ukončí definici smyčky `Do`.</span><span class="sxs-lookup"><span data-stu-id="82135-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82135-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82135-125">Remarks</span></span>  
 <span data-ttu-id="82135-126">`Do...Loop` strukturu použijte v případě, že chcete opakovat sadu příkazů v neurčitém počtu výskytů, dokud není splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="82135-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="82135-127">Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="82135-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="82135-128">K určení `condition`, ale ne obojí, můžete použít buď `While`, nebo `Until`.</span><span class="sxs-lookup"><span data-stu-id="82135-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="82135-129">Můžete testovat `condition` jenom jednou, a to buď na začátku, nebo na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="82135-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="82135-130">Pokud testujete `condition` na začátku smyčky (v příkazu `Do`), smyčka nemusí běžet ještě jednou.</span><span class="sxs-lookup"><span data-stu-id="82135-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="82135-131">Pokud testujete na konci smyčky (v příkazu `Loop`), smyčka vždy proběhne alespoň jednou.</span><span class="sxs-lookup"><span data-stu-id="82135-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="82135-132">Podmínka obvykle je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` nebo `False`).</span><span class="sxs-lookup"><span data-stu-id="82135-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="82135-133">To zahrnuje hodnoty jiných datových typů, například číselné typy, které byly převedeny na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="82135-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="82135-134">Smyčky `Do` můžete vnořovat vložením jedné smyčky do jiné.</span><span class="sxs-lookup"><span data-stu-id="82135-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="82135-135">Můžete také vnořit různé druhy řídicích struktur mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="82135-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="82135-136">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="82135-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82135-137">Struktura `Do...Loop` poskytuje větší flexibilitu než [while... Příkaz End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , protože umožňuje rozhodnout, jestli se má ukončit smyčka, když se `condition` zastaví `True` nebo když se poprvé stane `True`.</span><span class="sxs-lookup"><span data-stu-id="82135-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="82135-138">Také umožňuje testovat `condition` na začátku nebo na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="82135-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="82135-139">Ukončit</span><span class="sxs-lookup"><span data-stu-id="82135-139">Exit Do</span></span>  
 <span data-ttu-id="82135-140">Příkaz [Exit](../../../visual-basic/language-reference/statements/exit-statement.md) do může nabídnout alternativní způsob, jak ukončit `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="82135-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="82135-141">`Exit Do` přenáší řízení okamžitě na příkaz, který následuje po příkazu `Loop`.</span><span class="sxs-lookup"><span data-stu-id="82135-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="82135-142">`Exit Do` se často používá po vyhodnocení některé podmínky, například ve struktuře `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="82135-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="82135-143">Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="82135-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="82135-144">Jedním z použití `Exit Do` je testování podmínky, která by mohla způsobit nekonečnou *smyčku*, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů.</span><span class="sxs-lookup"><span data-stu-id="82135-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="82135-145">K ukončení smyčky můžete použít `Exit Do`.</span><span class="sxs-lookup"><span data-stu-id="82135-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="82135-146">Libovolný počet příkazů `Exit Do` můžete umístit kdekoli v `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="82135-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="82135-147">Při použití ve vnořených cyklech `Do` `Exit Do` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="82135-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82135-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="82135-148">Example</span></span>  
 <span data-ttu-id="82135-149">V následujícím příkladu budou příkazy ve smyčce nadále spuštěny, dokud je proměnná `index` větší než 10.</span><span class="sxs-lookup"><span data-stu-id="82135-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="82135-150">Klauzule `Until` je na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="82135-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="82135-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="82135-151">Example</span></span>  
 <span data-ttu-id="82135-152">Následující příklad používá klauzuli `While` namísto klauzule `Until` a `condition` je testován na začátku cyklu namísto na konci.</span><span class="sxs-lookup"><span data-stu-id="82135-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="82135-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="82135-153">Example</span></span>  
 <span data-ttu-id="82135-154">V následujícím příkladu `condition` zastaví smyčku, pokud je proměnná `index` větší než 100.</span><span class="sxs-lookup"><span data-stu-id="82135-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="82135-155">Příkaz `If` ve smyčce ale způsobí, že příkaz `Exit Do` zastaví smyčku v případě, že je proměnná indexu větší než 10.</span><span class="sxs-lookup"><span data-stu-id="82135-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="82135-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="82135-156">Example</span></span>  
 <span data-ttu-id="82135-157">Následující příklad přečte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="82135-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="82135-158">Metoda <xref:System.IO.File.OpenText%2A> otevře soubor a vrátí <xref:System.IO.StreamReader>, který přečte znaky.</span><span class="sxs-lookup"><span data-stu-id="82135-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="82135-159">V `Do...Loop` podmínka určuje <xref:System.IO.StreamReader.Peek%2A> metoda `StreamReader`, zda existují nějaké další znaky.</span><span class="sxs-lookup"><span data-stu-id="82135-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="82135-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82135-160">See also</span></span>

- [<span data-ttu-id="82135-161">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="82135-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="82135-162">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="82135-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="82135-163">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="82135-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="82135-164">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="82135-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="82135-165">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="82135-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="82135-166">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="82135-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
