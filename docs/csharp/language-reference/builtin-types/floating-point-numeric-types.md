---
title: Číselné typy s plovoucí desetinnou C# čárkou – referenční informace
description: Přehled předdefinovaných typů s C# plovoucí desetinnou čárkou
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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 17ae154780679dd1f42f43f1ec345cdc722815d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002191"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="148cf-103">Číselné typy s plovoucí desetinnouC# čárkou (referenční)</span><span class="sxs-lookup"><span data-stu-id="148cf-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="148cf-104">**Typy s plovoucí desetinnou** čárkou jsou podmnožinou **jednoduchých typů** a lze je inicializovat pomocí [*literálů*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="148cf-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="148cf-105">Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="148cf-105">All floating-point types are also value types.</span></span> <span data-ttu-id="148cf-106">Všechny číselné typy s plovoucí desetinnou čárkou podporují operátory [aritmetické](../operators/arithmetic-operators.md), [porovnání a rovnosti](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="148cf-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="148cf-107">Vlastnosti typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="148cf-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="148cf-108">C#podporuje následující předdefinované typy s plovoucí desetinnou čárkou:</span><span class="sxs-lookup"><span data-stu-id="148cf-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="148cf-109">C#typ/klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="148cf-109">C# type/keyword</span></span>|<span data-ttu-id="148cf-110">Přibližný rozsah</span><span class="sxs-lookup"><span data-stu-id="148cf-110">Approximate range</span></span>|<span data-ttu-id="148cf-111">Přesnost</span><span class="sxs-lookup"><span data-stu-id="148cf-111">Precision</span></span>|<span data-ttu-id="148cf-112">Velikost</span><span class="sxs-lookup"><span data-stu-id="148cf-112">Size</span></span>|<span data-ttu-id="148cf-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="148cf-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="148cf-114">± 1,5 × 10<sup>− 45</sup> až ± 3,4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="148cf-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="148cf-115">~ 6-9 číslic</span><span class="sxs-lookup"><span data-stu-id="148cf-115">~6-9 digits</span></span>|<span data-ttu-id="148cf-116">4 bajty</span><span class="sxs-lookup"><span data-stu-id="148cf-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="148cf-117">± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="148cf-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="148cf-118">~ 15-17 číslic</span><span class="sxs-lookup"><span data-stu-id="148cf-118">~15-17 digits</span></span>|<span data-ttu-id="148cf-119">8 bajtů</span><span class="sxs-lookup"><span data-stu-id="148cf-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="148cf-120">± 1,0 × 10<sup>– 28</sup> až 7,9228 × 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="148cf-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="148cf-121">28-29 číslic</span><span class="sxs-lookup"><span data-stu-id="148cf-121">28-29 digits</span></span>|<span data-ttu-id="148cf-122">16 bajtů</span><span class="sxs-lookup"><span data-stu-id="148cf-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="148cf-123">V předchozí tabulce je každé C# klíčové slovo Type ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="148cf-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="148cf-124">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="148cf-124">They are interchangeable.</span></span> <span data-ttu-id="148cf-125">Například následující deklarace deklaruje proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="148cf-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="148cf-126">Výchozí hodnota každého typu s plovoucí desetinnou čárkou je nula, `0`.</span><span class="sxs-lookup"><span data-stu-id="148cf-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="148cf-127">Každý z typů s plovoucí desetinnou čárkou má konstanty `MinValue` a `MaxValue`, které poskytují minimální a maximální hodnotu konečné hodnoty tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="148cf-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="148cf-128">Typy `float` a `double` také poskytují konstanty, které nepředstavují hodnoty nečíselné a nekonečno.</span><span class="sxs-lookup"><span data-stu-id="148cf-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="148cf-129">Například typ `double` poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="148cf-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="148cf-130">Vzhledem k tomu, že typ `decimal` má větší přesnost a menší rozsah než obě `float` a `double`, je vhodné pro finanční a peněžní výpočty.</span><span class="sxs-lookup"><span data-stu-id="148cf-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="148cf-131">Ve výrazu můžete kombinovat [integrální](integral-numeric-types.md) typy a typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="148cf-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="148cf-132">V tomto případě jsou integrální typy převedeny na typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="148cf-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="148cf-133">Vyhodnocení výrazu je provedeno podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="148cf-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="148cf-134">Pokud je jeden z typů s plovoucí desetinnou čárkou `double`, výraz se vyhodnotí jako `double` nebo na [logickou](../keywords/bool.md) hodnotu v relačních porovnáních nebo porovnávání pro rovnost.</span><span class="sxs-lookup"><span data-stu-id="148cf-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="148cf-135">Pokud ve výrazu není žádný typ `double`, výraz se vyhodnotí jako `float` nebo na [logickou](../keywords/bool.md) hodnotu v relačních porovnáních nebo porovnávání pro rovnost.</span><span class="sxs-lookup"><span data-stu-id="148cf-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="148cf-136">Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:</span><span class="sxs-lookup"><span data-stu-id="148cf-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="148cf-137">Kladná a záporná nula</span><span class="sxs-lookup"><span data-stu-id="148cf-137">Positive and negative zero</span></span>
- <span data-ttu-id="148cf-138">Kladné a záporné nekonečno</span><span class="sxs-lookup"><span data-stu-id="148cf-138">Positive and negative infinity</span></span>
- <span data-ttu-id="148cf-139">Hodnota není číslo (NaN).</span><span class="sxs-lookup"><span data-stu-id="148cf-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="148cf-140">Konečná sada nenulových hodnot</span><span class="sxs-lookup"><span data-stu-id="148cf-140">The finite set of nonzero values</span></span>

<span data-ttu-id="148cf-141">Další informace o těchto hodnotách najdete v tématu IEEE standard pro binární aritmetické operace s plovoucí desetinnou čárkou, která je k dispozici na webu [IEEE](https://www.ieee.org) .</span><span class="sxs-lookup"><span data-stu-id="148cf-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="148cf-142">K formátování hodnoty s plovoucí desetinnou čárkou můžete použít buď [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) , nebo [řetězce vlastního číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="148cf-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="148cf-143">Literály s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="148cf-143">Floating-point literals</span></span>

<span data-ttu-id="148cf-144">Ve výchozím nastavení je číselný literál s plovoucí desetinnou čárkou na pravé straně operátoru přiřazení považován za `double`.</span><span class="sxs-lookup"><span data-stu-id="148cf-144">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="148cf-145">Můžete použít přípony pro převod plovoucí desetinné čárky nebo integrálního literálu na konkrétní typ:</span><span class="sxs-lookup"><span data-stu-id="148cf-145">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="148cf-146">Přípona `d` nebo `D` převede literál na `double`.</span><span class="sxs-lookup"><span data-stu-id="148cf-146">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="148cf-147">Přípona `f` nebo `F` převede literál na `float`.</span><span class="sxs-lookup"><span data-stu-id="148cf-147">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="148cf-148">Přípona `m` nebo `M` převede literál na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="148cf-148">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="148cf-149">Následující příklady znázorňují jednotlivé přípony:</span><span class="sxs-lookup"><span data-stu-id="148cf-149">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="148cf-150">Převody</span><span class="sxs-lookup"><span data-stu-id="148cf-150">Conversions</span></span>

<span data-ttu-id="148cf-151">Existuje implicitní převod (nazývaný *rozšiřující převod*) z `float` na `double`, protože rozsah hodnot `float` je správnou podmnožinou `double` a nedochází ke ztrátě přesnosti od `float` do `double`.</span><span class="sxs-lookup"><span data-stu-id="148cf-151">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="148cf-152">Je nutné použít explicitní přetypování pro převod jednoho typu s plovoucí desetinnou čárkou na jiný typ s plovoucí desetinnou čárkou, pokud implicitní převod není definován ze zdrojového typu na cílový typ.</span><span class="sxs-lookup"><span data-stu-id="148cf-152">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="148cf-153">Tato metoda se nazývá *zužující převod*.</span><span class="sxs-lookup"><span data-stu-id="148cf-153">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="148cf-154">Explicitní případ je vyžadován, protože převod může mít za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="148cf-154">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="148cf-155">Neexistuje žádný implicitní převod mezi jinými typy s plovoucí desetinnou čárkou a typem `decimal`, protože typ `decimal` má větší přesnost než `float` nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="148cf-155">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="148cf-156">Další informace o implicitním číselném převodu naleznete v tématu [implicitní číselná převodová tabulka](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="148cf-156">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="148cf-157">Další informace o explicitních číselných převodech naleznete v tématu [explicitní číselná](../keywords/explicit-numeric-conversions-table.md)převodová tabulka.</span><span class="sxs-lookup"><span data-stu-id="148cf-157">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="148cf-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="148cf-158">See also</span></span>

- [<span data-ttu-id="148cf-159">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="148cf-159">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="148cf-160">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="148cf-160">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="148cf-161">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="148cf-161">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="148cf-162">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="148cf-162">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="148cf-163">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="148cf-163">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="148cf-164">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="148cf-164">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="148cf-165">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="148cf-165">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="148cf-166">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="148cf-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="148cf-167">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="148cf-167">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
