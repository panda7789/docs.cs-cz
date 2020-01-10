---
title: 'Postupy: Vytvoření výrazu lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 1c65841e4c124252cfa41bcd4d0c305a426687ee
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632347"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="69542-102">Postupy: Vytvoření výrazu lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69542-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="69542-103">*Výraz lambda* je funkce nebo podprogram, který nemá název.</span><span class="sxs-lookup"><span data-stu-id="69542-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="69542-104">Výraz lambda lze použít všude, kde je typ delegáta platný.</span><span class="sxs-lookup"><span data-stu-id="69542-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="69542-105">Vytvoření jednořádkové funkce výrazu lambda na jednom řádku</span><span class="sxs-lookup"><span data-stu-id="69542-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="69542-106">V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Function`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="69542-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="69542-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="69542-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="69542-108">V závorkách přímo po `Function`zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="69542-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="69542-109">Všimněte si, že po `Function`neurčíte název.</span><span class="sxs-lookup"><span data-stu-id="69542-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="69542-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="69542-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="69542-111">Po seznamu parametrů zadejte jako tělo funkce jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="69542-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="69542-112">Hodnota, na kterou se výraz vyhodnocuje, je hodnota vrácená funkcí.</span><span class="sxs-lookup"><span data-stu-id="69542-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="69542-113">K určení návratového typu nepoužíváte klauzuli `As`.</span><span class="sxs-lookup"><span data-stu-id="69542-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="69542-114">Výraz lambda zavoláte předáním celočíselného argumentu.</span><span class="sxs-lookup"><span data-stu-id="69542-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="69542-115">Stejný výsledek lze také provést pomocí následujícího příkladu:</span><span class="sxs-lookup"><span data-stu-id="69542-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="69542-116">Vytvoření dílčí rutiny lambda výrazu na jednom řádku</span><span class="sxs-lookup"><span data-stu-id="69542-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="69542-117">V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69542-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="69542-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="69542-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="69542-119">V závorkách přímo po `Sub`zadejte parametry subrutiny.</span><span class="sxs-lookup"><span data-stu-id="69542-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="69542-120">Všimněte si, že po `Sub`neurčíte název.</span><span class="sxs-lookup"><span data-stu-id="69542-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="69542-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="69542-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="69542-122">Po seznamu parametrů zadejte jeden příkaz jako tělo dílčí rutiny.</span><span class="sxs-lookup"><span data-stu-id="69542-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="69542-123">Výraz lambda zavoláte předáním argumentu řetězce.</span><span class="sxs-lookup"><span data-stu-id="69542-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="69542-124">Vytvoření víceřádkové funkce výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="69542-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="69542-125">V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Function`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69542-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="69542-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="69542-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="69542-127">V závorkách přímo po `Function`zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="69542-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="69542-128">Všimněte si, že po `Function`neurčíte název.</span><span class="sxs-lookup"><span data-stu-id="69542-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="69542-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="69542-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="69542-130">Stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="69542-130">Press ENTER.</span></span> <span data-ttu-id="69542-131">Příkaz `End Function` je automaticky přidán.</span><span class="sxs-lookup"><span data-stu-id="69542-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="69542-132">V těle funkce přidejte následující kód, který vytvoří výraz a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="69542-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="69542-133">K určení návratového typu nepoužíváte klauzuli `As`.</span><span class="sxs-lookup"><span data-stu-id="69542-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="69542-134">Výraz lambda zavoláte předáním celočíselného argumentu.</span><span class="sxs-lookup"><span data-stu-id="69542-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="69542-135">Vytvoření víceřádkové subrutiny výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="69542-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="69542-136">V jakékoli situaci, kdy se dá použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="69542-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="69542-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="69542-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="69542-138">V závorkách přímo po `Sub`zadejte parametry subrutiny.</span><span class="sxs-lookup"><span data-stu-id="69542-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="69542-139">Všimněte si, že po `Sub`neurčíte název.</span><span class="sxs-lookup"><span data-stu-id="69542-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="69542-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="69542-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="69542-141">Stiskněte ENTER.</span><span class="sxs-lookup"><span data-stu-id="69542-141">Press ENTER.</span></span> <span data-ttu-id="69542-142">Příkaz `End Sub` je automaticky přidán.</span><span class="sxs-lookup"><span data-stu-id="69542-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="69542-143">V těle funkce přidejte následující kód, který se spustí při vyvolání podrutiny.</span><span class="sxs-lookup"><span data-stu-id="69542-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="69542-144">Výraz lambda zavoláte předáním argumentu řetězce.</span><span class="sxs-lookup"><span data-stu-id="69542-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="69542-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="69542-145">Example</span></span>  
 <span data-ttu-id="69542-146">Běžné použití výrazů lambda je definovat funkci, která může být předána jako argument pro parametr, jehož typ je `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="69542-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="69542-147">V následujícím příkladu metoda <xref:System.Diagnostics.Process.GetProcesses%2A> vrátí pole procesů spuštěných v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="69542-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="69542-148">Metoda <xref:System.Linq.Enumerable.Where%2A> z <xref:System.Linq.Enumerable> třídy vyžaduje jako argument delegáta `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="69542-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="69542-149">Výraz lambda v příkladu se používá pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="69542-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="69542-150">Vrátí `True` pro každý proces, který má pouze jedno vlákno, a ty jsou vybrány v `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="69542-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="69542-151">Předchozí příklad je ekvivalentní následujícímu kódu, který je napsán v syntaxi LINQ (Language-Integrated Query):</span><span class="sxs-lookup"><span data-stu-id="69542-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="69542-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69542-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="69542-153">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="69542-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="69542-154">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="69542-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="69542-155">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="69542-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="69542-156">Delegáti</span><span class="sxs-lookup"><span data-stu-id="69542-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="69542-157">Postupy: Předání procedur jinému postupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69542-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="69542-158">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="69542-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="69542-159">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69542-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
