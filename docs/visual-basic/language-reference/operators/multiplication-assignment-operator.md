---
title: "*= – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0a2c638f3faaf20fadb745ef437941ee29d4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8ad75-102">*= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ad75-102">*= Operator (Visual Basic)</span></span>
<span data-ttu-id="8ad75-103">Vynásobí hodnotou výrazu hodnotu proměnné nebo vlastnosti a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8ad75-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ad75-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8ad75-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8ad75-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8ad75-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8ad75-106">Required.</span></span> <span data-ttu-id="8ad75-107">Číselné proměnné nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8ad75-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8ad75-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8ad75-108">Required.</span></span> <span data-ttu-id="8ad75-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="8ad75-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ad75-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ad75-110">Remarks</span></span>  
 <span data-ttu-id="8ad75-111">Element na levé straně `*=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="8ad75-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8ad75-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8ad75-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8ad75-113">`*=` Operátor nejprve vynásobí hodnotu výrazu (na pravé straně operátoru) podle hodnoty proměnné nebo vlastnosti (na levé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="8ad75-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="8ad75-114">Výsledek této operace operátor poté přiřadí proměnné nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8ad75-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8ad75-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="8ad75-115">Overloading</span></span>  
 <span data-ttu-id="8ad75-116">[* Operátor](../../../visual-basic/language-reference/operators/multiplication-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="8ad75-116">The [* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8ad75-117">Přetížení `*` operátor má vliv na chování `*=` operátor.</span><span class="sxs-lookup"><span data-stu-id="8ad75-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="8ad75-118">Pokud váš kód používá `*=` na třídu nebo strukturu, která přetížení `*`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="8ad75-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8ad75-119">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8ad75-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ad75-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ad75-120">Example</span></span>  
 <span data-ttu-id="8ad75-121">Následující příklad používá `*=` operátor mají vynásobit jeden `Integer` proměnné sekundu a přiřadit výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="8ad75-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8ad75-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ad75-122">See Also</span></span>  
 [<span data-ttu-id="8ad75-123">* – Operátor</span><span class="sxs-lookup"><span data-stu-id="8ad75-123">* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)  
 [<span data-ttu-id="8ad75-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="8ad75-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="8ad75-125">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="8ad75-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="8ad75-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ad75-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="8ad75-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="8ad75-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="8ad75-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="8ad75-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
