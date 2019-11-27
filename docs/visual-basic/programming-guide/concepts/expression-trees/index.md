---
title: Stromy výrazů
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 4ca3b56f48368e465560fc5edd60c0df8dd4e1c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344703"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="9b0e7-102">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b0e7-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="9b0e7-103">Stromy výrazů reprezentují kód v datové struktuře podobné stromu, kde každý uzel je výraz, například volání metody nebo binární operace, například `x < y`.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="9b0e7-104">Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="9b0e7-105">To umožňuje dynamickou úpravu spustitelného kódu, spuštění dotazů LINQ v různých databázích a vytváření dynamických dotazů.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="9b0e7-106">Další informace o stromech výrazů v LINQ naleznete v tématu [How to: use Expression Trees to Dynamic dotazy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="9b0e7-107">Stromy výrazů se používají také v dynamickém jazykovém modulu runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a .NET Framework a umožňují zapisovačům kompilátoru vysílat stromy výrazů namísto jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="9b0e7-108">Další informace o DLR najdete v tématu [Přehled dynamického jazykového modulu runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="9b0e7-109">Můžete mít kompilátor C# nebo Visual Basic vytvořit strom výrazu pro vás na základě anonymního výrazu lambda nebo můžete vytvořit stromy výrazů ručně pomocí <xref:System.Linq.Expressions>ho oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="9b0e7-110">Vytváření stromů výrazů ze výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="9b0e7-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="9b0e7-111">Když je výraz lambda přiřazen proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor generuje kód pro sestavení stromu výrazu, který reprezentuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="9b0e7-112">Kompilátor Visual Basic může generovat stromy výrazů pouze z výrazů lambda výrazů (nebo jednoduchých výrazů lambda).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="9b0e7-113">Nelze analyzovat výrazy lambda příkazů (nebo víceřádkové výrazy lambda).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="9b0e7-114">Další informace o výrazech lambda v Visual Basic naleznete v tématu [lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="9b0e7-115">Následující příklady kódu ukazují, jak má kompilátor Visual Basic vytvořit strom výrazu, který představuje výraz lambda `Function(num) num < 5`.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="9b0e7-116">Vytváření stromů výrazů pomocí rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9b0e7-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="9b0e7-117">Chcete-li vytvořit stromy výrazů pomocí rozhraní API, použijte třídu <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="9b0e7-118">Tato třída obsahuje statické metody továrny, které vytvářejí uzly stromu výrazů specifických typů, například <xref:System.Linq.Expressions.ParameterExpression>, které představují proměnnou nebo parametr nebo <xref:System.Linq.Expressions.MethodCallExpression>, které představují volání metody.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="9b0e7-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a jiné typy specifické pro výraz jsou také definovány v oboru názvů <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="9b0e7-120">Tyto typy jsou odvozeny z <xref:System.Linq.Expressions.Expression>abstraktního typu.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="9b0e7-121">Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který představuje výraz lambda `Function(num) num < 5` pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="9b0e7-122">V .NET Framework 4 nebo novějších rozhraní API stromů výrazů podporuje také přiřazení a výrazy toku řízení, jako jsou smyčky, podmíněné bloky a `try-catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="9b0e7-123">Pomocí rozhraní API můžete vytvořit stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda kompilátorem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="9b0e7-124">Následující příklad ukazuje, jak vytvořit strom výrazu, který vypočítá faktoriál čísla.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="9b0e7-125">Další informace naleznete v tématu [generování dynamických metod pomocí stromů výrazů v aplikaci Visual studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="9b0e7-126">Analýza stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="9b0e7-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="9b0e7-127">Následující příklad kódu ukazuje, jak lze rozložit strom výrazu reprezentující výraz lambda `Function(num) num < 5` na jeho části.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="9b0e7-128">Neměnnosti stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="9b0e7-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="9b0e7-129">Stromy výrazů by měly být neměnné.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-129">Expression trees should be immutable.</span></span> <span data-ttu-id="9b0e7-130">To znamená, že pokud chcete upravit strom výrazu, je nutné vytvořit nový strom výrazu zkopírováním stávajícího a nahrazením uzlů v něm.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="9b0e7-131">K procházení stávajícího stromu výrazů můžete použít návštěvníka stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="9b0e7-132">Další informace najdete v tématu [Postup: Změna stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="9b0e7-133">Kompilování stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="9b0e7-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="9b0e7-134">Typ <xref:System.Linq.Expressions.Expression%601> poskytuje metodu <xref:System.Linq.Expressions.Expression%601.Compile%2A>, která zkompiluje kód reprezentovaný stromem výrazu do delegáta spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="9b0e7-135">Následující příklad kódu ukazuje, jak zkompilovat strom výrazu a spustit výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="9b0e7-136">Další informace najdete v tématu [Postup: spuštění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0e7-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b0e7-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="9b0e7-138">Postupy: spouštění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b0e7-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="9b0e7-139">Postupy: Změna stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b0e7-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="9b0e7-140">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="9b0e7-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="9b0e7-141">Přehled DLR (Dynamic Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="9b0e7-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="9b0e7-142">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b0e7-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
