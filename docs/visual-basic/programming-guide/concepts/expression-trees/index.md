---
title: Stromy výrazů
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: b2266cbae0a9a8a07c2a3569efa33d162ffedd1d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266414"
---
# <a name="expression-trees-visual-basic"></a>Stromy výrazů (Visual Basic)
Stromy výrazů představují kód v datové struktuře podobné stromu, kde každý uzel je výraz, `x < y`například volání metody nebo binární operace, například .  
  
 Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů. To umožňuje dynamickou modifikaci spustitelného kódu, provádění linq dotazů v různých databázích a vytváření dynamických dotazů. Další informace o stromech výrazů v linq naleznete v [tématu How to: Use Expression Trees to Build Dynamic Queries (Visual Basic).](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)  
  
 Stromy výrazů se také používají v dynamickém jazyku runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a rozhraním .NET Framework a k povolení autorům kompilátoru vyzařovat stromy výrazů namísto zprostředkujícího jazyka Microsoft (MSIL). Další informace o dlr naleznete [v tématu Přehled dynamického jazykového běhu](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Kompilátor jazyka C# nebo Visual Basic může vytvořit strom výrazů na základě anonymního výrazu lambda <xref:System.Linq.Expressions> nebo můžete vytvořit stromy výrazů ručně pomocí oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů z výrazů Lambda  
 Když je výraz lambda přiřazen proměnné <xref:System.Linq.Expressions.Expression%601>typu , kompilátor vydává kód k vytvoření stromu výrazů, který představuje výraz lambda.  
  
 Kompilátor jazyka visual basic může generovat stromy výrazů pouze z výrazu lambdas (nebo jednořádkové lambdas). Nemůže analyzovat prohlášení lambdas (nebo multi-line lambdas). Další informace o výrazech lambda v jazyce Visual Basic naleznete v [tématu Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak mít kompilátor jazyka vytvořit strom výrazů, který představuje výraz `Function(num) num < 5`lambda .  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů pomocí rozhraní API  
 Chcete-li vytvořit stromy výrazů <xref:System.Linq.Expressions.Expression> pomocí rozhraní API, použijte třídu. Tato třída obsahuje statické metody factory, které vytvářejí uzly stromu výrazu určitých typů, <xref:System.Linq.Expressions.ParameterExpression>například , který představuje proměnnou nebo parametr nebo <xref:System.Linq.Expressions.MethodCallExpression>, který představuje volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a další typy specifické pro výraz <xref:System.Linq.Expressions> jsou také definovány v oboru názvů. Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression>.  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazů, `Function(num) num < 5` který představuje výraz lambda pomocí rozhraní API.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější výraz stromy rozhraní API také podporuje přiřazení a `try-catch` řízení toku výrazy, jako jsou smyčky, podmíněné bloky a bloky. Pomocí rozhraní API můžete vytvořit stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda kompilátorem jazyka. Následující příklad ukazuje, jak vytvořit strom výrazů, který vypočítá faktoriál čísla.  
  
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

Další informace naleznete [v tématu Generování dynamických metod se stromy výrazů v sadě Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza stromů výrazů  
 Následující příklad kódu ukazuje, jak lze rozdělit strom `Function(num) num < 5` výrazu, který představuje výraz lambda, na jeho části.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnnost výrazových stromů  
 Stromy výrazů by měly být neměnné. To znamená, že pokud chcete upravit strom výrazů, musíte vytvořit nový strom výrazů zkopírováním existujícího stromu a nahrazením uzlů v něm. Návštěvník stromu výrazů můžete použít k procházení existujícího stromu výrazů. Další informace naleznete v [tématu How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilace stromů výrazů  
 Typ <xref:System.Linq.Expressions.Expression%601> poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která zkompiluje kód reprezentovaný stromem výrazů do spustitelného delegáta.  
  
 Následující příklad kódu ukazuje, jak zkompilovat strom výrazů a spustit výsledný kód.  
  
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
  
 Další informace naleznete v [tématu How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Expressions>
- [Postup: Spuštění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Postup: Změna stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [Lambda výrazy](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Přehled dynamického jazykového běhu](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepty programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
