---
title: "Stromy výrazů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 250da307d024b1011e1fb04cd84eb25e41af3fa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="expression-trees-c"></a><span data-ttu-id="0a403-102">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="0a403-102">Expression Trees (C#)</span></span>
<span data-ttu-id="0a403-103">Stromy výrazů představují kódu ve stromu jako datová struktura, kde každý uzel je výraz, například, volání metody nebo binární operace, jako `x < y`.</span><span class="sxs-lookup"><span data-stu-id="0a403-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="0a403-104">Můžete zkompilování a spuštění kódu reprezentována stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="0a403-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="0a403-105">To umožňuje dynamické úpravy spustitelného kódu, provádění LINQ dotazy v různých databází a vytváření dynamických dotazů.</span><span class="sxs-lookup"><span data-stu-id="0a403-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="0a403-106">Další informace o stromů výrazů v technologii LINQ najdete v tématu [postupy: použití stromů výrazů k vytvoření dynamických dotazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="0a403-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="0a403-107">Stromy výrazů se také používají v dynamické language runtime (DLR) zajistit interoperabilitu mezi dynamických jazyků a rozhraní .NET Framework a umožňuje kompilátoru zapisovače pro vydávání stromů výrazů místo Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="0a403-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="0a403-108">Další informace o DLR najdete v tématu [přehled dynamického modulu Runtime jazyka](https://msdn.microsoft.com/library/dd233052).</span><span class="sxs-lookup"><span data-stu-id="0a403-108">For more information about the DLR, see [Dynamic Language Runtime Overview](https://msdn.microsoft.com/library/dd233052).</span></span>  
  
 <span data-ttu-id="0a403-109">Můžete mít kompilátor jazyka C# nebo Visual Basic vytvořit strom výrazu pro založené na výrazu lambda anonymní, nebo stromů výrazů můžete vytvořit ručně pomocí <xref:System.Linq.Expressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0a403-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="0a403-110">Vytváření stromů výrazů z výrazů Lambda</span><span class="sxs-lookup"><span data-stu-id="0a403-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="0a403-111">Když je výrazu lambda přiřazený k proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor vydává kód k vytvoření strom výrazu, který představuje výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="0a403-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="0a403-112">Kompilátor jazyka C# můžete vygenerovat stromů výrazů pouze z výrazu lambda výrazy (nebo jeden řádek lambdas).</span><span class="sxs-lookup"><span data-stu-id="0a403-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="0a403-113">Nelze analyzovat, lambda (nebo lambdas více řádků).</span><span class="sxs-lookup"><span data-stu-id="0a403-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="0a403-114">Další informace o výrazy lambda v jazyce C#, najdete v části [výrazy Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0a403-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="0a403-115">Následující příklady kódu ukazují, jak máte vytvořit strom výrazu, který představuje výrazu lambda kompilátor jazyka C# `num => num < 5`.</span><span class="sxs-lookup"><span data-stu-id="0a403-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="0a403-116">Vytváření stromů výrazů pomocí rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0a403-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="0a403-117">Chcete-li vytvořit stromů výrazů pomocí rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídy.</span><span class="sxs-lookup"><span data-stu-id="0a403-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="0a403-118">Tato třída obsahuje metody pro statické objekt pro vytváření, které uzly stromu konkrétní typů, například vytvoření výrazu <xref:System.Linq.Expressions.ParameterExpression>, která představuje proměnné nebo parametru, nebo <xref:System.Linq.Expressions.MethodCallExpression>, která reprezentuje volání metody.</span><span class="sxs-lookup"><span data-stu-id="0a403-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="0a403-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, a další výraz specifické typy je definována v <xref:System.Linq.Expressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0a403-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="0a403-120">Tyto typy jsou odvozeny od abstraktní typ <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="0a403-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="0a403-121">Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který představuje výrazu lambda `num => num < 5` pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0a403-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for   
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="0a403-122">V rozhraní .NET Framework 4 nebo novější, rozhraní API stromů výrazů také podporuje přiřazení a řízení toku výrazy například smyčky, podmíněné bloky a `try-catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="0a403-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="0a403-123">Stromy výrazů, které jsou složitější než ty, které je možné vytvářet z výrazů lambda kompilátor jazyka C# můžete vytvořit pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0a403-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="0a403-124">Následující příklad ukazuje, jak vytvořit strom výrazu, která by vypočítala faktoriál čísla.</span><span class="sxs-lookup"><span data-stu-id="0a403-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.   
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="0a403-125">Další informace najdete v tématu [generování dynamických metod s stromů výrazů v sadě Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513), které se rovněž vztahují na novější verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a403-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="0a403-126">Analýza stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="0a403-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="0a403-127">Následující příklad kódu ukazuje, jak výraz strom, který představuje výrazu lambda `num => num < 5` lze rozložit na jejích částí.</span><span class="sxs-lookup"><span data-stu-id="0a403-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="0a403-128">Neměnitelnosti stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="0a403-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="0a403-129">Stromy výrazů by měl být neměnitelný.</span><span class="sxs-lookup"><span data-stu-id="0a403-129">Expression trees should be immutable.</span></span> <span data-ttu-id="0a403-130">To znamená, že pokud chcete upravit strom výrazu, musí vytvořit novou větev výraz tak, že stávající a nahraďte uzly v něm.</span><span class="sxs-lookup"><span data-stu-id="0a403-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="0a403-131">Procházení na stávající strom výrazu, můžete použít návštěvník výrazu stromu.</span><span class="sxs-lookup"><span data-stu-id="0a403-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="0a403-132">Další informace najdete v tématu [postupy: Úprava stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0a403-132">For more information, see [How to: Modify Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="0a403-133">Kompilování stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="0a403-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="0a403-134"><xref:System.Linq.Expressions.Expression%601> Typ poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metoda kompilovaný kód reprezentována strom výrazu do delegáta spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="0a403-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="0a403-135">Následující příklad kódu ukazuje, jak na strom výrazu zkompilování a spuštění výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="0a403-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="0a403-136">Další informace najdete v tématu [postup: provedení stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0a403-136">For more information, see [How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a403-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a403-137">See Also</span></span>  
 <xref:System.Linq.Expressions>  
 [<span data-ttu-id="0a403-138">Postupy: provádění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="0a403-138">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="0a403-139">Postupy: úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="0a403-139">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [<span data-ttu-id="0a403-140">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="0a403-140">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="0a403-141">Přehled Dynamic Language Runtime</span><span class="sxs-lookup"><span data-stu-id="0a403-141">Dynamic Language Runtime Overview</span></span>](https://msdn.microsoft.com/library/dd233052)  
 [<span data-ttu-id="0a403-142">Programování konceptů (C#)</span><span class="sxs-lookup"><span data-stu-id="0a403-142">Programming Concepts (C#)</span></span>](../../../../csharp/programming-guide/concepts/index.md)
