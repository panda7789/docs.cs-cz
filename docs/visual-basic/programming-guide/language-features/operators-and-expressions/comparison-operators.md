---
title: Operátory porovnání v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77c5520be63d6d05cc4b895b99b466cd8e486f6a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="ca84d-102">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca84d-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="ca84d-103">Relační operátory porovnání dvou výrazů a vrátí `Boolean` hodnotu, která představuje vztah jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="ca84d-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="ca84d-104">Pro porovnání číselných hodnot, operátory porovnávání řetězců a operátory porovnání objektů existují operátory.</span><span class="sxs-lookup"><span data-stu-id="ca84d-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="ca84d-105">Všechny tři typy operátory jsou popsané v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ca84d-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="ca84d-106">Porovnání číselných hodnot</span><span class="sxs-lookup"><span data-stu-id="ca84d-106">Comparing Numeric Values</span></span>  
 <span data-ttu-id="ca84d-107">Visual Basic porovná číselných hodnot pomocí šesti číselné relační operátory.</span><span class="sxs-lookup"><span data-stu-id="ca84d-107">Visual Basic compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="ca84d-108">Každý operátor má jako operandy dvou výrazů, která se vyhodnotí jako číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ca84d-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="ca84d-109">V následující tabulce jsou uvedeny operátory a zobrazuje příklady jednotlivých.</span><span class="sxs-lookup"><span data-stu-id="ca84d-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="ca84d-110">Operátor</span><span class="sxs-lookup"><span data-stu-id="ca84d-110">Operator</span></span>|<span data-ttu-id="ca84d-111">Stav testování</span><span class="sxs-lookup"><span data-stu-id="ca84d-111">Condition tested</span></span>|<span data-ttu-id="ca84d-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="ca84d-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="ca84d-113">`=` (Rovnosti)</span><span class="sxs-lookup"><span data-stu-id="ca84d-113">`=` (Equality)</span></span>|<span data-ttu-id="ca84d-114">Je hodnota první výraz rovná hodnotě druhý?</span><span class="sxs-lookup"><span data-stu-id="ca84d-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="ca84d-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="ca84d-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="ca84d-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="ca84d-118">`<>` (Nerovnost)</span><span class="sxs-lookup"><span data-stu-id="ca84d-118">`<>` (Inequality)</span></span>|<span data-ttu-id="ca84d-119">Je hodnota první výraz nerovné na hodnotu druhý?</span><span class="sxs-lookup"><span data-stu-id="ca84d-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="ca84d-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="ca84d-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="ca84d-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="ca84d-123">`<` (Méně než)</span><span class="sxs-lookup"><span data-stu-id="ca84d-123">`<` (Less than)</span></span>|<span data-ttu-id="ca84d-124">Je hodnota první výraz menší než hodnota druhého?</span><span class="sxs-lookup"><span data-stu-id="ca84d-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="ca84d-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="ca84d-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="ca84d-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="ca84d-128">`>` (Větší než)</span><span class="sxs-lookup"><span data-stu-id="ca84d-128">`>` (Greater than)</span></span>|<span data-ttu-id="ca84d-129">Je větší než hodnota druhá hodnota první výraz?</span><span class="sxs-lookup"><span data-stu-id="ca84d-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="ca84d-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="ca84d-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="ca84d-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="ca84d-133">`<=` (Je menší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="ca84d-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="ca84d-134">Je hodnota první výraz menší než nebo rovna hodnotě druhý?</span><span class="sxs-lookup"><span data-stu-id="ca84d-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="ca84d-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="ca84d-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="ca84d-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="ca84d-138">`>=` (Je větší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="ca84d-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="ca84d-139">Hodnota první výraz, který je větší než nebo rovna hodnotě druhý?</span><span class="sxs-lookup"><span data-stu-id="ca84d-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="ca84d-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="ca84d-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="ca84d-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="ca84d-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="ca84d-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="ca84d-143">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="ca84d-143">Comparing Strings</span></span>  
 <span data-ttu-id="ca84d-144">Porovnání řetězců pomocí jazyka Visual Basic [jako operátor](../../../../visual-basic/language-reference/operators/like-operator.md) i číselné relační operátory.</span><span class="sxs-lookup"><span data-stu-id="ca84d-144">Visual Basic compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="ca84d-145">`Like` Operátor umožňuje určit vzor.</span><span class="sxs-lookup"><span data-stu-id="ca84d-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="ca84d-146">Řetězec se pak porovná vzor, a pokud odpovídá, výsledkem je `True`.</span><span class="sxs-lookup"><span data-stu-id="ca84d-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="ca84d-147">Jinak, výsledkem je `False`.</span><span class="sxs-lookup"><span data-stu-id="ca84d-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="ca84d-148">Číselné operátory umožňují porovnat `String` hodnoty podle jejich pořadí, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ca84d-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="ca84d-149">Výsledek v předchozím příkladu je `True` vzhledem k tomu, že první znak v řetězci první seřadí před první znak argumentu k druhému řetězci.</span><span class="sxs-lookup"><span data-stu-id="ca84d-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="ca84d-150">Kdyby stejná prvních znaků porovnání bude pokračovat na další znak v oba řetězce a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ca84d-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="ca84d-151">Můžete také otestovat rovnosti řetězců pomocí operátoru rovnosti, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ca84d-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="ca84d-152">Pokud jeden řetězec předpona jiné, jako je například "aa" a "aaa", považuje za delší řetězec být větší než kratší řetězec.</span><span class="sxs-lookup"><span data-stu-id="ca84d-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="ca84d-153">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ca84d-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="ca84d-154">Pořadí řazení je založena na binární porovnání nebo textové porovnání v závislosti na nastavení `Option Compare`.</span><span class="sxs-lookup"><span data-stu-id="ca84d-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="ca84d-155">Další informace najdete v části [Option Compare – příkaz](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca84d-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="ca84d-156">Porovnávání objektů</span><span class="sxs-lookup"><span data-stu-id="ca84d-156">Comparing Objects</span></span>  
 <span data-ttu-id="ca84d-157">Visual Basic porovná dvě proměnné objektových referencí s [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) a [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ca84d-157">Visual Basic compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="ca84d-158">Můžete použít některý z těchto operátorů k určení, zda dva referenční proměnné odkazují na stejnou instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="ca84d-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="ca84d-159">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ca84d-159">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="ca84d-160">V předchozím příkladu `x Is y` vyhodnotí jako `True`, protože obě proměnné odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="ca84d-160">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="ca84d-161">Protějšek tímto výsledkem na následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ca84d-161">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 <span data-ttu-id="ca84d-162">V předchozím příkladu `x Is y` vyhodnotí jako `False`, protože i když proměnné odkazují na objekty stejného typu, odkazují jiné instance daného typu.</span><span class="sxs-lookup"><span data-stu-id="ca84d-162">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="ca84d-163">Pokud chcete otestovat dva objekty není odkazující na stejnou instanci `IsNot` operátor umožňuje vyhnout gramaticky clumsy kombinaci `Not` a `Is`.</span><span class="sxs-lookup"><span data-stu-id="ca84d-163">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="ca84d-164">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ca84d-164">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 <span data-ttu-id="ca84d-165">V předchozím příkladu `If a IsNot b` je ekvivalentní `If Not a Is b`.</span><span class="sxs-lookup"><span data-stu-id="ca84d-165">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="ca84d-166">Porovnání typ objektu</span><span class="sxs-lookup"><span data-stu-id="ca84d-166">Comparing Object Type</span></span>  
 <span data-ttu-id="ca84d-167">Můžete zkontrolovat, zda je objekt určitého typu se `TypeOf`... `Is` výraz.</span><span class="sxs-lookup"><span data-stu-id="ca84d-167">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="ca84d-168">Syntaxe vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="ca84d-168">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="ca84d-169">Když `typename` Určuje typ rozhraní, pak se `TypeOf`... `Is` výraz vrátí `True` Pokud objekt implementuje typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ca84d-169">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="ca84d-170">Když `typename` je typu třídy, pak vrátí výraz `True` Pokud instanci zadané třídy nebo třídy, která je odvozena ze třídy zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="ca84d-170">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="ca84d-171">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ca84d-171">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 <span data-ttu-id="ca84d-172">V předchozím příkladu `TypeOf x Is Control` výraz vyhodnocen jako `True` protože typ `x` je `Button`, který dědí z `Control`.</span><span class="sxs-lookup"><span data-stu-id="ca84d-172">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="ca84d-173">Další informace najdete v tématu [typeof – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ca84d-173">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca84d-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca84d-174">See Also</span></span>  
 [<span data-ttu-id="ca84d-175">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="ca84d-175">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="ca84d-176">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="ca84d-176">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="ca84d-177">Operátory</span><span class="sxs-lookup"><span data-stu-id="ca84d-177">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)  
 [<span data-ttu-id="ca84d-178">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca84d-178">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="ca84d-179">Operátory řetězení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca84d-179">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="ca84d-180">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca84d-180">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
