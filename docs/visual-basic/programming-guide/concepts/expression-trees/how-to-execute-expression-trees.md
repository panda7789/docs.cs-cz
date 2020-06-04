---
title: 'Postupy: Provádění stromů výrazů'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 7b7b08ea1a7a1310b1d98876be96f1fa28ecba91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375327"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Postupy: spouštění stromů výrazů (Visual Basic)
V tomto tématu se dozvíte, jak spustit strom výrazu. Provádění stromu výrazů může vracet hodnotu nebo může provést pouze akci, jako je například volání metody.  
  
 Spustit lze pouze stromy výrazů, které reprezentují výrazy lambda. Stromy výrazů, které představují výrazy lambda, jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601> . Chcete-li spustit tyto stromy výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření spustitelného delegáta a poté vyvolejte delegáta.  
  
> [!NOTE]
> Pokud typ delegáta není znám, to znamená, že výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a nikoli <xref:System.Linq.Expressions.Expression%601> , je nutné zavolat <xref:System.Delegate.DynamicInvoke%2A> metodu na delegáta místo přímého vyvolání.  
  
 Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má jako tělo původní strom výrazu, voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Potom můžete spustit výraz lambda, jak je popsáno výše v této části.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak spustit strom výrazu, který představuje zvýšení čísla na výkon vytvořením lambda výrazu a jeho provedením. Zobrazí se výsledek, který představuje číslo umocněné na výkon.  
  
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
  
## <a name="compile-the-code"></a>Kompilovat kód  
  
- Zahrňte obor názvů System. Linq. Expressions.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (Visual Basic)](index.md)
- [Postupy: Změna stromů výrazů (Visual Basic)](how-to-modify-expression-trees.md)
