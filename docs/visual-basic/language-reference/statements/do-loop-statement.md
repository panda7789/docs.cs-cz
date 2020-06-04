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
ms.openlocfilehash: a9ec6caccbe161a39b592a642a938b81bae911a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404781"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="22f67-102">Do...Loop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22f67-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="22f67-103">Opakuje blok příkazů, dokud `Boolean` je podmínka `True` nebo dokud se podmínka nevrátí `True` .</span><span class="sxs-lookup"><span data-stu-id="22f67-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22f67-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="22f67-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="22f67-105">Parts</span></span>  
  
|<span data-ttu-id="22f67-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="22f67-106">Term</span></span>|<span data-ttu-id="22f67-107">Definice</span><span class="sxs-lookup"><span data-stu-id="22f67-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="22f67-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="22f67-108">Required.</span></span> <span data-ttu-id="22f67-109">Spustí definici `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="22f67-110">Povinné `Until` , pokud se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="22f67-110">Required unless `Until` is used.</span></span> <span data-ttu-id="22f67-111">Opakujte smyčku, dokud `condition` není `False` .</span><span class="sxs-lookup"><span data-stu-id="22f67-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="22f67-112">Povinné `While` , pokud se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="22f67-112">Required unless `While` is used.</span></span> <span data-ttu-id="22f67-113">Opakujte smyčku, dokud `condition` není `True` .</span><span class="sxs-lookup"><span data-stu-id="22f67-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="22f67-114">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="22f67-114">Optional.</span></span> <span data-ttu-id="22f67-115">`Boolean`vyjádření.</span><span class="sxs-lookup"><span data-stu-id="22f67-115">`Boolean` expression.</span></span> <span data-ttu-id="22f67-116">Pokud `condition` je `Nothing` , Visual Basic považuje za `False` .</span><span class="sxs-lookup"><span data-stu-id="22f67-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="22f67-117">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="22f67-117">Optional.</span></span> <span data-ttu-id="22f67-118">Jeden nebo více příkazů, které se opakují během nebo do `condition` `True` .</span><span class="sxs-lookup"><span data-stu-id="22f67-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="22f67-119">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="22f67-119">Optional.</span></span> <span data-ttu-id="22f67-120">Přenese řízení na další iteraci `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="22f67-121">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="22f67-121">Optional.</span></span> <span data-ttu-id="22f67-122">Přenese řízení ze `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="22f67-123">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="22f67-123">Required.</span></span> <span data-ttu-id="22f67-124">Ukončí definici `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f67-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22f67-125">Remarks</span></span>  
 <span data-ttu-id="22f67-126">Strukturu použijte `Do...Loop` , pokud chcete opakovat sadu příkazů neurčitým počtem opakování, dokud není splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="22f67-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="22f67-127">Pokud chcete příkazy opakovat v nastaveném počtu opakování, [pro... Další příkaz](for-next-statement.md) je obvykle lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="22f67-127">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="22f67-128">Můžete použít buď `While` nebo `Until` k zadání `condition` , ale ne obojího.</span><span class="sxs-lookup"><span data-stu-id="22f67-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="22f67-129">Můžete testovat `condition` pouze jednou, a to buď na začátku, nebo na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="22f67-130">Pokud testujete `condition` na začátku smyčky (v `Do` příkazu), smyčka nemusí běžet současně.</span><span class="sxs-lookup"><span data-stu-id="22f67-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="22f67-131">Pokud testujete na konci smyčky (v `Loop` příkazu), smyčka vždy proběhne alespoň jednou.</span><span class="sxs-lookup"><span data-stu-id="22f67-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="22f67-132">Podmínka obvykle je výsledkem porovnání dvou hodnot, ale může to být libovolný výraz, který je vyhodnocen jako logická hodnota [datového typu](../data-types/boolean-data-type.md) ( `True` nebo `False` ).</span><span class="sxs-lookup"><span data-stu-id="22f67-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="22f67-133">To zahrnuje hodnoty jiných datových typů, například číselné typy, které byly převedeny na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="22f67-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="22f67-134">Smyčky můžete vnořovat vložením `Do` jedné smyčky do jiné.</span><span class="sxs-lookup"><span data-stu-id="22f67-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="22f67-135">Můžete také vnořit různé druhy řídicích struktur mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="22f67-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="22f67-136">Další informace najdete v tématu [vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="22f67-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22f67-137">`Do...Loop`Struktura poskytuje větší flexibilitu než [while... Příkaz End While](while-end-while-statement.md) , protože umožňuje rozhodnout, zda chcete ukončit smyčku při `condition` zastavení `True` nebo kdy se bude nacházet poprvé `True` .</span><span class="sxs-lookup"><span data-stu-id="22f67-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="22f67-138">Také vám umožňuje testovat buď na `condition` začátku, nebo na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="22f67-139">Ukončit</span><span class="sxs-lookup"><span data-stu-id="22f67-139">Exit Do</span></span>  
 <span data-ttu-id="22f67-140">Příkaz [Exit](exit-statement.md) do může nabídnout alternativní způsob, jak ukončit `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="22f67-140">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="22f67-141">`Exit Do`přenáší řízení okamžitě na příkaz, který následuje po `Loop` příkazu.</span><span class="sxs-lookup"><span data-stu-id="22f67-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="22f67-142">`Exit Do`se často používá po vyhodnocení některé podmínky, například ve `If...Then...Else` struktuře.</span><span class="sxs-lookup"><span data-stu-id="22f67-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="22f67-143">Můžete chtít ukončit smyčku, pokud zjistíte podmínku, která je nepotřebná nebo nemožná, aby pokračovala v iteraci, jako je například chybná hodnota nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="22f67-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="22f67-144">Jedním z nich `Exit Do` je testování podmínky, která by mohla způsobit *nekonečné opakování*, což je smyčka, která by mohla vést k velkému nebo dokonce nekonečnému počtu časů.</span><span class="sxs-lookup"><span data-stu-id="22f67-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="22f67-145">Můžete použít `Exit Do` k opuštění smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="22f67-146">Můžete zahrnout libovolný počet `Exit Do` příkazů kdekoli v `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="22f67-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="22f67-147">Při použití v rámci vnořených `Do` smyček `Exit Do` přenáší řízení z nejvnitřnější smyčky a na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="22f67-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f67-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="22f67-148">Example</span></span>  
 <span data-ttu-id="22f67-149">V následujícím příkladu jsou příkazy ve smyčce nadále spuštěny, dokud `index` je proměnná větší než 10.</span><span class="sxs-lookup"><span data-stu-id="22f67-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="22f67-150">`Until`Klauzule je na konci smyčky.</span><span class="sxs-lookup"><span data-stu-id="22f67-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="22f67-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="22f67-151">Example</span></span>  
 <span data-ttu-id="22f67-152">Následující příklad používá `While` klauzuli namísto `Until` klauzule a `condition` je testován na začátku smyčky místo na konci.</span><span class="sxs-lookup"><span data-stu-id="22f67-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="22f67-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="22f67-153">Example</span></span>  
 <span data-ttu-id="22f67-154">V následujícím příkladu `condition` zastaví smyčka, pokud `index` je proměnná větší než 100.</span><span class="sxs-lookup"><span data-stu-id="22f67-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="22f67-155">`If`Příkaz ve smyčce ale způsobí, že `Exit Do` příkaz zastaví smyčku, když je proměnná indexu větší než 10.</span><span class="sxs-lookup"><span data-stu-id="22f67-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="22f67-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="22f67-156">Example</span></span>  
 <span data-ttu-id="22f67-157">Následující příklad přečte všechny řádky v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="22f67-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="22f67-158"><xref:System.IO.File.OpenText%2A>Metoda otevře soubor a vrátí hodnotu <xref:System.IO.StreamReader> , která přečte znaky.</span><span class="sxs-lookup"><span data-stu-id="22f67-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="22f67-159">V `Do...Loop` podmínce <xref:System.IO.StreamReader.Peek%2A> Metoda `StreamReader` Určuje, zda existují nějaké další znaky.</span><span class="sxs-lookup"><span data-stu-id="22f67-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="22f67-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="22f67-160">See also</span></span>

- [<span data-ttu-id="22f67-161">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="22f67-161">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="22f67-162">For...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="22f67-162">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="22f67-163">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="22f67-163">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="22f67-164">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="22f67-164">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="22f67-165">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="22f67-165">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="22f67-166">While...End While – příkaz</span><span class="sxs-lookup"><span data-stu-id="22f67-166">While...End While Statement</span></span>](while-end-while-statement.md)
