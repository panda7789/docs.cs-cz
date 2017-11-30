---
title: "/= – operátor [Visual Basic]"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94448856072a949582e64577287134c4b975bfec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1783f-102">/= – operátor [Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="1783f-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="1783f-103">Vydělí hodnoty proměnné nebo vlastnosti hodnotou výrazu a s plovoucí desetinnou čárkou výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1783f-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1783f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1783f-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="1783f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1783f-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1783f-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1783f-106">Required.</span></span> <span data-ttu-id="1783f-107">Číselné proměnné nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1783f-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="1783f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1783f-108">Required.</span></span> <span data-ttu-id="1783f-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="1783f-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1783f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1783f-110">Remarks</span></span>  
 <span data-ttu-id="1783f-111">Element na levé straně `/=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="1783f-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1783f-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="1783f-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1783f-113">`/=` Operátor nejprve vydělí hodnoty proměnné nebo vlastnosti (na levé straně operátoru) hodnotou výrazu (na pravé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="1783f-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="1783f-114">Operátor poté přiřadí proměnné nebo vlastnost s plovoucí desetinnou čárkou výsledek této operace.</span><span class="sxs-lookup"><span data-stu-id="1783f-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="1783f-115">Tento příkaz přiřadí `Double` hodnotu pro proměnnou nebo vlastnost na levé straně.</span><span class="sxs-lookup"><span data-stu-id="1783f-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="1783f-116">Pokud `Option Strict` je `On`, `variableorproperty` musí být `Double`.</span><span class="sxs-lookup"><span data-stu-id="1783f-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="1783f-117">Pokud `Option Strict` je `Off`, Visual Basic provede implicitní převod a přiřadí výslednou hodnotu pro `variableorproperty`, se možná chyba v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1783f-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="1783f-118">Další informace najdete v tématu [Widening a zužující převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1783f-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1783f-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1783f-119">Overloading</span></span>  
 <span data-ttu-id="1783f-120">[/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="1783f-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1783f-121">Přetížení `/` operátor má vliv na chování `/=` operátor.</span><span class="sxs-lookup"><span data-stu-id="1783f-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="1783f-122">Pokud váš kód používá `/=` na třídu nebo strukturu, která přetížení `/`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="1783f-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1783f-123">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1783f-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1783f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="1783f-124">Example</span></span>  
 <span data-ttu-id="1783f-125">Následující příklad používá `/=` operátor rozdělit jednu `Integer` proměnné sekundu a přiřadit podílu první proměnné.</span><span class="sxs-lookup"><span data-stu-id="1783f-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1783f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1783f-126">See Also</span></span>  
 [<span data-ttu-id="1783f-127">/ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1783f-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="1783f-128">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="1783f-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="1783f-129">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="1783f-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="1783f-130">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="1783f-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="1783f-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1783f-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1783f-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="1783f-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="1783f-133">Příkazy</span><span class="sxs-lookup"><span data-stu-id="1783f-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
