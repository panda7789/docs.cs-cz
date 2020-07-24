---
title: Stromy výrazů (C#)
description: Přečtěte si o stromech výrazů. Podívejte se, jak zkompilovat a spustit kód reprezentovaný těmito datovými strukturami, kde každý uzel je výraz.
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 2fa8577dd945650edebf84459de10c0c3bd04225
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105574"
---
# <a name="expression-trees-c"></a><span data-ttu-id="d7f77-104">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="d7f77-104">Expression Trees (C#)</span></span>
<span data-ttu-id="d7f77-105">Stromy výrazů reprezentují kód v datové struktuře podobné stromu, kde každý uzel je výraz, například volání metody nebo binární operace, jako je například `x < y` .</span><span class="sxs-lookup"><span data-stu-id="d7f77-105">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="d7f77-106">Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="d7f77-106">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="d7f77-107">To umožňuje dynamickou úpravu spustitelného kódu, spuštění dotazů LINQ v různých databázích a vytváření dynamických dotazů.</span><span class="sxs-lookup"><span data-stu-id="d7f77-107">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="d7f77-108">Další informace o stromech výrazů v LINQ naleznete v tématu [How to use Expression Trees to Dynamic dotazy (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d7f77-108">For more information about expression trees in LINQ, see [How to use expression trees to build dynamic queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>
  
 <span data-ttu-id="d7f77-109">Stromy výrazů se také používají v dynamickém jazykovém modulu runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a rozhraním .NET a umožňují zapisovačům kompilátoru vysílat stromy výrazů namísto jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d7f77-109">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and .NET and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="d7f77-110">Další informace o DLR najdete v tématu [Přehled dynamického jazykového modulu runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d7f77-110">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="d7f77-111">Můžete mít kompilátor C# nebo Visual Basic vytvořit strom výrazu pro vás na základě anonymního výrazu lambda, nebo můžete vytvořit stromy výrazů ručně pomocí <xref:System.Linq.Expressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d7f77-111">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="d7f77-112">Vytváření stromů výrazů ze výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="d7f77-112">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="d7f77-113">Když je výraz lambda přiřazen proměnné typu <xref:System.Linq.Expressions.Expression%601> , kompilátor generuje kód pro sestavení stromu výrazu, který reprezentuje lambda výraz.</span><span class="sxs-lookup"><span data-stu-id="d7f77-113">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="d7f77-114">Kompilátor jazyka C# může generovat stromy výrazů pouze z výrazů lambda výrazů (nebo jednoduchých výrazů lambda).</span><span class="sxs-lookup"><span data-stu-id="d7f77-114">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="d7f77-115">Nelze analyzovat výrazy lambda příkazů (nebo víceřádkové výrazy lambda).</span><span class="sxs-lookup"><span data-stu-id="d7f77-115">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="d7f77-116">Další informace o výrazech lambda v jazyce C# naleznete v tématu [lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d7f77-116">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="d7f77-117">Následující příklady kódu ukazují, jak má kompilátor jazyka C# vytvořit strom výrazu, který představuje výraz lambda `num => num < 5` .</span><span class="sxs-lookup"><span data-stu-id="d7f77-117">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="d7f77-118">Vytváření stromů výrazů pomocí rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d7f77-118">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="d7f77-119">Chcete-li vytvořit stromy výrazů pomocí rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídu.</span><span class="sxs-lookup"><span data-stu-id="d7f77-119">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="d7f77-120">Tato třída obsahuje statické metody továrny, které vytvářejí uzly stromu výrazů specifických typů, například <xref:System.Linq.Expressions.ParameterExpression> , které představují proměnnou nebo parametr, nebo <xref:System.Linq.Expressions.MethodCallExpression> , které představují volání metody.</span><span class="sxs-lookup"><span data-stu-id="d7f77-120">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="d7f77-121"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> a další typy specifické pro výraz jsou také definovány v <xref:System.Linq.Expressions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d7f77-121"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="d7f77-122">Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression> .</span><span class="sxs-lookup"><span data-stu-id="d7f77-122">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="d7f77-123">Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který reprezentuje lambda výraz `num => num < 5` pomocí rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d7f77-123">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="d7f77-124">V .NET Framework 4 nebo novějších rozhraní API stromů výrazů podporuje také přiřazení a vývojové výrazy řízení, jako jsou smyčky, podmíněné bloky a `try-catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="d7f77-124">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="d7f77-125">Pomocí rozhraní API můžete vytvořit stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda kompilátorem jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="d7f77-125">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="d7f77-126">Následující příklad ukazuje, jak vytvořit strom výrazu, který vypočítá faktoriál čísla.</span><span class="sxs-lookup"><span data-stu-id="d7f77-126">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="d7f77-127">Další informace naleznete v tématu [generování dynamických metod pomocí stromů výrazů v aplikaci Visual studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7f77-127">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="d7f77-128">Analýza stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="d7f77-128">Parsing Expression Trees</span></span>  
 <span data-ttu-id="d7f77-129">Následující příklad kódu ukazuje, jak je možné rozložit strom výrazu reprezentující výraz lambda `num => num < 5` na jeho části.</span><span class="sxs-lookup"><span data-stu-id="d7f77-129">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="d7f77-130">Neměnnosti stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="d7f77-130">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="d7f77-131">Stromy výrazů by měly být neměnné.</span><span class="sxs-lookup"><span data-stu-id="d7f77-131">Expression trees should be immutable.</span></span> <span data-ttu-id="d7f77-132">To znamená, že pokud chcete upravit strom výrazu, je nutné vytvořit nový strom výrazu zkopírováním stávajícího a nahrazením uzlů v něm.</span><span class="sxs-lookup"><span data-stu-id="d7f77-132">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="d7f77-133">K procházení stávajícího stromu výrazů můžete použít návštěvníka stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="d7f77-133">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="d7f77-134">Další informace najdete v tématu [Postup úpravy stromů výrazů (C#)](./how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="d7f77-134">For more information, see [How to modify expression trees (C#)](./how-to-modify-expression-trees.md).</span></span>
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="d7f77-135">Kompilování stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="d7f77-135">Compiling Expression Trees</span></span>  
 <span data-ttu-id="d7f77-136"><xref:System.Linq.Expressions.Expression%601>Typ poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která zkompiluje kód reprezentovaný stromem výrazu do delegáta spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="d7f77-136">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="d7f77-137">Následující příklad kódu ukazuje, jak zkompilovat strom výrazu a spustit výsledný kód.</span><span class="sxs-lookup"><span data-stu-id="d7f77-137">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="d7f77-138">Další informace najdete v tématu [spuštění stromů výrazů (C#)](./how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="d7f77-138">For more information, see [How to execute expression trees (C#)](./how-to-execute-expression-trees.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d7f77-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7f77-139">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="d7f77-140">Spuštění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="d7f77-140">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="d7f77-141">Postup úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="d7f77-141">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="d7f77-142">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="d7f77-142">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="d7f77-143">Přehled dynamického jazykového modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d7f77-143">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="d7f77-144">Koncepty programování (C#)</span><span class="sxs-lookup"><span data-stu-id="d7f77-144">Programming Concepts (C#)</span></span>](../index.md)
