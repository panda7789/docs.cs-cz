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
ms.openlocfilehash: fe5d7b3dcb55192167512e0934e09cff7dfddb6d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819646"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bd455-102">^= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd455-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="bd455-103">Vyvolá hodnotu proměnné nebo vlastnosti k elektrické energie výrazu a přiřadí výsledek zpět na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bd455-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd455-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd455-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="bd455-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bd455-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="bd455-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="bd455-106">Required.</span></span> <span data-ttu-id="bd455-107">Všechny číselné proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bd455-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="bd455-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="bd455-108">Required.</span></span> <span data-ttu-id="bd455-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="bd455-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd455-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd455-110">Remarks</span></span>  
 <span data-ttu-id="bd455-111">Element na levé straně `^=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="bd455-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bd455-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="bd455-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="bd455-113">`^=` Nejprve Umocní hodnotu proměnné nebo vlastnosti (na levé straně operátoru) k elektrické energie hodnota výrazu (na pravé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="bd455-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="bd455-114">Operátor, který se pak přiřadí výsledek této operace zpět na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bd455-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="bd455-115">Visual Basic vždy provádí umocnění v [datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="bd455-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="bd455-116">Jakýkoli jiný typ operandy jsou převedeny na `Double`, a výsledek je vždy `Double`.</span><span class="sxs-lookup"><span data-stu-id="bd455-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="bd455-117">Hodnota `expression` může být zlomkové záporné nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="bd455-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bd455-118">Přetížení</span><span class="sxs-lookup"><span data-stu-id="bd455-118">Overloading</span></span>  
 <span data-ttu-id="bd455-119">[^ – Operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="bd455-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bd455-120">Přetížení `^` operátor má vliv na chování `^=` operátor.</span><span class="sxs-lookup"><span data-stu-id="bd455-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="bd455-121">Pokud váš kód používá `^=` v třídě nebo struktuře, která přetížení `^`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="bd455-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bd455-122">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bd455-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd455-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd455-123">Example</span></span>  
 <span data-ttu-id="bd455-124">V následujícím příkladu `^=` operátor zvýšit hodnotu jedné `Integer` proměnné k elektrické energie z druhé proměnné a přiřadit výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd455-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="bd455-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd455-125">See also</span></span>

- [<span data-ttu-id="bd455-126">^ – operátor</span><span class="sxs-lookup"><span data-stu-id="bd455-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="bd455-127">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="bd455-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="bd455-128">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="bd455-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="bd455-129">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd455-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bd455-130">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="bd455-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="bd455-131">Příkazy</span><span class="sxs-lookup"><span data-stu-id="bd455-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
