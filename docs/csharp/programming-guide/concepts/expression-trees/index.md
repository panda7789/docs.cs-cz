---
title: Stromy výrazů (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 14ca5394a21b8dddb6c4431e6cabbf44a2f9add2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326495"
---
# <a name="expression-trees-c"></a>Stromy výrazů (C#)
Stromy výrazů představují kódu ve stromu jako datová struktura, kde každý uzel je výraz, například, volání metody nebo binární operace, jako `x < y`.  
  
 Můžete zkompilování a spuštění kódu reprezentována stromů výrazů. To umožňuje dynamické úpravy spustitelného kódu, provádění LINQ dotazy v různých databází a vytváření dynamických dotazů. Další informace o stromů výrazů v technologii LINQ najdete v tématu [postupy: použití stromů výrazů k vytvoření dynamických dotazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Stromy výrazů se také používají v dynamické language runtime (DLR) zajistit interoperabilitu mezi dynamických jazyků a rozhraní .NET Framework a umožňuje kompilátoru zapisovače pro vydávání stromů výrazů místo Microsoft (MSIL intermediate language). Další informace o DLR najdete v tématu [přehled dynamického modulu Runtime jazyka](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Můžete mít kompilátor jazyka C# nebo Visual Basic vytvořit strom výrazu pro založené na výrazu lambda anonymní, nebo stromů výrazů můžete vytvořit ručně pomocí <xref:System.Linq.Expressions> oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů z výrazů Lambda  
 Když je výrazu lambda přiřazený k proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor vydává kód k vytvoření strom výrazu, který představuje výrazu lambda.  
  
 Kompilátor jazyka C# můžete vygenerovat stromů výrazů pouze z výrazu lambda výrazy (nebo jeden řádek lambdas). Nelze analyzovat, lambda (nebo lambdas více řádků). Další informace o výrazy lambda v jazyce C#, najdete v části [výrazy Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak máte vytvořit strom výrazu, který představuje výrazu lambda kompilátor jazyka C# `num => num < 5`.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů pomocí rozhraní API  
 Chcete-li vytvořit stromů výrazů pomocí rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídy. Tato třída obsahuje metody pro statické objekt pro vytváření, které uzly stromu konkrétní typů, například vytvoření výrazu <xref:System.Linq.Expressions.ParameterExpression>, která představuje proměnné nebo parametru, nebo <xref:System.Linq.Expressions.MethodCallExpression>, která reprezentuje volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, a další výraz specifické typy je definována v <xref:System.Linq.Expressions> oboru názvů. Tyto typy jsou odvozeny od abstraktní typ <xref:System.Linq.Expressions.Expression>.  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který představuje výrazu lambda `num => num < 5` pomocí rozhraní API.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější, rozhraní API stromů výrazů také podporuje přiřazení a řízení toku výrazy například smyčky, podmíněné bloky a `try-catch` bloky. Stromy výrazů, které jsou složitější než ty, které je možné vytvářet z výrazů lambda kompilátor jazyka C# můžete vytvořit pomocí rozhraní API. Následující příklad ukazuje, jak vytvořit strom výrazu, která by vypočítala faktoriál čísla.  
  
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

Další informace najdete v tématu [generování dynamických metod s stromů výrazů v sadě Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které se rovněž vztahují na novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza stromů výrazů  
 Následující příklad kódu ukazuje, jak výraz strom, který představuje výrazu lambda `num => num < 5` lze rozložit na jejích částí.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnitelnosti stromů výrazů  
 Stromy výrazů by měl být neměnitelný. To znamená, že pokud chcete upravit strom výrazu, musí vytvořit novou větev výraz tak, že stávající a nahraďte uzly v něm. Procházení na stávající strom výrazu, můžete použít návštěvník výrazu stromu. Další informace najdete v tématu [postupy: Úprava stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilování stromů výrazů  
 <xref:System.Linq.Expressions.Expression%601> Typ poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metoda kompilovaný kód reprezentována strom výrazu do delegáta spustitelný soubor.  
  
 Následující příklad kódu ukazuje, jak na strom výrazu zkompilování a spuštění výsledný kód.  
  
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
  
 Další informace najdete v tématu [postup: provedení stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Expressions>  
 [Postupy: provádění stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Postupy: úpravy stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [Výrazy lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Přehled DLR (Dynamic Language Runtime)](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [Programování konceptů (C#)](../../../../csharp/programming-guide/concepts/index.md)
