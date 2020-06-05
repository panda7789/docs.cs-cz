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
ms.openlocfilehash: 516cb21e02d9fb2cd4b8d72282bb74163e1fb14b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371762"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="39592-102">= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39592-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="39592-103">Přiřadí hodnotu proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="39592-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39592-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39592-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="39592-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="39592-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="39592-106">Jakákoli zapisovatelná proměnná nebo libovolná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="39592-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="39592-107">Libovolný literál, konstanta nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="39592-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39592-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39592-108">Remarks</span></span>  
 <span data-ttu-id="39592-109">Element na levé straně znaménka rovná se ( `=` ) může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="39592-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="39592-110">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="39592-110">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="39592-111">`=`Operátor přiřadí hodnotu přímo k proměnné nebo vlastnosti nalevo.</span><span class="sxs-lookup"><span data-stu-id="39592-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39592-112">`=`Operátor je také použit jako operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="39592-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="39592-113">Podrobnosti naleznete v tématu [operátory porovnání](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="39592-113">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="39592-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="39592-114">Overloading</span></span>  
 <span data-ttu-id="39592-115">`=`Operátor může být přetížen pouze jako relační relační operátor, nikoli jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="39592-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="39592-116">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="39592-116">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39592-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="39592-117">Example</span></span>  
 <span data-ttu-id="39592-118">Následující příklad ukazuje operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="39592-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="39592-119">Hodnota na pravé straně je přiřazena k proměnné na levé straně.</span><span class="sxs-lookup"><span data-stu-id="39592-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="39592-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="39592-120">See also</span></span>

- [<span data-ttu-id="39592-121">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="39592-121">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="39592-122">\* = – Operátor</span><span class="sxs-lookup"><span data-stu-id="39592-122">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="39592-123">+ = – Operátor</span><span class="sxs-lookup"><span data-stu-id="39592-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="39592-124">-= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39592-124">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="39592-125">/= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39592-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="39592-126">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="39592-126">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="39592-127">^ = – Operátor</span><span class="sxs-lookup"><span data-stu-id="39592-127">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="39592-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="39592-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="39592-129">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="39592-129">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="39592-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="39592-130">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="39592-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="39592-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
