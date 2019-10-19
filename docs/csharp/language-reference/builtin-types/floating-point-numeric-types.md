---
title: Číselné typy s plovoucí desetinnou C# čárkou – referenční informace
description: Přehled předdefinovaných typů s C# plovoucí desetinnou čárkou
ms.date: 10/18/2019
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
ms.openlocfilehash: fa6cbb869d90113414cc6f8ffe231386c3596b1d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579373"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="bf798-103">Číselné typy s plovoucí desetinnouC# čárkou (referenční)</span><span class="sxs-lookup"><span data-stu-id="bf798-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="bf798-104">**Typy s plovoucí desetinnou** čárkou jsou podmnožinou **jednoduchých typů** a lze je inicializovat pomocí [*literálů*](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="bf798-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#real-literals).</span></span> <span data-ttu-id="bf798-105">Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="bf798-105">All floating-point types are also value types.</span></span> <span data-ttu-id="bf798-106">Všechny číselné typy s plovoucí desetinnou čárkou podporují operátory [aritmetické](../operators/arithmetic-operators.md), [porovnání](../operators/comparison-operators.md)a [rovnosti](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="bf798-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="bf798-107">Vlastnosti typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="bf798-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="bf798-108">C#podporuje následující předdefinované typy s plovoucí desetinnou čárkou:</span><span class="sxs-lookup"><span data-stu-id="bf798-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="bf798-109">C#typ/klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="bf798-109">C# type/keyword</span></span>|<span data-ttu-id="bf798-110">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="bf798-110">Approximate range</span></span>|<span data-ttu-id="bf798-111">Přesnost</span><span class="sxs-lookup"><span data-stu-id="bf798-111">Precision</span></span>|<span data-ttu-id="bf798-112">Velikost</span><span class="sxs-lookup"><span data-stu-id="bf798-112">Size</span></span>|<span data-ttu-id="bf798-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="bf798-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="bf798-114">± 1,5 × 10<sup>− 45</sup> až ± 3,4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="bf798-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="bf798-115">~ 6-9 číslic</span><span class="sxs-lookup"><span data-stu-id="bf798-115">~6-9 digits</span></span>|<span data-ttu-id="bf798-116">4 bajty</span><span class="sxs-lookup"><span data-stu-id="bf798-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="bf798-117">± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="bf798-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="bf798-118">~ 15-17 číslic</span><span class="sxs-lookup"><span data-stu-id="bf798-118">~15-17 digits</span></span>|<span data-ttu-id="bf798-119">8 bajtů</span><span class="sxs-lookup"><span data-stu-id="bf798-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="bf798-120">± 1,0 × 10<sup>– 28</sup> až 7,9228 × 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="bf798-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="bf798-121">28-29 číslic</span><span class="sxs-lookup"><span data-stu-id="bf798-121">28-29 digits</span></span>|<span data-ttu-id="bf798-122">16 bajtů</span><span class="sxs-lookup"><span data-stu-id="bf798-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="bf798-123">V předchozí tabulce je každé C# klíčové slovo Type ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="bf798-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="bf798-124">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="bf798-124">They are interchangeable.</span></span> <span data-ttu-id="bf798-125">Například následující deklarace deklaruje proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="bf798-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="bf798-126">Výchozí hodnota každého typu s plovoucí desetinnou čárkou je nula, `0`.</span><span class="sxs-lookup"><span data-stu-id="bf798-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="bf798-127">Každý z typů s plovoucí desetinnou čárkou má konstanty `MinValue` a `MaxValue`, které poskytují minimální a maximální hodnotu konečné hodnoty tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="bf798-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="bf798-128">Typy `float` a `double` také poskytují konstanty, které nepředstavují hodnoty nečíselné a nekonečno.</span><span class="sxs-lookup"><span data-stu-id="bf798-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="bf798-129">Například typ `double` poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bf798-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bf798-130">Vzhledem k tomu, že typ `decimal` má větší přesnost a menší rozsah než obě `float` a `double`, je vhodné pro finanční a peněžní výpočty.</span><span class="sxs-lookup"><span data-stu-id="bf798-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="bf798-131">Ve výrazu můžete kombinovat [integrální](integral-numeric-types.md) typy a typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="bf798-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="bf798-132">V tomto případě jsou integrální typy převedeny na typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="bf798-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="bf798-133">Vyhodnocení výrazu je provedeno podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="bf798-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="bf798-134">Pokud je jeden z typů s plovoucí desetinnou čárkou `double`, výraz se vyhodnotí jako `double` nebo [bool](../keywords/bool.md) v relačních porovnáních a porovnávání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="bf798-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="bf798-135">Pokud ve výrazu není žádný typ `double`, výraz se vyhodnotí jako `float` nebo [bool](../keywords/bool.md) v relačních porovnáních a porovnávání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="bf798-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="bf798-136">Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:</span><span class="sxs-lookup"><span data-stu-id="bf798-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="bf798-137">Kladná a záporná nula</span><span class="sxs-lookup"><span data-stu-id="bf798-137">Positive and negative zero</span></span>
- <span data-ttu-id="bf798-138">Kladné a záporné nekonečno</span><span class="sxs-lookup"><span data-stu-id="bf798-138">Positive and negative infinity</span></span>
- <span data-ttu-id="bf798-139">Hodnota není číslo (NaN).</span><span class="sxs-lookup"><span data-stu-id="bf798-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="bf798-140">Konečná sada nenulových hodnot</span><span class="sxs-lookup"><span data-stu-id="bf798-140">The finite set of nonzero values</span></span>

<span data-ttu-id="bf798-141">Další informace o těchto hodnotách najdete v tématu IEEE standard pro binární aritmetické operace s plovoucí desetinnou čárkou, která je k dispozici na webu [IEEE](https://www.ieee.org) .</span><span class="sxs-lookup"><span data-stu-id="bf798-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="bf798-142">K formátování hodnoty s plovoucí desetinnou čárkou můžete použít buď [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) , nebo [řetězce vlastního číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="bf798-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="bf798-143">Reálné literály</span><span class="sxs-lookup"><span data-stu-id="bf798-143">Real literals</span></span>

<span data-ttu-id="bf798-144">Typ reálného literálu je určen jeho příponou takto:</span><span class="sxs-lookup"><span data-stu-id="bf798-144">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="bf798-145">Literál bez přípony nebo s příponou `d` nebo `D` je typu `double`</span><span class="sxs-lookup"><span data-stu-id="bf798-145">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="bf798-146">Literál s příponou `f` nebo `F` je typu `float`</span><span class="sxs-lookup"><span data-stu-id="bf798-146">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="bf798-147">Literál s příponou `m` nebo `M` je typu `decimal`</span><span class="sxs-lookup"><span data-stu-id="bf798-147">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="bf798-148">Následující kód ukazuje příklad každé z nich:</span><span class="sxs-lookup"><span data-stu-id="bf798-148">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="bf798-149">Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="bf798-149">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="bf798-150">Oddělovač číslic se dá použít u všech druhů číselných literálů.</span><span class="sxs-lookup"><span data-stu-id="bf798-150">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="bf798-151">Můžete také použít vědeckou notaci, to znamená, že určíte exponent, který je součástí reálného literálu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="bf798-151">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="bf798-152">Převody</span><span class="sxs-lookup"><span data-stu-id="bf798-152">Conversions</span></span>

<span data-ttu-id="bf798-153">Existuje implicitní převod (nazývaný *rozšiřující převod*) z `float` na `double`, protože rozsah hodnot `float` je správnou podmnožinou `double` a nedochází ke ztrátě přesnosti od `float` do `double`.</span><span class="sxs-lookup"><span data-stu-id="bf798-153">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="bf798-154">Je nutné použít explicitní přetypování pro převod jednoho typu s plovoucí desetinnou čárkou na jiný typ s plovoucí desetinnou čárkou, pokud implicitní převod není definován ze zdrojového typu na cílový typ.</span><span class="sxs-lookup"><span data-stu-id="bf798-154">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="bf798-155">Tato metoda se nazývá *zužující převod*.</span><span class="sxs-lookup"><span data-stu-id="bf798-155">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="bf798-156">Explicitní případ je vyžadován, protože převod může mít za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="bf798-156">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="bf798-157">Neexistuje žádný implicitní převod mezi jinými typy s plovoucí desetinnou čárkou a typem `decimal`, protože typ `decimal` má větší přesnost než `float` nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="bf798-157">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="bf798-158">Další informace o implicitním číselném převodu naleznete v tématu [implicitní číselná převodová tabulka](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="bf798-158">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="bf798-159">Další informace o explicitních číselných převodech naleznete v tématu [explicitní číselná](../keywords/explicit-numeric-conversions-table.md)převodová tabulka.</span><span class="sxs-lookup"><span data-stu-id="bf798-159">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bf798-160">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bf798-160">C# language specification</span></span>

<span data-ttu-id="bf798-161">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="bf798-161">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bf798-162">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="bf798-162">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="bf798-163">Typ Decimal</span><span class="sxs-lookup"><span data-stu-id="bf798-163">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="bf798-164">Reálné literály</span><span class="sxs-lookup"><span data-stu-id="bf798-164">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="bf798-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf798-165">See also</span></span>

- [<span data-ttu-id="bf798-166">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="bf798-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bf798-167">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="bf798-167">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="bf798-168">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="bf798-168">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="bf798-169">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="bf798-169">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="bf798-170">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="bf798-170">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="bf798-171">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="bf798-171">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="bf798-172">Řetězce standardního číselného formátu</span><span class="sxs-lookup"><span data-stu-id="bf798-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
