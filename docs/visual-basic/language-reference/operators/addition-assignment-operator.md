---
title: += – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: f12a0560d984f871110c02f1df2c2ec42b68809b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604013"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="fe253-102">+= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe253-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="fe253-103">Přidá hodnotu číselného výrazu na hodnotu číselného proměnné nebo vlastnosti a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fe253-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="fe253-104">Můžete také použít ke zřetězení `String` výraz, který se `String` proměnné nebo vlastnost a přiřadit výsledek, který má proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fe253-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe253-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe253-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="fe253-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="fe253-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="fe253-107">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fe253-107">Required.</span></span> <span data-ttu-id="fe253-108">Všechny číselné nebo `String` proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fe253-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="fe253-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fe253-109">Required.</span></span> <span data-ttu-id="fe253-110">Všechny číselné nebo `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="fe253-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe253-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe253-111">Remarks</span></span>  
 <span data-ttu-id="fe253-112">Element na levé straně `+=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="fe253-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="fe253-113">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="fe253-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="fe253-114">`+=` Operátor přidá hodnotu jeho vpravo proměnné nebo vlastnosti na levé straně a výsledek přiřadí proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="fe253-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="fe253-115">`+=` Operátor můžete také použít ke zřetězení `String` výraz jeho vpravo `String` proměnnou nebo na jeho levé straně a přiřadit výsledek, který má proměnná, nebo vlastností na levé straně.</span><span class="sxs-lookup"><span data-stu-id="fe253-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe253-116">Při použití `+=` operátor, nemusí být schopní určit, zda dojde k přidání nebo řetězec zřetězení.</span><span class="sxs-lookup"><span data-stu-id="fe253-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="fe253-117">Použití `&=` operátor řetězení odstranit nejednoznačnost a k poskytování samoobslužných dokumentů kódu.</span><span class="sxs-lookup"><span data-stu-id="fe253-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="fe253-118">Tento operátor přiřazení implicitně provádí, ale není zužující převody Pokud prostředí kompilace vynucuje přísné sémantiku rozšíření.</span><span class="sxs-lookup"><span data-stu-id="fe253-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="fe253-119">Další informace o těchto převody najdete v tématu [Widening a zužující převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="fe253-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="fe253-120">Další informace o striktní a projektovou sémantiku, najdete v části [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe253-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="fe253-121">Pokud sémantiku projektovou jsou povoleny, `+=` operátor implicitně provádí řadu řetězec a číselné převody stejné jako ty provádí `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="fe253-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="fe253-122">Informace o těchto převody v [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="fe253-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fe253-123">Přetížení</span><span class="sxs-lookup"><span data-stu-id="fe253-123">Overloading</span></span>  
 <span data-ttu-id="fe253-124">`+` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="fe253-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fe253-125">Přetížení `+` operátor má vliv na chování `+=` operátor.</span><span class="sxs-lookup"><span data-stu-id="fe253-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="fe253-126">Pokud váš kód používá `+=` na třídu nebo strukturu, která přetížení `+`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="fe253-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fe253-127">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fe253-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe253-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe253-128">Example</span></span>  
 <span data-ttu-id="fe253-129">Následující příklad používá `+=` operátor kombinovat s jinou hodnotu jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fe253-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="fe253-130">První část používá `+=` s číselné proměnné, které chcete přidat jednu hodnotu do jiné.</span><span class="sxs-lookup"><span data-stu-id="fe253-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="fe253-131">Druhá část používá `+=` s `String` proměnné, které chcete zřetězit jednu hodnotu druhou.</span><span class="sxs-lookup"><span data-stu-id="fe253-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="fe253-132">V obou případech je výsledek přiřazen první proměnné.</span><span class="sxs-lookup"><span data-stu-id="fe253-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 <span data-ttu-id="fe253-133">Hodnota `num1` je nyní 13 a hodnotu `str1` je nyní "103".</span><span class="sxs-lookup"><span data-stu-id="fe253-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe253-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe253-134">See Also</span></span>  
 [<span data-ttu-id="fe253-135">+ – operátor</span><span class="sxs-lookup"><span data-stu-id="fe253-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [<span data-ttu-id="fe253-136">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="fe253-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="fe253-137">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="fe253-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="fe253-138">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="fe253-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="fe253-139">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe253-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="fe253-140">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="fe253-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="fe253-141">Příkazy</span><span class="sxs-lookup"><span data-stu-id="fe253-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
