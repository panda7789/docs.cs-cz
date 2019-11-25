---
title: Porovnání hodnot
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346289"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="4a89a-102">Porovnání hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a89a-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="4a89a-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span><span class="sxs-lookup"><span data-stu-id="4a89a-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="4a89a-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span><span class="sxs-lookup"><span data-stu-id="4a89a-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="4a89a-105">Examples of such an expression are as follows.</span><span class="sxs-lookup"><span data-stu-id="4a89a-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="4a89a-106">The first expression evaluates to `True`, because 45 is greater than 26.</span><span class="sxs-lookup"><span data-stu-id="4a89a-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="4a89a-107">The second example evaluates to `False`, because 26 is not greater than 45.</span><span class="sxs-lookup"><span data-stu-id="4a89a-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="4a89a-108">You can also compare numeric expressions in this fashion.</span><span class="sxs-lookup"><span data-stu-id="4a89a-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="4a89a-109">The expressions you compare can themselves be complex expressions, as in the following example.</span><span class="sxs-lookup"><span data-stu-id="4a89a-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="4a89a-110">The preceding complex expression includes literals, variables, and function calls.</span><span class="sxs-lookup"><span data-stu-id="4a89a-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="4a89a-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span><span class="sxs-lookup"><span data-stu-id="4a89a-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="4a89a-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span><span class="sxs-lookup"><span data-stu-id="4a89a-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="4a89a-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span><span class="sxs-lookup"><span data-stu-id="4a89a-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="4a89a-114">The `=` sign is a comparison operator as well as an assignment operator.</span><span class="sxs-lookup"><span data-stu-id="4a89a-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="4a89a-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="4a89a-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="4a89a-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="4a89a-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="4a89a-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="4a89a-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="4a89a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a89a-118">See also</span></span>

- [<span data-ttu-id="4a89a-119">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="4a89a-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="4a89a-120">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="4a89a-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="4a89a-121">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a89a-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="4a89a-122">Postupy: Výpočet numerických hodnot</span><span class="sxs-lookup"><span data-stu-id="4a89a-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="4a89a-123">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a89a-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
