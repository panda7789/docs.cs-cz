---
title: Operátory porovnání
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
ms.openlocfilehash: bcd51d70c5c7bd08991c7433e244316a82daa9da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371788"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="ac24d-102">Operátory porovnání (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac24d-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="ac24d-103">Níže jsou uvedeny operátory porovnání definované v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac24d-103">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="ac24d-104">`<`podnikatel</span><span class="sxs-lookup"><span data-stu-id="ac24d-104">`<` operator</span></span>

 <span data-ttu-id="ac24d-105">`<=`podnikatel</span><span class="sxs-lookup"><span data-stu-id="ac24d-105">`<=` operator</span></span>

 <span data-ttu-id="ac24d-106">`>`podnikatel</span><span class="sxs-lookup"><span data-stu-id="ac24d-106">`>` operator</span></span>

 <span data-ttu-id="ac24d-107">`>=`podnikatel</span><span class="sxs-lookup"><span data-stu-id="ac24d-107">`>=` operator</span></span>

 <span data-ttu-id="ac24d-108">`=`podnikatel</span><span class="sxs-lookup"><span data-stu-id="ac24d-108">`=` operator</span></span>

 <span data-ttu-id="ac24d-109">`<>`podnikatel</span><span class="sxs-lookup"><span data-stu-id="ac24d-109">`<>` operator</span></span>

 [<span data-ttu-id="ac24d-110">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="ac24d-110">Is Operator</span></span>](is-operator.md)

 [<span data-ttu-id="ac24d-111">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="ac24d-111">IsNot Operator</span></span>](isnot-operator.md)

 [<span data-ttu-id="ac24d-112">Like – operátor</span><span class="sxs-lookup"><span data-stu-id="ac24d-112">Like Operator</span></span>](like-operator.md)

 <span data-ttu-id="ac24d-113">Tyto operátory porovnávají dva výrazy a určí, zda jsou nebo nejsou rovny, a pokud ne, jak se liší.</span><span class="sxs-lookup"><span data-stu-id="ac24d-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="ac24d-114">`Is`, `IsNot` a `Like` jsou podrobněji popsány na samostatných stránkách s usnadněním.</span><span class="sxs-lookup"><span data-stu-id="ac24d-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="ac24d-115">Relační operátory porovnání jsou podrobněji popsány na této stránce.</span><span class="sxs-lookup"><span data-stu-id="ac24d-115">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac24d-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac24d-116">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="ac24d-117">Součásti</span><span class="sxs-lookup"><span data-stu-id="ac24d-117">Parts</span></span>
 `result`  
 <span data-ttu-id="ac24d-118">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac24d-118">Required.</span></span> <span data-ttu-id="ac24d-119">`Boolean`Hodnota představující výsledek porovnání.</span><span class="sxs-lookup"><span data-stu-id="ac24d-119">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="ac24d-120">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="ac24d-120">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="ac24d-121">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac24d-121">Required.</span></span> <span data-ttu-id="ac24d-122">Libovolný výraz</span><span class="sxs-lookup"><span data-stu-id="ac24d-122">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="ac24d-123">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac24d-123">Required.</span></span> <span data-ttu-id="ac24d-124">Jakýkoli relační operátor porovnání.</span><span class="sxs-lookup"><span data-stu-id="ac24d-124">Any relational comparison operator.</span></span>

 <span data-ttu-id="ac24d-125">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="ac24d-125">`object1`, `object2`</span></span>  
 <span data-ttu-id="ac24d-126">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac24d-126">Required.</span></span> <span data-ttu-id="ac24d-127">Názvy referenčních objektů.</span><span class="sxs-lookup"><span data-stu-id="ac24d-127">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="ac24d-128">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac24d-128">Required.</span></span> <span data-ttu-id="ac24d-129">Libovolný `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="ac24d-129">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="ac24d-130">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac24d-130">Required.</span></span> <span data-ttu-id="ac24d-131">Libovolný `String` výraz nebo rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="ac24d-131">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac24d-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac24d-132">Remarks</span></span>
 <span data-ttu-id="ac24d-133">Následující tabulka obsahuje seznam relačních operátorů porovnání a podmínky, které určují, zda `result` jsou `True` nebo `False` .</span><span class="sxs-lookup"><span data-stu-id="ac24d-133">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="ac24d-134">Operátor</span><span class="sxs-lookup"><span data-stu-id="ac24d-134">Operator</span></span>|<span data-ttu-id="ac24d-135">`True`Přestože</span><span class="sxs-lookup"><span data-stu-id="ac24d-135">`True` if</span></span>|<span data-ttu-id="ac24d-136">`False`Přestože</span><span class="sxs-lookup"><span data-stu-id="ac24d-136">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="ac24d-137">`<`(Menší než)</span><span class="sxs-lookup"><span data-stu-id="ac24d-137">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="ac24d-138">`<=`(Je menší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="ac24d-138">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="ac24d-139">`>`(Je větší než)</span><span class="sxs-lookup"><span data-stu-id="ac24d-139">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="ac24d-140">`>=`(Je větší než nebo rovno)</span><span class="sxs-lookup"><span data-stu-id="ac24d-140">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="ac24d-141">`=`(Je rovno)</span><span class="sxs-lookup"><span data-stu-id="ac24d-141">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="ac24d-142">`<>`(Není rovno)</span><span class="sxs-lookup"><span data-stu-id="ac24d-142">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="ac24d-143">[Operátor =](assignment-operator.md) se používá také jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ac24d-143">The [= Operator](assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="ac24d-144">`Is`Operátor, `IsNot` operátor a `Like` operátor mají specifické funkce porovnání, které se liší od operátorů v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="ac24d-144">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="ac24d-145">Porovnávání čísel</span><span class="sxs-lookup"><span data-stu-id="ac24d-145">Comparing Numbers</span></span>
 <span data-ttu-id="ac24d-146">Když porovnáte výraz typu `Single` k jednomu typu `Double` , `Single` je výraz převeden na `Double` .</span><span class="sxs-lookup"><span data-stu-id="ac24d-146">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="ac24d-147">Toto chování je opakem chování zjištěného v Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="ac24d-147">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="ac24d-148">Podobně při porovnání výrazu typu `Decimal` s výrazem typu `Single` nebo `Double` `Decimal` je výraz převeden na `Single` nebo `Double` .</span><span class="sxs-lookup"><span data-stu-id="ac24d-148">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="ac24d-149">U `Decimal` výrazů může dojít ke ztrátě jakékoli desetinné hodnoty menší než 1e-28.</span><span class="sxs-lookup"><span data-stu-id="ac24d-149">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="ac24d-150">Tato ztráta zlomkové hodnoty může způsobit porovnání dvou hodnot, které jsou stejné, pokud nejsou.</span><span class="sxs-lookup"><span data-stu-id="ac24d-150">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="ac24d-151">Z tohoto důvodu byste měli být opatrní při použití rovnosti ( `=` ) pro porovnání dvou proměnných s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="ac24d-151">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="ac24d-152">Je bezpečnější testovat, zda absolutní hodnota rozdílu mezi dvěma čísly je menší než malá přijatelná tolerance.</span><span class="sxs-lookup"><span data-stu-id="ac24d-152">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="ac24d-153">Nepřesnost plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="ac24d-153">Floating-point Imprecision</span></span>
 <span data-ttu-id="ac24d-154">Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že nemají vždy přesnou reprezentaci v paměti.</span><span class="sxs-lookup"><span data-stu-id="ac24d-154">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="ac24d-155">To může vést k neočekávaným výsledkům z určitých operací, jako je porovnání hodnot a [operátor mod](mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ac24d-155">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](mod-operator.md).</span></span> <span data-ttu-id="ac24d-156">Další informace najdete v tématu [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="ac24d-156">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="ac24d-157">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="ac24d-157">Comparing Strings</span></span>
 <span data-ttu-id="ac24d-158">Při porovnávání řetězců jsou řetězcové výrazy vyhodnocovány na základě pořadí řazení podle abecedy, které závisí na `Option Compare` nastavení.</span><span class="sxs-lookup"><span data-stu-id="ac24d-158">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="ac24d-159">`Option Compare Binary`porovnávání řetězců základů v pořadí řazení odvozené z interních binárních reprezentace znaků.</span><span class="sxs-lookup"><span data-stu-id="ac24d-159">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="ac24d-160">Pořadí řazení je určeno znakovou stránkou.</span><span class="sxs-lookup"><span data-stu-id="ac24d-160">The sort order is determined by the code page.</span></span> <span data-ttu-id="ac24d-161">Následující příklad ukazuje typické binární pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="ac24d-161">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="ac24d-162">`Option Compare Text`porovnávání řetězců základů nerozlišuje velká a malá písmena. určuje pořadí řazení textu určené národním prostředím vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ac24d-162">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="ac24d-163">Při nastavování `Option Compare Text` a řazení znaků v předchozím příkladu platí následující pořadí řazení textu:</span><span class="sxs-lookup"><span data-stu-id="ac24d-163">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="ac24d-164">Závislost národního prostředí</span><span class="sxs-lookup"><span data-stu-id="ac24d-164">Locale Dependence</span></span>
 <span data-ttu-id="ac24d-165">Když nastavíte `Option Compare Text` , výsledek porovnání řetězců může záviset na národním prostředí, ve kterém je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="ac24d-165">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="ac24d-166">Dva znaky se můžou porovnat stejně jako v jednom národním prostředí, ale ne v jiném.</span><span class="sxs-lookup"><span data-stu-id="ac24d-166">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="ac24d-167">Pokud používáte porovnání řetězců k rozhodování o důležitých rozhodnutích, například o tom, jestli se má přijmout pokus o přihlášení, měli byste být upozorňováni na citlivost národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="ac24d-167">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="ac24d-168">Zvažte buď nastavení `Option Compare Binary` , nebo volání metody <xref:Microsoft.VisualBasic.Strings.StrComp%2A> , která vezme národní prostředí v úvahu.</span><span class="sxs-lookup"><span data-stu-id="ac24d-168">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="ac24d-169">Programování bez beztypových relačních operátorů porovnání</span><span class="sxs-lookup"><span data-stu-id="ac24d-169">Typeless Programming with Relational Comparison Operators</span></span>
 <span data-ttu-id="ac24d-170">Použití relačních operátorů porovnání s `Object` výrazy není v rámci povoleno `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="ac24d-170">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="ac24d-171">Když `Option Strict` je `Off` , a buď `expression1` nebo `expression2` je `Object` výraz, běhové typy určují, jak jsou porovnány.</span><span class="sxs-lookup"><span data-stu-id="ac24d-171">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="ac24d-172">Následující tabulka ukazuje, jak jsou porovnány výrazy a výsledek porovnání v závislosti na typu modulu runtime operandů.</span><span class="sxs-lookup"><span data-stu-id="ac24d-172">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="ac24d-173">Pokud jsou operandy</span><span class="sxs-lookup"><span data-stu-id="ac24d-173">If operands are</span></span>|<span data-ttu-id="ac24d-174">Porovnání je</span><span class="sxs-lookup"><span data-stu-id="ac24d-174">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="ac24d-175">Protokoly`String`</span><span class="sxs-lookup"><span data-stu-id="ac24d-175">Both `String`</span></span>|<span data-ttu-id="ac24d-176">Porovnání řazení založené na charakteristikách řazení řetězců.</span><span class="sxs-lookup"><span data-stu-id="ac24d-176">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="ac24d-177">Oba číslice</span><span class="sxs-lookup"><span data-stu-id="ac24d-177">Both numeric</span></span>|<span data-ttu-id="ac24d-178">Objekty převedené na `Double` číselné porovnání</span><span class="sxs-lookup"><span data-stu-id="ac24d-178">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="ac24d-179">Jedna číselná a jedna`String`</span><span class="sxs-lookup"><span data-stu-id="ac24d-179">One numeric and one `String`</span></span>|<span data-ttu-id="ac24d-180">Je `String` proveden převod na `Double` číselné porovnání.</span><span class="sxs-lookup"><span data-stu-id="ac24d-180">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="ac24d-181">Pokud `String` nelze převést na `Double` , <xref:System.InvalidCastException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ac24d-181">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="ac24d-182">Oba typy odkazují na jiné než`String`</span><span class="sxs-lookup"><span data-stu-id="ac24d-182">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="ac24d-183"><xref:System.InvalidCastException>Je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ac24d-183">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="ac24d-184">Číselná porovnání se považují `Nothing` za 0.</span><span class="sxs-lookup"><span data-stu-id="ac24d-184">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="ac24d-185">Porovnávání řetězců považuje `Nothing` za `""` (prázdný řetězec).</span><span class="sxs-lookup"><span data-stu-id="ac24d-185">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="ac24d-186">Přetížení</span><span class="sxs-lookup"><span data-stu-id="ac24d-186">Overloading</span></span>
 <span data-ttu-id="ac24d-187">Relační operátory porovnání ( `<` .</span><span class="sxs-lookup"><span data-stu-id="ac24d-187">The relational comparison operators (`<`.</span></span> <span data-ttu-id="ac24d-188">`<=`, `>` , `>=` , `=` , `<>` ) mohou být *přetíženy*, což znamená, že třída nebo struktura může předefinovat jejich chování, pokud operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="ac24d-188">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ac24d-189">Pokud váš kód používá některý z těchto operátorů v takové třídě nebo struktuře, ujistěte se, že rozumíte předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="ac24d-189">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="ac24d-190">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ac24d-190">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="ac24d-191">Všimněte si, že [operátor =](assignment-operator.md) může být přetížen pouze jako relační operátor porovnání, nikoli jako operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ac24d-191">Notice that the [= Operator](assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="ac24d-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac24d-192">Example</span></span>
 <span data-ttu-id="ac24d-193">Následující příklad ukazuje různé způsoby použití relačních relačních operátorů, které slouží k porovnání výrazů.</span><span class="sxs-lookup"><span data-stu-id="ac24d-193">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="ac24d-194">Relační operátory porovnání vracejí `Boolean` výsledek, který představuje, zda se vyhodnocuje uvedený výraz `True` .</span><span class="sxs-lookup"><span data-stu-id="ac24d-194">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="ac24d-195">Použijete-li `>` `<` operátory a na řetězce, bude porovnání provedeno pomocí normálního pořadí řazení řetězců v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="ac24d-195">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="ac24d-196">Tato objednávka může být závislá na nastavení národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="ac24d-196">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="ac24d-197">Bez ohledu na to, zda řazení rozlišuje velká a malá písmena, závisí na nastavení [Možnosti porovnat](../statements/option-compare-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="ac24d-197">Whether the sort is case-sensitive or not depends on the [Option Compare](../statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="ac24d-198">V předchozím příkladu se první porovnávání vrátí `False` a zbývající porovnání vrátí `True` .</span><span class="sxs-lookup"><span data-stu-id="ac24d-198">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac24d-199">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac24d-199">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="ac24d-200">= – Operátor</span><span class="sxs-lookup"><span data-stu-id="ac24d-200">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="ac24d-201">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac24d-201">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ac24d-202">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ac24d-202">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ac24d-203">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="ac24d-203">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="ac24d-204">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac24d-204">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
