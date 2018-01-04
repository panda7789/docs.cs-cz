---
title: "Stromy výrazů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee31d85214fba474db8a3f7499d867cc09bd41a0
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="expression-trees-visual-basic"></a>Stromy výrazů (Visual Basic)
Stromy výrazů představují kódu ve stromu jako datová struktura, kde každý uzel je výraz, například, volání metody nebo binární operace, jako `x < y`.  
  
 Můžete zkompilování a spuštění kódu reprezentována stromů výrazů. To umožňuje dynamické úpravy spustitelného kódu, provádění LINQ dotazy v různých databází a vytváření dynamických dotazů. Další informace o stromů výrazů v technologii LINQ najdete v tématu [postupy: použití stromů výrazů k vytvoření dynamických dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Stromy výrazů se také používají v dynamické language runtime (DLR) zajistit interoperabilitu mezi dynamických jazyků a rozhraní .NET Framework a umožňuje kompilátoru zapisovače pro vydávání stromů výrazů místo Microsoft (MSIL intermediate language). Další informace o DLR najdete v tématu [přehled dynamického modulu Runtime jazyka](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
 Můžete mít kompilátor jazyka C# nebo Visual Basic vytvořit strom výrazu pro založené na výrazu lambda anonymní, nebo stromů výrazů můžete vytvořit ručně pomocí <xref:System.Linq.Expressions> oboru názvů.  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>Vytváření stromů výrazů z výrazů Lambda  
 Když je výrazu lambda přiřazený k proměnné typu <xref:System.Linq.Expressions.Expression%601>, kompilátor vydává kód k vytvoření strom výrazu, který představuje výrazu lambda.  
  
 Visual Basic – kompilátor může generovat stromů výrazů pouze z výrazu lambda výrazy (nebo jeden řádek lambdas). Nelze analyzovat, lambda (nebo lambdas více řádků). Další informace o výrazy lambda v jazyce Visual Basic najdete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Následující příklady kódu ukazují, jak mají Visual Basic – kompilátor vytvořit strom výrazu, který představuje výrazu lambda `Function(num) num < 5`.  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>Vytváření stromů výrazů pomocí rozhraní API  
 Chcete-li vytvořit stromů výrazů pomocí rozhraní API, použijte <xref:System.Linq.Expressions.Expression> třídy. Tato třída obsahuje metody pro statické objekt pro vytváření, které uzly stromu konkrétní typů, například vytvoření výrazu <xref:System.Linq.Expressions.ParameterExpression>, která představuje proměnné nebo parametru, nebo <xref:System.Linq.Expressions.MethodCallExpression>, která reprezentuje volání metody. <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, a další výraz specifické typy je definována v <xref:System.Linq.Expressions> oboru názvů. Tyto typy jsou odvozeny od abstraktní typ <xref:System.Linq.Expressions.Expression>.  
  
 Následující příklad kódu ukazuje, jak vytvořit strom výrazu, který představuje výrazu lambda `Function(num) num < 5` pomocí rozhraní API.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější, rozhraní API stromů výrazů také podporuje přiřazení a řízení toku výrazy například smyčky, podmíněné bloky a `try-catch` bloky. Stromy výrazů, které jsou složitější než ty, které lze vytvořit z výrazy lambda ve Visual Basic – kompilátor můžete vytvořit pomocí rozhraní API. Následující příklad ukazuje, jak vytvořit strom výrazu, která by vypočítala faktoriál čísla.  
  
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

Další informace najdete v tématu [generování dynamických metod s stromů výrazů v sadě Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513), které se rovněž vztahují na novější verze sady Visual Studio.
  
## <a name="parsing-expression-trees"></a>Analýza stromů výrazů  
 Následující příklad kódu ukazuje, jak výraz strom, který představuje výrazu lambda `Function(num) num < 5` lze rozložit na jejích částí.  
  
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
  
## <a name="immutability-of-expression-trees"></a>Neměnitelnosti stromů výrazů  
 Stromy výrazů by měl být neměnitelný. To znamená, že pokud chcete upravit strom výrazu, musí vytvořit novou větev výraz tak, že stávající a nahraďte uzly v něm. Procházení na stávající strom výrazu, můžete použít návštěvník výrazu stromu. Další informace najdete v tématu [postupy: Úprava stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## <a name="compiling-expression-trees"></a>Kompilování stromů výrazů  
 <xref:System.Linq.Expressions.Expression%601> Typ poskytuje <xref:System.Linq.Expressions.Expression%601.Compile%2A> metoda kompilovaný kód reprezentována strom výrazu do delegáta spustitelný soubor.  
  
 Následující příklad kódu ukazuje, jak na strom výrazu zkompilování a spuštění výsledný kód.  
  
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
  
 Další informace najdete v tématu [postup: provedení stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Expressions>  
 [Postupy: provádění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Postupy: úpravy stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [Výrazy lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Přehled DLR (Dynamic Language Runtime)](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [Programování konceptů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
