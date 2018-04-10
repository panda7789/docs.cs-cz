---
title: = – operátor (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="4ede8-102">= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ede8-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="4ede8-103">Přiřazuje hodnotu proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4ede8-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ede8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ede8-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="4ede8-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4ede8-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="4ede8-106">Všechny zapisovatelné proměnné nebo libovolné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4ede8-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="4ede8-107">Všechny literál, konstanta nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="4ede8-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ede8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ede8-108">Remarks</span></span>  
 <span data-ttu-id="4ede8-109">Element na levé straně znaménkem rovnosti (`=`) může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="4ede8-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="4ede8-110">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="4ede8-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="4ede8-111">`=` Operátor přiřadí hodnota v jeho pravé proměnnou nebo vlastnost na levé straně.</span><span class="sxs-lookup"><span data-stu-id="4ede8-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ede8-112">`=` Operátor slouží také jako operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="4ede8-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="4ede8-113">Podrobnosti najdete v tématu [operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4ede8-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4ede8-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="4ede8-114">Overloading</span></span>  
 <span data-ttu-id="4ede8-115">`=` Operátor může být přetížené pouze jako operátor porovnání relační, ne jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4ede8-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="4ede8-116">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4ede8-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ede8-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ede8-117">Example</span></span>  
 <span data-ttu-id="4ede8-118">Následující příklad ukazuje operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4ede8-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="4ede8-119">Hodnota na pravé straně je přiřazena k proměnné na levé straně.</span><span class="sxs-lookup"><span data-stu-id="4ede8-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4ede8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ede8-120">See Also</span></span>  
 [<span data-ttu-id="4ede8-121">& = – operátor</span><span class="sxs-lookup"><span data-stu-id="4ede8-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="4ede8-122">\* = – Operátor</span><span class="sxs-lookup"><span data-stu-id="4ede8-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="4ede8-123">+= – Operátor</span><span class="sxs-lookup"><span data-stu-id="4ede8-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="4ede8-124">-= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ede8-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="4ede8-125">/ = – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ede8-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="4ede8-126">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="4ede8-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="4ede8-127">^ = – Operátor</span><span class="sxs-lookup"><span data-stu-id="4ede8-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="4ede8-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="4ede8-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="4ede8-129">Operátory porovnávání</span><span class="sxs-lookup"><span data-stu-id="4ede8-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="4ede8-130">Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4ede8-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="4ede8-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="4ede8-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
