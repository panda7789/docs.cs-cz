---
title: Stromy výrazů (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 7e63bf28f10070daa9624daa67bd5118fa67874d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926720"
---
# <a name="expression-trees-c"></a>Stromy výrazů (C#)
Stromy výrazů reprezentují kód v datové struktuře podobné stromu, kde každý uzel je výraz, například volání metody nebo binární operace, jako `x < y`je například.  
  
 Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů. To umožňuje dynamickou úpravu spustitelného kódu, spuštění dotazů LINQ v různých databázích a vytváření dynamických dotazů. Další informace o stromech výrazů v LINQ naleznete v [tématu How to: Použití stromů výrazů k sestavení dynamických dotazů (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Stromy výrazů se používají také v dynamickém jazykovém modulu runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a .NET Framework a umožňují zapisovačům kompilátoru vysílat stromy výrazů namísto jazyka MSIL (Microsoft Intermediate Language). Další informace o DLR najdete v tématu [Přehled dynamického jazykového modulu runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Můžete mít kompilátor C# nebo Visual Basic vytvořit strom výrazu pro vás na základě anonymního výrazu lambda nebo můžete vytvořit stromy výrazů ručně pomocí <xref:System.Linq.Expressions> oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů ze výrazů lambda  
 Když je výraz lambda přiřazen proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor generuje kód pro sestavení stromu výrazu, který reprezentuje lambda výraz.  
  
 C# Kompilátor může generovat stromy výrazů pouze z výrazů lambda výrazů (nebo jednoduchých výrazů lambda). Nelze analyzovat výrazy lambda příkazů (nebo víceřádkové výrazy lambda). Další informace o výrazech lambda v C#naleznete v tématu [lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak má C# kompilátor vytvořit strom výrazu, který představuje výraz `num => num < 5`lambda.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů pomocí rozhraní API  
 Chcete-li vytvořit stromy výrazů pomocí rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídu. Tato třída obsahuje statické metody továrny, které vytvářejí uzly stromu výrazů specifických typů, <xref:System.Linq.Expressions.ParameterExpression>například, které představují proměnnou nebo parametr, nebo <xref:System.Linq.Expressions.MethodCallExpression>, které představují volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a další typy specifické pro výraz jsou také definovány <xref:System.Linq.Expressions> v oboru názvů. Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression>.  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který reprezentuje lambda výraz `num => num < 5` pomocí rozhraní API.  
  
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
  
 V .NET Framework 4 nebo novějších rozhraní API stromů výrazů podporuje také přiřazení a vývojové výrazy řízení, jako jsou smyčky, podmíněné bloky a `try-catch` bloky. Pomocí rozhraní API můžete vytvářet stromy výrazů, které jsou složitější než ty, které je možné vytvořit z výrazů lambda C# kompilátorem. Následující příklad ukazuje, jak vytvořit strom výrazu, který vypočítá faktoriál čísla.  
  
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

Další informace naleznete v tématu [generování dynamických metod pomocí stromů výrazů v aplikaci Visual studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza stromů výrazů  
 Následující příklad kódu ukazuje, jak je možné rozložit strom výrazu reprezentující výraz `num => num < 5` lambda na jeho části.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnnosti stromů výrazů  
 Stromy výrazů by měly být neměnné. To znamená, že pokud chcete upravit strom výrazu, je nutné vytvořit nový strom výrazu zkopírováním stávajícího a nahrazením uzlů v něm. K procházení stávajícího stromu výrazů můžete použít návštěvníka stromu výrazu. Další informace najdete v tématu [jak: Úprava stromů výrazů (C#)](./how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilování stromů výrazů  
 <xref:System.Linq.Expressions.Expression%601> Typ<xref:System.Linq.Expressions.Expression%601.Compile%2A> poskytuje metodu, která zkompiluje kód reprezentovaný stromem výrazu do delegáta spustitelného souboru.  
  
 Následující příklad kódu ukazuje, jak zkompilovat strom výrazu a spustit výsledný kód.  
  
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
  
 Další informace najdete v tématu [jak: Spuštění stromů výrazů (C#)](./how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Expressions>
- [Postupy: Spuštění stromů výrazů (C#)](./how-to-execute-expression-trees.md)
- [Postupy: Úprava stromů výrazů (C#)](./how-to-modify-expression-trees.md)
- [Výrazy lambda](../../statements-expressions-operators/lambda-expressions.md)
- [Přehled DLR (Dynamic Language Runtime)](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepty programování (C#)](../index.md)
