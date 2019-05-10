---
title: 'Postupy: Provádění stromů výrazů (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 034a391a21e685a6ceb8342bb1738ff34381cebb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598042"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="e7284-102">Postupy: Provádění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e7284-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="e7284-103">Toto téma ukazuje, jak spustit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="e7284-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="e7284-104">Provádění strom výrazu může vracet hodnotu, nebo ji může provádět jenom akce, jako je volání metody.</span><span class="sxs-lookup"><span data-stu-id="e7284-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="e7284-105">Je možné provést pouze stromů výrazů, které představují výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="e7284-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="e7284-106">Stromy výrazů, které představují lambda výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="e7284-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="e7284-107">K provádění těchto stromů výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metody k vytvoření delegáta spustitelný soubor a pak vyvolejte delegáta.</span><span class="sxs-lookup"><span data-stu-id="e7284-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7284-108">Pokud je typ delegáta není znám, to znamená, výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a ne <xref:System.Linq.Expressions.Expression%601>, je třeba zavolat <xref:System.Delegate.DynamicInvoke%2A> metoda delegátu namísto vyvolání přímo.</span><span class="sxs-lookup"><span data-stu-id="e7284-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="e7284-109">Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má původní stromu výrazů jako jeho textu pomocí volání <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="e7284-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="e7284-110">Pak můžete spustit výraz lambda, jak bylo popsáno dříve v této části.</span><span class="sxs-lookup"><span data-stu-id="e7284-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7284-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7284-111">Example</span></span>  
 <span data-ttu-id="e7284-112">Následující příklad kódu ukazuje, jak provést strom výrazů, který představuje číslo mocninu vyvolání pomocí vytvoření výrazu lambda a spustíte ji.</span><span class="sxs-lookup"><span data-stu-id="e7284-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="e7284-113">Výsledek, který představuje číslo vyvolána k elektrické energie, se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="e7284-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7284-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e7284-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="e7284-115">Pokud se už neodkazuje, přidejte odkaz na System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="e7284-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
- <span data-ttu-id="e7284-116">Zahrnout System.Linq.Expressions oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e7284-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7284-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7284-117">See also</span></span>

- [<span data-ttu-id="e7284-118">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e7284-118">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="e7284-119">Postupy: Úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e7284-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
