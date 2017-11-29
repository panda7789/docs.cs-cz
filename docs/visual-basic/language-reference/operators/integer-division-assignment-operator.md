---
title: "\\=Operátor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ba74f7a433687b306e8b4273f3a2a6d60583396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator"></a><span data-ttu-id="d23bb-102">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="d23bb-102">\\= Operator</span></span>
<span data-ttu-id="d23bb-103">Vydělí hodnoty proměnné nebo vlastnosti hodnotou výrazu a přiřadí proměnné nebo vlastnosti celé číslo.</span><span class="sxs-lookup"><span data-stu-id="d23bb-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d23bb-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d23bb-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d23bb-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d23bb-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d23bb-106">Required.</span></span> <span data-ttu-id="d23bb-107">Číselné proměnné nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d23bb-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="d23bb-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d23bb-108">Required.</span></span> <span data-ttu-id="d23bb-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="d23bb-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d23bb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d23bb-110">Remarks</span></span>  
 <span data-ttu-id="d23bb-111">Element na levé straně `\=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="d23bb-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d23bb-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="d23bb-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d23bb-113">`\=` Operátor vydělí hodnoty proměnné nebo vlastnosti na levé straně, se hodnota na záhlavím vpravo a přiřadí proměnné nebo vlastnosti na levé straně, celé číslo</span><span class="sxs-lookup"><span data-stu-id="d23bb-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="d23bb-114">Další informace o dělení celého čísla v tématu [\ – operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d23bb-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d23bb-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="d23bb-115">Overloading</span></span>  
 <span data-ttu-id="d23bb-116">`\` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="d23bb-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d23bb-117">Přetížení `\` operátor má vliv na chování `\=` operátor.</span><span class="sxs-lookup"><span data-stu-id="d23bb-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="d23bb-118">Pokud váš kód používá `\=` na třídu nebo strukturu, která přetížení `\`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="d23bb-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d23bb-119">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d23bb-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d23bb-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="d23bb-120">Example</span></span>  
 <span data-ttu-id="d23bb-121">Následující příklad používá `\=` operátor rozdělit jednu `Integer` proměnné sekundu a přiřadit na celé číslo vést k první proměnné.</span><span class="sxs-lookup"><span data-stu-id="d23bb-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d23bb-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d23bb-122">See Also</span></span>  
 [<span data-ttu-id="d23bb-123">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d23bb-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="d23bb-124">/ = – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d23bb-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="d23bb-125">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="d23bb-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="d23bb-126">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="d23bb-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="d23bb-127">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d23bb-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d23bb-128">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="d23bb-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d23bb-129">Příkazy</span><span class="sxs-lookup"><span data-stu-id="d23bb-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
