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
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="534b6-102">Postupy: spouštění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="534b6-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="534b6-103">V tomto tématu se dozvíte, jak spustit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="534b6-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="534b6-104">Provádění stromu výrazů může vracet hodnotu nebo může provést pouze akci, jako je například volání metody.</span><span class="sxs-lookup"><span data-stu-id="534b6-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="534b6-105">Spustit lze pouze stromy výrazů, které reprezentují výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="534b6-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="534b6-106">Stromy výrazů, které představují výrazy lambda, jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="534b6-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="534b6-107">Chcete-li spustit tyto stromy výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření spustitelného delegáta a poté vyvolejte delegáta.</span><span class="sxs-lookup"><span data-stu-id="534b6-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="534b6-108">Pokud typ delegáta není znám, to znamená, že výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a nikoli <xref:System.Linq.Expressions.Expression%601> , je nutné zavolat <xref:System.Delegate.DynamicInvoke%2A> metodu na delegáta místo přímého vyvolání.</span><span class="sxs-lookup"><span data-stu-id="534b6-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="534b6-109">Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má jako tělo původní strom výrazu, voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="534b6-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="534b6-110">Potom můžete spustit výraz lambda, jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="534b6-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="534b6-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="534b6-111">Example</span></span>  
 <span data-ttu-id="534b6-112">Následující příklad kódu ukazuje, jak spustit strom výrazu, který představuje zvýšení čísla na výkon vytvořením lambda výrazu a jeho provedením.</span><span class="sxs-lookup"><span data-stu-id="534b6-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="534b6-113">Zobrazí se výsledek, který představuje číslo umocněné na výkon.</span><span class="sxs-lookup"><span data-stu-id="534b6-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compile-the-code"></a><span data-ttu-id="534b6-114">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="534b6-114">Compile the code</span></span>  
  
- <span data-ttu-id="534b6-115">Zahrňte obor názvů System. Linq. Expressions.</span><span class="sxs-lookup"><span data-stu-id="534b6-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534b6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="534b6-116">See also</span></span>

- [<span data-ttu-id="534b6-117">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="534b6-117">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="534b6-118">Postupy: Změna stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="534b6-118">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
