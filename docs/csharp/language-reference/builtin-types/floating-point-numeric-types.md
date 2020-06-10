---
title: Číselné typy s plovoucí desetinnou čárkou – reference jazyka C#
description: 'Přečtěte si o integrovaných typech s plovoucí desetinnou čárkou v jazyce C#: float, Double a Decimal'
ms.date: 02/10/2020
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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a1142d1aa04003ae1942902672cfc7a05edc99c0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662664"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="8d3fd-103">Číselné typy s plovoucí desetinnou čárkou (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8d3fd-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="8d3fd-104">*Číselné typy s plovoucí desetinnou* čárkou reprezentují reálné číslo.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="8d3fd-105">Všechny číselné typy s plovoucí desetinnou čárkou jsou [typy hodnot](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="8d3fd-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="8d3fd-106">Jsou to také [jednoduché typy](value-types.md#built-in-value-types) a lze je inicializovat pomocí [literálů](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="8d3fd-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="8d3fd-107">Všechny číselné typy s plovoucí desetinnou čárkou podporují operátory [aritmetické](../operators/arithmetic-operators.md), [porovnání](../operators/comparison-operators.md)a [rovnosti](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="8d3fd-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="8d3fd-108">Vlastnosti typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="8d3fd-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="8d3fd-109">Jazyk C# podporuje následující předdefinované typy s plovoucí desetinnou čárkou:</span><span class="sxs-lookup"><span data-stu-id="8d3fd-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="8d3fd-110">Typ/klíčové slovo jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d3fd-110">C# type/keyword</span></span>|<span data-ttu-id="8d3fd-111">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="8d3fd-111">Approximate range</span></span>|<span data-ttu-id="8d3fd-112">Přesnost</span><span class="sxs-lookup"><span data-stu-id="8d3fd-112">Precision</span></span>|<span data-ttu-id="8d3fd-113">Velikost</span><span class="sxs-lookup"><span data-stu-id="8d3fd-113">Size</span></span>|<span data-ttu-id="8d3fd-114">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="8d3fd-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="8d3fd-115">± 1,5 × 10<sup>− 45</sup> až ± 3,4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="8d3fd-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="8d3fd-116">~ 6-9 číslic</span><span class="sxs-lookup"><span data-stu-id="8d3fd-116">~6-9 digits</span></span>|<span data-ttu-id="8d3fd-117">4 bajty</span><span class="sxs-lookup"><span data-stu-id="8d3fd-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="8d3fd-118">± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="8d3fd-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="8d3fd-119">~ 15-17 číslic</span><span class="sxs-lookup"><span data-stu-id="8d3fd-119">~15-17 digits</span></span>|<span data-ttu-id="8d3fd-120">8 bajtů</span><span class="sxs-lookup"><span data-stu-id="8d3fd-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="8d3fd-121">± 1,0 × 10<sup>– 28</sup> až 7,9228 × 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="8d3fd-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="8d3fd-122">28-29 číslic</span><span class="sxs-lookup"><span data-stu-id="8d3fd-122">28-29 digits</span></span>|<span data-ttu-id="8d3fd-123">16 bajtů</span><span class="sxs-lookup"><span data-stu-id="8d3fd-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="8d3fd-124">V předchozí tabulce je každé klíčové slovo typu C# ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="8d3fd-125">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-125">They are interchangeable.</span></span> <span data-ttu-id="8d3fd-126">Například následující deklarace deklaruje proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="8d3fd-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="8d3fd-127">Výchozí hodnota každého typu s plovoucí desetinnou čárkou je nula, `0` .</span><span class="sxs-lookup"><span data-stu-id="8d3fd-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="8d3fd-128">Každý z typů s plovoucí desetinnou čárkou `MinValue` má `MaxValue` konstanty a, které poskytují minimální a maximální konečnou hodnotu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="8d3fd-129">`float`Typy a `double` také poskytují konstanty, které představují hodnoty nečíselné a nekonečno.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="8d3fd-130">Například `double` Typ poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType> , <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8d3fd-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8d3fd-131">Vzhledem k tomu, že `decimal` typ má větší přesnost a menší rozsah než obojí `float` `double` , je vhodný pro finanční a peněžní výpočty.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="8d3fd-132">Můžete kombinovat [integrální](integral-numeric-types.md) typy a `float` `double` typy a ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="8d3fd-133">V tomto případě jsou celočíselné typy implicitně převedeny na jeden z typů s plovoucí desetinnou čárkou a v případě potřeby `float` je typ implicitně převeden na `double` .</span><span class="sxs-lookup"><span data-stu-id="8d3fd-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="8d3fd-134">Výraz se vyhodnotí takto:</span><span class="sxs-lookup"><span data-stu-id="8d3fd-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="8d3fd-135">Pokud je `double` ve výrazu typ, je výraz vyhodnocen jako `double` nebo [`bool`](bool.md) v porovnání s relačním a rovností.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="8d3fd-136">Pokud `double` ve výrazu není žádný typ, výraz se vyhodnotí jako `float` nebo `bool` v relačních porovnáních a porovnávání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="8d3fd-137">Můžete také kombinovat integrální typy a `decimal` typ ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="8d3fd-138">V tomto případě jsou celočíselné typy implicitně převedeny na `decimal` typ a výraz je vyhodnocen jako `decimal` nebo `bool` v porovnání s relačním a rovností.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="8d3fd-139">Ve výrazu nelze kombinovat `decimal` typ s `float` typy a `double` .</span><span class="sxs-lookup"><span data-stu-id="8d3fd-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="8d3fd-140">V takovém případě, pokud chcete provádět operace aritmetické, porovnání nebo rovnosti, je nutné explicitně převést operandy buď z nebo na `decimal` typ, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="8d3fd-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="8d3fd-141">K formátování hodnoty s plovoucí desetinnou čárkou můžete použít buď [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) , nebo [řetězce vlastního číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="8d3fd-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="8d3fd-142">Reálné literály</span><span class="sxs-lookup"><span data-stu-id="8d3fd-142">Real literals</span></span>

<span data-ttu-id="8d3fd-143">Typ reálného literálu je určen jeho příponou takto:</span><span class="sxs-lookup"><span data-stu-id="8d3fd-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="8d3fd-144">Literál bez přípony nebo s `d` `D` příponou nebo je typu.`double`</span><span class="sxs-lookup"><span data-stu-id="8d3fd-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="8d3fd-145">Literál s `f` `F` příponou nebo je typu.`float`</span><span class="sxs-lookup"><span data-stu-id="8d3fd-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="8d3fd-146">Literál s `m` `M` příponou nebo je typu.`decimal`</span><span class="sxs-lookup"><span data-stu-id="8d3fd-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="8d3fd-147">Následující kód ukazuje příklad každé z nich:</span><span class="sxs-lookup"><span data-stu-id="8d3fd-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="8d3fd-148">Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován počínaje jazykem C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="8d3fd-149">Oddělovač číslic se dá použít u všech druhů číselných literálů.</span><span class="sxs-lookup"><span data-stu-id="8d3fd-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="8d3fd-150">Můžete také použít vědeckou notaci, to znamená, že určíte exponent, který je součástí reálného literálu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="8d3fd-150">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="8d3fd-151">Převody</span><span class="sxs-lookup"><span data-stu-id="8d3fd-151">Conversions</span></span>

<span data-ttu-id="8d3fd-152">Existuje pouze jeden implicitní převod mezi číselnými typy s plovoucí desetinnou čárkou: od `float` do `double` .</span><span class="sxs-lookup"><span data-stu-id="8d3fd-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="8d3fd-153">Můžete však převést libovolný typ s plovoucí desetinnou čárkou na jakýkoli jiný typ s plovoucí desetinnou čárkou s [explicitním přetypováním](../operators/type-testing-and-cast.md#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="8d3fd-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="8d3fd-154">Další informace najdete v tématu [integrované číselné převody](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8d3fd-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d3fd-155">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d3fd-155">C# language specification</span></span>

<span data-ttu-id="8d3fd-156">Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8d3fd-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8d3fd-157">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="8d3fd-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="8d3fd-158">Typ Decimal</span><span class="sxs-lookup"><span data-stu-id="8d3fd-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="8d3fd-159">Reálné literály</span><span class="sxs-lookup"><span data-stu-id="8d3fd-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="8d3fd-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d3fd-160">See also</span></span>

- [<span data-ttu-id="8d3fd-161">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="8d3fd-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8d3fd-162">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="8d3fd-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="8d3fd-163">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="8d3fd-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="8d3fd-164">Standardní řetězce formátu čísla</span><span class="sxs-lookup"><span data-stu-id="8d3fd-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="8d3fd-165">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="8d3fd-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
