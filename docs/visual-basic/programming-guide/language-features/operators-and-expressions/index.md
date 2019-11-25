---
title: Operátory a výrazy
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: fa410a739be2da8802e76a35068448263ddec1fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343613"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="3cc2b-102">Operátory a výrazy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3cc2b-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="3cc2b-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="3cc2b-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="3cc2b-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="3cc2b-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="3cc2b-107">Types of Operators</span><span class="sxs-lookup"><span data-stu-id="3cc2b-107">Types of Operators</span></span>  
 <span data-ttu-id="3cc2b-108">Visual Basic provides the following types of operators:</span><span class="sxs-lookup"><span data-stu-id="3cc2b-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="3cc2b-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="3cc2b-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="3cc2b-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="3cc2b-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="3cc2b-113">The value elements that are combined with an operator are called *operands* of that operator.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="3cc2b-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="3cc2b-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="3cc2b-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="3cc2b-116">Evaluation of Expressions</span><span class="sxs-lookup"><span data-stu-id="3cc2b-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="3cc2b-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="3cc2b-118">The following are examples of expressions.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="3cc2b-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="3cc2b-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="3cc2b-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span><span class="sxs-lookup"><span data-stu-id="3cc2b-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3cc2b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cc2b-122">See also</span></span>

- [<span data-ttu-id="3cc2b-123">Operátory</span><span class="sxs-lookup"><span data-stu-id="3cc2b-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="3cc2b-124">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="3cc2b-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="3cc2b-125">Příkazy</span><span class="sxs-lookup"><span data-stu-id="3cc2b-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
