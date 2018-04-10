---
title: '&amp;= – Operátor (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 929a9e8c3384451679fc52ad478eb03219d67192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="cc751-102">&amp;= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc751-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="cc751-103">Zřetězí `String` výraz, který se `String` proměnné nebo vlastnosti a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc751-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc751-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc751-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="cc751-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="cc751-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="cc751-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cc751-106">Required.</span></span> <span data-ttu-id="cc751-107">Všechny `String` proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc751-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="cc751-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cc751-108">Required.</span></span> <span data-ttu-id="cc751-109">Všechny `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="cc751-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc751-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc751-110">Remarks</span></span>  
 <span data-ttu-id="cc751-111">Element na levé straně `&=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="cc751-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="cc751-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="cc751-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="cc751-113">`&=` Operátor zřetězí `String` výraz jeho vpravo `String` proměnné nebo vlastnosti na levé straně a přiřadí výsledek proměnné nebo vlastnost na levé straně.</span><span class="sxs-lookup"><span data-stu-id="cc751-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cc751-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="cc751-114">Overloading</span></span>  
 <span data-ttu-id="cc751-115">[& Operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="cc751-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cc751-116">Přetížení `&` operátor má vliv na chování `&=` operátor.</span><span class="sxs-lookup"><span data-stu-id="cc751-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="cc751-117">Pokud váš kód používá `&=` na třídu nebo strukturu, která přetížení `&`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="cc751-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cc751-118">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cc751-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc751-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc751-119">Example</span></span>  
 <span data-ttu-id="cc751-120">Následující příklad používá `&=` operátor ke zřetězení dva `String` proměnné a přiřazení výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="cc751-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cc751-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc751-121">See Also</span></span>  
 [<span data-ttu-id="cc751-122">& – Operátor</span><span class="sxs-lookup"><span data-stu-id="cc751-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="cc751-123">+= – Operátor</span><span class="sxs-lookup"><span data-stu-id="cc751-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="cc751-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="cc751-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="cc751-125">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="cc751-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="cc751-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc751-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="cc751-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="cc751-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="cc751-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="cc751-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
