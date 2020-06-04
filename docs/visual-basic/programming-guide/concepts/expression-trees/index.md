---
title: Stromy výrazů
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 5d30b2e2e66aa322e6d43b5fbf4a4baf3435b2a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410964"
---
# <a name="expression-trees-visual-basic"></a>Stromy výrazů (Visual Basic)
Stromy výrazů reprezentují kód v datové struktuře podobné stromu, kde každý uzel je výraz, například volání metody nebo binární operace, jako je například `x < y` .  
  
 Můžete zkompilovat a spustit kód reprezentovaný stromy výrazů. To umožňuje dynamickou úpravu spustitelného kódu, spuštění dotazů LINQ v různých databázích a vytváření dynamických dotazů. Další informace o stromech výrazů v LINQ naleznete v tématu [How to: use Expression Trees to Dynamic dotazy (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Stromy výrazů se používají také v dynamickém jazykovém modulu runtime (DLR) k zajištění interoperability mezi dynamickými jazyky a .NET Framework a umožňují zapisovačům kompilátoru vysílat stromy výrazů namísto jazyka MSIL (Microsoft Intermediate Language). Další informace o DLR najdete v tématu [Přehled dynamického jazykového modulu runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Můžete mít kompilátor C# nebo Visual Basic vytvořit strom výrazu pro vás na základě anonymního výrazu lambda, nebo můžete vytvořit stromy výrazů ručně pomocí <xref:System.Linq.Expressions> oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů ze výrazů lambda  
 Když je výraz lambda přiřazen proměnné typu <xref:System.Linq.Expressions.Expression%601> , kompilátor generuje kód pro sestavení stromu výrazu, který reprezentuje lambda výraz.  
  
 Kompilátor Visual Basic může generovat stromy výrazů pouze z výrazů lambda výrazů (nebo jednoduchých výrazů lambda). Nelze analyzovat výrazy lambda příkazů (nebo víceřádkové výrazy lambda). Další informace o výrazech lambda v Visual Basic naleznete v tématu [lambda Expressions](../../language-features/procedures/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak má kompilátor Visual Basic vytvořit strom výrazu, který představuje výraz lambda `Function(num) num < 5` .  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů pomocí rozhraní API  
 Chcete-li vytvořit stromy výrazů pomocí rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídu. Tato třída obsahuje statické metody továrny, které vytvářejí uzly stromu výrazů specifických typů, například <xref:System.Linq.Expressions.ParameterExpression> , které představují proměnnou nebo parametr, nebo <xref:System.Linq.Expressions.MethodCallExpression> , které představují volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> a další typy specifické pro výraz jsou také definovány v <xref:System.Linq.Expressions> oboru názvů. Tyto typy jsou odvozeny z abstraktního typu <xref:System.Linq.Expressions.Expression> .  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který reprezentuje lambda výraz `Function(num) num < 5` pomocí rozhraní API.  
  
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
  
 V .NET Framework 4 nebo novějších rozhraní API stromů výrazů podporuje také přiřazení a vývojové výrazy řízení, jako jsou smyčky, podmíněné bloky a `try-catch` bloky. Pomocí rozhraní API můžete vytvořit stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazů lambda kompilátorem Visual Basic. Následující příklad ukazuje, jak vytvořit strom výrazu, který vypočítá faktoriál čísla.  
  
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

Další informace naleznete v tématu [generování dynamických metod pomocí stromů výrazů v aplikaci Visual studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), které platí také pro novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza stromů výrazů  
 Následující příklad kódu ukazuje, jak je možné rozložit strom výrazu reprezentující výraz lambda `Function(num) num < 5` na jeho části.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnnosti stromů výrazů  
 Stromy výrazů by měly být neměnné. To znamená, že pokud chcete upravit strom výrazu, je nutné vytvořit nový strom výrazu zkopírováním stávajícího a nahrazením uzlů v něm. K procházení stávajícího stromu výrazů můžete použít návštěvníka stromu výrazu. Další informace najdete v tématu [Postup: Změna stromů výrazů (Visual Basic)](how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilování stromů výrazů  
 <xref:System.Linq.Expressions.Expression%601>Typ poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodu, která zkompiluje kód reprezentovaný stromem výrazu do delegáta spustitelného souboru.  
  
 Následující příklad kódu ukazuje, jak zkompilovat strom výrazu a spustit výsledný kód.  
  
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
  
 Další informace najdete v tématu [Postup: spuštění stromů výrazů (Visual Basic)](how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Expressions>
- [Postupy: spouštění stromů výrazů (Visual Basic)](how-to-execute-expression-trees.md)
- [Postupy: Změna stromů výrazů (Visual Basic)](how-to-modify-expression-trees.md)
- [Výrazy lambda](../../language-features/procedures/lambda-expressions.md)
- [Přehled dynamického jazykového modulu runtime](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [Koncepty programování (Visual Basic)](../index.md)
