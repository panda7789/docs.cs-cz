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
# <a name="expression-trees-c"></a>Stromy výrazů (C#)
Stromy výrazů představují kód v datové struktuře podobné stromu, kde každý uzel je výraz, `x < y`například volání metody nebo binární operace, například .  
  
 Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů. To umožňuje dynamickou modifikaci spustitelného kódu, provádění linq dotazů v různých databázích a vytváření dynamických dotazů. Další informace o stromech výrazů v linq naleznete v [tématu Jak pomocí stromů výrazů vytvářet dynamické dotazy (C#).](./how-to-use-expression-trees-to-build-dynamic-queries.md)
  
 Stromy výrazů se také používají v dynamickém jazyku runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a rozhraním .NET Framework a k povolení autorům kompilátoru vyzařovat stromy výrazů namísto zprostředkujícího jazyka Microsoft (MSIL). Další informace o dlr naleznete [v tématu Přehled dynamického jazykového běhu](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Kompilátor jazyka C# nebo Visual Basic může vytvořit strom výrazů na základě anonymního výrazu lambda <xref:System.Linq.Expressions> nebo můžete vytvořit stromy výrazů ručně pomocí oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů z výrazů Lambda  
 Když je výraz lambda přiřazen proměnné <xref:System.Linq.Expressions.Expression%601>typu , kompilátor vydává kód k vytvoření stromu výrazů, který představuje výraz lambda.  
  
 Kompilátor Jazyka C# může generovat stromy výrazů pouze z výrazu lambdas (nebo jednořádkové lambdy). Nemůže analyzovat prohlášení lambdas (nebo multi-line lambdas). Další informace o výrazech lambda v c#, naleznete v [tématu Lambda Výrazy](../../statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak mít kompilátor Jazyka C# vytvořit `num => num < 5`strom výrazů, který představuje výraz lambda .  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů pomocí rozhraní API  
 Chcete-li vytvořit stromy výrazů <xref:System.Linq.Expressions.Expression> pomocí rozhraní API, použijte třídu. Tato třída obsahuje statické metody factory, které vytvářejí uzly stromu výrazu určitých typů, <xref:System.Linq.Expressions.ParameterExpression>například , který představuje proměnnou nebo parametr nebo <xref:System.Linq.Expressions.MethodCallExpression>, který představuje volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a další typy specifické pro výraz <xref:System.Linq.Expressions> jsou také definovány v oboru názvů. Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression>.  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazů, `num => num < 5` který představuje výraz lambda pomocí rozhraní API.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější výraz stromy rozhraní API také podporuje přiřazení a `try-catch` řízení toku výrazy, jako jsou smyčky, podmíněné bloky a bloky. Pomocí rozhraní API můžete vytvořit stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda kompilátorem Jazyka C#. Následující příklad ukazuje, jak vytvořit strom výrazů, který vypočítá faktoriál čísla.  
  
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

Další informace naleznete [v tématu Generování dynamických metod se stromy výrazů v sadě Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza stromů výrazů  
 Následující příklad kódu ukazuje, jak lze rozdělit strom `num => num < 5` výrazu, který představuje výraz lambda, na jeho části.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnnost výrazových stromů  
 Stromy výrazů by měly být neměnné. To znamená, že pokud chcete upravit strom výrazů, musíte vytvořit nový strom výrazů zkopírováním existujícího stromu a nahrazením uzlů v něm. Návštěvník stromu výrazů můžete použít k procházení existujícího stromu výrazů. Další informace naleznete v tématu [Jak upravit stromy výrazů (C#).](./how-to-modify-expression-trees.md)
  
## <a name="compiling-expression-trees"></a>Kompilace stromů výrazů  
 Typ <xref:System.Linq.Expressions.Expression%601> poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která zkompiluje kód reprezentovaný stromem výrazů do spustitelného delegáta.  
  
 Následující příklad kódu ukazuje, jak zkompilovat strom výrazů a spustit výsledný kód.  
  
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
  
 Další informace naleznete v tématu [Jak spustit stromy výrazů (C#).](./how-to-execute-expression-trees.md)
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Expressions>
- [Jak spustit stromy výrazů (C#)](./how-to-execute-expression-trees.md)
- [Jak upravit stromy výrazů (C#)](./how-to-modify-expression-trees.md)
- [Lambda výrazy](../../statements-expressions-operators/lambda-expressions.md)
- [Přehled dynamického jazykového běhu](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepty programování (C#)](../index.md)
