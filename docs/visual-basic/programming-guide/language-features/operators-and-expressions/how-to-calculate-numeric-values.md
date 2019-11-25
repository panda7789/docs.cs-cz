---
title: 'Postupy: Výpočet numerických hodnot'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348971"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="4b4e1-102">Postupy: Výpočet numerických hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b4e1-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="4b4e1-103">You can calculate numeric values through the use of numeric expressions.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="4b4e1-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="4b4e1-105">Calculating Numeric Values</span><span class="sxs-lookup"><span data-stu-id="4b4e1-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="4b4e1-106">To calculate a numeric value</span><span class="sxs-lookup"><span data-stu-id="4b4e1-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="4b4e1-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="4b4e1-108">The following example shows some valid numeric expressions.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="4b4e1-109">The first three lines show a literal, a constant, and a variable.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="4b4e1-110">Each one forms a valid numeric expression by itself.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="4b4e1-111">The final line shows a combination of a variable with two literals.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="4b4e1-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="4b4e1-113">You must use the expression as part of a complete statement.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="4b4e1-114">To store a numeric value</span><span class="sxs-lookup"><span data-stu-id="4b4e1-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="4b4e1-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="4b4e1-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="4b4e1-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b4e1-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="4b4e1-118">Multiple Operators</span><span class="sxs-lookup"><span data-stu-id="4b4e1-118">Multiple Operators</span></span>  
 <span data-ttu-id="4b4e1-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="4b4e1-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="4b4e1-121">To override normal operator precedence</span><span class="sxs-lookup"><span data-stu-id="4b4e1-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="4b4e1-122">Use parentheses to enclose the operations you want to be performed first.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="4b4e1-123">The following example shows two different results with the same operands and operators.</span><span class="sxs-lookup"><span data-stu-id="4b4e1-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="4b4e1-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span><span class="sxs-lookup"><span data-stu-id="4b4e1-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="4b4e1-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="4b4e1-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="4b4e1-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="4b4e1-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b4e1-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b4e1-127">See also</span></span>

- [<span data-ttu-id="4b4e1-128">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="4b4e1-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="4b4e1-129">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="4b4e1-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="4b4e1-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="4b4e1-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="4b4e1-131">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b4e1-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4b4e1-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="4b4e1-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="4b4e1-133">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="4b4e1-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
