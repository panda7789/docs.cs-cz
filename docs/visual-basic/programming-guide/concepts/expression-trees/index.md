---
title: Stromy výrazů
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: b2266cbae0a9a8a07c2a3569efa33d162ffedd1d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266414"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="9d071-102">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d071-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="9d071-103">Stromy výrazů představují kód v datové struktuře podobné stromu, kde každý uzel je výraz, `x < y`například volání metody nebo binární operace, například .</span><span class="sxs-lookup"><span data-stu-id="9d071-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="9d071-104">Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="9d071-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="9d071-105">To umožňuje dynamickou modifikaci spustitelného kódu, provádění linq dotazů v různých databázích a vytváření dynamických dotazů.</span><span class="sxs-lookup"><span data-stu-id="9d071-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="9d071-106">Další informace o stromech výrazů v linq naleznete v [tématu How to: Use Expression Trees to Build Dynamic Queries (Visual Basic).](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)</span><span class="sxs-lookup"><span data-stu-id="9d071-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="9d071-107">Stromy výrazů se také používají v dynamickém jazyku runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a rozhraním .NET Framework a k povolení autorům kompilátoru vyzařovat stromy výrazů namísto zprostředkujícího jazyka Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="9d071-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="9d071-108">Další informace o dlr naleznete [v tématu Přehled dynamického jazykového běhu](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9d071-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="9d071-109">Kompilátor jazyka C# nebo Visual Basic může vytvořit strom výrazů na základě anonymního výrazu lambda <xref:System.Linq.Expressions> nebo můžete vytvořit stromy výrazů ručně pomocí oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9d071-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="9d071-110">Vytváření stromů výrazů z výrazů Lambda</span><span class="sxs-lookup"><span data-stu-id="9d071-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="9d071-111">Když je výraz lambda přiřazen proměnné <xref:System.Linq.Expressions.Expression%601>typu , kompilátor vydává kód k vytvoření stromu výrazů, který představuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="9d071-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="9d071-112">Kompilátor jazyka visual basic může generovat stromy výrazů pouze z výrazu lambdas (nebo jednořádkové lambdas).</span><span class="sxs-lookup"><span data-stu-id="9d071-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="9d071-113">Nemůže analyzovat prohlášení lambdas (nebo multi-line lambdas).</span><span class="sxs-lookup"><span data-stu-id="9d071-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="9d071-114">Další informace o výrazech lambda v jazyce Visual Basic naleznete v [tématu Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9d071-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="9d071-115">Následující příklady kódu ukazují, jak mít kompilátor jazyka vytvořit strom výrazů, který představuje výraz `Function(num) num < 5`lambda .</span><span class="sxs-lookup"><span data-stu-id="9d071-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="9d071-116">Vytváření stromů výrazů pomocí rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9d071-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="9d071-117">Chcete-li vytvořit stromy výrazů <xref:System.Linq.Expressions.Expression> pomocí rozhraní API, použijte třídu.</span><span class="sxs-lookup"><span data-stu-id="9d071-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="9d071-118">Tato třída obsahuje statické metody factory, které vytvářejí uzly stromu výrazu určitých typů, <xref:System.Linq.Expressions.ParameterExpression>například , který představuje proměnnou nebo parametr nebo <xref:System.Linq.Expressions.MethodCallExpression>, který představuje volání metody.</span><span class="sxs-lookup"><span data-stu-id="9d071-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="9d071-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a další typy specifické pro výraz <xref:System.Linq.Expressions> jsou také definovány v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9d071-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="9d071-120">Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="9d071-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="9d071-121">Následující příklad kódu ukazuje, jak vytvořit strom výrazů, `Function(num) num < 5` který představuje výraz lambda pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9d071-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="9d071-122">V rozhraní .NET Framework 4 nebo novější výraz stromy rozhraní API také podporuje přiřazení a `try-catch` řízení toku výrazy, jako jsou smyčky, podmíněné bloky a bloky.</span><span class="sxs-lookup"><span data-stu-id="9d071-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="9d071-123">Pomocí rozhraní API můžete vytvořit stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda kompilátorem jazyka.</span><span class="sxs-lookup"><span data-stu-id="9d071-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="9d071-124">Následující příklad ukazuje, jak vytvořit strom výrazů, který vypočítá faktoriál čísla.</span><span class="sxs-lookup"><span data-stu-id="9d071-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="9d071-125">Další informace naleznete [v tématu Generování dynamických metod se stromy výrazů v sadě Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d071-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="9d071-126">Analýza stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="9d071-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="9d071-127">Následující příklad kódu ukazuje, jak lze rozdělit strom `Function(num) num < 5` výrazu, který představuje výraz lambda, na jeho části.</span><span class="sxs-lookup"><span data-stu-id="9d071-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="9d071-128">Neměnnost výrazových stromů</span><span class="sxs-lookup"><span data-stu-id="9d071-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="9d071-129">Stromy výrazů by měly být neměnné.</span><span class="sxs-lookup"><span data-stu-id="9d071-129">Expression trees should be immutable.</span></span> <span data-ttu-id="9d071-130">To znamená, že pokud chcete upravit strom výrazů, musíte vytvořit nový strom výrazů zkopírováním existujícího stromu a nahrazením uzlů v něm.</span><span class="sxs-lookup"><span data-stu-id="9d071-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="9d071-131">Návštěvník stromu výrazů můžete použít k procházení existujícího stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="9d071-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="9d071-132">Další informace naleznete v [tématu How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="9d071-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="9d071-133">Kompilace stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="9d071-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="9d071-134">Typ <xref:System.Linq.Expressions.Expression%601> poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která zkompiluje kód reprezentovaný stromem výrazů do spustitelného delegáta.</span><span class="sxs-lookup"><span data-stu-id="9d071-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="9d071-135">Následující příklad kódu ukazuje, jak zkompilovat strom výrazů a spustit výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="9d071-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="9d071-136">Další informace naleznete v [tématu How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="9d071-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d071-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d071-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="9d071-138">Postup: Spuštění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d071-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="9d071-139">Postup: Změna stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d071-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="9d071-140">Lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="9d071-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="9d071-141">Přehled dynamického jazykového běhu</span><span class="sxs-lookup"><span data-stu-id="9d071-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="9d071-142">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d071-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
