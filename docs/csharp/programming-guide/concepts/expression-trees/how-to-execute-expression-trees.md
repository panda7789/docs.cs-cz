---
title: "Postupy: provádění stromů výrazů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9a87c9893de2b70c47f0ed78a92adc6bce10db7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-expression-trees-c"></a>Postupy: provádění stromů výrazů (C#)
Toto téma ukazuje, jak provést strom výrazu se nezdařilo. Provádění strom výrazu může vrátit hodnotu nebo ji může provádět jenom akce, jako při volání metody.  
  
 Můžete provést pouze stromů výrazů, které představují výrazy lambda. Stromy výrazů, které představují lambda – výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>. Chcete-li provést tyto stromů výrazů, volejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření delegáta spustitelný soubor a pak vyvolejte delegát.  
  
> [!NOTE]
>  Pokud je typ delegát není znám, výrazu lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a není <xref:System.Linq.Expressions.Expression%601>, musí volat <xref:System.Delegate.DynamicInvoke%2A> metodu delegáta místo vyvolání ji přímo.  
  
 Pokud strom výrazu nepředstavuje výrazu lambda, můžete vytvořit nové výrazu lambda, který má původní strom výrazu jako jeho text voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metoda. Potom můžete provést výrazu lambda, jak je popsáno výše v této části.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak provést strom výrazu představující vyvolání čísla na zadanou mocninu. pomocí vytvoření výrazu lambda a její provedení. Výsledek, který představuje číslo vyvolá exponentem, se zobrazí.  
  
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
  
-   Přidáte odkaz na projekt na System.Core.dll, pokud se už neodkazuje.  
  
-   Obor názvů System.Linq.Expressions patří.  
  
## <a name="see-also"></a>Viz také  
 [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Postupy: úpravy stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
