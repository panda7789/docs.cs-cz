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
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236060"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="343a8-103">Číselné typy s plovoucí desetinnou čárkou (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="343a8-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="343a8-104">**Typy s plovoucí desetinnou čárkou** jsou podmnožinou **jednoduché typy** a mohou být inicializovány pomocí [ *literály*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="343a8-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="343a8-105">Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="343a8-105">All floating-point types are also value types.</span></span> <span data-ttu-id="343a8-106">Všechny číselné typy s plovoucí desetinnou čárkou podporují [aritmetické](../operators/arithmetic-operators.md), [porovnání a rovnost](../operators/equality-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="343a8-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="343a8-107">Vlastnosti typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="343a8-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="343a8-108">C#podporuje následující předdefinované typy s plovoucí desetinnou čárkou:</span><span class="sxs-lookup"><span data-stu-id="343a8-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="343a8-109">C#typ nebo klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="343a8-109">C# type/keyword</span></span>|<span data-ttu-id="343a8-110">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="343a8-110">Approximate range</span></span>|<span data-ttu-id="343a8-111">Přesnost</span><span class="sxs-lookup"><span data-stu-id="343a8-111">Precision</span></span>|<span data-ttu-id="343a8-112">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="343a8-112">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|
|`float`|<span data-ttu-id="343a8-113">±1.5 x 10<sup>−45</sup> k ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="343a8-113">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="343a8-114">~ 6. až 9 číslic</span><span class="sxs-lookup"><span data-stu-id="343a8-114">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="343a8-115">±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="343a8-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="343a8-116">~ 15-17 číslic</span><span class="sxs-lookup"><span data-stu-id="343a8-116">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="343a8-117">±1.0 x 10<sup>– 28</sup> k ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="343a8-117">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="343a8-118">28 – 29 číslic</span><span class="sxs-lookup"><span data-stu-id="343a8-118">28-29 digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="343a8-119">V předchozí tabulce každý C# – klíčové slovo typ ve sloupci nejvíce vlevo je alias pro odpovídající typ formátu .NET.</span><span class="sxs-lookup"><span data-stu-id="343a8-119">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="343a8-120">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="343a8-120">They are interchangeable.</span></span> <span data-ttu-id="343a8-121">Například následující deklarace deklarování proměnných stejného typu:</span><span class="sxs-lookup"><span data-stu-id="343a8-121">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="343a8-122">Výchozí hodnota u každého typu s plovoucí desetinnou čárkou je nula, `0`.</span><span class="sxs-lookup"><span data-stu-id="343a8-122">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="343a8-123">Každý z typů s plovoucí desetinnou čárkou nemá `MinValue` a `MaxValue` konstanty, minimální a maximální konečnou hodnotu daného typu.</span><span class="sxs-lookup"><span data-stu-id="343a8-123">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="343a8-124">`float` a `double` typy také poskytují konstanty, které představují hodnoty not a number a nekonečno.</span><span class="sxs-lookup"><span data-stu-id="343a8-124">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="343a8-125">Například `double` typ poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="343a8-125">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="343a8-126">Protože `decimal` typ má větší přesnost a má menší rozsah než obě `float` a `double`, je vhodný pro výpočty finančních a přepočty měn.</span><span class="sxs-lookup"><span data-stu-id="343a8-126">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="343a8-127">Je možné kombinovat [integrální](integral-numeric-types.md) typy a typy s plovoucí desetinnou čárkou ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="343a8-127">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="343a8-128">V takovém případě integrální typy jsou převedeny na typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="343a8-128">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="343a8-129">Vyhodnocení výrazu se provádí dle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="343a8-129">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="343a8-130">Pokud jeden z typů s plovoucí desetinnou čárkou je `double`, je výraz vyhodnocen `double`, nebo [bool](../keywords/bool.md) v relační porovnání nebo porovnání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="343a8-130">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="343a8-131">Pokud není žádný `double` zadejte výraz, výraz je vyhodnocen jako `float`, nebo [bool](../keywords/bool.md) v relační porovnání nebo porovnání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="343a8-131">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="343a8-132">Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:</span><span class="sxs-lookup"><span data-stu-id="343a8-132">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="343a8-133">Kladnou a zápornou nulou</span><span class="sxs-lookup"><span data-stu-id="343a8-133">Positive and negative zero</span></span>
- <span data-ttu-id="343a8-134">Kladné a záporné nekonečno.</span><span class="sxs-lookup"><span data-stu-id="343a8-134">Positive and negative infinity</span></span>
- <span data-ttu-id="343a8-135">Hodnota not-a-Number (NaN)</span><span class="sxs-lookup"><span data-stu-id="343a8-135">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="343a8-136">Konečná sada nenulové hodnoty</span><span class="sxs-lookup"><span data-stu-id="343a8-136">The finite set of nonzero values</span></span>

<span data-ttu-id="343a8-137">Další informace o těchto hodnotách naleznete v části Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](https://www.ieee.org) webu.</span><span class="sxs-lookup"><span data-stu-id="343a8-137">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="343a8-138">Můžete použít buď [řetězce standardního číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md) nebo [vlastní řetězce číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) pro formátování hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="343a8-138">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="343a8-139">Literály s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="343a8-139">Floating-point literals</span></span>

<span data-ttu-id="343a8-140">Ve výchozím nastavení, je číselný literál s plovoucí desetinnou čárkou na pravé straně operátoru považováno za `double`.</span><span class="sxs-lookup"><span data-stu-id="343a8-140">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="343a8-141">Můžete převést literál s plovoucí desetinnou čárkou nebo celočíselné na konkrétní typ přípony:</span><span class="sxs-lookup"><span data-stu-id="343a8-141">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="343a8-142">`d` Nebo `D` přípona převede na literál `double`.</span><span class="sxs-lookup"><span data-stu-id="343a8-142">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="343a8-143">`f` Nebo `F` přípona převede na literál `float`.</span><span class="sxs-lookup"><span data-stu-id="343a8-143">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="343a8-144">`m` Nebo `M` přípona převede na literál `decimal`.</span><span class="sxs-lookup"><span data-stu-id="343a8-144">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="343a8-145">Následující příklady ukazují jednotlivých přípon:</span><span class="sxs-lookup"><span data-stu-id="343a8-145">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="343a8-146">Převody</span><span class="sxs-lookup"><span data-stu-id="343a8-146">Conversions</span></span>

<span data-ttu-id="343a8-147">Je implicitní převod (volá *rozšiřující převod*) z `float` k `double` protože rozsah `float` hodnoty jsou správné podmnožinou `double` a nedochází ke ztrátě přesnosti z `float` k `double`.</span><span class="sxs-lookup"><span data-stu-id="343a8-147">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="343a8-148">Převést jeden typ s plovoucí desetinnou čárkou k jinému typu s plovoucí desetinnou čárkou, když implicitní převod není definován zdrojový typ pro cílový typ je nutné použít explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="343a8-148">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="343a8-149">Jedná se *zužující převod*.</span><span class="sxs-lookup"><span data-stu-id="343a8-149">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="343a8-150">Explicitní případu se totiž převod může dojít ke ztrátě.</span><span class="sxs-lookup"><span data-stu-id="343a8-150">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="343a8-151">Neexistuje žádný implicitní převod mezi ostatní typy s plovoucí desetinnou čárkou a `decimal` typu, protože `decimal` typ má zato větší přesnost než buď `float` nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="343a8-151">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="343a8-152">Další informace o implicitním číselném převodu naleznete v tématu [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="343a8-152">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="343a8-153">Další informace o explicitním číselném převodu naleznete v tématu [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="343a8-153">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="343a8-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="343a8-154">See also</span></span>

- [<span data-ttu-id="343a8-155">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="343a8-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="343a8-156">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="343a8-156">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="343a8-157">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="343a8-157">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="343a8-158">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="343a8-158">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="343a8-159">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="343a8-159">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="343a8-160">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="343a8-160">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="343a8-161">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="343a8-161">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="343a8-162">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="343a8-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="343a8-163">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="343a8-163">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
