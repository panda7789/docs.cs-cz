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
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="82edd-103">Spuštění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="82edd-103">How to execute expression trees (C#)</span></span>
<span data-ttu-id="82edd-104">V tomto tématu se dozvíte, jak spustit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="82edd-104">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="82edd-105">Provádění stromu výrazů může vracet hodnotu nebo může provést pouze akci, jako je například volání metody.</span><span class="sxs-lookup"><span data-stu-id="82edd-105">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="82edd-106">Spustit lze pouze stromy výrazů, které reprezentují výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="82edd-106">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="82edd-107">Stromy výrazů, které představují výrazy lambda, jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="82edd-107">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="82edd-108">Chcete-li spustit tyto stromy výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření spustitelného delegáta a poté vyvolejte delegáta.</span><span class="sxs-lookup"><span data-stu-id="82edd-108">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82edd-109">Pokud typ delegáta není znám, to znamená, že výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a nikoli <xref:System.Linq.Expressions.Expression%601> , je nutné zavolat <xref:System.Delegate.DynamicInvoke%2A> metodu na delegáta místo přímého vyvolání.</span><span class="sxs-lookup"><span data-stu-id="82edd-109">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="82edd-110">Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má jako tělo původní strom výrazu, voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="82edd-110">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="82edd-111">Potom můžete spustit výraz lambda, jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="82edd-111">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82edd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="82edd-112">Example</span></span>  
 <span data-ttu-id="82edd-113">Následující příklad kódu ukazuje, jak spustit strom výrazu, který představuje zvýšení čísla na výkon vytvořením lambda výrazu a jeho provedením.</span><span class="sxs-lookup"><span data-stu-id="82edd-113">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="82edd-114">Zobrazí se výsledek, který představuje číslo umocněné na výkon.</span><span class="sxs-lookup"><span data-stu-id="82edd-114">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="82edd-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="82edd-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="82edd-116">Zahrňte obor názvů System. Linq. Expressions.</span><span class="sxs-lookup"><span data-stu-id="82edd-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82edd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="82edd-117">See also</span></span>

- [<span data-ttu-id="82edd-118">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="82edd-118">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="82edd-119">Postup úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="82edd-119">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
