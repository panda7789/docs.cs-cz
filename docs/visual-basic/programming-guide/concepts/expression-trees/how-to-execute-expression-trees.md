---
title: 'Postupy: Provádění stromů výrazů'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 82801728596449869e5124c3fc92c9c0673f5dd9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332982"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="0c69d-102">How to: Execute Expression Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c69d-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="0c69d-103">This topic shows you how to execute an expression tree.</span><span class="sxs-lookup"><span data-stu-id="0c69d-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="0c69d-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span><span class="sxs-lookup"><span data-stu-id="0c69d-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="0c69d-105">Only expression trees that represent lambda expressions can be executed.</span><span class="sxs-lookup"><span data-stu-id="0c69d-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="0c69d-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="0c69d-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="0c69d-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span><span class="sxs-lookup"><span data-stu-id="0c69d-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c69d-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span><span class="sxs-lookup"><span data-stu-id="0c69d-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="0c69d-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span><span class="sxs-lookup"><span data-stu-id="0c69d-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="0c69d-110">Then, you can execute the lambda expression as described earlier in this section.</span><span class="sxs-lookup"><span data-stu-id="0c69d-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c69d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c69d-111">Example</span></span>  
 <span data-ttu-id="0c69d-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span><span class="sxs-lookup"><span data-stu-id="0c69d-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="0c69d-113">The result, which represents the number raised to the power, is displayed.</span><span class="sxs-lookup"><span data-stu-id="0c69d-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c69d-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0c69d-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="0c69d-115">Include the System.Linq.Expressions namespace.</span><span class="sxs-lookup"><span data-stu-id="0c69d-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c69d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c69d-116">See also</span></span>

- [<span data-ttu-id="0c69d-117">Expression Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c69d-117">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="0c69d-118">How to: Modify Expression Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c69d-118">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
