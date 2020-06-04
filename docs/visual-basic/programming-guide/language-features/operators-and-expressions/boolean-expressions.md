---
title: Výrazy logických hodnot
ms.date: 07/20/2015
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
ms.openlocfilehash: 8d34eb4c8b14bb4754f2a3cf5b6f9a7601aa4662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388955"
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="1535f-102">Výrazy logických hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1535f-102">Boolean Expressions (Visual Basic)</span></span>
<span data-ttu-id="1535f-103">*Logický výraz* je výraz, který je vyhodnocen jako hodnota [logického datového typu](../../../language-reference/data-types/boolean-data-type.md): `True` nebo `False` .</span><span class="sxs-lookup"><span data-stu-id="1535f-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="1535f-104">`Boolean`výrazy mohou mít několik forem.</span><span class="sxs-lookup"><span data-stu-id="1535f-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="1535f-105">Nejjednodušší je přímé porovnání hodnoty `Boolean` proměnné s `Boolean` literálem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1535f-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="1535f-106">Dva významy operátoru =</span><span class="sxs-lookup"><span data-stu-id="1535f-106">Two Meanings of the = Operator</span></span>  
 <span data-ttu-id="1535f-107">Všimněte si, že příkaz přiřazení `newCustomer = True` vypadá stejně jako výraz v předchozím příkladu, ale provádí jinou funkci a je použit odlišně.</span><span class="sxs-lookup"><span data-stu-id="1535f-107">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="1535f-108">V předchozím příkladu výraz `newCustomer = True` představuje logickou hodnotu a `=` znaménko je interpretováno jako operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="1535f-108">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="1535f-109">V samostatném příkazu `=` je znaménko interpretováno jako operátor přiřazení a přiřadí hodnotu na pravé straně k proměnné na levé straně.</span><span class="sxs-lookup"><span data-stu-id="1535f-109">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="1535f-110">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1535f-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 <span data-ttu-id="1535f-111">Další informace naleznete v tématu [porovnání hodnot](value-comparisons.md) a [příkazy](../../../language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="1535f-111">For further information, see [Value Comparisons](value-comparisons.md) and [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="1535f-112">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="1535f-112">Comparison Operators</span></span>  
 <span data-ttu-id="1535f-113">Relační operátory, jako `=` například,,, `<` `>` `<>` , `<=` a `>=` poskytují logické výrazy porovnáním výrazu na levé straně operátoru k výrazu na pravé straně operátoru a vyhodnocení výsledku jako `True` nebo `False` .</span><span class="sxs-lookup"><span data-stu-id="1535f-113">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="1535f-114">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1535f-114">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="1535f-115">Vzhledem k tomu, že 42 je menší než 81, logický výraz v předchozím příkladu je vyhodnocen jako `True` .</span><span class="sxs-lookup"><span data-stu-id="1535f-115">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="1535f-116">Další informace o tomto typu výrazu naleznete v tématu [porovnání hodnot](value-comparisons.md).</span><span class="sxs-lookup"><span data-stu-id="1535f-116">For more information on this kind of expression, see [Value Comparisons](value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="1535f-117">Operátory porovnání kombinované s logickými operátory</span><span class="sxs-lookup"><span data-stu-id="1535f-117">Comparison Operators Combined with Logical Operators</span></span>  
 <span data-ttu-id="1535f-118">Výrazy porovnání lze kombinovat pomocí logických operátorů k tvorbě složitějších logických výrazů.</span><span class="sxs-lookup"><span data-stu-id="1535f-118">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="1535f-119">Následující příklad ukazuje použití relačních operátorů ve spojení s logickým operátorem.</span><span class="sxs-lookup"><span data-stu-id="1535f-119">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="1535f-120">V předchozím příkladu hodnota celkového výrazu závisí na hodnotách výrazů na každé straně `And` operátoru.</span><span class="sxs-lookup"><span data-stu-id="1535f-120">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="1535f-121">Pokud jsou oba výrazy `True` , pak se celkový výraz vyhodnotí jako `True` .</span><span class="sxs-lookup"><span data-stu-id="1535f-121">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="1535f-122">Pokud je některý z těchto výrazů `False` , pak se celý výraz vyhodnotí jako `False` .</span><span class="sxs-lookup"><span data-stu-id="1535f-122">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="1535f-123">Operátory krátkodobého okruhu</span><span class="sxs-lookup"><span data-stu-id="1535f-123">Short-Circuiting Operators</span></span>  
 <span data-ttu-id="1535f-124">Logické operátory `AndAlso` a `OrElse` chování se projevují jako *krátkodobé okruhy*.</span><span class="sxs-lookup"><span data-stu-id="1535f-124">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="1535f-125">Operátor krátkého okruhu nejprve vyhodnocuje levý operand.</span><span class="sxs-lookup"><span data-stu-id="1535f-125">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="1535f-126">Pokud levý operand určí hodnotu celého výrazu, pak spuštění programu pokračuje bez vyhodnocení správného výrazu.</span><span class="sxs-lookup"><span data-stu-id="1535f-126">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="1535f-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1535f-127">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 <span data-ttu-id="1535f-128">V předchozím příkladu operátor vyhodnocuje levý výraz, `45 < 12` .</span><span class="sxs-lookup"><span data-stu-id="1535f-128">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="1535f-129">Vzhledem k tomu, že se levý výraz vyhodnotí jako `False` , musí se celý logický výraz vyhodnotit na `False` .</span><span class="sxs-lookup"><span data-stu-id="1535f-129">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="1535f-130">Provádění programu proto přeskočí provádění kódu v rámci `If` bloku bez vyhodnocení pravého výrazu, `testFunction(3)` .</span><span class="sxs-lookup"><span data-stu-id="1535f-130">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="1535f-131">Tento příklad nevolá, `testFunction()` protože levý výraz padělaný celý výraz.</span><span class="sxs-lookup"><span data-stu-id="1535f-131">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="1535f-132">Podobně platí, že pokud se na levém výrazu v logickém výrazu používá `OrElse` vyhodnocení `True` , provádění pokračuje na další řádek kódu bez vyhodnocení pravého výrazu, protože levý výraz již ověřil celý výraz.</span><span class="sxs-lookup"><span data-stu-id="1535f-132">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="1535f-133">Porovnání s operátory bez krátkých okruhů</span><span class="sxs-lookup"><span data-stu-id="1535f-133">Comparison with Non-Short-Circuiting Operators</span></span>  
 <span data-ttu-id="1535f-134">Naopak obě strany logického operátoru jsou vyhodnocovány při použití logických operátorů `And` a `Or` .</span><span class="sxs-lookup"><span data-stu-id="1535f-134">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="1535f-135">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1535f-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 <span data-ttu-id="1535f-136">Předchozí příklad volá `testFunction()` i v případě, že se levý výraz vyhodnotí jako `False` .</span><span class="sxs-lookup"><span data-stu-id="1535f-136">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="1535f-137">Výrazy kulatého závorky</span><span class="sxs-lookup"><span data-stu-id="1535f-137">Parenthetical Expressions</span></span>  
 <span data-ttu-id="1535f-138">Můžete použít kulaté závorky k řízení pořadí vyhodnocení logických výrazů.</span><span class="sxs-lookup"><span data-stu-id="1535f-138">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="1535f-139">Nejprve se vyhodnocují výrazy, které jsou uzavřeny v závorkách.</span><span class="sxs-lookup"><span data-stu-id="1535f-139">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="1535f-140">Pro více úrovní vnoření je přednost udělena nejhlouběji vnořeným výrazům.</span><span class="sxs-lookup"><span data-stu-id="1535f-140">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="1535f-141">V závorkách hodnocení pokračuje podle pravidel přednosti operátoru.</span><span class="sxs-lookup"><span data-stu-id="1535f-141">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="1535f-142">Další informace najdete v tématu [Priorita operátorů v Visual Basic](../../../language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="1535f-142">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1535f-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="1535f-143">See also</span></span>

- [<span data-ttu-id="1535f-144">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1535f-144">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="1535f-145">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="1535f-145">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="1535f-146">Příkazy</span><span class="sxs-lookup"><span data-stu-id="1535f-146">Statements</span></span>](../statements.md)
- [<span data-ttu-id="1535f-147">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="1535f-147">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="1535f-148">Účinná kombinace operátorů</span><span class="sxs-lookup"><span data-stu-id="1535f-148">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="1535f-149">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1535f-149">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1535f-150">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="1535f-150">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)
