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
ms.openlocfilehash: 4b8f36397d0f52866ebe9fa188d6b163364aeffc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838997"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3d505-102">+= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d505-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="3d505-103">Přidá hodnotu číselného výrazu hodnotu číselného proměnnou nebo vlastnost a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3d505-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="3d505-104">Je také možné zřetězit `String` výraz, který se `String` proměnnou nebo vlastnost a přiřadit výsledek, který má proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3d505-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d505-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d505-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="3d505-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="3d505-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="3d505-107">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3d505-107">Required.</span></span> <span data-ttu-id="3d505-108">Všechny číselné nebo `String` proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3d505-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="3d505-109">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3d505-109">Required.</span></span> <span data-ttu-id="3d505-110">Všechny číselné nebo `String` výrazu.</span><span class="sxs-lookup"><span data-stu-id="3d505-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d505-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d505-111">Remarks</span></span>  
 <span data-ttu-id="3d505-112">Element na levé straně `+=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="3d505-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="3d505-113">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3d505-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="3d505-114">`+=` Operátor přidá hodnotu napravo na proměnnou nebo vlastnost na levé straně a výsledek přiřadí proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="3d505-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="3d505-115">`+=` Operátor je také možné zřetězit `String` výraz na jeho právo `String` proměnnou nebo vlastnost jeho vlevo a přiřadit výsledek, který má proměnnou nebo vlastnost na levé straně.</span><span class="sxs-lookup"><span data-stu-id="3d505-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d505-116">Při použití `+=` operátoru, nemusí být schopní určit, zda dojde k přidání nebo řetězec zřetězení.</span><span class="sxs-lookup"><span data-stu-id="3d505-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="3d505-117">Použití `&=` operátoru pro zřetězení, chcete-li odstranit nejednoznačnost a k poskytování samoobslužných dokumentace kódu.</span><span class="sxs-lookup"><span data-stu-id="3d505-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="3d505-118">Tento operátor přiřazení implicitně provádí, ale není zužujících převodů, pokud prostředí kompilace Vynutí striktní sémantiku rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3d505-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="3d505-119">Další informace o tyto převody, naleznete v tématu [Widening a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="3d505-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="3d505-120">Další informace o striktním a povolující sémantiku, naleznete v tématu [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d505-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="3d505-121">Pokud jsou povoleny povolující sémantiku, `+=` operátor provádí implicitně různé řetězcové a číselné převody, které jsou stejné jako ty prováděné `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="3d505-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="3d505-122">Podrobnosti o tyto převody, naleznete v tématu [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3d505-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3d505-123">Přetížení</span><span class="sxs-lookup"><span data-stu-id="3d505-123">Overloading</span></span>  
 <span data-ttu-id="3d505-124">`+` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="3d505-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3d505-125">Přetížení `+` operátor má vliv na chování `+=` operátor.</span><span class="sxs-lookup"><span data-stu-id="3d505-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="3d505-126">Pokud váš kód používá `+=` v třídě nebo struktuře, která přetížení `+`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="3d505-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3d505-127">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3d505-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d505-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d505-128">Example</span></span>  
 <span data-ttu-id="3d505-129">V následujícím příkladu `+=` operátor zkombinovat hodnoty jedné proměnné s jinou.</span><span class="sxs-lookup"><span data-stu-id="3d505-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="3d505-130">První část používá `+=` s číselné proměnné přidat jednu hodnotu do jiné.</span><span class="sxs-lookup"><span data-stu-id="3d505-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="3d505-131">Druhá část používá `+=` s `String` proměnné ke zřetězení jednu hodnotu druhou.</span><span class="sxs-lookup"><span data-stu-id="3d505-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="3d505-132">V obou případech platí výsledek je přiřazen k první proměnné.</span><span class="sxs-lookup"><span data-stu-id="3d505-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="3d505-133">Hodnota `num1` 13 a hodnota je nyní `str1` je nyní "103".</span><span class="sxs-lookup"><span data-stu-id="3d505-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d505-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d505-134">See also</span></span>

- [<span data-ttu-id="3d505-135">+ – operátor</span><span class="sxs-lookup"><span data-stu-id="3d505-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="3d505-136">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="3d505-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="3d505-137">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="3d505-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="3d505-138">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="3d505-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="3d505-139">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d505-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3d505-140">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="3d505-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3d505-141">Příkazy</span><span class="sxs-lookup"><span data-stu-id="3d505-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
