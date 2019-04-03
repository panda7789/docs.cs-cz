---
title: 'Postupy: Vytvoření výrazu Lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 8754049e493ab23b1e7b01d0f315b00bdebf0378
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841417"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="9feef-102">Postupy: Vytvoření výrazu Lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9feef-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="9feef-103">A *výraz lambda* je funkce nebo podprogramu, který nemá název.</span><span class="sxs-lookup"><span data-stu-id="9feef-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="9feef-104">Výraz lambda je možné bez ohledu na typ delegáta je platný.</span><span class="sxs-lookup"><span data-stu-id="9feef-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="9feef-105">Vytvořit funkci výraz lambda jednořádkového</span><span class="sxs-lookup"><span data-stu-id="9feef-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="9feef-106">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Function`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9feef-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="9feef-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="9feef-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="9feef-108">V závorkách přímo po `Function`, zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="9feef-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="9feef-109">Všimněte si, že nezadáte název po `Function`.</span><span class="sxs-lookup"><span data-stu-id="9feef-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="9feef-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="9feef-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="9feef-111">Následující seznam parametrů zadejte jeden výraz jako tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="9feef-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="9feef-112">Výraz je vyhodnocen jako hodnota je hodnota vrácená funkcí.</span><span class="sxs-lookup"><span data-stu-id="9feef-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="9feef-113">Je velmi riskantní používat `As` klauzule k určení návratového typu.</span><span class="sxs-lookup"><span data-stu-id="9feef-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="9feef-114">Můžete pro volání výrazu lambda předáním celočíselný argument.</span><span class="sxs-lookup"><span data-stu-id="9feef-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4.  <span data-ttu-id="9feef-115">Případně stejného výsledku lze dosáhnout v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9feef-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="9feef-116">Chcete-li vytvořit výraz lambda jednořádkového podprogram</span><span class="sxs-lookup"><span data-stu-id="9feef-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="9feef-117">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9feef-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="9feef-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="9feef-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="9feef-119">V závorkách přímo po `Sub`, typ parametrů volanému podprogramu.</span><span class="sxs-lookup"><span data-stu-id="9feef-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="9feef-120">Všimněte si, že nezadáte název po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="9feef-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="9feef-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="9feef-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="9feef-122">Následující seznam parametrů zadejte jako text podprogramu jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="9feef-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="9feef-123">Můžete pro volání výrazu lambda předáním jako argument řetězec.</span><span class="sxs-lookup"><span data-stu-id="9feef-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="9feef-124">K vytvoření víceřádkového výrazu lambda výraz funkce</span><span class="sxs-lookup"><span data-stu-id="9feef-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="9feef-125">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Function`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9feef-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="9feef-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="9feef-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="9feef-127">V závorkách přímo po `Function`, zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="9feef-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="9feef-128">Všimněte si, že nezadáte název po `Function`.</span><span class="sxs-lookup"><span data-stu-id="9feef-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="9feef-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="9feef-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="9feef-130">Stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="9feef-130">Press ENTER.</span></span> <span data-ttu-id="9feef-131">`End Function` Je automaticky přidán příkaz.</span><span class="sxs-lookup"><span data-stu-id="9feef-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="9feef-132">V těle funkce přidejte následující kód k vytvoření výrazu a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9feef-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="9feef-133">Je velmi riskantní používat `As` klauzule k určení návratového typu.</span><span class="sxs-lookup"><span data-stu-id="9feef-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="9feef-134">Můžete pro volání výrazu lambda předáním celočíselný argument.</span><span class="sxs-lookup"><span data-stu-id="9feef-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="9feef-135">K vytvoření víceřádkového výrazu lambda výraz podprogram</span><span class="sxs-lookup"><span data-stu-id="9feef-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="9feef-136">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9feef-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="9feef-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="9feef-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="9feef-138">V závorkách přímo po `Sub`, typ parametrů volanému podprogramu.</span><span class="sxs-lookup"><span data-stu-id="9feef-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="9feef-139">Všimněte si, že nezadáte název po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="9feef-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="9feef-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="9feef-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="9feef-141">Stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="9feef-141">Press ENTER.</span></span> <span data-ttu-id="9feef-142">`End Sub` Je automaticky přidán příkaz.</span><span class="sxs-lookup"><span data-stu-id="9feef-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="9feef-143">V těle funkce přidejte následující kód pro spuštění při vyvolání podprogramu.</span><span class="sxs-lookup"><span data-stu-id="9feef-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="9feef-144">Můžete pro volání výrazu lambda předáním jako argument řetězec.</span><span class="sxs-lookup"><span data-stu-id="9feef-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="9feef-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="9feef-145">Example</span></span>  
 <span data-ttu-id="9feef-146">Běžné použití výrazů lambda je definice funkce, které lze předat jako argument pro parametr, jehož typ je `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="9feef-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="9feef-147">V následujícím příkladu <xref:System.Diagnostics.Process.GetProcesses%2A> metoda vrátí pole z procesů spuštěných na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="9feef-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="9feef-148"><xref:System.Linq.Enumerable.Where%2A> Metodu z <xref:System.Linq.Enumerable> vyžaduje třídu `Boolean` jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="9feef-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="9feef-149">Výraz lambda v příkladu se používá pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="9feef-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="9feef-150">Vrátí `True` pro každý proces, který má pouze jedno vlákno, a ty jsou vybrány v `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="9feef-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="9feef-151">Předchozí příklad je ekvivalentní následující kód, který je napsán v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxi:</span><span class="sxs-lookup"><span data-stu-id="9feef-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="9feef-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9feef-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="9feef-153">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="9feef-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="9feef-154">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="9feef-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="9feef-155">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="9feef-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9feef-156">Delegáti</span><span class="sxs-lookup"><span data-stu-id="9feef-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="9feef-157">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9feef-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="9feef-158">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="9feef-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="9feef-159">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9feef-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
