---
title: "Postupy: provádění stromů výrazů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a13f13659472b7620b6df070815ace1d6fb0de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="4e18e-102">Postupy: provádění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e18e-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="4e18e-103">Toto téma ukazuje, jak provést strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="4e18e-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="4e18e-104">Provádění strom výrazu může vrátit hodnotu nebo ji může provádět jenom akce, jako při volání metody.</span><span class="sxs-lookup"><span data-stu-id="4e18e-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="4e18e-105">Můžete provést pouze stromů výrazů, které představují výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="4e18e-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="4e18e-106">Stromy výrazů, které představují lambda – výrazy jsou typu <xref:System.Linq.Expressions.LambdaExpression> nebo <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="4e18e-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="4e18e-107">Chcete-li provést tyto stromů výrazů, volejte <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodu pro vytvoření delegáta spustitelný soubor a pak vyvolejte delegát.</span><span class="sxs-lookup"><span data-stu-id="4e18e-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e18e-108">Pokud je typ delegát není znám, výrazu lambda je typu <xref:System.Linq.Expressions.LambdaExpression> a není <xref:System.Linq.Expressions.Expression%601>, musí volat <xref:System.Delegate.DynamicInvoke%2A> metodu delegáta místo vyvolání ji přímo.</span><span class="sxs-lookup"><span data-stu-id="4e18e-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="4e18e-109">Pokud strom výrazu nepředstavuje výrazu lambda, můžete vytvořit nové výrazu lambda, který má původní strom výrazu jako jeho text voláním <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="4e18e-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="4e18e-110">Potom můžete provést výrazu lambda, jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="4e18e-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e18e-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e18e-111">Example</span></span>  
 <span data-ttu-id="4e18e-112">Následující příklad kódu ukazuje, jak provést strom výrazu představující vyvolání čísla na zadanou mocninu. pomocí vytvoření výrazu lambda a její provedení.</span><span class="sxs-lookup"><span data-stu-id="4e18e-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="4e18e-113">Výsledek, který představuje číslo vyvolá exponentem, se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="4e18e-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e18e-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4e18e-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4e18e-115">Přidáte odkaz na projekt na System.Core.dll, pokud se už neodkazuje.</span><span class="sxs-lookup"><span data-stu-id="4e18e-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="4e18e-116">Obor názvů System.Linq.Expressions patří.</span><span class="sxs-lookup"><span data-stu-id="4e18e-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e18e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e18e-117">See Also</span></span>  
 [<span data-ttu-id="4e18e-118">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e18e-118">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="4e18e-119">Postupy: úpravy stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e18e-119">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
