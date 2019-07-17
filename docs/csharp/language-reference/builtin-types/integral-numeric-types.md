---
title: Integrální číselné typy - C# odkaz
description: Další oblasti, velikosti úložiště a používá pro každý integrální číselné typy.
ms.date: 06/25/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236079"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="9f0b1-103">Integrální číselné typy (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="9f0b1-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="9f0b1-104">**Integrální číselné typy** jsou podmnožinou **jednoduché typy** a mohou být inicializovány pomocí [ *literály*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="9f0b1-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="9f0b1-105">Typy hodnot jsou také všechny celočíselné typy.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-105">All integral types are also value types.</span></span> <span data-ttu-id="9f0b1-106">Všechny integrální číselné typy. podpora [aritmetické](../operators/arithmetic-operators.md), [bitový logický](../operators/bitwise-and-shift-operators.md), [porovnání a rovnost](../operators/equality-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="9f0b1-107">Vlastnosti celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="9f0b1-107">Characteristics of the integral types</span></span>

<span data-ttu-id="9f0b1-108">C#podporuje následující předdefinované integrální typy:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="9f0b1-109">C#typ nebo klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="9f0b1-109">C# type/keyword</span></span>|<span data-ttu-id="9f0b1-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9f0b1-110">Range</span></span>|<span data-ttu-id="9f0b1-111">Velikost</span><span class="sxs-lookup"><span data-stu-id="9f0b1-111">Size</span></span>|<span data-ttu-id="9f0b1-112">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="9f0b1-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="9f0b1-113">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="9f0b1-113">-128 to 127</span></span>|<span data-ttu-id="9f0b1-114">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9f0b1-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="9f0b1-115">0 až 255</span><span class="sxs-lookup"><span data-stu-id="9f0b1-115">0 to 255</span></span>|<span data-ttu-id="9f0b1-116">Celé číslo bez znaménka 8 bitů</span><span class="sxs-lookup"><span data-stu-id="9f0b1-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="9f0b1-117">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="9f0b1-117">-32,768 to 32,767</span></span>|<span data-ttu-id="9f0b1-118">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9f0b1-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="9f0b1-119">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="9f0b1-119">0 to 65,535</span></span>|<span data-ttu-id="9f0b1-120">Celé číslo bez znaménka 16 bitů</span><span class="sxs-lookup"><span data-stu-id="9f0b1-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="9f0b1-121">-2 147 483 648 do 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="9f0b1-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="9f0b1-122">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9f0b1-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="9f0b1-123">0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="9f0b1-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="9f0b1-124">Nepodepsané 32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="9f0b1-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="9f0b1-125">-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="9f0b1-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="9f0b1-126">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9f0b1-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="9f0b1-127">0 na 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="9f0b1-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="9f0b1-128">64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="9f0b1-129">V předchozí tabulce každý C# – klíčové slovo typ ve sloupci nejvíce vlevo je alias pro odpovídající typ formátu .NET.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="9f0b1-130">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-130">They are interchangeable.</span></span> <span data-ttu-id="9f0b1-131">Například následující deklarace deklarování proměnných stejného typu:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="9f0b1-132">Výchozí hodnota každý integrální typ je nula, `0`.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="9f0b1-133">Každý z celočíselných typů má `MinValue` a `MaxValue` konstanty, minimální a maximální hodnotu daného typu.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="9f0b1-134">Použití <xref:System.Numerics.BigInteger?displayProperty=nameWithType> strukturu představující celé číslo se znaménkem s žádná horní nebo dolní meze.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="9f0b1-135">Integrální literály</span><span class="sxs-lookup"><span data-stu-id="9f0b1-135">Integral literals</span></span>

<span data-ttu-id="9f0b1-136">Integrální literály lze zadat jako *desítkové literály*, *šestnáctkové literály*, nebo *binární literály:* .</span><span class="sxs-lookup"><span data-stu-id="9f0b1-136">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="9f0b1-137">Níže je uveden příklad každé:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-137">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="9f0b1-138">Desítkové literály nevyžadují jakoukoli předponu.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-138">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="9f0b1-139">`x` Nebo `X` označuje, že předpona *šestnáctkové literál*.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-139">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="9f0b1-140">`b` Nebo `B` označuje, že předpona *binární literál*.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-140">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="9f0b1-141">Deklarace `binaryLiteral` demonstruje použití `_` jako *oddělovač číslic*.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-141">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="9f0b1-142">Oddělovač číslic jde použít s všechny číselné literály.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-142">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="9f0b1-143">Binární literály a oddělovače číslic `_` podporuje workflowy C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-143">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="9f0b1-144">Přípony literálu</span><span class="sxs-lookup"><span data-stu-id="9f0b1-144">Literal suffixes</span></span>

<span data-ttu-id="9f0b1-145">`l` Nebo `L` příponu Určuje, že by měl být celočíselný literál `long` typu.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-145">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="9f0b1-146">`ul` Nebo `UL` Určuje příponu `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-146">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="9f0b1-147">Pokud `L` přípona se používá na literál, který je větší než 9,223,372,036,854,775,807 (maximální hodnota `long`), hodnota převedená na `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-147">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="9f0b1-148">Pokud se překročí Hodnota reprezentovaná celočíselný literál <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, Chyba kompilátoru [CS1021](../../misc/cs1021.md) vyvolá.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-148">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="9f0b1-149">Malé písmeno "l" můžete použít jako příponu.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-149">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="9f0b1-150">Nicméně tím se vygeneruje upozornění kompilátoru protože písmeno "l" je snadno zaměnitelná s číslicí "1".</span><span class="sxs-lookup"><span data-stu-id="9f0b1-150">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="9f0b1-151">Pro přehlednost použijte "L".</span><span class="sxs-lookup"><span data-stu-id="9f0b1-151">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="9f0b1-152">Typ celočíselný literál</span><span class="sxs-lookup"><span data-stu-id="9f0b1-152">Type of an integral literal</span></span>

<span data-ttu-id="9f0b1-153">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-153">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="9f0b1-154">Celočíselný literál lze převést na typ s menší rozsah, než je výchozí přiřazení nebo výraz přetypování:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-154">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="9f0b1-155">Celočíselný literál lze převést na typ s větším než výchozí, pomocí přiřazení, přetypování nebo příponu na literál:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-155">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="9f0b1-156">Převody</span><span class="sxs-lookup"><span data-stu-id="9f0b1-156">Conversions</span></span>

<span data-ttu-id="9f0b1-157">Je implicitní převod (volá se *rozšiřující převod*) mezi dvou celočíselných typů kde cílový typ můžete uložit všechny hodnoty typu zdroje.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="9f0b1-158">Například je implicitní převod z `int` k `long` protože rozsah `int` hodnoty jsou správné podmnožinou `long`.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="9f0b1-159">Nejsou k dispozici implicitní převod z menší celočíselný typ bez znaménka větší celočíselný typ se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="9f0b1-160">Existuje také implicitní převod z libovolný integrální typ na libovolný typ s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="9f0b1-161">Neexistuje žádný implicitní převod z libovolný integrální typ se znaménkem na libovolný integrální typ bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="9f0b1-162">Pro převod jedné celočíselného typu na jiný celočíselný typ při implicitní převod není definován zdrojový typ pro cílový typ je nutné použít explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="9f0b1-163">Jedná se *zužující převod*.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="9f0b1-164">Explicitní případu se totiž převod může dojít ke ztrátě.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f0b1-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-165">See also</span></span>

- [<span data-ttu-id="9f0b1-166">C#Specifikace jazyka - integrální typy</span><span class="sxs-lookup"><span data-stu-id="9f0b1-166">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="9f0b1-167">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="9f0b1-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9f0b1-168">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="9f0b1-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="9f0b1-169">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="9f0b1-169">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="9f0b1-170">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="9f0b1-170">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="9f0b1-171">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="9f0b1-171">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="9f0b1-172">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="9f0b1-172">Numerics in .NET</span></span>](../../../standard/numerics.md)
