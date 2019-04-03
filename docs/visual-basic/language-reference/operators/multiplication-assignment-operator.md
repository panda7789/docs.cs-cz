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
ms.openlocfilehash: 7c009a6b3acfe1528a2c34ed1e10735ac86507e6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839311"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b5251-102">\*= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5251-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="b5251-103">Vynásobí hodnotu proměnné nebo vlastnosti hodnotou výrazu a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5251-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5251-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b5251-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b5251-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b5251-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b5251-106">Required.</span></span> <span data-ttu-id="b5251-107">Všechny číselné proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5251-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="b5251-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b5251-108">Required.</span></span> <span data-ttu-id="b5251-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="b5251-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5251-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5251-110">Remarks</span></span>  
 <span data-ttu-id="b5251-111">Element na levé straně `*=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="b5251-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b5251-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b5251-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b5251-113">`*=` Operátor nejprve vynásobí hodnotu výrazu (na pravé straně operátoru) hodnotu proměnné nebo vlastnosti (na levé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="b5251-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="b5251-114">Operátor, který se pak přiřadí výsledek této operace na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b5251-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b5251-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="b5251-115">Overloading</span></span>  
 <span data-ttu-id="b5251-116">[\* – Operátor](../../../visual-basic/language-reference/operators/multiplication-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="b5251-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b5251-117">Přetížení `*` operátor má vliv na chování `*=` operátor.</span><span class="sxs-lookup"><span data-stu-id="b5251-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="b5251-118">Pokud váš kód používá `*=` v třídě nebo struktuře, která přetížení `*`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="b5251-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b5251-119">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b5251-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5251-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5251-120">Example</span></span>  
 <span data-ttu-id="b5251-121">V následujícím příkladu `*=` operátor násobit jeden `Integer` proměnné tak, že druhé a přiřadit výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="b5251-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b5251-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5251-122">See also</span></span>

- [<span data-ttu-id="b5251-123">\* – operátor</span><span class="sxs-lookup"><span data-stu-id="b5251-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="b5251-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="b5251-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="b5251-125">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="b5251-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b5251-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5251-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b5251-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="b5251-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b5251-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="b5251-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
