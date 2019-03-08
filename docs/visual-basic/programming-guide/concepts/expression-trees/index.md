---
title: Stromy výrazů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
---
# <a name="expression-trees-visual-basic"></a>Stromy výrazů (Visual Basic)
Stromy výrazů představují kódu ve stromu jako datová struktura, kde každý uzel pracuje, výrazem, například, volání metody nebo binární operace, jako `x < y`.  
  
 Můžete zkompilovat a spustit kód reprezentována stromy výrazů. To umožňuje dynamickou změnu spustitelného kódu, provádění LINQ dotazy v různých databází a vytvoření dynamických dotazů. Další informace o stromů výrazů v technologii LINQ, naleznete v tématu [jak: Použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Stromy výrazů se také používají v dynamické jazykovým modulem runtime (DLR) k poskytování vzájemná funkční spolupráce mezi dynamické jazyky a rozhraní .NET Framework a umožňuje autorům generování stromů výrazů místo jazyk Microsoft intermediate language (MSIL). Další informace o DLR najdete v tématu [přehled dynamického modulu Runtime jazyka](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Kompilátor jazyka C# nebo Visual Basic vytvářet strom výrazu, založené na anonymní lambda výrazu nebo stromů výrazů můžete vytvořit ručně pomocí může mít <xref:System.Linq.Expressions> oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů z výrazů Lambda  
 Pokud je výraz lambda přiřazen proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor generuje kód pro vytváření strom výrazů, který představuje výraz lambda.  
  
 Kompilátor jazyka Visual Basic můžete vygenerovat stromů výrazů jenom z výrazu lambda (nebo výrazy lambda jednořádkového). Nelze analyzovat, příkazové lambdy (nebo víceřádkových výrazů lambda). Další informace o výrazech lambda v jazyce Visual Basic najdete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak pomocí kompilátoru jazyka Visual Basic vytvářet strom výrazů, který představuje výraz lambda `Function(num) num < 5`.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů s použitím rozhraní API  
 K vytvoření stromů výrazů s použitím rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídy. Tato třída obsahuje metody pro vytváření statických objektů, které vytvářejí výraz uzly stromu konkrétní typy, například <xref:System.Linq.Expressions.ParameterExpression>, která představuje proměnná nebo parametr, nebo <xref:System.Linq.Expressions.MethodCallExpression>, která reprezentuje volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, a další výraz konkrétní typy jsou také definovány v <xref:System.Linq.Expressions> oboru názvů. Tyto typy jsou odvozeny od abstraktní typ <xref:System.Linq.Expressions.Expression>.  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazů, který představuje výraz lambda `Function(num) num < 5` pomocí rozhraní API.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější, rozhraní API stromů výrazů také podporuje přiřazení a řízení toku výrazů například smyčky, podmíněné bloky a `try-catch` bloky. S použitím rozhraní API, můžete vytvořit stromů výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda v kompilátoru jazyka Visual Basic. Následující příklad ukazuje, jak vytvořit strom výrazů, který vypočítá faktoriál čísla.  
  
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

Další informace najdete v tématu [generování dynamických metod s stromů výrazů v sadě Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), což platí i pro novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza kódu stromů výrazů  
 Následující příklad kódu ukazuje, jak strom výrazu, který představuje výraz lambda `Function(num) num < 5` lze rozložit na jejích částí.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnnost stromů výrazů  
 Stromy výrazů by měl být neměnitelný. To znamená, že pokud chcete upravit strom výrazu, musí vytvořit nové stromu výrazů zkopírováním existující a nahraďte v ní uzly. Návštěvníka stromu výrazu můžete použít k procházení na stávající strom výrazu. Další informace najdete v tématu [jak: Úpravy stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilování stromů výrazů  
 <xref:System.Linq.Expressions.Expression%601> Typ poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která se kompiluje kód reprezentována strom výrazu na spustitelný soubor delegáta.  
  
 Následující příklad kódu ukazuje, jak na strom výrazu kompilace a spuštění výsledného kódu.  
  
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
  
 Další informace najdete v tématu [jak: Provádění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Linq.Expressions>
- [Postupy: Provádění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Postupy: Úpravy stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Výrazy lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Přehled DLR (Dynamic Language Runtime)](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepty programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
