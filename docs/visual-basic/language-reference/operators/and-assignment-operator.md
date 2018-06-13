---
title: '&amp;= – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: c3db2d4095600f32af92d1a4ce1f806a3f032af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601878"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="9ba35-102">&amp;= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ba35-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="9ba35-103">Zřetězí `String` výraz, který se `String` proměnné nebo vlastnosti a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9ba35-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ba35-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9ba35-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9ba35-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9ba35-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9ba35-106">Required.</span></span> <span data-ttu-id="9ba35-107">Všechny `String` proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9ba35-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="9ba35-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9ba35-108">Required.</span></span> <span data-ttu-id="9ba35-109">Všechny `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="9ba35-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ba35-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ba35-110">Remarks</span></span>  
 <span data-ttu-id="9ba35-111">Element na levé straně `&=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="9ba35-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9ba35-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9ba35-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="9ba35-113">`&=` Operátor zřetězí `String` výraz jeho vpravo `String` proměnné nebo vlastnosti na levé straně a přiřadí výsledek proměnné nebo vlastnost na levé straně.</span><span class="sxs-lookup"><span data-stu-id="9ba35-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9ba35-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="9ba35-114">Overloading</span></span>  
 <span data-ttu-id="9ba35-115">[& Operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="9ba35-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9ba35-116">Přetížení `&` operátor má vliv na chování `&=` operátor.</span><span class="sxs-lookup"><span data-stu-id="9ba35-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="9ba35-117">Pokud váš kód používá `&=` na třídu nebo strukturu, která přetížení `&`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="9ba35-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9ba35-118">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9ba35-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ba35-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ba35-119">Example</span></span>  
 <span data-ttu-id="9ba35-120">Následující příklad používá `&=` operátor ke zřetězení dva `String` proměnné a přiřazení výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="9ba35-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9ba35-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ba35-121">See Also</span></span>  
 [<span data-ttu-id="9ba35-122">& – operátor</span><span class="sxs-lookup"><span data-stu-id="9ba35-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="9ba35-123">+= – operátor</span><span class="sxs-lookup"><span data-stu-id="9ba35-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="9ba35-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="9ba35-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="9ba35-125">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="9ba35-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="9ba35-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ba35-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="9ba35-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="9ba35-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="9ba35-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="9ba35-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
