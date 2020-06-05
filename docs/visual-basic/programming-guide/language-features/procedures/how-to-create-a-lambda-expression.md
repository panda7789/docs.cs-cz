---
title: 'Postupy: Vytvoření výrazu lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 7affc84fa501ba98bdfa93835f0b0e381580b9bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388384"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="be035-102">Postupy: Vytvoření výrazu lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be035-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="be035-103">*Výraz lambda* je funkce nebo podprogram, který nemá název.</span><span class="sxs-lookup"><span data-stu-id="be035-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="be035-104">Výraz lambda lze použít všude, kde je typ delegáta platný.</span><span class="sxs-lookup"><span data-stu-id="be035-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="be035-105">Vytvoření jednořádkové funkce výrazu lambda na jednom řádku</span><span class="sxs-lookup"><span data-stu-id="be035-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="be035-106">V jakékoli situaci, kdy může být použit typ delegáta, zadejte klíčové slovo `Function` , jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="be035-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="be035-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="be035-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="be035-108">V závorkách přímo za `Function` Zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="be035-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="be035-109">Všimněte si, že neurčíte název po `Function` .</span><span class="sxs-lookup"><span data-stu-id="be035-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="be035-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="be035-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="be035-111">Po seznamu parametrů zadejte jako tělo funkce jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="be035-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="be035-112">Hodnota, na kterou se výraz vyhodnocuje, je hodnota vrácená funkcí.</span><span class="sxs-lookup"><span data-stu-id="be035-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="be035-113">`As`K určení návratového typu nepoužíváte klauzuli.</span><span class="sxs-lookup"><span data-stu-id="be035-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="be035-114">Výraz lambda zavoláte předáním celočíselného argumentu.</span><span class="sxs-lookup"><span data-stu-id="be035-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="be035-115">Stejný výsledek lze také provést pomocí následujícího příkladu:</span><span class="sxs-lookup"><span data-stu-id="be035-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="be035-116">Vytvoření dílčí rutiny lambda výrazu na jednom řádku</span><span class="sxs-lookup"><span data-stu-id="be035-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="be035-117">V jakékoli situaci, kdy lze použít typ delegáta, zadejte klíčové slovo `Sub` , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="be035-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="be035-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="be035-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="be035-119">V závorkách přímo po `Sub` Zadejte parametry subrutiny.</span><span class="sxs-lookup"><span data-stu-id="be035-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="be035-120">Všimněte si, že neurčíte název po `Sub` .</span><span class="sxs-lookup"><span data-stu-id="be035-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="be035-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="be035-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="be035-122">Po seznamu parametrů zadejte jeden příkaz jako tělo dílčí rutiny.</span><span class="sxs-lookup"><span data-stu-id="be035-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="be035-123">Výraz lambda zavoláte předáním argumentu řetězce.</span><span class="sxs-lookup"><span data-stu-id="be035-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="be035-124">Vytvoření víceřádkové funkce výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="be035-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="be035-125">V jakékoli situaci, kdy lze použít typ delegáta, zadejte klíčové slovo `Function` , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="be035-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="be035-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="be035-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="be035-127">V závorkách přímo za `Function` Zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="be035-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="be035-128">Všimněte si, že neurčíte název po `Function` .</span><span class="sxs-lookup"><span data-stu-id="be035-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="be035-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="be035-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="be035-130">Stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="be035-130">Press ENTER.</span></span> <span data-ttu-id="be035-131">`End Function`Příkaz se přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="be035-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="be035-132">V těle funkce přidejte následující kód, který vytvoří výraz a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="be035-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="be035-133">`As`K určení návratového typu nepoužíváte klauzuli.</span><span class="sxs-lookup"><span data-stu-id="be035-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="be035-134">Výraz lambda zavoláte předáním celočíselného argumentu.</span><span class="sxs-lookup"><span data-stu-id="be035-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="be035-135">Vytvoření víceřádkové subrutiny výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="be035-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="be035-136">V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Sub` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="be035-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="be035-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="be035-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="be035-138">V závorkách přímo po `Sub` Zadejte parametry subrutiny.</span><span class="sxs-lookup"><span data-stu-id="be035-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="be035-139">Všimněte si, že neurčíte název po `Sub` .</span><span class="sxs-lookup"><span data-stu-id="be035-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="be035-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="be035-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="be035-141">Stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="be035-141">Press ENTER.</span></span> <span data-ttu-id="be035-142">`End Sub`Příkaz se přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="be035-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="be035-143">V těle funkce přidejte následující kód, který se spustí při vyvolání podrutiny.</span><span class="sxs-lookup"><span data-stu-id="be035-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="be035-144">Výraz lambda zavoláte předáním argumentu řetězce.</span><span class="sxs-lookup"><span data-stu-id="be035-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="be035-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="be035-145">Example</span></span>  
 <span data-ttu-id="be035-146">Běžné použití výrazů lambda je definovat funkci, která může být předána jako argument pro parametr, jehož typ je `Delegate` .</span><span class="sxs-lookup"><span data-stu-id="be035-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="be035-147">V následujícím příkladu <xref:System.Diagnostics.Process.GetProcesses%2A> Metoda vrátí pole procesů spuštěných v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="be035-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="be035-148"><xref:System.Linq.Enumerable.Where%2A>Metoda z <xref:System.Linq.Enumerable> třídy vyžaduje `Boolean` delegáta jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="be035-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="be035-149">Výraz lambda v příkladu se používá pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="be035-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="be035-150">Vrátí se `True` pro každý proces, který má pouze jedno vlákno, a ty jsou vybrány v `filteredList` .</span><span class="sxs-lookup"><span data-stu-id="be035-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="be035-151">Předchozí příklad je ekvivalentní následujícímu kódu, který je napsán v syntaxi LINQ (Language-Integrated Query):</span><span class="sxs-lookup"><span data-stu-id="be035-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="be035-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="be035-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="be035-153">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="be035-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="be035-154">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="be035-154">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="be035-155">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="be035-155">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="be035-156">Delegáti</span><span class="sxs-lookup"><span data-stu-id="be035-156">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="be035-157">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be035-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="be035-158">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="be035-158">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="be035-159">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be035-159">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
