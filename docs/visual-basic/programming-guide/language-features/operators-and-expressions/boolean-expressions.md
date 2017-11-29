---
title: "Výrazy logických hodnot (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 48071c6833f9841fa42311dda59d6959c0645ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="69eb7-102">Výrazy logických hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69eb7-102">Boolean Expressions (Visual Basic)</span></span>
<span data-ttu-id="69eb7-103">A *logický výraz* je výraz, který se vyhodnotí na hodnotu [datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="69eb7-104">`Boolean`Výrazy lze provést několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="69eb7-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="69eb7-105">Nejjednodušší je přímé porovnání hodnoty `Boolean` proměnnou `Boolean` literál, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69eb7-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="69eb7-106">Dva význam = – operátor</span><span class="sxs-lookup"><span data-stu-id="69eb7-106">Two Meanings of the = Operator</span></span>  
 <span data-ttu-id="69eb7-107">Všimněte si, že příkaz přiřazení `newCustomer = True` vypadá stejně jako výraz v předchozím příkladu, ale provádí různé funkce a se používá jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="69eb7-107">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="69eb7-108">V předchozím příkladu výraz `newCustomer = True` představuje logickou hodnotu a `=` přihlašovací interpretována jako operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="69eb7-108">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="69eb7-109">V samostatné příkazu `=` přihlašovací interpretována jako operátor přiřazení a přiřadí hodnota na pravé straně proměnnou na levé straně.</span><span class="sxs-lookup"><span data-stu-id="69eb7-109">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="69eb7-110">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69eb7-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 <span data-ttu-id="69eb7-111">Další informace najdete v tématu [porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) a [příkazy](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="69eb7-111">For further information, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) and [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="69eb7-112">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="69eb7-112">Comparison Operators</span></span>  
 <span data-ttu-id="69eb7-113">Operátory porovnání jako `=`, `<`, `>`, `<>`, `<=`, a `>=` vytvořit tak, že porovnáte výraz na levé straně operátoru výrazu na pravé straně logické výrazy operátor a vyhodnocení výsledek v podobě `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-113">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="69eb7-114">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69eb7-114">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="69eb7-115">Protože 42 je menší než 81, logický výraz v předchozím příkladu se vyhodnocuje `True`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-115">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="69eb7-116">Další informace o tento druh výraz najdete v tématu [porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span><span class="sxs-lookup"><span data-stu-id="69eb7-116">For more information on this kind of expression, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="69eb7-117">Operátory porovnání v kombinaci s logické operátory</span><span class="sxs-lookup"><span data-stu-id="69eb7-117">Comparison Operators Combined with Logical Operators</span></span>  
 <span data-ttu-id="69eb7-118">Výrazy porovnání lze spojovat pomocí logických operátorů k vytvoření složitějších výrazy logických hodnot.</span><span class="sxs-lookup"><span data-stu-id="69eb7-118">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="69eb7-119">Následující příklad ukazuje použití operátory porovnání ve spojení s logický operátor.</span><span class="sxs-lookup"><span data-stu-id="69eb7-119">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="69eb7-120">V předchozím příkladu hodnotu celkové výrazu závisí na hodnotách výrazů na každé straně `And` operátor.</span><span class="sxs-lookup"><span data-stu-id="69eb7-120">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="69eb7-121">Pokud jsou oba výrazy `True`, pak celkové výraz vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-121">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="69eb7-122">Pokud je buď výraz `False`, pak celý výraz vyhodnocen `False`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-122">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="69eb7-123">Krátká smyčka operátory</span><span class="sxs-lookup"><span data-stu-id="69eb7-123">Short-Circuiting Operators</span></span>  
 <span data-ttu-id="69eb7-124">Logické operátory `AndAlso` a `OrElse` vykazovat chování známé jako *krátká smyčka*.</span><span class="sxs-lookup"><span data-stu-id="69eb7-124">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="69eb7-125">Levý operand vyhodnotí short-circuiting operátor nejdřív.</span><span class="sxs-lookup"><span data-stu-id="69eb7-125">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="69eb7-126">Pokud levý operand Určuje hodnotu celého výrazu, spuštění programu pokračuje bez vyhodnocení pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="69eb7-126">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="69eb7-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69eb7-127">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 <span data-ttu-id="69eb7-128">V předchozím příkladu operátor vyhodnotí levý výraz `45 < 12`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-128">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="69eb7-129">Protože levý výraz vyhodnocen jako `False`, se musí vyhodnotit celý logický výraz `False`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-129">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="69eb7-130">Spuštění programu proto přeskočí spuštění kódu v rámci `If` bloku bez vyhodnocení pravý výraz `testFunction(3)`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-130">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="69eb7-131">Tento příklad nevyvolá `testFunction()` protože levý výraz falsifies celý výraz.</span><span class="sxs-lookup"><span data-stu-id="69eb7-131">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="69eb7-132">Podobně pokud levý výraz logický výraz pomocí `OrElse` vyhodnotí jako `True`, provádění pokračuje bez vyhodnocení pravý výraz dalším řádku kódu, protože levý výraz už ověřila celý výraz.</span><span class="sxs-lookup"><span data-stu-id="69eb7-132">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="69eb7-133">Porovnání s bez krátké Circuiting operátory</span><span class="sxs-lookup"><span data-stu-id="69eb7-133">Comparison with Non-Short-Circuiting Operators</span></span>  
 <span data-ttu-id="69eb7-134">Oproti tomu vyhodnocují obou stranách logický operátor při logické operátory `And` a `Or` se používají.</span><span class="sxs-lookup"><span data-stu-id="69eb7-134">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="69eb7-135">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69eb7-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 <span data-ttu-id="69eb7-136">Předchozí příklad volání `testFunction()` Přestože levý výraz vyhodnocen jako `False`.</span><span class="sxs-lookup"><span data-stu-id="69eb7-136">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="69eb7-137">Výrazy se závorkami</span><span class="sxs-lookup"><span data-stu-id="69eb7-137">Parenthetical Expressions</span></span>  
 <span data-ttu-id="69eb7-138">Závorky můžete použít k řízení pořadí vyhodnocování výrazy logických hodnot.</span><span class="sxs-lookup"><span data-stu-id="69eb7-138">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="69eb7-139">Nejprve vyhodnotit výrazy uzavřena v závorkách.</span><span class="sxs-lookup"><span data-stu-id="69eb7-139">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="69eb7-140">Pro více úrovní vnoření přednost před udělena nejvíce hluboko vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="69eb7-140">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="69eb7-141">V uvozovkách vyhodnocení pokračuje podle pravidel objektů operátorů.</span><span class="sxs-lookup"><span data-stu-id="69eb7-141">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="69eb7-142">Další informace najdete v tématu [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="69eb7-142">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69eb7-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="69eb7-143">See Also</span></span>  
 [<span data-ttu-id="69eb7-144">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69eb7-144">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="69eb7-145">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="69eb7-145">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="69eb7-146">Příkazy</span><span class="sxs-lookup"><span data-stu-id="69eb7-146">Statements</span></span>](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="69eb7-147">Operátory porovnávání</span><span class="sxs-lookup"><span data-stu-id="69eb7-147">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="69eb7-148">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="69eb7-148">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [<span data-ttu-id="69eb7-149">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69eb7-149">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="69eb7-150">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="69eb7-150">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
