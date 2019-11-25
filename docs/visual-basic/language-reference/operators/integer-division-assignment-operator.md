---
title: '\= – operátor'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 600acf9b41b63358da245fe602595fee4093b15b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330947"
---
# <a name="-operator"></a><span data-ttu-id="f70ad-102">\\= Operator</span><span class="sxs-lookup"><span data-stu-id="f70ad-102">\\= Operator</span></span>
<span data-ttu-id="f70ad-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="f70ad-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f70ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f70ad-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f70ad-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f70ad-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f70ad-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f70ad-106">Required.</span></span> <span data-ttu-id="f70ad-107">Any numeric variable or property.</span><span class="sxs-lookup"><span data-stu-id="f70ad-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="f70ad-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f70ad-108">Required.</span></span> <span data-ttu-id="f70ad-109">Any numeric expression.</span><span class="sxs-lookup"><span data-stu-id="f70ad-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f70ad-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f70ad-110">Remarks</span></span>  
 <span data-ttu-id="f70ad-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="f70ad-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f70ad-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f70ad-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="f70ad-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span><span class="sxs-lookup"><span data-stu-id="f70ad-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="f70ad-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f70ad-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f70ad-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="f70ad-115">Overloading</span></span>  
 <span data-ttu-id="f70ad-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="f70ad-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f70ad-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span><span class="sxs-lookup"><span data-stu-id="f70ad-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="f70ad-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="f70ad-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f70ad-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f70ad-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f70ad-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="f70ad-120">Example</span></span>  
 <span data-ttu-id="f70ad-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span><span class="sxs-lookup"><span data-stu-id="f70ad-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="f70ad-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f70ad-122">See also</span></span>

- [<span data-ttu-id="f70ad-123">\ Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f70ad-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="f70ad-124">/= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f70ad-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="f70ad-125">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="f70ad-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="f70ad-126">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="f70ad-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="f70ad-127">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f70ad-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f70ad-128">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="f70ad-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f70ad-129">Příkazy</span><span class="sxs-lookup"><span data-stu-id="f70ad-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
