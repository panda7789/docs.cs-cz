---
title: 'Postupy: Vytvoření výrazu Lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344543"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="cf208-102">Postupy: Vytvoření výrazu Lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf208-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="cf208-103">A *výraz lambda* je funkce nebo podprogramu, který nemá název.</span><span class="sxs-lookup"><span data-stu-id="cf208-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="cf208-104">Výraz lambda je možné bez ohledu na typ delegáta je platný.</span><span class="sxs-lookup"><span data-stu-id="cf208-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="cf208-105">Vytvořit funkci výraz lambda jednořádkového</span><span class="sxs-lookup"><span data-stu-id="cf208-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="cf208-106">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Function`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cf208-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="cf208-107">V závorkách přímo po `Function`, zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="cf208-107">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="cf208-108">Všimněte si, že nezadáte název po `Function`.</span><span class="sxs-lookup"><span data-stu-id="cf208-108">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. <span data-ttu-id="cf208-109">Následující seznam parametrů zadejte jeden výraz jako tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="cf208-109">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="cf208-110">Výraz je vyhodnocen jako hodnota je hodnota vrácená funkcí.</span><span class="sxs-lookup"><span data-stu-id="cf208-110">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="cf208-111">Je velmi riskantní používat `As` klauzule k určení návratového typu.</span><span class="sxs-lookup"><span data-stu-id="cf208-111">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="cf208-112">Můžete pro volání výrazu lambda předáním celočíselný argument.</span><span class="sxs-lookup"><span data-stu-id="cf208-112">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="cf208-113">Případně stejného výsledku lze dosáhnout v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cf208-113">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="cf208-114">Chcete-li vytvořit výraz lambda jednořádkového podprogram</span><span class="sxs-lookup"><span data-stu-id="cf208-114">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="cf208-115">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cf208-115">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="cf208-116">V závorkách přímo po `Sub`, typ parametrů volanému podprogramu.</span><span class="sxs-lookup"><span data-stu-id="cf208-116">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="cf208-117">Všimněte si, že nezadáte název po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="cf208-117">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. <span data-ttu-id="cf208-118">Následující seznam parametrů zadejte jako text podprogramu jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="cf208-118">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="cf208-119">Můžete pro volání výrazu lambda předáním jako argument řetězec.</span><span class="sxs-lookup"><span data-stu-id="cf208-119">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="cf208-120">K vytvoření víceřádkového výrazu lambda výraz funkce</span><span class="sxs-lookup"><span data-stu-id="cf208-120">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="cf208-121">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Function`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cf208-121">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="cf208-122">V závorkách přímo po `Function`, zadejte parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="cf208-122">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="cf208-123">Všimněte si, že nezadáte název po `Function`.</span><span class="sxs-lookup"><span data-stu-id="cf208-123">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. <span data-ttu-id="cf208-124">Stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="cf208-124">Press ENTER.</span></span> <span data-ttu-id="cf208-125">`End Function` Je automaticky přidán příkaz.</span><span class="sxs-lookup"><span data-stu-id="cf208-125">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="cf208-126">V těle funkce přidejte následující kód k vytvoření výrazu a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cf208-126">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="cf208-127">Je velmi riskantní používat `As` klauzule k určení návratového typu.</span><span class="sxs-lookup"><span data-stu-id="cf208-127">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="cf208-128">Můžete pro volání výrazu lambda předáním celočíselný argument.</span><span class="sxs-lookup"><span data-stu-id="cf208-128">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="cf208-129">K vytvoření víceřádkového výrazu lambda výraz podprogram</span><span class="sxs-lookup"><span data-stu-id="cf208-129">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="cf208-130">V každé situaci, kdy může použít typ delegáta, zadejte klíčové slovo `Sub`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cf208-130">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="cf208-131">V závorkách přímo po `Sub`, typ parametrů volanému podprogramu.</span><span class="sxs-lookup"><span data-stu-id="cf208-131">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="cf208-132">Všimněte si, že nezadáte název po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="cf208-132">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. <span data-ttu-id="cf208-133">Stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="cf208-133">Press ENTER.</span></span> <span data-ttu-id="cf208-134">`End Sub` Je automaticky přidán příkaz.</span><span class="sxs-lookup"><span data-stu-id="cf208-134">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="cf208-135">V těle funkce přidejte následující kód pro spuštění při vyvolání podprogramu.</span><span class="sxs-lookup"><span data-stu-id="cf208-135">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="cf208-136">Můžete pro volání výrazu lambda předáním jako argument řetězec.</span><span class="sxs-lookup"><span data-stu-id="cf208-136">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="cf208-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf208-137">Example</span></span>  
 <span data-ttu-id="cf208-138">Běžné použití výrazů lambda je definice funkce, které lze předat jako argument pro parametr, jehož typ je `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="cf208-138">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="cf208-139">V následujícím příkladu <xref:System.Diagnostics.Process.GetProcesses%2A> metoda vrátí pole z procesů spuštěných na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="cf208-139">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="cf208-140"><xref:System.Linq.Enumerable.Where%2A> Metodu z <xref:System.Linq.Enumerable> vyžaduje třídu `Boolean` jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="cf208-140">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="cf208-141">Výraz lambda v příkladu se používá pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="cf208-141">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="cf208-142">Vrátí `True` pro každý proces, který má pouze jedno vlákno, a ty jsou vybrány v `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="cf208-142">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="cf208-143">Předchozí příklad je ekvivalentní následující kód, který je napsán v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntaxi:</span><span class="sxs-lookup"><span data-stu-id="cf208-143">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="cf208-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf208-144">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="cf208-145">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="cf208-145">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="cf208-146">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="cf208-146">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="cf208-147">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="cf208-147">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="cf208-148">Delegáty</span><span class="sxs-lookup"><span data-stu-id="cf208-148">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="cf208-149">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf208-149">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="cf208-150">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="cf208-150">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="cf208-151">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf208-151">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
