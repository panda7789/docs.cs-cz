---
title: Operátor \= (Visual Basic)
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
ms.openlocfilehash: d7b4a6946cc38984272a6b63e14e8c1db2825a5e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700670"
---
# <a name="-operator"></a><span data-ttu-id="8e45c-102">\\ = – operátor</span><span class="sxs-lookup"><span data-stu-id="8e45c-102">\\= Operator</span></span>
<span data-ttu-id="8e45c-103">Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí celočíselný výsledek proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8e45c-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e45c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e45c-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8e45c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8e45c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8e45c-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8e45c-106">Required.</span></span> <span data-ttu-id="8e45c-107">Jakákoli číselná proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8e45c-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8e45c-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8e45c-108">Required.</span></span> <span data-ttu-id="8e45c-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="8e45c-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e45c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e45c-110">Remarks</span></span>  
 <span data-ttu-id="8e45c-111">Element na levé straně operátoru `\=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="8e45c-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8e45c-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8e45c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8e45c-113">Operátor `\=` rozděluje hodnotu proměnné nebo vlastnosti nalevo od hodnoty vpravo a přiřadí celočíselný výsledek proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="8e45c-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="8e45c-114">Další informace o celočíselném dělení naleznete v tématu [operátor \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8e45c-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8e45c-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="8e45c-115">Overloading</span></span>  
 <span data-ttu-id="8e45c-116">Operátor `\` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8e45c-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8e45c-117">Přetížení operátoru `\` má vliv na chování operátoru `\=`.</span><span class="sxs-lookup"><span data-stu-id="8e45c-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="8e45c-118">Pokud váš kód používá `\=` na třídě nebo struktuře, která přetěžuje `\`, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="8e45c-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8e45c-119">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8e45c-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e45c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e45c-120">Example</span></span>  
 <span data-ttu-id="8e45c-121">Následující příklad používá operátor `\=` k rozdělení jedné proměnné `Integer` o sekundu a přiřazení celého výsledku k první proměnné.</span><span class="sxs-lookup"><span data-stu-id="8e45c-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="8e45c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e45c-122">See also</span></span>

- [<span data-ttu-id="8e45c-123">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e45c-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="8e45c-124">/= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e45c-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="8e45c-125">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="8e45c-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8e45c-126">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="8e45c-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="8e45c-127">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e45c-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8e45c-128">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="8e45c-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8e45c-129">Příkazy</span><span class="sxs-lookup"><span data-stu-id="8e45c-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
