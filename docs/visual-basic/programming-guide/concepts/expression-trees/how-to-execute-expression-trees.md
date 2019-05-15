---
title: 'Postupy: Provádění stromů výrazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 62d3febf7090c6662e5593bbaf94c04236a162e9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592138"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="c766f-102">Postupy: Provádění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c766f-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="c766f-103">Toto téma ukazuje, jak spustit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="c766f-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="c766f-104">Provádění strom výrazu může vracet hodnotu, nebo ji může provádět jenom akce, jako je volání metody.</span><span class="sxs-lookup"><span data-stu-id="c766f-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="c766f-105">Je možné provést pouze stromů výrazů, které představují výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="c766f-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="c766f-106">Stromy výrazů, které představují lambda výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="c766f-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="c766f-107">K provádění těchto stromů výrazů, zavolejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metody k vytvoření delegáta spustitelný soubor a pak vyvolejte delegáta.</span><span class="sxs-lookup"><span data-stu-id="c766f-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c766f-108">Pokud je typ delegáta není znám, to znamená, výraz lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a ne <xref:System.Linq.Expressions.Expression%601>, je třeba zavolat <xref:System.Delegate.DynamicInvoke%2A> metoda delegátu namísto vyvolání přímo.</span><span class="sxs-lookup"><span data-stu-id="c766f-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="c766f-109">Pokud strom výrazu lambda výraz nepředstavuje, můžete vytvořit nový výraz lambda, který má původní stromu výrazů jako jeho textu pomocí volání <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="c766f-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="c766f-110">Pak můžete spustit výraz lambda, jak bylo popsáno dříve v této části.</span><span class="sxs-lookup"><span data-stu-id="c766f-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c766f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c766f-111">Example</span></span>  
 <span data-ttu-id="c766f-112">Následující příklad kódu ukazuje, jak provést strom výrazů, který představuje číslo mocninu vyvolání pomocí vytvoření výrazu lambda a spustíte ji.</span><span class="sxs-lookup"><span data-stu-id="c766f-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="c766f-113">Výsledek, který představuje číslo vyvolána k elektrické energie, se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="c766f-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c766f-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c766f-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="c766f-115">Zahrnout System.Linq.Expressions oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c766f-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c766f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c766f-116">See also</span></span>

- [<span data-ttu-id="c766f-117">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c766f-117">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="c766f-118">Postupy: Úpravy stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c766f-118">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
