---
title: "Postupy: Vytvoření výrazu lambda (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16365b64e5430be61c113ac7601154df260e4ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="9f4aa-102">Postupy: Vytvoření výrazu lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f4aa-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="9f4aa-103">A *výrazu lambda* je funkce nebo podprogramu, který nemá název.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="9f4aa-104">Výraz lambda lze použít bez ohledu na typ delegáta je platný.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="9f4aa-105">Chcete-li vytvořit funkci výrazu lambda jeden řádek</span><span class="sxs-lookup"><span data-stu-id="9f4aa-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="9f4aa-106">V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Function`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9f4aa-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="9f4aa-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="9f4aa-108">V závorkách přímo po `Function`, zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="9f4aa-109">Všimněte si, že nezadáte název po `Function`.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="9f4aa-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="9f4aa-111">Následující seznam parametrů zadejte jako text funkce jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="9f4aa-112">Hodnota, která je výsledkem výrazu je hodnota vráceným funkcí.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="9f4aa-113">Nepoužívejte `As` klauzule zadat návratový typ.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     <span data-ttu-id="9f4aa-114">Můžete pro volání výrazu lambda předávání v argument celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  <span data-ttu-id="9f4aa-115">Alternativně stejného výsledku se dosahuje prostřednictvím v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9f4aa-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="9f4aa-116">Chcete-li vytvořit podprogramu výrazu lambda jeden řádek</span><span class="sxs-lookup"><span data-stu-id="9f4aa-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="9f4aa-117">V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="9f4aa-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="9f4aa-119">V závorkách přímo po `Sub`, parametry podprogramu typu.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="9f4aa-120">Všimněte si, že nezadáte název po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="9f4aa-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="9f4aa-122">Následující seznam parametrů zadejte jako text podprogramu jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     <span data-ttu-id="9f4aa-123">Můžete pro volání výrazu lambda předávání v argument řetězce.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="9f4aa-124">Chcete-li vytvořit výraz funkce Víceřádkový lambda</span><span class="sxs-lookup"><span data-stu-id="9f4aa-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="9f4aa-125">V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Function`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="9f4aa-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="9f4aa-127">V závorkách přímo po `Function`, zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="9f4aa-128">Všimněte si, že nezadáte název po `Function`.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="9f4aa-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="9f4aa-130">Stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-130">Press ENTER.</span></span> <span data-ttu-id="9f4aa-131">`End Function` Je automaticky přidán příkaz.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="9f4aa-132">V hlavní funkce přidejte následující kód k vytvoření výrazu a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="9f4aa-133">Nepoužívejte `As` klauzule zadat návratový typ.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     <span data-ttu-id="9f4aa-134">Můžete pro volání výrazu lambda předávání v argument celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="9f4aa-135">Chcete-li vytvořit výraz podprogramu Víceřádkový lambda</span><span class="sxs-lookup"><span data-stu-id="9f4aa-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="9f4aa-136">V každé situaci, kdy může použít typem delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9f4aa-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="9f4aa-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="9f4aa-138">V závorkách přímo po `Sub`, parametry podprogramu typu.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="9f4aa-139">Všimněte si, že nezadáte název po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="9f4aa-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="9f4aa-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="9f4aa-141">Stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-141">Press ENTER.</span></span> <span data-ttu-id="9f4aa-142">`End Sub` Je automaticky přidán příkaz.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="9f4aa-143">V hlavní funkce přidejte následující kód provést při vyvolání podprogramu.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     <span data-ttu-id="9f4aa-144">Můžete pro volání výrazu lambda předávání v argument řetězce.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a><span data-ttu-id="9f4aa-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f4aa-145">Example</span></span>  
 <span data-ttu-id="9f4aa-146">Běžné použití výrazů lambda je určit funkce, které lze předat ve jako argument pro parametr s jiným typem `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="9f4aa-147">V následujícím příkladu <xref:System.Diagnostics.Process.GetProcesses%2A> metoda vrátí pole procesů spuštěných v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="9f4aa-148"><xref:System.Linq.Enumerable.Where%2A> Metoda z <xref:System.Linq.Enumerable> vyžaduje třídy `Boolean` delegovat jako její argument.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="9f4aa-149">Výraz lambda v příkladu se používá k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="9f4aa-150">Vrátí `True` pro každý proces, který má pouze jedno vlákno, a ty, které jsou vybrány v `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="9f4aa-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 <span data-ttu-id="9f4aa-151">Předchozí příklad je ekvivalentní následující kód, který je napsána v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxe:</span><span class="sxs-lookup"><span data-stu-id="9f4aa-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9f4aa-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f4aa-152">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 [<span data-ttu-id="9f4aa-153">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="9f4aa-153">Lambda Expressions</span></span>](./lambda-expressions.md)  
 [<span data-ttu-id="9f4aa-154">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="9f4aa-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="9f4aa-155">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="9f4aa-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="9f4aa-156">Delegáti</span><span class="sxs-lookup"><span data-stu-id="9f4aa-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="9f4aa-157">Postupy: předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f4aa-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="9f4aa-158">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="9f4aa-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="9f4aa-159">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f4aa-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
