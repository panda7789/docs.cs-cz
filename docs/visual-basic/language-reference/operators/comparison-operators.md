---
title: Operátory porovnání (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 4e37f55b4c873c3dbea22a8edf0e5e2b58824720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604923"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="91f72-102">Operátory porovnání (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91f72-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="91f72-103">Níže jsou uvedeny operátory porovnání definované v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="91f72-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="91f72-104">`<` Operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-104">`<` operator</span></span>  
  
 <span data-ttu-id="91f72-105">`<=` Operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-105">`<=` operator</span></span>  
  
 <span data-ttu-id="91f72-106">`>` Operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-106">`>` operator</span></span>  
  
 <span data-ttu-id="91f72-107">`>=` Operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-107">`>=` operator</span></span>  
  
 <span data-ttu-id="91f72-108">`=` Operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-108">`=` operator</span></span>  
  
 <span data-ttu-id="91f72-109">`<>` Operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="91f72-110">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="91f72-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="91f72-111">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="91f72-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="91f72-112">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="91f72-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="91f72-113">Tyto operátory porovnání dvou výrazů k určení, zda jsou stejné, a pokud ne, jak se liší.</span><span class="sxs-lookup"><span data-stu-id="91f72-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="91f72-114">`Is`, `IsNot`, a `Like` jsou podrobně popsané na samostatné stránky nápovědy.</span><span class="sxs-lookup"><span data-stu-id="91f72-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="91f72-115">Relační relační operátory jsou podrobně popsané na této stránce.</span><span class="sxs-lookup"><span data-stu-id="91f72-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f72-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91f72-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="91f72-117">Součásti</span><span class="sxs-lookup"><span data-stu-id="91f72-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="91f72-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="91f72-118">Required.</span></span> <span data-ttu-id="91f72-119">A `Boolean` hodnotu představující výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="91f72-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="91f72-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="91f72-120">Required.</span></span> <span data-ttu-id="91f72-121">Jakýkoli výraz.</span><span class="sxs-lookup"><span data-stu-id="91f72-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="91f72-122">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="91f72-122">Required.</span></span> <span data-ttu-id="91f72-123">Libovolný relační operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="91f72-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="91f72-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="91f72-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="91f72-125">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="91f72-125">Required.</span></span> <span data-ttu-id="91f72-126">Všechny názvy objektů odkaz.</span><span class="sxs-lookup"><span data-stu-id="91f72-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="91f72-127">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="91f72-127">Required.</span></span> <span data-ttu-id="91f72-128">Všechny `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="91f72-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="91f72-129">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="91f72-129">Required.</span></span> <span data-ttu-id="91f72-130">Všechny `String` výraz nebo rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="91f72-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91f72-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91f72-131">Remarks</span></span>  
 <span data-ttu-id="91f72-132">Následující tabulka obsahuje seznam relační relační operátory a podmínky určující, zda `result` je `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="91f72-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="91f72-133">Operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-133">Operator</span></span>|<span data-ttu-id="91f72-134">`True` Pokud</span><span class="sxs-lookup"><span data-stu-id="91f72-134">`True` if</span></span>|<span data-ttu-id="91f72-135">`False` Pokud</span><span class="sxs-lookup"><span data-stu-id="91f72-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="91f72-136">`<` (Méně než)</span><span class="sxs-lookup"><span data-stu-id="91f72-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="91f72-137">`<=` (Je menší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="91f72-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="91f72-138">`>` (Větší než)</span><span class="sxs-lookup"><span data-stu-id="91f72-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="91f72-139">`>=` (Je větší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="91f72-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="91f72-140">`=` (Rovno)</span><span class="sxs-lookup"><span data-stu-id="91f72-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="91f72-141">`<>` (Není rovno)</span><span class="sxs-lookup"><span data-stu-id="91f72-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="91f72-142">[= – Operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) se používá jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="91f72-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="91f72-143">`Is` Operátor, `IsNot` operátor a `Like` operátor mají konkrétní porovnání funkcí, které se liší od operátory v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="91f72-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="91f72-144">Porovnání čísla</span><span class="sxs-lookup"><span data-stu-id="91f72-144">Comparing Numbers</span></span>  
 <span data-ttu-id="91f72-145">Při porovnání výrazu typu `Single` na jednu z typu `Double`, `Single` výrazu je převést na `Double`.</span><span class="sxs-lookup"><span data-stu-id="91f72-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="91f72-146">Toto chování je opačné tomuto chování dochází v jazyce Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="91f72-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="91f72-147">Podobně když porovnání výrazu typu `Decimal` do výrazu typu `Single` nebo `Double`, `Decimal` výrazu je převést na `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="91f72-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="91f72-148">Pro `Decimal` výrazy, všechny desetinnou hodnotu menší než 1E-28 mohou být ztraceny.</span><span class="sxs-lookup"><span data-stu-id="91f72-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="91f72-149">Takové ztrátě desetinnou hodnotu, může způsobit dvě hodnoty k porovnání jako s rovnocennými, když se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="91f72-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="91f72-150">Z tohoto důvodu můžete dbát na při použití rovnosti (`=`) k porovnání dvou proměnné s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="91f72-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="91f72-151">Je bezpečnější a otestovat, jestli absolutní hodnotu rozdíl mezi dvěma čísly je menší než malé přípustné tolerance.</span><span class="sxs-lookup"><span data-stu-id="91f72-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="91f72-152">S plovoucí desetinnou čárkou nepřesnosti</span><span class="sxs-lookup"><span data-stu-id="91f72-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="91f72-153">Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají znázornění přesné v paměti.</span><span class="sxs-lookup"><span data-stu-id="91f72-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="91f72-154">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a [Mod operátor](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="91f72-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="91f72-155">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="91f72-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="91f72-156">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="91f72-156">Comparing Strings</span></span>  
 <span data-ttu-id="91f72-157">Při porovnávání řetězců se vyhodnotí výrazy řetězec na jejich abecedním pořadí, což závisí na základě `Option Compare` nastavení.</span><span class="sxs-lookup"><span data-stu-id="91f72-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="91f72-158">`Option Compare Binary` základů řetězec porovnání na pořadí řazení odvozené z interní binární reprezentace znaky.</span><span class="sxs-lookup"><span data-stu-id="91f72-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="91f72-159">Pořadí řazení je určen podle znakové stránky.</span><span class="sxs-lookup"><span data-stu-id="91f72-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="91f72-160">Následující příklad ukazuje typické binární řazení.</span><span class="sxs-lookup"><span data-stu-id="91f72-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="91f72-161">`Option Compare Text` základů řetězec porovnání na pořadí řazení velká a malá písmena, textovou dáno národního prostředí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="91f72-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="91f72-162">Když nastavíte `Option Compare Text` a seřadit znaky v předchozím příkladu, platí následující pořadí řazení text:</span><span class="sxs-lookup"><span data-stu-id="91f72-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="91f72-163">Závislost na národním prostředí</span><span class="sxs-lookup"><span data-stu-id="91f72-163">Locale Dependence</span></span>  
 <span data-ttu-id="91f72-164">Když nastavíte `Option Compare Text`, výsledku porovnání řetězců, může záviset na národním prostředí, ve kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="91f72-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="91f72-165">Dva znaky může porovnat jako rovná jeden národního prostředí, ale ne v jiném.</span><span class="sxs-lookup"><span data-stu-id="91f72-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="91f72-166">Pokud používáte porovnání řetězců učinění důležitých rozhodnutí, jako je například, jestli se má přijmout pokus o přihlášení, musí být výstraha národního prostředí velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="91f72-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="91f72-167">Vezměte v úvahu buď nastavení `Option Compare Binary` nebo volání <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, který bere v úvahu národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="91f72-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="91f72-168">Programování bez psaní s porovnání relační operátory</span><span class="sxs-lookup"><span data-stu-id="91f72-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="91f72-169">Použití operátorů relační porovnání s `Object` výrazy není povolen v kontextu `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="91f72-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="91f72-170">Když `Option Strict` je `Off`a buď `expression1` nebo `expression2` je `Object` výrazu typy spuštění určují, jak jsou porovnávány.</span><span class="sxs-lookup"><span data-stu-id="91f72-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="91f72-171">V následující tabulce jsou uvedeny porovnání výrazy a výsledek z porovnání, v závislosti na typu runtime operandy.</span><span class="sxs-lookup"><span data-stu-id="91f72-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="91f72-172">Pokud jsou operandy</span><span class="sxs-lookup"><span data-stu-id="91f72-172">If operands are</span></span>|<span data-ttu-id="91f72-173">Porovnání se</span><span class="sxs-lookup"><span data-stu-id="91f72-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="91f72-174">Obě `String`</span><span class="sxs-lookup"><span data-stu-id="91f72-174">Both `String`</span></span>|<span data-ttu-id="91f72-175">Seřadí porovnání založené na řetězci řazení charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="91f72-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="91f72-176">Jedná se o číselné</span><span class="sxs-lookup"><span data-stu-id="91f72-176">Both numeric</span></span>|<span data-ttu-id="91f72-177">Objekty převést na `Double`, číselné porovnání.</span><span class="sxs-lookup"><span data-stu-id="91f72-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="91f72-178">Jedna číslice a jeden `String`</span><span class="sxs-lookup"><span data-stu-id="91f72-178">One numeric and one `String`</span></span>|<span data-ttu-id="91f72-179">`String` Jsou převedeny na `Double` a je provedeno číselné porovnání.</span><span class="sxs-lookup"><span data-stu-id="91f72-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="91f72-180">Pokud `String` nelze převést na `Double`, <xref:System.InvalidCastException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="91f72-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="91f72-181">Odkazové typy jiné než je buď nebo obě `String`</span><span class="sxs-lookup"><span data-stu-id="91f72-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="91f72-182"><xref:System.InvalidCastException> Je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="91f72-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="91f72-183">Číselné porovnání považovat `Nothing` jako 0.</span><span class="sxs-lookup"><span data-stu-id="91f72-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="91f72-184">Porovnání řetězců považovat `Nothing` jako `""` (prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="91f72-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="91f72-185">Přetížení</span><span class="sxs-lookup"><span data-stu-id="91f72-185">Overloading</span></span>  
 <span data-ttu-id="91f72-186">Porovnání relační operátory (`<`.</span><span class="sxs-lookup"><span data-stu-id="91f72-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="91f72-187">`<=``>`, `>=`, `=`, `<>`) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat jejich chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="91f72-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="91f72-188">Pokud váš kód používá některé z těchto operátorů na takové třídu nebo strukturu, ujistěte se, že rozumíte Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="91f72-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="91f72-189">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="91f72-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="91f72-190">Všimněte si, že [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) může být přetížené pouze jako operátor porovnání relační, ne jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="91f72-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91f72-191">Příklad</span><span class="sxs-lookup"><span data-stu-id="91f72-191">Example</span></span>  
 <span data-ttu-id="91f72-192">Následující příklad ukazuje různé používá relační relační operátory, které můžete použít k porovnání výrazy.</span><span class="sxs-lookup"><span data-stu-id="91f72-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="91f72-193">Vrátí porovnání relační operátory `Boolean` výsledek, který představuje zda stanovené výraz vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="91f72-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="91f72-194">Pokud použijete `>` a `<` operátorům řetězce, porovnání se provádí pomocí normální abecedním pořadí řazení řetězců.</span><span class="sxs-lookup"><span data-stu-id="91f72-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="91f72-195">Toto pořadí může být závislá na vaše nastavení národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="91f72-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="91f72-196">Řazení není jestli malá a velká písmena, nebo není závislá [možnost porovnat](../../../visual-basic/language-reference/statements/option-compare-statement.md) nastavení.</span><span class="sxs-lookup"><span data-stu-id="91f72-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="91f72-197">V předchozím příkladu, vrátí první porovnání `False` a vrátit zbývající porovnání `True`.</span><span class="sxs-lookup"><span data-stu-id="91f72-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f72-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="91f72-198">See Also</span></span>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="91f72-199">= – operátor</span><span class="sxs-lookup"><span data-stu-id="91f72-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="91f72-200">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91f72-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="91f72-201">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="91f72-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="91f72-202">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="91f72-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="91f72-203">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91f72-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
