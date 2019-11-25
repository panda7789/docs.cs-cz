---
title: Spuštění stromů výrazů (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: e7d408ea154572dc8b45d2e67bca3f05837868d2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969884"
---
# <a name="how-to-execute-expression-trees-c"></a>Spuštění stromů výrazů (C#)
V tomto tématu se dozvíte, jak spustit strom výrazu. Provádění stromu výrazů může vracet hodnotu nebo může provést pouze akci, jako je například volání metody.  
  
 Spustit lze pouze stromy výrazů, které reprezentují výrazy lambda. Stromy výrazů, které představují výrazy lambda, jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>. Chcete-li spustit tyto stromy výrazů, zavolejte metodu <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> pro vytvoření spustitelného delegáta a poté vyvolejte delegáta.  
  
> [!NOTE]
> Pokud typ delegáta není znám, to znamená, že výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a není <xref:System.Linq.Expressions.Expression%601>, je nutné volat metodu <xref:System.Delegate.DynamicInvoke%2A> na delegátu namísto přímého vyvolání.  
  
 Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má jako tělo původní strom výrazu, voláním metody <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>. Potom můžete spustit výraz lambda, jak je popsáno výše v této části.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak spustit strom výrazu, který představuje zvýšení čísla na výkon vytvořením lambda výrazu a jeho provedením. Zobrazí se výsledek, který představuje číslo umocněné na výkon.  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zahrňte obor názvů System. Linq. Expressions.  
  
## <a name="see-also"></a>Viz také:

- [Stromy výrazů (C#)](./index.md)
- [Postup úpravy stromů výrazů (C#)](./how-to-modify-expression-trees.md)
