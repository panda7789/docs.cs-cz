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
ms.openlocfilehash: ca4c519dd80c07f54dc1c3dfe70daf6948446363
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591844"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9f5b4-102">= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f5b4-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="9f5b4-103">Přiřadí hodnotu proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f5b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f5b4-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="9f5b4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9f5b4-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9f5b4-106">Jakákoli zapisovatelná proměnná nebo libovolná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="9f5b4-107">Libovolný literál, konstanta nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f5b4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f5b4-108">Remarks</span></span>  
 <span data-ttu-id="9f5b4-109">Element na levé straně znaménka rovná se (`=`) může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9f5b4-110">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9f5b4-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="9f5b4-111">Operátor `=` přiřadí hodnotu vpravo k proměnné nebo vlastnosti nalevo.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f5b4-112">Operátor `=` se používá také jako operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="9f5b4-113">Podrobnosti naleznete v tématu [operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9f5b4-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9f5b4-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="9f5b4-114">Overloading</span></span>  
 <span data-ttu-id="9f5b4-115">Operátor `=` může být přetížen pouze jako relační relační operátor, nikoli jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="9f5b4-116">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9f5b4-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f5b4-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f5b4-117">Example</span></span>  
 <span data-ttu-id="9f5b4-118">Následující příklad ukazuje operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="9f5b4-119">Hodnota na pravé straně je přiřazena k proměnné na levé straně.</span><span class="sxs-lookup"><span data-stu-id="9f5b4-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9f5b4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f5b4-120">See also</span></span>

- [<span data-ttu-id="9f5b4-121">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="9f5b4-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="9f5b4-122">\*= – operátor</span><span class="sxs-lookup"><span data-stu-id="9f5b4-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="9f5b4-123">+= – operátor</span><span class="sxs-lookup"><span data-stu-id="9f5b4-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="9f5b4-124">-= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f5b4-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="9f5b4-125">/= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f5b4-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="9f5b4-126">\\ = – operátor</span><span class="sxs-lookup"><span data-stu-id="9f5b4-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="9f5b4-127">^= – operátor</span><span class="sxs-lookup"><span data-stu-id="9f5b4-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="9f5b4-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="9f5b4-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="9f5b4-129">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="9f5b4-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="9f5b4-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="9f5b4-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="9f5b4-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="9f5b4-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
