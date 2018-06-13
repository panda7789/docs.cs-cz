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
ms.openlocfilehash: e12cdc1ae405b877d4d27d1947c98dcb51938ba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604936"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="6ed46-102">Do...Loop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ed46-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="6ed46-103">Opakuje blok příkazů při `Boolean` podmínka je `True` nebo dokud nebude podmínku `True`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed46-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="6ed46-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6ed46-105">Parts</span></span>  
  
|<span data-ttu-id="6ed46-106">Termín</span><span class="sxs-lookup"><span data-stu-id="6ed46-106">Term</span></span>|<span data-ttu-id="6ed46-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6ed46-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="6ed46-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6ed46-108">Required.</span></span> <span data-ttu-id="6ed46-109">Spustí definice `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="6ed46-110">Povinné Pokud `Until` se používá.</span><span class="sxs-lookup"><span data-stu-id="6ed46-110">Required unless `Until` is used.</span></span> <span data-ttu-id="6ed46-111">Opakujte opakovat do `condition` je `False`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="6ed46-112">Povinné Pokud `While` se používá.</span><span class="sxs-lookup"><span data-stu-id="6ed46-112">Required unless `While` is used.</span></span> <span data-ttu-id="6ed46-113">Opakujte opakovat do `condition` je `True`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="6ed46-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6ed46-114">Optional.</span></span> <span data-ttu-id="6ed46-115">`Boolean` Výraz.</span><span class="sxs-lookup"><span data-stu-id="6ed46-115">`Boolean` expression.</span></span> <span data-ttu-id="6ed46-116">Pokud `condition` je `Nothing`, Visual Basic považuje za `False`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="6ed46-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6ed46-117">Optional.</span></span> <span data-ttu-id="6ed46-118">Jeden nebo více příkazů, které se opakují při nebo dokud, `condition` je `True`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="6ed46-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6ed46-119">Optional.</span></span> <span data-ttu-id="6ed46-120">Přenosy ovládacího prvku do další iterace `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="6ed46-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6ed46-121">Optional.</span></span> <span data-ttu-id="6ed46-122">Přenosy ovládacího prvku mimo `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="6ed46-123">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6ed46-123">Required.</span></span> <span data-ttu-id="6ed46-124">Ukončí definice `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ed46-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ed46-125">Remarks</span></span>  
 <span data-ttu-id="6ed46-126">Použití `Do...Loop` struktury, pokud má být opakován sadu příkazů na nekonečný počet dobu, dokud je podmínka.</span><span class="sxs-lookup"><span data-stu-id="6ed46-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="6ed46-127">Pokud chcete opakujte příkazy se stanoveným počtem dobu, [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) je obvykle lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="6ed46-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="6ed46-128">Můžete použít buď `While` nebo `Until` k určení `condition`, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="6ed46-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="6ed46-129">Můžete otestovat `condition` pouze jednou, při spuštění nebo ukončení smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="6ed46-130">Pokud otestujete `condition` na začátku smyčky (v `Do` příkaz), smyčky nemusí být možné spustit ještě jednou.</span><span class="sxs-lookup"><span data-stu-id="6ed46-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="6ed46-131">Pokud otestujete na konci smyčky (v `Loop` příkaz), provedení vždy cyklu aspoň jednou.</span><span class="sxs-lookup"><span data-stu-id="6ed46-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="6ed46-132">Podmínka obvykle výsledkem porovnání dvou hodnot, ale může být libovolný výraz, který se vyhodnocuje [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) hodnotu (`True` nebo `False`).</span><span class="sxs-lookup"><span data-stu-id="6ed46-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="6ed46-133">To zahrnuje hodnoty jiné datové typy, jako je například číselnými typy, které byly převedeny na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="6ed46-134">Lze vnořit `Do` smyčky umístěním jednoho smyčky v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="6ed46-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="6ed46-135">Můžete také vnořovat různé druhy řídicí struktury v rámci navzájem.</span><span class="sxs-lookup"><span data-stu-id="6ed46-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="6ed46-136">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="6ed46-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ed46-137">`Do...Loop` Struktura vám dává větší flexibilitu, než [při... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md) vzhledem k tomu, že se můžete rozhodnout, zda chcete ukončení smyčky při `condition` zastaví se `True` nebo když se nejprve stane `True`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="6ed46-138">Také umožňuje otestovat `condition` na začátku nebo konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="6ed46-139">Ukončete proveďte</span><span class="sxs-lookup"><span data-stu-id="6ed46-139">Exit Do</span></span>  
 <span data-ttu-id="6ed46-140">[Ukončete provést](../../../visual-basic/language-reference/statements/exit-statement.md) příkaz může poskytnout alternativní způsob ukončení `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="6ed46-141">`Exit Do` předá řízení příkaz, který následuje `Loop` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ed46-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="6ed46-142">`Exit Do` Po vyhodnocení některé podmínky, například v se často používá `If...Then...Else` struktura.</span><span class="sxs-lookup"><span data-stu-id="6ed46-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="6ed46-143">Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která umožňuje nepotřebné nebo dokonce znemožňují pokračujte iterace, třeba chybná hodnota nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="6ed46-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="6ed46-144">Jedno použití `Exit Do` je otestovat pro podmínku, která by mohla způsobovat *nekonečná smyčka*, což je smyčku, který by mohl spustit velký, nebo i nekonečné stanovený počet.</span><span class="sxs-lookup"><span data-stu-id="6ed46-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="6ed46-145">Můžete použít `Exit Do` abyste se vyhnuli smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="6ed46-146">Může obsahovat libovolný počet `Exit Do` příkazy kdekoli v `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="6ed46-147">Při použití uvnitř vnořené `Do` smyčky, `Exit Do` přenosy ovládacího prvku mimo nejvnitřnější smyčky a do další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="6ed46-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ed46-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ed46-148">Example</span></span>  
 <span data-ttu-id="6ed46-149">V následujícím příkladu, příkazy v smyčky dál běžet, dokud `index` proměnná je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="6ed46-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="6ed46-150">`Until` Klauzule je na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ed46-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ed46-151">Example</span></span>  
 <span data-ttu-id="6ed46-152">Následující příklad používá `While` klauzule místo `Until` klauzuli a `condition` je testován na začátku smyčky místo na konci.</span><span class="sxs-lookup"><span data-stu-id="6ed46-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ed46-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ed46-153">Example</span></span>  
 <span data-ttu-id="6ed46-154">V následujícím příkladu `condition` zastaví smyčky při `index` proměnné je větší než 100.</span><span class="sxs-lookup"><span data-stu-id="6ed46-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="6ed46-155">`If` Příkaz ve smyčce, ale způsobuje `Exit Do` příkaz k zastavení smyčky do proměnné index je větší než 10.</span><span class="sxs-lookup"><span data-stu-id="6ed46-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ed46-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ed46-156">Example</span></span>  
 <span data-ttu-id="6ed46-157">Následující příklad načte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="6ed46-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="6ed46-158"><xref:System.IO.File.OpenText%2A> Metoda otevře soubor a vrátí <xref:System.IO.StreamReader> , který čte znaky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="6ed46-159">V `Do...Loop` podmínky, <xref:System.IO.StreamReader.Peek%2A> metodu `StreamReader` určí, zda jsou všechny další znaky.</span><span class="sxs-lookup"><span data-stu-id="6ed46-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6ed46-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ed46-160">See Also</span></span>  
 [<span data-ttu-id="6ed46-161">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="6ed46-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="6ed46-162">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="6ed46-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="6ed46-163">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="6ed46-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="6ed46-164">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="6ed46-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="6ed46-165">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="6ed46-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="6ed46-166">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="6ed46-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
