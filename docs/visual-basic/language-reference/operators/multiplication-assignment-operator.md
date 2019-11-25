---
title: '*= – operátor'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 4b60fa44a92bff683e13f850da025d7fe753618d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349789"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9bf8a-102">\*= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bf8a-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="9bf8a-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bf8a-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9bf8a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9bf8a-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9bf8a-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-106">Required.</span></span> <span data-ttu-id="9bf8a-107">Any numeric variable or property.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="9bf8a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-108">Required.</span></span> <span data-ttu-id="9bf8a-109">Any numeric expression.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bf8a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bf8a-110">Remarks</span></span>  
 <span data-ttu-id="9bf8a-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9bf8a-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9bf8a-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="9bf8a-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span><span class="sxs-lookup"><span data-stu-id="9bf8a-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="9bf8a-114">The operator then assigns the result of that operation to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9bf8a-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="9bf8a-115">Overloading</span></span>  
 <span data-ttu-id="9bf8a-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9bf8a-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="9bf8a-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9bf8a-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9bf8a-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bf8a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bf8a-120">Example</span></span>  
 <span data-ttu-id="9bf8a-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span><span class="sxs-lookup"><span data-stu-id="9bf8a-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="9bf8a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bf8a-122">See also</span></span>

- [<span data-ttu-id="9bf8a-123">Operátor \*</span><span class="sxs-lookup"><span data-stu-id="9bf8a-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="9bf8a-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="9bf8a-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="9bf8a-125">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="9bf8a-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="9bf8a-126">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bf8a-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9bf8a-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="9bf8a-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9bf8a-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="9bf8a-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
