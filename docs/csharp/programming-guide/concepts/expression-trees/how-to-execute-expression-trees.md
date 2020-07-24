---
title: Spuštění stromů výrazů (C#)
description: Naučte se, jak spustit strom výrazu pro vrácení hodnoty nebo provedení akce, jako je volání metody.
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 9e306da545ba6c6275f36b8f6dd4e98bb91ed54e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105620"
---
# <a name="how-to-execute-expression-trees-c"></a>Spuštění stromů výrazů (C#)
V tomto tématu se dozvíte, jak spustit strom výrazu. Provádění stromu výrazů může vracet hodnotu nebo může provést pouze akci, jako je například volání metody.  
  
 Spustit lze pouze stromy výrazů, které reprezentují výrazy lambda. Stromy výrazů, které představují výrazy lambda, jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601> . Chcete-li spustit tyto stromy výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření spustitelného delegáta a poté vyvolejte delegáta.  
  
> [!NOTE]
> Pokud typ delegáta není znám, to znamená, že výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a nikoli <xref:System.Linq.Expressions.Expression%601> , je nutné zavolat <xref:System.Delegate.DynamicInvoke%2A> metodu na delegáta místo přímého vyvolání.  
  
 Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má jako tělo původní strom výrazu, voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Potom můžete spustit výraz lambda, jak je popsáno výše v této části.  
  
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
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](./index.md)
- [Postup úpravy stromů výrazů (C#)](./how-to-modify-expression-trees.md)
