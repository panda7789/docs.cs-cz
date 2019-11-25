---
title: = – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350203"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f77a3-102">= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f77a3-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="f77a3-103">Assigns a value to a variable or property.</span><span class="sxs-lookup"><span data-stu-id="f77a3-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f77a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f77a3-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="f77a3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f77a3-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f77a3-106">Any writable variable or any property.</span><span class="sxs-lookup"><span data-stu-id="f77a3-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="f77a3-107">Any literal, constant, or expression.</span><span class="sxs-lookup"><span data-stu-id="f77a3-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f77a3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f77a3-108">Remarks</span></span>  
 <span data-ttu-id="f77a3-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="f77a3-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f77a3-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f77a3-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="f77a3-111">The `=` operator assigns the value on its right to the variable or property on its left.</span><span class="sxs-lookup"><span data-stu-id="f77a3-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f77a3-112">The `=` operator is also used as a comparison operator.</span><span class="sxs-lookup"><span data-stu-id="f77a3-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="f77a3-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f77a3-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f77a3-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="f77a3-114">Overloading</span></span>  
 <span data-ttu-id="f77a3-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span><span class="sxs-lookup"><span data-stu-id="f77a3-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="f77a3-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f77a3-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f77a3-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f77a3-117">Example</span></span>  
 <span data-ttu-id="f77a3-118">The following example demonstrates the assignment operator.</span><span class="sxs-lookup"><span data-stu-id="f77a3-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="f77a3-119">The value on the right is assigned to the variable on the left.</span><span class="sxs-lookup"><span data-stu-id="f77a3-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f77a3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f77a3-120">See also</span></span>

- [<span data-ttu-id="f77a3-121">Operátor &=</span><span class="sxs-lookup"><span data-stu-id="f77a3-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="f77a3-122">Operátor \*=</span><span class="sxs-lookup"><span data-stu-id="f77a3-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="f77a3-123">Operátor +=</span><span class="sxs-lookup"><span data-stu-id="f77a3-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="f77a3-124">-= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f77a3-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="f77a3-125">/= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f77a3-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="f77a3-126">\\= Operator</span><span class="sxs-lookup"><span data-stu-id="f77a3-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="f77a3-127">Operátor ^=</span><span class="sxs-lookup"><span data-stu-id="f77a3-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="f77a3-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="f77a3-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="f77a3-129">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="f77a3-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="f77a3-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="f77a3-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="f77a3-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="f77a3-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
