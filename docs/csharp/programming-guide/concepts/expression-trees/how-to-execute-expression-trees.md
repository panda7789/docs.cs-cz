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
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="85b33-102">Postupy: provádění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="85b33-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="85b33-103">Toto téma ukazuje, jak provést strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="85b33-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="85b33-104">Provádění strom výrazu může vrátit hodnotu nebo ji může provádět jenom akce, jako při volání metody.</span><span class="sxs-lookup"><span data-stu-id="85b33-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="85b33-105">Můžete provést pouze stromů výrazů, které představují výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="85b33-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="85b33-106">Stromy výrazů, které představují lambda – výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="85b33-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="85b33-107">Chcete-li provést tyto stromů výrazů, volejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření delegáta spustitelný soubor a pak vyvolejte delegát.</span><span class="sxs-lookup"><span data-stu-id="85b33-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85b33-108">Pokud je typ delegát není znám, výrazu lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a není <xref:System.Linq.Expressions.Expression%601>, musí volat <xref:System.Delegate.DynamicInvoke%2A> metodu delegáta místo vyvolání ji přímo.</span><span class="sxs-lookup"><span data-stu-id="85b33-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="85b33-109">Pokud strom výrazu nepředstavuje výrazu lambda, můžete vytvořit nové výrazu lambda, který má původní strom výrazu jako jeho text voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="85b33-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="85b33-110">Potom můžete provést výrazu lambda, jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="85b33-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85b33-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="85b33-111">Example</span></span>  
 <span data-ttu-id="85b33-112">Následující příklad kódu ukazuje, jak provést strom výrazu představující vyvolání čísla na zadanou mocninu. pomocí vytvoření výrazu lambda a její provedení.</span><span class="sxs-lookup"><span data-stu-id="85b33-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="85b33-113">Výsledek, který představuje číslo vyvolá exponentem, se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="85b33-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="85b33-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="85b33-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="85b33-115">Přidáte odkaz na projekt na System.Core.dll, pokud se už neodkazuje.</span><span class="sxs-lookup"><span data-stu-id="85b33-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="85b33-116">Obor názvů System.Linq.Expressions patří.</span><span class="sxs-lookup"><span data-stu-id="85b33-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b33-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="85b33-117">See Also</span></span>  
 [<span data-ttu-id="85b33-118">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="85b33-118">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="85b33-119">Postupy: úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="85b33-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
