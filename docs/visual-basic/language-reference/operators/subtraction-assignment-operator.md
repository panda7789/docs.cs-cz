---
title: -= – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: be1ff4f10f6b30d8448d2441ee3ad2c1e2f80e2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013488"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="c27e7-102">-= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c27e7-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="c27e7-103">Odečte hodnotu výrazu od hodnoty proměnnou nebo vlastnost a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c27e7-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c27e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c27e7-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c27e7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c27e7-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c27e7-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c27e7-106">Required.</span></span> <span data-ttu-id="c27e7-107">Všechny číselné proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c27e7-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="c27e7-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c27e7-108">Required.</span></span> <span data-ttu-id="c27e7-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="c27e7-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c27e7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c27e7-110">Remarks</span></span>  
 <span data-ttu-id="c27e7-111">Element na levé straně `-=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="c27e7-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c27e7-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c27e7-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="c27e7-113">`-=` Operátor nejprve odečte hodnotu výrazu (na pravé straně operátoru) hodnotu proměnné nebo vlastnosti (na levé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="c27e7-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="c27e7-114">Operátor, který se pak přiřadí výsledek této operace na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c27e7-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c27e7-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="c27e7-115">Overloading</span></span>  
 <span data-ttu-id="c27e7-116">[-– Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="c27e7-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c27e7-117">Přetížení `-` operátor má vliv na chování `-=` operátor.</span><span class="sxs-lookup"><span data-stu-id="c27e7-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="c27e7-118">Pokud váš kód používá `-=` v třídě nebo struktuře, která přetížení `-`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="c27e7-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c27e7-119">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c27e7-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c27e7-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="c27e7-120">Example</span></span>  
 <span data-ttu-id="c27e7-121">V následujícím příkladu `-=` operátor odečíst jeden `Integer` proměnné z jiného a přiřadit výsledek, který má tato proměnná.</span><span class="sxs-lookup"><span data-stu-id="c27e7-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c27e7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c27e7-122">See also</span></span>

- [<span data-ttu-id="c27e7-123">-– Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c27e7-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="c27e7-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="c27e7-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="c27e7-125">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="c27e7-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="c27e7-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c27e7-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c27e7-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="c27e7-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c27e7-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="c27e7-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
