---
title: ^= – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 571ef26eb188d9044ec8f6c8e6e4b490780f17a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603493"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e9823-102">^= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9823-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="e9823-103">Vyvolá hodnoty proměnné nebo vlastnost exponentem výrazu a přiřadí výsledek zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e9823-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9823-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9823-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e9823-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e9823-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e9823-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e9823-106">Required.</span></span> <span data-ttu-id="e9823-107">Číselné proměnné nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e9823-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e9823-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e9823-108">Required.</span></span> <span data-ttu-id="e9823-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="e9823-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9823-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9823-110">Remarks</span></span>  
 <span data-ttu-id="e9823-111">Element na levé straně `^=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="e9823-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e9823-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="e9823-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e9823-113">`^=` Operátor nejprve vyvolá hodnota proměnné nebo vlastnosti (na levé straně operátoru) exponentem hodnotu výrazu (na pravé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="e9823-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="e9823-114">Operátor poté přiřadí výsledek této operace zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e9823-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="e9823-115">Visual Basic vždy provede exponenciální zápis v [dvojitý datový typ](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e9823-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="e9823-116">Operandy žádné jiného typu se převedou na `Double`, a výsledek je vždy `Double`.</span><span class="sxs-lookup"><span data-stu-id="e9823-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="e9823-117">Hodnota `expression` může být zlomkové záporné nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="e9823-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e9823-118">Přetížení</span><span class="sxs-lookup"><span data-stu-id="e9823-118">Overloading</span></span>  
 <span data-ttu-id="e9823-119">[^ – Operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="e9823-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e9823-120">Přetížení `^` operátor má vliv na chování `^=` operátor.</span><span class="sxs-lookup"><span data-stu-id="e9823-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="e9823-121">Pokud váš kód používá `^=` na třídu nebo strukturu, která přetížení `^`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="e9823-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e9823-122">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e9823-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9823-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9823-123">Example</span></span>  
 <span data-ttu-id="e9823-124">Následující příklad používá `^=` operátor umožňuje aktivovat hodnota jednoho `Integer` proměnné exponentem druhý proměnné a přiřazení výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="e9823-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e9823-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9823-125">See Also</span></span>  
 [<span data-ttu-id="e9823-126">^ – operátor</span><span class="sxs-lookup"><span data-stu-id="e9823-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [<span data-ttu-id="e9823-127">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="e9823-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="e9823-128">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="e9823-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="e9823-129">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9823-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e9823-130">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="e9823-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e9823-131">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e9823-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
