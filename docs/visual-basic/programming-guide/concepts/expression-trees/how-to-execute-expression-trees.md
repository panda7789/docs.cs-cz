---
title: 'Postupy: provádění stromů výrazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 5fbd9ea2842a87a941a1b572acadc93b0a7d2e11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643650"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Postupy: provádění stromů výrazů (Visual Basic)
Toto téma ukazuje, jak provést strom výrazu se nezdařilo. Provádění strom výrazu může vrátit hodnotu nebo ji může provádět jenom akce, jako při volání metody.  
  
 Můžete provést pouze stromů výrazů, které představují výrazy lambda. Stromy výrazů, které představují lambda – výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>. Chcete-li provést tyto stromů výrazů, volejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření delegáta spustitelný soubor a pak vyvolejte delegát.  
  
> [!NOTE]
>  Pokud je typ delegát není znám, výrazu lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a není <xref:System.Linq.Expressions.Expression%601>, musí volat <xref:System.Delegate.DynamicInvoke%2A> metodu delegáta místo vyvolání ji přímo.  
  
 Pokud strom výrazu nepředstavuje výrazu lambda, můžete vytvořit nové výrazu lambda, který má původní strom výrazu jako jeho text voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metoda. Potom můžete provést výrazu lambda, jak je popsáno výše v této části.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak provést strom výrazu představující vyvolání čísla na zadanou mocninu. pomocí vytvoření výrazu lambda a její provedení. Výsledek, který představuje číslo vyvolá exponentem, se zobrazí.  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Přidáte odkaz na projekt na System.Core.dll, pokud se už neodkazuje.  
  
-   Obor názvů System.Linq.Expressions patří.  
  
## <a name="see-also"></a>Viz také  
 [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Postupy: úpravy stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
