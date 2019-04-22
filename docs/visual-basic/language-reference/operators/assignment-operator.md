---
title: = – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: ad74e3ebc947af4f36022be838b69df6ce24997a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840286"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c54e6-102">= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c54e6-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="c54e6-103">Přiřadí hodnotu k proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c54e6-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c54e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c54e6-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="c54e6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c54e6-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c54e6-106">Jakékoli zapisovatelné proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c54e6-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="c54e6-107">Všechny literál, konstanta nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="c54e6-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c54e6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c54e6-108">Remarks</span></span>  
 <span data-ttu-id="c54e6-109">Element na levé straně znaménka rovnosti (`=`) může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="c54e6-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c54e6-110">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c54e6-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="c54e6-111">`=` Operátor přiřadí hodnotu napravo na proměnnou nebo vlastnost na levé straně.</span><span class="sxs-lookup"><span data-stu-id="c54e6-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c54e6-112">`=` Operátor slouží také jako operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="c54e6-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="c54e6-113">Podrobnosti najdete v tématu [operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c54e6-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c54e6-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="c54e6-114">Overloading</span></span>  
 <span data-ttu-id="c54e6-115">`=` Operátor může být přetížená pouze jako operátor porovnání relační, nikoli jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c54e6-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="c54e6-116">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c54e6-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c54e6-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c54e6-117">Example</span></span>  
 <span data-ttu-id="c54e6-118">Následující příklad ukazuje operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c54e6-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="c54e6-119">Hodnota na pravé straně je přiřazena k proměnné na levé straně.</span><span class="sxs-lookup"><span data-stu-id="c54e6-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c54e6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c54e6-120">See also</span></span>

- [<span data-ttu-id="c54e6-121">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="c54e6-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="c54e6-122">\*= – operátor</span><span class="sxs-lookup"><span data-stu-id="c54e6-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="c54e6-123">+= – operátor</span><span class="sxs-lookup"><span data-stu-id="c54e6-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="c54e6-124">-= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c54e6-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="c54e6-125">/ = – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c54e6-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="c54e6-126">\\= Operator</span><span class="sxs-lookup"><span data-stu-id="c54e6-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="c54e6-127">^= – operátor</span><span class="sxs-lookup"><span data-stu-id="c54e6-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="c54e6-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="c54e6-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="c54e6-129">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="c54e6-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="c54e6-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c54e6-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="c54e6-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="c54e6-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
