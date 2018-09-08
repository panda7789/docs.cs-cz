---
title: 'Postupy: provádění stromů výrazů (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 2aad970946e417d623907c9f832e2c6e29eef912
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192519"
---
# <a name="how-to-execute-expression-trees-c"></a>Postupy: provádění stromů výrazů (C#)
Toto téma ukazuje, jak spustit strom výrazu. Provádění strom výrazu může vracet hodnotu, nebo ji může provádět jenom akce, jako je volání metody.  
  
 Je možné provést pouze stromů výrazů, které představují výrazů lambda. Stromy výrazů, které představují lambda výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>. K provádění těchto stromů výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metody k vytvoření delegáta spustitelný soubor a pak vyvolejte delegáta.  
  
> [!NOTE]
>  Pokud je typ delegáta není znám, to znamená, výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a ne <xref:System.Linq.Expressions.Expression%601>, je třeba zavolat <xref:System.Delegate.DynamicInvoke%2A> metoda delegátu namísto vyvolání přímo.  
  
 Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má původní stromu výrazů jako jeho textu pomocí volání <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Pak můžete spustit výraz lambda, jak bylo popsáno dříve v této části.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak provést strom výrazů, který představuje číslo mocninu vyvolání pomocí vytvoření výrazu lambda a spustíte ji. Výsledek, který představuje číslo vyvolána k elektrické energie, se zobrazí.  
  
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
  
-   Pokud se už neodkazuje, přidejte odkaz na System.Core.dll.  
  
-   Zahrnout System.Linq.Expressions oboru názvů.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [Postupy: úpravy stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
