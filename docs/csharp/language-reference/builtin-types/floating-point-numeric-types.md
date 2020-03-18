---
title: Číselné typy s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou tázkou – odkaz
description: 'Informace o předdefinovaných typech c# s plovoucí desetinnou čárkou: float, double a decimal'
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
ms.openlocfilehash: 95b7f266654bbbcdcd0f81e3aa11cfc94af9f0e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77215239"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="6b04a-103">Číselné typy s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou tázkou (odkaz Jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b04a-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="6b04a-104">*Číselné typy s plovoucí desetinnou desetinnou desetinnou hodnotou* představují reálná čísla.</span><span class="sxs-lookup"><span data-stu-id="6b04a-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="6b04a-105">Všechny číselné typy s plovoucí desetinnou [desetinnou desetinnou hodnotou](value-types.md)jsou typy hodnot .</span><span class="sxs-lookup"><span data-stu-id="6b04a-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="6b04a-106">Jsou to také [jednoduché typy](value-types.md#built-in-value-types) a mohou být inicializovány [literály](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="6b04a-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="6b04a-107">Všechny číselné typy s plovoucí [desetinnou desetinnou hodnotou podporují aritmetické operátory](../operators/arithmetic-operators.md), [porovnání](../operators/comparison-operators.md)a [rovnost.](../operators/equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="6b04a-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="6b04a-108">Charakteristiky typů s plovoucí desetinnou tázkem</span><span class="sxs-lookup"><span data-stu-id="6b04a-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="6b04a-109">C# podporuje následující předdefinované typy s plovoucí desetinnou desetinnou a střední tok:</span><span class="sxs-lookup"><span data-stu-id="6b04a-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="6b04a-110">C# typ/klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="6b04a-110">C# type/keyword</span></span>|<span data-ttu-id="6b04a-111">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="6b04a-111">Approximate range</span></span>|<span data-ttu-id="6b04a-112">Přesnost</span><span class="sxs-lookup"><span data-stu-id="6b04a-112">Precision</span></span>|<span data-ttu-id="6b04a-113">Velikost</span><span class="sxs-lookup"><span data-stu-id="6b04a-113">Size</span></span>|<span data-ttu-id="6b04a-114">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="6b04a-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="6b04a-115">±1,5 x 10<sup>−45</sup> až ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="6b04a-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="6b04a-116">~6-9 číslic</span><span class="sxs-lookup"><span data-stu-id="6b04a-116">~6-9 digits</span></span>|<span data-ttu-id="6b04a-117">4 bajty</span><span class="sxs-lookup"><span data-stu-id="6b04a-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="6b04a-118">±5,0 × 10<sup>−324</sup> až ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="6b04a-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="6b04a-119">~15-17 číslic</span><span class="sxs-lookup"><span data-stu-id="6b04a-119">~15-17 digits</span></span>|<span data-ttu-id="6b04a-120">8 bajtů</span><span class="sxs-lookup"><span data-stu-id="6b04a-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="6b04a-121">±1,0 x 10<sup>-28</sup> až ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="6b04a-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="6b04a-122">28-29 číslic</span><span class="sxs-lookup"><span data-stu-id="6b04a-122">28-29 digits</span></span>|<span data-ttu-id="6b04a-123">16 bajtů</span><span class="sxs-lookup"><span data-stu-id="6b04a-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="6b04a-124">V předchozí tabulce je každé klíčové slovo typu C# ze sloupce zcela vlevo aliasem odpovídajícího typu .NET.</span><span class="sxs-lookup"><span data-stu-id="6b04a-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="6b04a-125">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="6b04a-125">They are interchangeable.</span></span> <span data-ttu-id="6b04a-126">Například následující deklarace deklarují proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="6b04a-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="6b04a-127">Výchozí hodnota každého typu s plovoucí `0`desetinnou cípem je nula .</span><span class="sxs-lookup"><span data-stu-id="6b04a-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="6b04a-128">Každý z typů `MinValue` s plovoucí `MaxValue` desetinnou desetinnou a konstantami, které poskytují minimální a maximální konečnou hodnotu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="6b04a-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="6b04a-129">Typy `float` `double` a také poskytují konstanty, které představují hodnoty ne čísla a nekonečna.</span><span class="sxs-lookup"><span data-stu-id="6b04a-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="6b04a-130">Například `double` typ obsahuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b04a-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6b04a-131">Vzhledem `decimal` k tomu, že typ `float` má `double`větší přesnost a menší rozsah než oba a , je vhodné pro finanční a měnové výpočty.</span><span class="sxs-lookup"><span data-stu-id="6b04a-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="6b04a-132">Můžete kombinovat [integrální](integral-numeric-types.md) typy `float` a a `double` typy ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="6b04a-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="6b04a-133">V tomto případě integrální typy jsou implicitně převedeny na jeden `float` z typů s plovoucí `double`desetinnou táceka a v případě potřeby je typ implicitně převeden na .</span><span class="sxs-lookup"><span data-stu-id="6b04a-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="6b04a-134">Výraz se vyhodnotí takto:</span><span class="sxs-lookup"><span data-stu-id="6b04a-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="6b04a-135">Pokud je `double` typ ve výrazu, výraz `double`vyhodnotí na , nebo [`bool`](bool.md) v relační a rovnosti porovnání.</span><span class="sxs-lookup"><span data-stu-id="6b04a-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="6b04a-136">Pokud není `double` žádný typ ve výrazu, `float`výraz vyhodnotí na , nebo `bool` v porovnání relační a rovnosti.</span><span class="sxs-lookup"><span data-stu-id="6b04a-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="6b04a-137">Můžete také kombinovat integrální typy a `decimal` typ ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="6b04a-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="6b04a-138">V tomto případě integrální typy `decimal` jsou implicitně převedeny `decimal`na `bool` typ a výraz vyhodnotí na , nebo v porovnání relační a rovnosti.</span><span class="sxs-lookup"><span data-stu-id="6b04a-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="6b04a-139">`decimal` Typ nelze kombinovat s `float` `double` typy a ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="6b04a-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="6b04a-140">V tomto případě, pokud chcete provést operace aritmetiky, porovnání nebo rovnosti, je nutné explicitně převést operandy z nebo na `decimal` typ, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="6b04a-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="6b04a-141">K formátování hodnoty s plovoucí desetinnou desetinnou hodnotou můžete použít [standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) nebo [vlastní číselné formátovací řetězce.](../../../standard/base-types/custom-numeric-format-strings.md)</span><span class="sxs-lookup"><span data-stu-id="6b04a-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="6b04a-142">Skutečné literály</span><span class="sxs-lookup"><span data-stu-id="6b04a-142">Real literals</span></span>

<span data-ttu-id="6b04a-143">Typ skutečného literálu je určen jeho příponou takto:</span><span class="sxs-lookup"><span data-stu-id="6b04a-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="6b04a-144">Doslovbez přípony nebo s `d` `D` příponou nebo je typu`double`</span><span class="sxs-lookup"><span data-stu-id="6b04a-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="6b04a-145">Literál s `f` `F` příponou nebo je typu`float`</span><span class="sxs-lookup"><span data-stu-id="6b04a-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="6b04a-146">Literál s `m` `M` příponou nebo je typu`decimal`</span><span class="sxs-lookup"><span data-stu-id="6b04a-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="6b04a-147">Následující kód ukazuje příklad každého z nich:</span><span class="sxs-lookup"><span data-stu-id="6b04a-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="6b04a-148">Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován počínaje C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="6b04a-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="6b04a-149">Oddělovač číslic můžete použít se všemi druhy číselných literál.</span><span class="sxs-lookup"><span data-stu-id="6b04a-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="6b04a-150">Můžete také použít vědecký zápis, to znamená, že zadáte exponentní část skutečného literálu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="6b04a-150">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="6b04a-151">Převody</span><span class="sxs-lookup"><span data-stu-id="6b04a-151">Conversions</span></span>

<span data-ttu-id="6b04a-152">Existuje pouze jeden implicitní převod mezi číselnými typy s plovoucí desetinnou desetinnou hodnotou: z `float` na `double`.</span><span class="sxs-lookup"><span data-stu-id="6b04a-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="6b04a-153">Můžete však převést libovolný typ s plovoucí desetinnou tácek na jakýkoli jiný typ s plovoucí desetinnou tácek s [explicitním přetypátkem](../operators/type-testing-and-cast.md#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="6b04a-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="6b04a-154">Další informace naleznete [v tématu Předdefinované číselné převody](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="6b04a-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6b04a-155">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b04a-155">C# language specification</span></span>

<span data-ttu-id="6b04a-156">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="6b04a-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="6b04a-157">Typy s plovoucí desetinnou tálicí</span><span class="sxs-lookup"><span data-stu-id="6b04a-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="6b04a-158">Desetinný typ</span><span class="sxs-lookup"><span data-stu-id="6b04a-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="6b04a-159">Skutečné literály</span><span class="sxs-lookup"><span data-stu-id="6b04a-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="6b04a-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b04a-160">See also</span></span>

- [<span data-ttu-id="6b04a-161">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="6b04a-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6b04a-162">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="6b04a-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="6b04a-163">Integrální typy</span><span class="sxs-lookup"><span data-stu-id="6b04a-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="6b04a-164">Standardní číselné formátovací řetězce</span><span class="sxs-lookup"><span data-stu-id="6b04a-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="6b04a-165">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="6b04a-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
