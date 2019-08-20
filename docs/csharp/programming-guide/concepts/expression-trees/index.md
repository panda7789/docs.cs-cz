---
title: Stromy výrazů (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: eb0276f705ccb333e5739a4873ee6832e7a1878f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595002"
---
# <a name="expression-trees-c"></a><span data-ttu-id="fc730-102">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="fc730-102">Expression Trees (C#)</span></span>
<span data-ttu-id="fc730-103">Stromy výrazů reprezentují kód v datové struktuře podobné stromu, kde každý uzel je výraz, například volání metody nebo binární operace, jako `x < y`je například.</span><span class="sxs-lookup"><span data-stu-id="fc730-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="fc730-104">Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="fc730-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="fc730-105">To umožňuje dynamickou úpravu spustitelného kódu, spuštění dotazů LINQ v různých databázích a vytváření dynamických dotazů.</span><span class="sxs-lookup"><span data-stu-id="fc730-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="fc730-106">Další informace o stromech výrazů v LINQ naleznete v [tématu How to: Použití stromů výrazů k sestavení dynamických dotazů (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="fc730-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="fc730-107">Stromy výrazů se používají také v dynamickém jazykovém modulu runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a .NET Framework a umožňují zapisovačům kompilátoru vysílat stromy výrazů namísto jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="fc730-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="fc730-108">Další informace o DLR najdete v tématu [Přehled dynamického jazykového modulu runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fc730-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="fc730-109">Můžete mít kompilátor C# nebo Visual Basic vytvořit strom výrazu pro vás na základě anonymního výrazu lambda nebo můžete vytvořit stromy výrazů ručně pomocí <xref:System.Linq.Expressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fc730-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="fc730-110">Vytváření stromů výrazů ze výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="fc730-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="fc730-111">Když je výraz lambda přiřazen proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor generuje kód pro sestavení stromu výrazu, který reprezentuje lambda výraz.</span><span class="sxs-lookup"><span data-stu-id="fc730-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="fc730-112">C# Kompilátor může generovat stromy výrazů pouze z výrazů lambda výrazů (nebo jednoduchých výrazů lambda).</span><span class="sxs-lookup"><span data-stu-id="fc730-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="fc730-113">Nelze analyzovat výrazy lambda příkazů (nebo víceřádkové výrazy lambda).</span><span class="sxs-lookup"><span data-stu-id="fc730-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="fc730-114">Další informace o výrazech lambda v C#naleznete v tématu [lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fc730-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="fc730-115">Následující příklady kódu ukazují, jak má C# kompilátor vytvořit strom výrazu, který představuje výraz `num => num < 5`lambda.</span><span class="sxs-lookup"><span data-stu-id="fc730-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="fc730-116">Vytváření stromů výrazů pomocí rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fc730-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="fc730-117">Chcete-li vytvořit stromy výrazů pomocí rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídu.</span><span class="sxs-lookup"><span data-stu-id="fc730-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="fc730-118">Tato třída obsahuje statické metody továrny, které vytvářejí uzly stromu výrazů specifických typů, <xref:System.Linq.Expressions.ParameterExpression>například, které představují proměnnou nebo parametr, nebo <xref:System.Linq.Expressions.MethodCallExpression>, které představují volání metody.</span><span class="sxs-lookup"><span data-stu-id="fc730-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="fc730-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a další typy specifické pro výraz jsou také definovány <xref:System.Linq.Expressions> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fc730-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="fc730-120">Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="fc730-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="fc730-121">Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který reprezentuje lambda výraz `num => num < 5` pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="fc730-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="fc730-122">V .NET Framework 4 nebo novějších rozhraní API stromů výrazů podporuje také přiřazení a vývojové výrazy řízení, jako jsou smyčky, podmíněné bloky a `try-catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="fc730-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="fc730-123">Pomocí rozhraní API můžete vytvářet stromy výrazů, které jsou složitější než ty, které je možné vytvořit z výrazů lambda C# kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="fc730-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="fc730-124">Následující příklad ukazuje, jak vytvořit strom výrazu, který vypočítá faktoriál čísla.</span><span class="sxs-lookup"><span data-stu-id="fc730-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="fc730-125">Další informace naleznete v tématu [generování dynamických metod pomocí stromů výrazů v aplikaci Visual studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc730-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="fc730-126">Analýza stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="fc730-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="fc730-127">Následující příklad kódu ukazuje, jak je možné rozložit strom výrazu reprezentující výraz `num => num < 5` lambda na jeho části.</span><span class="sxs-lookup"><span data-stu-id="fc730-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="fc730-128">Neměnnosti stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="fc730-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="fc730-129">Stromy výrazů by měly být neměnné.</span><span class="sxs-lookup"><span data-stu-id="fc730-129">Expression trees should be immutable.</span></span> <span data-ttu-id="fc730-130">To znamená, že pokud chcete upravit strom výrazu, je nutné vytvořit nový strom výrazu zkopírováním stávajícího a nahrazením uzlů v něm.</span><span class="sxs-lookup"><span data-stu-id="fc730-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="fc730-131">K procházení stávajícího stromu výrazů můžete použít návštěvníka stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="fc730-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="fc730-132">Další informace najdete v tématu [jak: Úprava stromů výrazů (C#)](./how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="fc730-132">For more information, see [How to: Modify Expression Trees (C#)](./how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="fc730-133">Kompilování stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="fc730-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="fc730-134"><xref:System.Linq.Expressions.Expression%601> Typ<xref:System.Linq.Expressions.Expression%601.Compile%2A> poskytuje metodu, která zkompiluje kód reprezentovaný stromem výrazu do delegáta spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="fc730-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="fc730-135">Následující příklad kódu ukazuje, jak zkompilovat strom výrazu a spustit výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="fc730-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="fc730-136">Další informace najdete v tématu [jak: Spuštění stromů výrazů (C#)](./how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="fc730-136">For more information, see [How to: Execute Expression Trees (C#)](./how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc730-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc730-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="fc730-138">Postupy: Spuštění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="fc730-138">How to: Execute Expression Trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="fc730-139">Postupy: Úprava stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="fc730-139">How to: Modify Expression Trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="fc730-140">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="fc730-140">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="fc730-141">Přehled DLR (Dynamic Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="fc730-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="fc730-142">Koncepty programování (C#)</span><span class="sxs-lookup"><span data-stu-id="fc730-142">Programming Concepts (C#)</span></span>](../index.md)
