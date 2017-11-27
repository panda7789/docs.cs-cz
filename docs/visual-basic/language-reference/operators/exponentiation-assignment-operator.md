---
title: "^= – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9f206-102">^= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f206-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="9f206-103">Vyvolá hodnoty proměnné nebo vlastnost exponentem výrazu a přiřadí výsledek zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9f206-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f206-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f206-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9f206-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9f206-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9f206-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9f206-106">Required.</span></span> <span data-ttu-id="9f206-107">Číselné proměnné nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9f206-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="9f206-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9f206-108">Required.</span></span> <span data-ttu-id="9f206-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="9f206-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f206-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f206-110">Remarks</span></span>  
 <span data-ttu-id="9f206-111">Element na levé straně `^=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="9f206-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9f206-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9f206-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="9f206-113">`^=` Operátor nejprve vyvolá hodnota proměnné nebo vlastnosti (na levé straně operátoru) exponentem hodnotu výrazu (na pravé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="9f206-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="9f206-114">Operátor poté přiřadí výsledek této operace zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9f206-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="9f206-115">Visual Basic vždy provede exponenciální zápis v [dvojitý datový typ](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="9f206-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="9f206-116">Operandy žádné jiného typu se převedou na `Double`, a výsledek je vždy `Double`.</span><span class="sxs-lookup"><span data-stu-id="9f206-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="9f206-117">Hodnota `expression` může být zlomkové záporné nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="9f206-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9f206-118">Přetížení</span><span class="sxs-lookup"><span data-stu-id="9f206-118">Overloading</span></span>  
 <span data-ttu-id="9f206-119">[^ – Operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="9f206-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9f206-120">Přetížení `^` operátor má vliv na chování `^=` operátor.</span><span class="sxs-lookup"><span data-stu-id="9f206-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="9f206-121">Pokud váš kód používá `^=` na třídu nebo strukturu, která přetížení `^`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="9f206-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9f206-122">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9f206-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f206-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f206-123">Example</span></span>  
 <span data-ttu-id="9f206-124">Následující příklad používá `^=` operátor umožňuje aktivovat hodnota jednoho `Integer` proměnné exponentem druhý proměnné a přiřazení výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="9f206-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9f206-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f206-125">See Also</span></span>  
 [<span data-ttu-id="9f206-126">^ – Operátor</span><span class="sxs-lookup"><span data-stu-id="9f206-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [<span data-ttu-id="9f206-127">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="9f206-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="9f206-128">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="9f206-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="9f206-129">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f206-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="9f206-130">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="9f206-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="9f206-131">Příkazy</span><span class="sxs-lookup"><span data-stu-id="9f206-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
