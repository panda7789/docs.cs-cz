---
title: 'Postupy: Provádění stromů výrazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: fde681905cded0e4043f52c5f2a29cee74b91209
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729350"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Postupy: Provádění stromů výrazů (Visual Basic)
Toto téma ukazuje, jak spustit strom výrazu. Provádění strom výrazu může vracet hodnotu, nebo ji může provádět jenom akce, jako je volání metody.  
  
 Je možné provést pouze stromů výrazů, které představují výrazů lambda. Stromy výrazů, které představují lambda výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>. K provádění těchto stromů výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metody k vytvoření delegáta spustitelný soubor a pak vyvolejte delegáta.  
  
> [!NOTE]
>  Pokud je typ delegáta není znám, to znamená, výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a ne <xref:System.Linq.Expressions.Expression%601>, je třeba zavolat <xref:System.Delegate.DynamicInvoke%2A> metoda delegátu namísto vyvolání přímo.  
  
 Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má původní stromu výrazů jako jeho textu pomocí volání <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Pak můžete spustit výraz lambda, jak bylo popsáno dříve v této části.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak provést strom výrazů, který představuje číslo mocninu vyvolání pomocí vytvoření výrazu lambda a spustíte ji. Výsledek, který představuje číslo vyvolána k elektrické energie, se zobrazí.  
  
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
  
-   Pokud se už neodkazuje, přidejte odkaz na System.Core.dll.  
  
-   Zahrnout System.Linq.Expressions oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Postupy: Úpravy stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
