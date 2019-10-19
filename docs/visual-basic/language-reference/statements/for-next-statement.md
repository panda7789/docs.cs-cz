---
title: For...Next – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: a60293fc837b6d12810a211892c391f24a46d4e6
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582964"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="92c5f-102">For...Next – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92c5f-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="92c5f-103">Opakuje skupinu příkazů v zadaném počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="92c5f-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="92c5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92c5f-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="92c5f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="92c5f-105">Parts</span></span>

|<span data-ttu-id="92c5f-106">Částí</span><span class="sxs-lookup"><span data-stu-id="92c5f-106">Part</span></span>|<span data-ttu-id="92c5f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="92c5f-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="92c5f-108">Vyžaduje se v příkazu `For`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-108">Required in the `For` statement.</span></span> <span data-ttu-id="92c5f-109">Číselná proměnná.</span><span class="sxs-lookup"><span data-stu-id="92c5f-109">Numeric variable.</span></span> <span data-ttu-id="92c5f-110">Řídicí proměnná pro smyčku.</span><span class="sxs-lookup"><span data-stu-id="92c5f-110">The control variable for the loop.</span></span> <span data-ttu-id="92c5f-111">Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="92c5f-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="92c5f-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-112">Optional.</span></span> <span data-ttu-id="92c5f-113">Datový typ `counter`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-113">Data type of `counter`.</span></span> <span data-ttu-id="92c5f-114">Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="92c5f-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="92c5f-115">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="92c5f-115">Required.</span></span> <span data-ttu-id="92c5f-116">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="92c5f-116">Numeric expression.</span></span> <span data-ttu-id="92c5f-117">Počáteční hodnota `counter`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="92c5f-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="92c5f-118">Required.</span></span> <span data-ttu-id="92c5f-119">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="92c5f-119">Numeric expression.</span></span> <span data-ttu-id="92c5f-120">Konečná hodnota `counter`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="92c5f-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-121">Optional.</span></span> <span data-ttu-id="92c5f-122">Číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="92c5f-122">Numeric expression.</span></span> <span data-ttu-id="92c5f-123">Hodnota, o kterou `counter` se při každém průchodu smyčkou zvýší.</span><span class="sxs-lookup"><span data-stu-id="92c5f-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="92c5f-124">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-124">Optional.</span></span> <span data-ttu-id="92c5f-125">Jeden nebo více příkazů mezi `For` a `Next`, které spouští zadaný počet opakování.</span><span class="sxs-lookup"><span data-stu-id="92c5f-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="92c5f-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-126">Optional.</span></span> <span data-ttu-id="92c5f-127">Převede řízení na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="92c5f-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-128">Optional.</span></span> <span data-ttu-id="92c5f-129">Přenáší řízení ze smyčky `For`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="92c5f-130">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="92c5f-130">Required.</span></span> <span data-ttu-id="92c5f-131">Ukončí definici smyčky `For`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="92c5f-132">Klíčové slovo `To` se v tomto příkazu používá k určení rozsahu čítače.</span><span class="sxs-lookup"><span data-stu-id="92c5f-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="92c5f-133">Toto klíčové slovo lze použít také v poli [Vybrat... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md) a v deklaracích Array.</span><span class="sxs-lookup"><span data-stu-id="92c5f-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="92c5f-134">Další informace o deklaracích pole naleznete v tématu [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="92c5f-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="92c5f-135">Jednoduché příklady</span><span class="sxs-lookup"><span data-stu-id="92c5f-135">Simple Examples</span></span>

<span data-ttu-id="92c5f-136">Použijete `For`... `Next` struktura, pokud chcete opakovat sadu příkazů, které mají nastaven počet opakování.</span><span class="sxs-lookup"><span data-stu-id="92c5f-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="92c5f-137">V následujícím příkladu `index` proměnná začíná hodnotou 1 a při každé iteraci smyčky se zvyšuje s každou iterací smyčky, po jejichž uplynutí hodnota `index` dosáhne 5.</span><span class="sxs-lookup"><span data-stu-id="92c5f-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="92c5f-138">V následujícím příkladu `number` proměnná začíná 2 a při každé iteraci smyčky se zkrátí 0,25 a po hodnotě `number` dosáhne 0.</span><span class="sxs-lookup"><span data-stu-id="92c5f-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="92c5f-139">Argument `Step` `-.25` snižuje hodnotu 0,25 na každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="92c5f-140">A [while... Příkaz End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) nebo [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md) funguje dobře, Pokud nevíte, jak dlouho chcete spustit příkazy ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="92c5f-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="92c5f-141">Nicméně pokud očekáváte, že se má smyčka spustit určitou dobu, `For`... `Next` smyčka je lepší volbou.</span><span class="sxs-lookup"><span data-stu-id="92c5f-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="92c5f-142">Určíte počet iterací při prvním zadání smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="92c5f-143">Vnořování smyček</span><span class="sxs-lookup"><span data-stu-id="92c5f-143">Nesting Loops</span></span>

<span data-ttu-id="92c5f-144">Smyčky `For` můžete vnořovat vložením jedné smyčky do jiné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="92c5f-145">Následující příklad ukazuje vnořené `For`... `Next` struktury, které mají různé hodnoty kroku.</span><span class="sxs-lookup"><span data-stu-id="92c5f-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="92c5f-146">Vnější smyčka vytvoří řetězec pro každou iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="92c5f-147">Vnitřní smyčka snižuje proměnnou počítadla smyčky pro každou iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="92c5f-148">Při vnořování smyček musí mít každá smyčka jedinečnou `counter` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="92c5f-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="92c5f-149">Různé struktury ovládacích prvků lze také vnořovat mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="92c5f-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="92c5f-150">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="92c5f-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="92c5f-151">Ukončit po a pokračovat pro</span><span class="sxs-lookup"><span data-stu-id="92c5f-151">Exit For and Continue For</span></span>

<span data-ttu-id="92c5f-152">Příkaz `Exit For` okamžitě ukončí `For`... `Next`</span><span class="sxs-lookup"><span data-stu-id="92c5f-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="92c5f-153">Loop a přenáší řízení příkazu, který následuje po příkazu `Next`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="92c5f-154">Příkaz `Continue For` přenáší řízení okamžitě na další iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="92c5f-155">Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="92c5f-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>

<span data-ttu-id="92c5f-156">Následující příklad ukazuje použití příkazů `Continue For` a `Exit For`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="92c5f-157">Do `For` můžete přidat libovolný počet příkazů `Exit For`... `Next`</span><span class="sxs-lookup"><span data-stu-id="92c5f-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="92c5f-158">Procházet.</span><span class="sxs-lookup"><span data-stu-id="92c5f-158">loop.</span></span> <span data-ttu-id="92c5f-159">Při použití v rámci vnořených `For`... `Next`</span><span class="sxs-lookup"><span data-stu-id="92c5f-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="92c5f-160">smyčky, `Exit For` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="92c5f-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="92c5f-161">`Exit For` se často používá po vyhodnocení nějaké podmínky (například ve struktuře `If`... `Then`... `Else`).</span><span class="sxs-lookup"><span data-stu-id="92c5f-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="92c5f-162">Můžete chtít použít `Exit For` pro následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="92c5f-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="92c5f-163">Pokračování iterace je zbytečné nebo nemožné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="92c5f-164">Tato podmínka může vytvořit chybná hodnota nebo žádost o ukončení.</span><span class="sxs-lookup"><span data-stu-id="92c5f-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="92c5f-165">@No__t_0... `Catch`... příkaz `Finally` zachytí výjimku.</span><span class="sxs-lookup"><span data-stu-id="92c5f-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="92c5f-166">@No__t_0 můžete použít na konci bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="92c5f-167">Máte nekonečné smyčky, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů.</span><span class="sxs-lookup"><span data-stu-id="92c5f-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="92c5f-168">Pokud tuto podmínku zjistíte, můžete ji použít `Exit For` a řídicí smyčku.</span><span class="sxs-lookup"><span data-stu-id="92c5f-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="92c5f-169">Další informace najdete v části [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md)</span><span class="sxs-lookup"><span data-stu-id="92c5f-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="92c5f-170">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="92c5f-170">Technical Implementation</span></span>

<span data-ttu-id="92c5f-171">Když `For`... Spustí se `Next` smyčka Visual Basic vyhodnotí `start`, `end` a `step`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="92c5f-172">Visual Basic vyhodnotí tyto hodnoty pouze v tuto chvíli a potom přiřadí `start` k `counter`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="92c5f-173">Než se spustí blok příkazu, Visual Basic porovná `counter` s `end`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="92c5f-174">Pokud je již `counter` větší než hodnota `end` (nebo menší, pokud je `step` záporné), cyklus `For` končí a řízení projde příkazu, který následuje po příkazu `Next`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="92c5f-175">V opačném případě se spustí blok příkazu.</span><span class="sxs-lookup"><span data-stu-id="92c5f-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="92c5f-176">Pokaždé, když Visual Basic nalezne `Next` příkaz, zvýší `counter` `step` a vrátí se do příkazu `For`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="92c5f-177">Znovu porovná `counter` `end` a znovu buď spustí blok, nebo ukončí smyčku v závislosti na výsledku.</span><span class="sxs-lookup"><span data-stu-id="92c5f-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="92c5f-178">Tento proces pokračuje, dokud `counter` neprojde `end` nebo byl zjištěn příkaz `Exit For`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="92c5f-179">Smyčka se neukončí, dokud `counter` neprojde `end`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="92c5f-180">Pokud je `counter` rovna `end`, smyčka pokračuje.</span><span class="sxs-lookup"><span data-stu-id="92c5f-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="92c5f-181">Porovnání, které určuje, zda je možné spustit blok, je `counter`  <=  `end` Pokud `step` kladné a `counter`  >=  `end`, pokud je `step` záporné.</span><span class="sxs-lookup"><span data-stu-id="92c5f-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="92c5f-182">Pokud změníte hodnotu `counter` dovnitř smyčky, váš kód může být obtížnější číst a ladit.</span><span class="sxs-lookup"><span data-stu-id="92c5f-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="92c5f-183">Změna hodnoty `start`, `end` nebo `step` nemá vliv na hodnoty iterace, které byly určeny při prvním zadání smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="92c5f-184">Pokud vnořování smyček, kompilátor signalizuje chybu, pokud nalezne příkaz `Next` úrovně vnějšího vnoření před příkaz `Next` vnitřní úrovně.</span><span class="sxs-lookup"><span data-stu-id="92c5f-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="92c5f-185">Kompilátor však může tuto chybu překrývají pouze v případě, že zadáte `counter` v každém příkazu `Next`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="92c5f-186">Argument kroku</span><span class="sxs-lookup"><span data-stu-id="92c5f-186">Step Argument</span></span>

<span data-ttu-id="92c5f-187">Hodnota `step` může být buď kladná, nebo záporná.</span><span class="sxs-lookup"><span data-stu-id="92c5f-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="92c5f-188">Tento parametr určuje zpracování smyčky podle následující tabulky:</span><span class="sxs-lookup"><span data-stu-id="92c5f-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="92c5f-189">**Hodnota kroku**</span><span class="sxs-lookup"><span data-stu-id="92c5f-189">**Step value**</span></span>|<span data-ttu-id="92c5f-190">**Smyčka se spustí, pokud**</span><span class="sxs-lookup"><span data-stu-id="92c5f-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="92c5f-191">Kladná nebo nulová</span><span class="sxs-lookup"><span data-stu-id="92c5f-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="92c5f-192">Záporný</span><span class="sxs-lookup"><span data-stu-id="92c5f-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="92c5f-193">Výchozí hodnota `step` je 1.</span><span class="sxs-lookup"><span data-stu-id="92c5f-193">The default value of `step` is 1.</span></span>

### <a name="BKMK_Counter"></a><span data-ttu-id="92c5f-194">Argument čítače</span><span class="sxs-lookup"><span data-stu-id="92c5f-194">Counter Argument</span></span>

<span data-ttu-id="92c5f-195">Následující tabulka uvádí, zda `counter` definuje novou místní proměnnou vymezenou na celou `For…Next` smyčku.</span><span class="sxs-lookup"><span data-stu-id="92c5f-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="92c5f-196">Toto určení závisí na tom, zda je `datatype` k dispozici a zda `counter` již byla definována.</span><span class="sxs-lookup"><span data-stu-id="92c5f-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="92c5f-197">Je `datatype` k dispozici?</span><span class="sxs-lookup"><span data-stu-id="92c5f-197">Is `datatype` present?</span></span>|<span data-ttu-id="92c5f-198">Je `counter` již definováno?</span><span class="sxs-lookup"><span data-stu-id="92c5f-198">Is `counter` already defined?</span></span>|<span data-ttu-id="92c5f-199">Výsledek (bez ohledu na to, zda `counter` definuje novou místní proměnnou vymezenou na celou `For...Next` smyčku)</span><span class="sxs-lookup"><span data-stu-id="92c5f-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="92c5f-200">Ne</span><span class="sxs-lookup"><span data-stu-id="92c5f-200">No</span></span>|<span data-ttu-id="92c5f-201">Ano</span><span class="sxs-lookup"><span data-stu-id="92c5f-201">Yes</span></span>|<span data-ttu-id="92c5f-202">Ne, protože `counter` je již definován.</span><span class="sxs-lookup"><span data-stu-id="92c5f-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="92c5f-203">Pokud rozsah `counter` není místní s postupem, dojde k upozornění v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="92c5f-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="92c5f-204">Ne</span><span class="sxs-lookup"><span data-stu-id="92c5f-204">No</span></span>|<span data-ttu-id="92c5f-205">Ne</span><span class="sxs-lookup"><span data-stu-id="92c5f-205">No</span></span>|<span data-ttu-id="92c5f-206">Ano.</span><span class="sxs-lookup"><span data-stu-id="92c5f-206">Yes.</span></span> <span data-ttu-id="92c5f-207">Datový typ je odvozený z výrazů `start`, `end` a `step`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="92c5f-208">Informace o odvození typu naleznete v tématu [Option include Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [místní typ odvození](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="92c5f-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="92c5f-209">Ano</span><span class="sxs-lookup"><span data-stu-id="92c5f-209">Yes</span></span>|<span data-ttu-id="92c5f-210">Ano</span><span class="sxs-lookup"><span data-stu-id="92c5f-210">Yes</span></span>|<span data-ttu-id="92c5f-211">Ano, ale pouze v případě, že je existující proměnná `counter` definovaná mimo proceduru.</span><span class="sxs-lookup"><span data-stu-id="92c5f-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="92c5f-212">Tato proměnná zůstane oddělená.</span><span class="sxs-lookup"><span data-stu-id="92c5f-212">That variable remains separate.</span></span> <span data-ttu-id="92c5f-213">Pokud je rozsah existující proměnné `counter` místní pro proceduru, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="92c5f-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="92c5f-214">Ano</span><span class="sxs-lookup"><span data-stu-id="92c5f-214">Yes</span></span>|<span data-ttu-id="92c5f-215">Ne</span><span class="sxs-lookup"><span data-stu-id="92c5f-215">No</span></span>|<span data-ttu-id="92c5f-216">Ano.</span><span class="sxs-lookup"><span data-stu-id="92c5f-216">Yes.</span></span>|

<span data-ttu-id="92c5f-217">Datový typ `counter` určuje typ iterace, který musí být jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="92c5f-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="92c5f-218">@No__t_0, `SByte`, `UShort` `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single` nebo 0.</span><span class="sxs-lookup"><span data-stu-id="92c5f-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="92c5f-219">Výčet, který deklarujete pomocí [příkazu enum](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="92c5f-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

- <span data-ttu-id="92c5f-220">@No__t_0.</span><span class="sxs-lookup"><span data-stu-id="92c5f-220">An `Object`.</span></span>

- <span data-ttu-id="92c5f-221">Typ `T`, který má následující operátory, kde `B` je typ, který lze použít ve výrazu `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="92c5f-222">Volitelně můžete zadat `counter` proměnnou v příkazu `Next`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="92c5f-223">Tato syntaxe vylepšuje čitelnost vašeho programu, zejména v případě, že máte vnořené `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="92c5f-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="92c5f-224">Je nutné zadat proměnnou, která se zobrazí v příslušném příkazu `For`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="92c5f-225">Výrazy `start`, `end` a `step` lze vyhodnotit na libovolný datový typ, který se rozšíří na typ `counter`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="92c5f-226">Použijete-li uživatelem definovaný typ pro `counter`, bude pravděpodobně nutné definovat `CType` operátor převodu pro převod typů `start`, `end` nebo `step` na typ `counter`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="92c5f-227">Příklad</span><span class="sxs-lookup"><span data-stu-id="92c5f-227">Example</span></span>

<span data-ttu-id="92c5f-228">Následující příklad odebere všechny prvky z obecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="92c5f-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="92c5f-229">Místo [pro každý... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md), příklad ukazuje `For`... příkaz `Next`, který se opakuje v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="92c5f-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="92c5f-230">Tento příklad používá tuto techniku, protože metoda `removeAt` způsobí, že prvky po odebraném prvku budou mít nižší hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="92c5f-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="92c5f-231">Příklad</span><span class="sxs-lookup"><span data-stu-id="92c5f-231">Example</span></span>

<span data-ttu-id="92c5f-232">Následující příklad prochází výčet deklarovaný pomocí [příkazu enum](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="92c5f-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="92c5f-233">Příklad</span><span class="sxs-lookup"><span data-stu-id="92c5f-233">Example</span></span>

<span data-ttu-id="92c5f-234">V následujícím příkladu parametry příkazu používají třídu, která má přetížení operátoru pro operátory `+`, `-`, `>=` a `<=`.</span><span class="sxs-lookup"><span data-stu-id="92c5f-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="92c5f-235">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92c5f-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="92c5f-236">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="92c5f-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="92c5f-237">Příkaz While...End While</span><span class="sxs-lookup"><span data-stu-id="92c5f-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="92c5f-238">Příkaz Do...Loop</span><span class="sxs-lookup"><span data-stu-id="92c5f-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="92c5f-239">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="92c5f-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="92c5f-240">Příkaz Exit</span><span class="sxs-lookup"><span data-stu-id="92c5f-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="92c5f-241">Kolekce</span><span class="sxs-lookup"><span data-stu-id="92c5f-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
