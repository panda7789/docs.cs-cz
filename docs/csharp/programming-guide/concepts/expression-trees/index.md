---
title: Stromy výrazů (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: f425ab38bf7bb54814fe777b7cb02180d022a8af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169633"
---
# <a name="expression-trees-c"></a><span data-ttu-id="e01f4-102">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e01f4-102">Expression Trees (C#)</span></span>
<span data-ttu-id="e01f4-103">Stromy výrazů představují kód v datové struktuře podobné stromu, kde každý uzel je výraz, `x < y`například volání metody nebo binární operace, například .</span><span class="sxs-lookup"><span data-stu-id="e01f4-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="e01f4-104">Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="e01f4-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="e01f4-105">To umožňuje dynamickou modifikaci spustitelného kódu, provádění linq dotazů v různých databázích a vytváření dynamických dotazů.</span><span class="sxs-lookup"><span data-stu-id="e01f4-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="e01f4-106">Další informace o stromech výrazů v linq naleznete v [tématu Jak pomocí stromů výrazů vytvářet dynamické dotazy (C#).](./how-to-use-expression-trees-to-build-dynamic-queries.md)</span><span class="sxs-lookup"><span data-stu-id="e01f4-106">For more information about expression trees in LINQ, see [How to use expression trees to build dynamic queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>
  
 <span data-ttu-id="e01f4-107">Stromy výrazů se také používají v dynamickém jazyku runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a rozhraním .NET Framework a k povolení autorům kompilátoru vyzařovat stromy výrazů namísto zprostředkujícího jazyka Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="e01f4-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="e01f4-108">Další informace o dlr naleznete [v tématu Přehled dynamického jazykového běhu](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e01f4-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="e01f4-109">Kompilátor jazyka C# nebo Visual Basic může vytvořit strom výrazů na základě anonymního výrazu lambda <xref:System.Linq.Expressions> nebo můžete vytvořit stromy výrazů ručně pomocí oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e01f4-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="e01f4-110">Vytváření stromů výrazů z výrazů Lambda</span><span class="sxs-lookup"><span data-stu-id="e01f4-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="e01f4-111">Když je výraz lambda přiřazen proměnné <xref:System.Linq.Expressions.Expression%601>typu , kompilátor vydává kód k vytvoření stromu výrazů, který představuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="e01f4-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="e01f4-112">Kompilátor Jazyka C# může generovat stromy výrazů pouze z výrazu lambdas (nebo jednořádkové lambdy).</span><span class="sxs-lookup"><span data-stu-id="e01f4-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="e01f4-113">Nemůže analyzovat prohlášení lambdas (nebo multi-line lambdas).</span><span class="sxs-lookup"><span data-stu-id="e01f4-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="e01f4-114">Další informace o výrazech lambda v c#, naleznete v [tématu Lambda Výrazy](../../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e01f4-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="e01f4-115">Následující příklady kódu ukazují, jak mít kompilátor Jazyka C# vytvořit `num => num < 5`strom výrazů, který představuje výraz lambda .</span><span class="sxs-lookup"><span data-stu-id="e01f4-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="e01f4-116">Vytváření stromů výrazů pomocí rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e01f4-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="e01f4-117">Chcete-li vytvořit stromy výrazů <xref:System.Linq.Expressions.Expression> pomocí rozhraní API, použijte třídu.</span><span class="sxs-lookup"><span data-stu-id="e01f4-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="e01f4-118">Tato třída obsahuje statické metody factory, které vytvářejí uzly stromu výrazu určitých typů, <xref:System.Linq.Expressions.ParameterExpression>například , který představuje proměnnou nebo parametr nebo <xref:System.Linq.Expressions.MethodCallExpression>, který představuje volání metody.</span><span class="sxs-lookup"><span data-stu-id="e01f4-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="e01f4-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a další typy specifické pro výraz <xref:System.Linq.Expressions> jsou také definovány v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e01f4-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="e01f4-120">Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="e01f4-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="e01f4-121">Následující příklad kódu ukazuje, jak vytvořit strom výrazů, `num => num < 5` který představuje výraz lambda pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e01f4-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="e01f4-122">V rozhraní .NET Framework 4 nebo novější výraz stromy rozhraní API také podporuje přiřazení a `try-catch` řízení toku výrazy, jako jsou smyčky, podmíněné bloky a bloky.</span><span class="sxs-lookup"><span data-stu-id="e01f4-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="e01f4-123">Pomocí rozhraní API můžete vytvořit stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda kompilátorem Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e01f4-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="e01f4-124">Následující příklad ukazuje, jak vytvořit strom výrazů, který vypočítá faktoriál čísla.</span><span class="sxs-lookup"><span data-stu-id="e01f4-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="e01f4-125">Další informace naleznete [v tématu Generování dynamických metod se stromy výrazů v sadě Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e01f4-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="e01f4-126">Analýza stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="e01f4-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="e01f4-127">Následující příklad kódu ukazuje, jak lze rozdělit strom `num => num < 5` výrazu, který představuje výraz lambda, na jeho části.</span><span class="sxs-lookup"><span data-stu-id="e01f4-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="e01f4-128">Neměnnost výrazových stromů</span><span class="sxs-lookup"><span data-stu-id="e01f4-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="e01f4-129">Stromy výrazů by měly být neměnné.</span><span class="sxs-lookup"><span data-stu-id="e01f4-129">Expression trees should be immutable.</span></span> <span data-ttu-id="e01f4-130">To znamená, že pokud chcete upravit strom výrazů, musíte vytvořit nový strom výrazů zkopírováním existujícího stromu a nahrazením uzlů v něm.</span><span class="sxs-lookup"><span data-stu-id="e01f4-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="e01f4-131">Návštěvník stromu výrazů můžete použít k procházení existujícího stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="e01f4-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="e01f4-132">Další informace naleznete v tématu [Jak upravit stromy výrazů (C#).](./how-to-modify-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="e01f4-132">For more information, see [How to modify expression trees (C#)](./how-to-modify-expression-trees.md).</span></span>
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="e01f4-133">Kompilace stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="e01f4-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="e01f4-134">Typ <xref:System.Linq.Expressions.Expression%601> poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která zkompiluje kód reprezentovaný stromem výrazů do spustitelného delegáta.</span><span class="sxs-lookup"><span data-stu-id="e01f4-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="e01f4-135">Následující příklad kódu ukazuje, jak zkompilovat strom výrazů a spustit výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="e01f4-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="e01f4-136">Další informace naleznete v tématu [Jak spustit stromy výrazů (C#).](./how-to-execute-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="e01f4-136">For more information, see [How to execute expression trees (C#)](./how-to-execute-expression-trees.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e01f4-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="e01f4-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="e01f4-138">Jak spustit stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e01f4-138">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="e01f4-139">Jak upravit stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e01f4-139">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="e01f4-140">Lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="e01f4-140">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="e01f4-141">Přehled dynamického jazykového běhu</span><span class="sxs-lookup"><span data-stu-id="e01f4-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="e01f4-142">Koncepty programování (C#)</span><span class="sxs-lookup"><span data-stu-id="e01f4-142">Programming Concepts (C#)</span></span>](../index.md)
