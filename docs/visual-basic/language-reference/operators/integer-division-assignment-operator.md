---
title: '\= Operátor'
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
ms.openlocfilehash: 4ebbf2eca7fb3cd208d979d7f3c77aa106569119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603558"
---
# <a name="-operator"></a><span data-ttu-id="bf582-102">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="bf582-102">\\= Operator</span></span>
<span data-ttu-id="bf582-103">Vydělí hodnoty proměnné nebo vlastnosti hodnotou výrazu a přiřadí proměnné nebo vlastnosti celé číslo.</span><span class="sxs-lookup"><span data-stu-id="bf582-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf582-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf582-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="bf582-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bf582-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="bf582-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bf582-106">Required.</span></span> <span data-ttu-id="bf582-107">Číselné proměnné nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf582-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="bf582-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bf582-108">Required.</span></span> <span data-ttu-id="bf582-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="bf582-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf582-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf582-110">Remarks</span></span>  
 <span data-ttu-id="bf582-111">Element na levé straně `\=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="bf582-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bf582-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="bf582-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="bf582-113">`\=` Operátor vydělí hodnoty proměnné nebo vlastnosti na levé straně, se hodnota na záhlavím vpravo a přiřadí proměnné nebo vlastnosti na levé straně, celé číslo</span><span class="sxs-lookup"><span data-stu-id="bf582-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="bf582-114">Další informace o dělení celého čísla v tématu [\ – operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bf582-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bf582-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="bf582-115">Overloading</span></span>  
 <span data-ttu-id="bf582-116">`\` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="bf582-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bf582-117">Přetížení `\` operátor má vliv na chování `\=` operátor.</span><span class="sxs-lookup"><span data-stu-id="bf582-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="bf582-118">Pokud váš kód používá `\=` na třídu nebo strukturu, která přetížení `\`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="bf582-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bf582-119">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bf582-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf582-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf582-120">Example</span></span>  
 <span data-ttu-id="bf582-121">Následující příklad používá `\=` operátor rozdělit jednu `Integer` proměnné sekundu a přiřadit na celé číslo vést k první proměnné.</span><span class="sxs-lookup"><span data-stu-id="bf582-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bf582-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf582-122">See Also</span></span>  
 [<span data-ttu-id="bf582-123">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf582-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="bf582-124">/ = – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf582-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="bf582-125">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="bf582-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="bf582-126">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="bf582-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="bf582-127">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf582-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="bf582-128">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="bf582-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="bf582-129">Příkazy</span><span class="sxs-lookup"><span data-stu-id="bf582-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
