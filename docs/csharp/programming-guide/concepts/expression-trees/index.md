---
title: 'Stromy výrazů (C#)'
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
---
# <a name="expression-trees-c"></a>Stromy výrazů (C#)
Stromy výrazů představují kódu ve stromu jako datová struktura, kde každý uzel pracuje, výrazem, například, volání metody nebo binární operace, jako `x < y`.  
  
 Můžete zkompilovat a spustit kód reprezentována stromy výrazů. To umožňuje dynamickou změnu spustitelného kódu, provádění LINQ dotazy v různých databází a vytvoření dynamických dotazů. Další informace o stromů výrazů v technologii LINQ, naleznete v tématu [jak: Použití stromů výrazů k sestavování dynamických dotazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Stromy výrazů se také používají v dynamické jazykovým modulem runtime (DLR) k poskytování vzájemná funkční spolupráce mezi dynamické jazyky a rozhraní .NET Framework a umožňuje autorům generování stromů výrazů místo jazyk Microsoft intermediate language (MSIL). Další informace o DLR najdete v tématu [přehled dynamického modulu Runtime jazyka](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Kompilátor jazyka C# nebo Visual Basic vytvářet strom výrazu, založené na anonymní lambda výrazu nebo stromů výrazů můžete vytvořit ručně pomocí může mít <xref:System.Linq.Expressions> oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů z výrazů Lambda  
 Pokud je výraz lambda přiřazen proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor generuje kód pro vytváření strom výrazů, který představuje výraz lambda.  
  
 Kompilátor jazyka C# můžete vygenerovat stromů výrazů jenom z výrazu lambda (nebo výrazy lambda jednořádkového). Nelze analyzovat, příkazové lambdy (nebo víceřádkových výrazů lambda). Další informace o výrazech lambda v jazyce C# najdete v tématu [výrazy Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak kompilátor jazyka C# vytvořit strom výrazů, který představuje výraz lambda `num => num < 5`.  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů s použitím rozhraní API  
 K vytvoření stromů výrazů s použitím rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídy. Tato třída obsahuje metody pro vytváření statických objektů, které vytvářejí výraz uzly stromu konkrétní typy, například <xref:System.Linq.Expressions.ParameterExpression>, která představuje proměnná nebo parametr, nebo <xref:System.Linq.Expressions.MethodCallExpression>, která reprezentuje volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, a další výraz konkrétní typy jsou také definovány v <xref:System.Linq.Expressions> oboru názvů. Tyto typy jsou odvozeny od abstraktní typ <xref:System.Linq.Expressions.Expression>.  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazů, který představuje výraz lambda `num => num < 5` pomocí rozhraní API.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější, rozhraní API stromů výrazů také podporuje přiřazení a řízení toku výrazů například smyčky, podmíněné bloky a `try-catch` bloky. S použitím rozhraní API, můžete vytvořit stromů výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda v kompilátoru jazyka C#. Následující příklad ukazuje, jak vytvořit strom výrazů, který vypočítá faktoriál čísla.  
  
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

Další informace najdete v tématu [generování dynamických metod s stromů výrazů v sadě Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), což platí i pro novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza kódu stromů výrazů  
 Následující příklad kódu ukazuje, jak strom výrazu, který představuje výraz lambda `num => num < 5` lze rozložit na jejích částí.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnnost stromů výrazů  
 Stromy výrazů by měl být neměnitelný. To znamená, že pokud chcete upravit strom výrazu, musí vytvořit nové stromu výrazů zkopírováním existující a nahraďte v ní uzly. Návštěvníka stromu výrazu můžete použít k procházení na stávající strom výrazu. Další informace najdete v tématu [jak: Úpravy stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilování stromů výrazů  
 <xref:System.Linq.Expressions.Expression%601> Typ poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která se kompiluje kód reprezentována strom výrazu na spustitelný soubor delegáta.  
  
 Následující příklad kódu ukazuje, jak na strom výrazu kompilace a spuštění výsledného kódu.  
  
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
  
 Další informace najdete v tématu [jak: Provádění stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Expressions>
- [Postupy: Provádění stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Postupy: Úpravy stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Výrazy lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Přehled DLR (Dynamic Language Runtime)](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepty programování (C#)](../../../../csharp/programming-guide/concepts/index.md)
