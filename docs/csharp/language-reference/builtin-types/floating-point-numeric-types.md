---
title: Číselné typy s plovoucí desetinnou čárkou - C# odkaz
description: Přehled vestavěné typy C# s plovoucí desetinnou čárkou
ms.date: 06/30/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664206"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="d5451-103">Číselné typy s plovoucí desetinnou čárkou (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="d5451-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="d5451-104">**Typy s plovoucí desetinnou čárkou** jsou podmnožinou **jednoduché typy** a mohou být inicializovány pomocí [ *literály*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="d5451-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="d5451-105">Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="d5451-105">All floating-point types are also value types.</span></span> <span data-ttu-id="d5451-106">Všechny číselné typy s plovoucí desetinnou čárkou podporují [aritmetické](../operators/arithmetic-operators.md) [porovnání a rovnost](../operators/equality-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="d5451-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md) [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

<span data-ttu-id="d5451-107">V následující tabulce jsou uvedeny přesnosti a přibližné rozsahy typů s plovoucí desetinnou čárkou:</span><span class="sxs-lookup"><span data-stu-id="d5451-107">The following table shows the precision and approximate ranges for the floating-point types:</span></span>
  
|<span data-ttu-id="d5451-108">type</span><span class="sxs-lookup"><span data-stu-id="d5451-108">Type</span></span>|<span data-ttu-id="d5451-109">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="d5451-109">Approximate range</span></span>|<span data-ttu-id="d5451-110">Přesnost</span><span class="sxs-lookup"><span data-stu-id="d5451-110">Precision</span></span>|  
|----------|-----------------------|---------------|  
|`float`|<span data-ttu-id="d5451-111">±1.5 x 10<sup>−45</sup> k ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="d5451-111">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="d5451-112">~ 6. až 9 číslic</span><span class="sxs-lookup"><span data-stu-id="d5451-112">~6-9 digits</span></span>|  
|`double`|<span data-ttu-id="d5451-113">±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="d5451-113">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="d5451-114">~ 15-17 číslic</span><span class="sxs-lookup"><span data-stu-id="d5451-114">~15-17 digits</span></span>|  
|`decimal`|<span data-ttu-id="d5451-115">±1.0 x 10<sup>– 28</sup> k ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="d5451-115">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="d5451-116">28 – 29 číslic</span><span class="sxs-lookup"><span data-stu-id="d5451-116">28-29 digits</span></span>|  

<span data-ttu-id="d5451-117">Výchozí hodnota pro všechny typy s plovoucí desetinnou čárkou je `0`.</span><span class="sxs-lookup"><span data-stu-id="d5451-117">The default value for all floating-point types is `0`.</span></span> <span data-ttu-id="d5451-118">Každý z typů s plovoucí desetinnou čárkou se konstanty s názvem `MinValue` a `MaxValue` pro minimální a maximální hodnotu daného typu.</span><span class="sxs-lookup"><span data-stu-id="d5451-118">Each of the floating-point types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span> <span data-ttu-id="d5451-119">`float` a `double` typy mají další konstanty pro `PositiveInfinity`, `NegativeInfinity`, a `NaN` (pro "nejedná se číslo").</span><span class="sxs-lookup"><span data-stu-id="d5451-119">The `float` and `double` types have additional constants for `PositiveInfinity`, `NegativeInfinity`, and `NaN` (for "Not a Number").</span></span> <span data-ttu-id="d5451-120">`decimal` Typ obsahuje konstanty pro `Zero`, `One`, a `MinusOne`.</span><span class="sxs-lookup"><span data-stu-id="d5451-120">The `decimal` type includes constants for `Zero`, `One`, and `MinusOne`.</span></span>

<span data-ttu-id="d5451-121">`decimal` Typ má větší přesnost a má menší rozsah než obě `float` a `double`, takže je vhodné pro výpočty finančních a přepočty měn.</span><span class="sxs-lookup"><span data-stu-id="d5451-121">The `decimal` type has more precision and a smaller range than both `float` and `double`, which makes it appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="d5451-122">Integrální typy a typy s plovoucí desetinnou čárkou ve výrazu můžete kombinovat.</span><span class="sxs-lookup"><span data-stu-id="d5451-122">You can mix integral types and floating-point types in an expression.</span></span> <span data-ttu-id="d5451-123">V takovém případě integrální typy jsou převedeny na typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="d5451-123">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="d5451-124">Vyhodnocení výrazu se provádí dle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="d5451-124">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="d5451-125">Pokud jeden z typů s plovoucí desetinnou čárkou je `double`, je výraz vyhodnocen `double`, nebo [bool](../keywords/bool.md) v relační porovnání nebo porovnání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="d5451-125">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="d5451-126">Pokud není žádný `double` zadejte výraz, výraz je vyhodnocen jako `float`, nebo [bool](../keywords/bool.md) v relační porovnání nebo porovnání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="d5451-126">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="d5451-127">Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:</span><span class="sxs-lookup"><span data-stu-id="d5451-127">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="d5451-128">Kladnou a zápornou nulou</span><span class="sxs-lookup"><span data-stu-id="d5451-128">Positive and negative zero</span></span>
- <span data-ttu-id="d5451-129">Kladné a záporné nekonečno.</span><span class="sxs-lookup"><span data-stu-id="d5451-129">Positive and negative infinity</span></span>
- <span data-ttu-id="d5451-130">Hodnota not-a-Number (NaN)</span><span class="sxs-lookup"><span data-stu-id="d5451-130">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="d5451-131">Konečná sada nenulové hodnoty</span><span class="sxs-lookup"><span data-stu-id="d5451-131">The finite set of nonzero values</span></span>

<span data-ttu-id="d5451-132">Další informace o těchto hodnotách naleznete v části Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](https://www.ieee.org) webu.</span><span class="sxs-lookup"><span data-stu-id="d5451-132">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="d5451-133">Můžete použít buď [řetězce standardního číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md) nebo [vlastní řetězce číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) pro formátování hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="d5451-133">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="d5451-134">Literály s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="d5451-134">Floating-point literals</span></span>

<span data-ttu-id="d5451-135">Ve výchozím nastavení, je číselný literál s plovoucí desetinnou čárkou na pravé straně operátoru považováno za `double`.</span><span class="sxs-lookup"><span data-stu-id="d5451-135">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="d5451-136">Můžete převést literál s plovoucí desetinnou čárkou nebo celočíselné na konkrétní typ přípony:</span><span class="sxs-lookup"><span data-stu-id="d5451-136">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="d5451-137">`d` Nebo `D` přípona převede na literál `double`.</span><span class="sxs-lookup"><span data-stu-id="d5451-137">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="d5451-138">`f` Nebo `F` přípona převede na literál `float`.</span><span class="sxs-lookup"><span data-stu-id="d5451-138">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="d5451-139">`m` Nebo `M` přípona převede na literál `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d5451-139">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="d5451-140">Následující příklady ukazují jednotlivých přípon:</span><span class="sxs-lookup"><span data-stu-id="d5451-140">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="d5451-141">Převody</span><span class="sxs-lookup"><span data-stu-id="d5451-141">Conversions</span></span>

<span data-ttu-id="d5451-142">Je implicitní převod (volá *rozšiřující převod*) z `float` k `double` protože rozsah `float` hodnoty jsou správné podmnožinou `double` a nedochází ke ztrátě přesnosti z `float` k `double`.</span><span class="sxs-lookup"><span data-stu-id="d5451-142">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span> 

<span data-ttu-id="d5451-143">Převést jeden typ s plovoucí desetinnou čárkou k jinému typu s plovoucí desetinnou čárkou, když implicitní převod není definován zdrojový typ pro cílový typ je nutné použít explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="d5451-143">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="d5451-144">Jedná se *zužující převod*.</span><span class="sxs-lookup"><span data-stu-id="d5451-144">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="d5451-145">Explicitní případu se totiž převod může dojít ke ztrátě.</span><span class="sxs-lookup"><span data-stu-id="d5451-145">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="d5451-146">Neexistuje žádný implicitní převod mezi ostatní typy s plovoucí desetinnou čárkou a `decimal` typu, protože `decimal` typ má zato větší přesnost než buď `float` nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="d5451-146">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="d5451-147">Další informace o implicitním číselném převodu naleznete v tématu [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="d5451-147">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="d5451-148">Další informace o explicitním číselném převodu naleznete v tématu [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="d5451-148">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5451-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5451-149">See also</span></span>

- [<span data-ttu-id="d5451-150">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5451-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d5451-151">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="d5451-151">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="d5451-152">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="d5451-152">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="d5451-153">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="d5451-153">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="d5451-154">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="d5451-154">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="d5451-155">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="d5451-155">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="d5451-156">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="d5451-156">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="d5451-157">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="d5451-157">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="d5451-158">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="d5451-158">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="d5451-159">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="d5451-159">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
