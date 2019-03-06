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
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: c8835d1c42a02fa65e9acc9bd1c1f06fcfd4af02
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359819"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="5e57a-102">Operátory porovnání (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e57a-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="5e57a-103">Níže jsou operátory porovnání, které jsou definovány v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5e57a-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="5e57a-104">`<` – Operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-104">`<` operator</span></span>  
  
 <span data-ttu-id="5e57a-105">`<=` – Operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-105">`<=` operator</span></span>  
  
 <span data-ttu-id="5e57a-106">`>` – Operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-106">`>` operator</span></span>  
  
 <span data-ttu-id="5e57a-107">`>=` – Operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-107">`>=` operator</span></span>  
  
 <span data-ttu-id="5e57a-108">`=` – Operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-108">`=` operator</span></span>  
  
 <span data-ttu-id="5e57a-109">`<>` – Operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="5e57a-110">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="5e57a-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="5e57a-111">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="5e57a-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="5e57a-112">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="5e57a-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="5e57a-113">Tyto operátory porovnávají dva výrazy k určení, zda jsou stejné, a pokud ne, jak se liší.</span><span class="sxs-lookup"><span data-stu-id="5e57a-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="5e57a-114">`Is`, `IsNot`, a `Like` jsou podrobně popsány v na samostatných stránkách nápovědy.</span><span class="sxs-lookup"><span data-stu-id="5e57a-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="5e57a-115">Relační porovnávací operátory jsou podrobně popsány v na této stránce.</span><span class="sxs-lookup"><span data-stu-id="5e57a-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e57a-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e57a-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="5e57a-117">Součásti</span><span class="sxs-lookup"><span data-stu-id="5e57a-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="5e57a-118">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5e57a-118">Required.</span></span> <span data-ttu-id="5e57a-119">A `Boolean` hodnotu představující výsledek porovnání.</span><span class="sxs-lookup"><span data-stu-id="5e57a-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="5e57a-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5e57a-120">Required.</span></span> <span data-ttu-id="5e57a-121">Libovolný výraz.</span><span class="sxs-lookup"><span data-stu-id="5e57a-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="5e57a-122">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5e57a-122">Required.</span></span> <span data-ttu-id="5e57a-123">Libovolný relační operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="5e57a-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="5e57a-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="5e57a-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="5e57a-125">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5e57a-125">Required.</span></span> <span data-ttu-id="5e57a-126">Všechny odkazy názvy objektů.</span><span class="sxs-lookup"><span data-stu-id="5e57a-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="5e57a-127">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5e57a-127">Required.</span></span> <span data-ttu-id="5e57a-128">Žádné `String` výrazu.</span><span class="sxs-lookup"><span data-stu-id="5e57a-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="5e57a-129">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5e57a-129">Required.</span></span> <span data-ttu-id="5e57a-130">Žádné `String` výraz nebo rozsahu znaků.</span><span class="sxs-lookup"><span data-stu-id="5e57a-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e57a-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e57a-131">Remarks</span></span>  
 <span data-ttu-id="5e57a-132">Následující tabulka obsahuje seznam relační relační operátory a podmínky, které určují, jestli `result` je `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="5e57a-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="5e57a-133">Operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-133">Operator</span></span>|<span data-ttu-id="5e57a-134">`True` If</span><span class="sxs-lookup"><span data-stu-id="5e57a-134">`True` if</span></span>|<span data-ttu-id="5e57a-135">`False` If</span><span class="sxs-lookup"><span data-stu-id="5e57a-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="5e57a-136">`<` (Méně než)</span><span class="sxs-lookup"><span data-stu-id="5e57a-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="5e57a-137">`<=` (Menší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="5e57a-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="5e57a-138">`>` (Větší než)</span><span class="sxs-lookup"><span data-stu-id="5e57a-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="5e57a-139">`>=` (Větší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="5e57a-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="5e57a-140">`=` (Rovná se)</span><span class="sxs-lookup"><span data-stu-id="5e57a-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="5e57a-141">`<>` (Není rovno)</span><span class="sxs-lookup"><span data-stu-id="5e57a-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="5e57a-142">[= – Operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) slouží také jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="5e57a-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="5e57a-143">`Is` Operátoru `IsNot` operátor a `Like` operátor mít konkrétní porovnání funkcí, které se liší od operátorů v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="5e57a-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="5e57a-144">Porovnání čísel</span><span class="sxs-lookup"><span data-stu-id="5e57a-144">Comparing Numbers</span></span>  
 <span data-ttu-id="5e57a-145">Při porovnávání výraz typu `Single` do jednoho typu `Double`, `Single` výrazu je převedena na `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e57a-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="5e57a-146">Toto chování je než tomuto chování dochází v jazyce Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="5e57a-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="5e57a-147">Podobně při porovnávání výraz typu `Decimal` ve výrazu typu `Single` nebo `Double`, `Decimal` výrazu je převedena na `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e57a-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="5e57a-148">Pro `Decimal` výrazy, všechny desetinná hodnota menší než 1E-28 může být ztracené.</span><span class="sxs-lookup"><span data-stu-id="5e57a-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="5e57a-149">Takové ztrátě desetinná hodnota může způsobit, že dvě hodnoty a vyhodnoceny jako shodné, když se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="5e57a-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="5e57a-150">Z tohoto důvodu, které byste měli věnovat pozornost při použití rovnosti (`=`) Chcete-li porovnat dvě proměnné s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="5e57a-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="5e57a-151">Je bezpečnější k ověření, zda absolutní hodnota rozdílu daných dvou čísel je menší než malé přípustné.</span><span class="sxs-lookup"><span data-stu-id="5e57a-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="5e57a-152">S plovoucí desetinnou čárkou nepřesnost</span><span class="sxs-lookup"><span data-stu-id="5e57a-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="5e57a-153">Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají přesnou reprezentací v paměti.</span><span class="sxs-lookup"><span data-stu-id="5e57a-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="5e57a-154">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a [Mod operátor](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5e57a-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="5e57a-155">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="5e57a-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="5e57a-156">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="5e57a-156">Comparing Strings</span></span>  
 <span data-ttu-id="5e57a-157">Při porovnávání řetězců řetězcové výrazy jsou vyhodnocovány v pořadí jejich abecední řazení, která závisí na `Option Compare` nastavení.</span><span class="sxs-lookup"><span data-stu-id="5e57a-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="5e57a-158">`Option Compare Binary` na pořadí řazení odvozený z vnitřní binární reprezentace znaků při porovnávání řetězců základních tříd.</span><span class="sxs-lookup"><span data-stu-id="5e57a-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="5e57a-159">Pořadí řazení se určuje podle kódové stránky.</span><span class="sxs-lookup"><span data-stu-id="5e57a-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="5e57a-160">Následující příklad ukazuje typické binární řazení.</span><span class="sxs-lookup"><span data-stu-id="5e57a-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="5e57a-161">`Option Compare Text` Při porovnávání na určené národní prostředí vaší aplikace velkých a malých písmen, textové řazení řetězců základních tříd.</span><span class="sxs-lookup"><span data-stu-id="5e57a-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="5e57a-162">Pokud nastavíte `Option Compare Text` a řazení znaků v předchozím příkladu, použije textové řazení:</span><span class="sxs-lookup"><span data-stu-id="5e57a-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="5e57a-163">Závislost na národním prostředí</span><span class="sxs-lookup"><span data-stu-id="5e57a-163">Locale Dependence</span></span>  
 <span data-ttu-id="5e57a-164">Pokud nastavíte `Option Compare Text`, výsledku porovnání řetězců může záviset na národním prostředí, ve kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="5e57a-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="5e57a-165">Stejné jedno prostředí, ale není v druhém může porovnat dva znaky.</span><span class="sxs-lookup"><span data-stu-id="5e57a-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="5e57a-166">Pokud používáte porovnání řetězců učinění důležitých rozhodnutí, jako je například, jestli se má přijmout pokus o přihlášení, musí být výstraha citlivosti národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="5e57a-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="5e57a-167">Vezměte v úvahu buď nastavení `Option Compare Binary` nebo volání <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, který bere v úvahu národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="5e57a-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="5e57a-168">Programování bez psaní s relačními relační operátory</span><span class="sxs-lookup"><span data-stu-id="5e57a-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="5e57a-169">Použití operátorů relační porovnání s `Object` výrazů není povolen v kontextu `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="5e57a-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="5e57a-170">Když `Option Strict` je `Off`a buď `expression1` nebo `expression2` je `Object` výrazu, typy za běhu zjistit, jak jsou porovnány.</span><span class="sxs-lookup"><span data-stu-id="5e57a-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="5e57a-171">V následující tabulce najdete porovnání výrazy a výsledkem porovnání, v závislosti na typu runtime z operandů.</span><span class="sxs-lookup"><span data-stu-id="5e57a-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="5e57a-172">Pokud jsou operandy</span><span class="sxs-lookup"><span data-stu-id="5e57a-172">If operands are</span></span>|<span data-ttu-id="5e57a-173">Porovnání</span><span class="sxs-lookup"><span data-stu-id="5e57a-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="5e57a-174">Obojí `String`</span><span class="sxs-lookup"><span data-stu-id="5e57a-174">Both `String`</span></span>|<span data-ttu-id="5e57a-175">Seřadit podle vlastnosti řazení řetězců porovnání.</span><span class="sxs-lookup"><span data-stu-id="5e57a-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="5e57a-176">Číselné</span><span class="sxs-lookup"><span data-stu-id="5e57a-176">Both numeric</span></span>|<span data-ttu-id="5e57a-177">Objekty převedeny na `Double`, číselné porovnání.</span><span class="sxs-lookup"><span data-stu-id="5e57a-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="5e57a-178">Jedna číslice a jeden `String`</span><span class="sxs-lookup"><span data-stu-id="5e57a-178">One numeric and one `String`</span></span>|<span data-ttu-id="5e57a-179">`String` Je převedena na `Double` a číselné porovnání je provedeno.</span><span class="sxs-lookup"><span data-stu-id="5e57a-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="5e57a-180">Pokud `String` nelze převést na `Double`, <xref:System.InvalidCastException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="5e57a-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="5e57a-181">Jeden nebo oba jsou odkazové typy jiné než `String`</span><span class="sxs-lookup"><span data-stu-id="5e57a-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="5e57a-182"><xref:System.InvalidCastException> Je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="5e57a-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="5e57a-183">Číselné porovnání považovat `Nothing` jako 0.</span><span class="sxs-lookup"><span data-stu-id="5e57a-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="5e57a-184">Porovnávání řetězců považovat `Nothing` jako `""` (prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="5e57a-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5e57a-185">Přetížení</span><span class="sxs-lookup"><span data-stu-id="5e57a-185">Overloading</span></span>  
 <span data-ttu-id="5e57a-186">Relační porovnávací operátory (`<`.</span><span class="sxs-lookup"><span data-stu-id="5e57a-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="5e57a-187">`<=``>`, `>=`, `=`, `<>`) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jejich chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="5e57a-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5e57a-188">Pokud váš kód používá některou z těchto operátorů na takové třídy nebo struktury, ujistěte se, že rozumíte Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="5e57a-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="5e57a-189">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5e57a-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="5e57a-190">Všimněte si, [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md) může být přetížená pouze jako operátor porovnání relační, nikoli jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="5e57a-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e57a-191">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e57a-191">Example</span></span>  
 <span data-ttu-id="5e57a-192">Následující příklad ukazuje různé možnosti použití relační porovnávací operátory, které můžete použít k porovnání výrazy.</span><span class="sxs-lookup"><span data-stu-id="5e57a-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="5e57a-193">Vrátí relační relační operátory `Boolean` výsledek, který představuje zda uvedená výraz je vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="5e57a-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="5e57a-194">Pokud použijete `>` a `<` operátory na řetězce, je provedeno porovnání použitím normální abecedním pořadí řazení řetězců.</span><span class="sxs-lookup"><span data-stu-id="5e57a-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="5e57a-195">Toto pořadí může být závislé na nastavení národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="5e57a-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="5e57a-196">Určuje, zda je řazení malá a velká písmena nebo není závislá [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) nastavení.</span><span class="sxs-lookup"><span data-stu-id="5e57a-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 <span data-ttu-id="5e57a-197">V předchozím příkladu vrátí první porovnání `False` a vrátit zbývající porovnání `True`.</span><span class="sxs-lookup"><span data-stu-id="5e57a-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e57a-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e57a-198">See also</span></span>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="5e57a-199">= – operátor</span><span class="sxs-lookup"><span data-stu-id="5e57a-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="5e57a-200">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e57a-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5e57a-201">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="5e57a-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5e57a-202">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="5e57a-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="5e57a-203">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e57a-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
