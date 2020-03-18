---
title: Jak spustit stromy výrazů (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: e7d408ea154572dc8b45d2e67bca3f05837868d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969884"
---
# <a name="how-to-execute-expression-trees-c"></a>Jak spustit stromy výrazů (C#)
Toto téma ukazuje, jak spustit strom výrazů. Spuštění stromu výrazmůže vrátit hodnotu nebo může pouze provést akci, jako je například volání metody.  
  
 Mohou být spuštěny pouze stromy výrazů, které představují výrazy lambda. Stromy výrazů, které představují výrazy <xref:System.Linq.Expressions.LambdaExpression> <xref:System.Linq.Expressions.Expression%601>lambda, jsou typu nebo . Chcete-li spustit tyto <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> stromy výrazů, zavolejte metodu k vytvoření spustitelného delegáta a potom vyvolat delegáta.  
  
> [!NOTE]
> Pokud typ delegáta není znám, to znamená, že výraz <xref:System.Linq.Expressions.LambdaExpression> lambda je typu a nikoli <xref:System.Linq.Expressions.Expression%601>, musíte volat metodu <xref:System.Delegate.DynamicInvoke%2A> delegáta namísto jeho přímého vyvolání.  
  
 Pokud strom výrazu nepředstavuje výraz lambda, můžete vytvořit nový výraz lambda, který má jako <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> své tělo původní strom výrazů, voláním metody. Potom můžete spustit výraz lambda, jak je popsáno výše v této části.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak spustit strom výrazu, který představuje zvýšení číslo k mocní vytvořením výrazu lambda a jeho spuštěním. Zobrazí se výsledek, který představuje číslo umocněné k napájení.  
  
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
  
- Zahrňte obor názvů System.Linq.Expressions.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](./index.md)
- [Jak upravit stromy výrazů (C#)](./how-to-modify-expression-trees.md)
