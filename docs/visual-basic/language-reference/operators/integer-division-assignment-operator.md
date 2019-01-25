---
title: '\= – Operátor (Visual Basic)'
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
ms.openlocfilehash: 8985fb081443d931be3210c81099d510e2da057d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491893"
---
# <a name="-operator"></a><span data-ttu-id="bf5a4-102">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="bf5a4-102">\\= Operator</span></span>
<span data-ttu-id="bf5a4-103">Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí proměnné nebo vlastnosti výsledku celého čísla.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf5a4-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="bf5a4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bf5a4-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="bf5a4-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-106">Required.</span></span> <span data-ttu-id="bf5a4-107">Všechny číselné proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="bf5a4-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-108">Required.</span></span> <span data-ttu-id="bf5a4-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf5a4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf5a4-110">Remarks</span></span>  
 <span data-ttu-id="bf5a4-111">Element na levé straně `\=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bf5a4-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a4-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="bf5a4-113">`\=` Operátor vydělí hodnotu proměnné nebo vlastnosti na levé straně hodnotou napravo a přiřadí proměnné nebo vlastnosti na levé straně celé číslo výsledku</span><span class="sxs-lookup"><span data-stu-id="bf5a4-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="bf5a4-114">Další informace o dělení celého čísla, naleznete v tématu [\ – operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a4-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bf5a4-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="bf5a4-115">Overloading</span></span>  
 <span data-ttu-id="bf5a4-116">`\` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bf5a4-117">Přetížení `\` operátor má vliv na chování `\=` operátor.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="bf5a4-118">Pokud váš kód používá `\=` v třídě nebo struktuře, která přetížení `\`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bf5a4-119">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a4-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf5a4-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf5a4-120">Example</span></span>  
 <span data-ttu-id="bf5a4-121">V následujícím příkladu `\=` operátor rozdělit jeden `Integer` proměnné tak, že druhé a přiřadit na celé číslo. následkem toho se první proměnné.</span><span class="sxs-lookup"><span data-stu-id="bf5a4-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bf5a4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf5a4-122">See also</span></span>
- [<span data-ttu-id="bf5a4-123">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf5a4-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="bf5a4-124">/ = – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf5a4-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="bf5a4-125">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="bf5a4-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="bf5a4-126">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="bf5a4-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="bf5a4-127">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf5a4-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bf5a4-128">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="bf5a4-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="bf5a4-129">Příkazy</span><span class="sxs-lookup"><span data-stu-id="bf5a4-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
