---
title: '*= – operátor (Visual Basic)'
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
ms.openlocfilehash: 47d3239af6ff24501e6babc23c0db4103c477796
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701071"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ec634-102">\*= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec634-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="ec634-103">Vynásobí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí výsledek proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ec634-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec634-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec634-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ec634-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ec634-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ec634-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ec634-106">Required.</span></span> <span data-ttu-id="ec634-107">Jakákoli číselná proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ec634-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ec634-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ec634-108">Required.</span></span> <span data-ttu-id="ec634-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="ec634-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec634-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec634-110">Remarks</span></span>  
 <span data-ttu-id="ec634-111">Element na levé straně operátoru `*=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="ec634-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ec634-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ec634-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ec634-113">Operátor `*=` nejprve vynásobí hodnotu výrazu (na pravé straně operátoru) hodnotou proměnné nebo vlastnosti (na levé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="ec634-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="ec634-114">Operátor potom přiřadí výsledek této operace proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ec634-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ec634-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="ec634-115">Overloading</span></span>  
 <span data-ttu-id="ec634-116">[Operátor \*](../../../visual-basic/language-reference/operators/multiplication-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="ec634-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ec634-117">Přetížení operátoru `*` má vliv na chování operátoru `*=`.</span><span class="sxs-lookup"><span data-stu-id="ec634-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="ec634-118">Pokud váš kód používá `*=` na třídě nebo struktuře, která přetěžuje `*`, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="ec634-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ec634-119">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ec634-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec634-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec634-120">Example</span></span>  
 <span data-ttu-id="ec634-121">V následujícím příkladu je použit operátor `*=` k vynásobení jedné proměnné `Integer` sekundou a k první proměnné se přiřadí výsledek.</span><span class="sxs-lookup"><span data-stu-id="ec634-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ec634-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec634-122">See also</span></span>

- [<span data-ttu-id="ec634-123">Operátor \*</span><span class="sxs-lookup"><span data-stu-id="ec634-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="ec634-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="ec634-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="ec634-125">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="ec634-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="ec634-126">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec634-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ec634-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ec634-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ec634-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="ec634-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
