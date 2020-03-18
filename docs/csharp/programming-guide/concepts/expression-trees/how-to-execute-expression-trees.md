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
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="f6796-102">Jak spustit stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="f6796-102">How to execute expression trees (C#)</span></span>
<span data-ttu-id="f6796-103">Toto téma ukazuje, jak spustit strom výrazů.</span><span class="sxs-lookup"><span data-stu-id="f6796-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="f6796-104">Spuštění stromu výrazmůže vrátit hodnotu nebo může pouze provést akci, jako je například volání metody.</span><span class="sxs-lookup"><span data-stu-id="f6796-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="f6796-105">Mohou být spuštěny pouze stromy výrazů, které představují výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="f6796-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="f6796-106">Stromy výrazů, které představují výrazy <xref:System.Linq.Expressions.LambdaExpression> <xref:System.Linq.Expressions.Expression%601>lambda, jsou typu nebo .</span><span class="sxs-lookup"><span data-stu-id="f6796-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="f6796-107">Chcete-li spustit tyto <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> stromy výrazů, zavolejte metodu k vytvoření spustitelného delegáta a potom vyvolat delegáta.</span><span class="sxs-lookup"><span data-stu-id="f6796-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6796-108">Pokud typ delegáta není znám, to znamená, že výraz <xref:System.Linq.Expressions.LambdaExpression> lambda je typu a nikoli <xref:System.Linq.Expressions.Expression%601>, musíte volat metodu <xref:System.Delegate.DynamicInvoke%2A> delegáta namísto jeho přímého vyvolání.</span><span class="sxs-lookup"><span data-stu-id="f6796-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="f6796-109">Pokud strom výrazu nepředstavuje výraz lambda, můžete vytvořit nový výraz lambda, který má jako <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> své tělo původní strom výrazů, voláním metody.</span><span class="sxs-lookup"><span data-stu-id="f6796-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="f6796-110">Potom můžete spustit výraz lambda, jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="f6796-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6796-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6796-111">Example</span></span>  
 <span data-ttu-id="f6796-112">Následující příklad kódu ukazuje, jak spustit strom výrazu, který představuje zvýšení číslo k mocní vytvořením výrazu lambda a jeho spuštěním.</span><span class="sxs-lookup"><span data-stu-id="f6796-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="f6796-113">Zobrazí se výsledek, který představuje číslo umocněné k napájení.</span><span class="sxs-lookup"><span data-stu-id="f6796-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6796-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f6796-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="f6796-115">Zahrňte obor názvů System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="f6796-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6796-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6796-116">See also</span></span>

- [<span data-ttu-id="f6796-117">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="f6796-117">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="f6796-118">Jak upravit stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="f6796-118">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
