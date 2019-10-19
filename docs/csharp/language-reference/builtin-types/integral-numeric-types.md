---
title: Celočíselné číselné typy C# – referenční informace
description: Seznamte se s rozsahem, velikostí úložiště a s využitím pro každý celočíselný numerický typ.
ms.date: 10/18/2019
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
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579185"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="8b790-103">Integrální číselné typy (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="8b790-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="8b790-104">**Integrální číselné typy** jsou podmnožinou **jednoduchých typů** a lze je inicializovat pomocí [*literálů*](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="8b790-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integer-literals).</span></span> <span data-ttu-id="8b790-105">Všechny celočíselné typy jsou také typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="8b790-105">All integral types are also value types.</span></span> <span data-ttu-id="8b790-106">Všechny integrální číselné typy podporují [aritmetické](../operators/arithmetic-operators.md)a [logické](../operators/bitwise-and-shift-operators.md)operátory, [porovnání](../operators/comparison-operators.md)a [rovnost](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="8b790-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="8b790-107">Charakteristiky integrálních typů</span><span class="sxs-lookup"><span data-stu-id="8b790-107">Characteristics of the integral types</span></span>

<span data-ttu-id="8b790-108">C#podporuje následující předdefinované celočíselné typy:</span><span class="sxs-lookup"><span data-stu-id="8b790-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="8b790-109">C#typ/klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="8b790-109">C# type/keyword</span></span>|<span data-ttu-id="8b790-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8b790-110">Range</span></span>|<span data-ttu-id="8b790-111">Velikost</span><span class="sxs-lookup"><span data-stu-id="8b790-111">Size</span></span>|<span data-ttu-id="8b790-112">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="8b790-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="8b790-113">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="8b790-113">-128 to 127</span></span>|<span data-ttu-id="8b790-114">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8b790-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="8b790-115">0 až 255</span><span class="sxs-lookup"><span data-stu-id="8b790-115">0 to 255</span></span>|<span data-ttu-id="8b790-116">8bitové celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="8b790-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="8b790-117">-32 768 až 32 767</span><span class="sxs-lookup"><span data-stu-id="8b790-117">-32,768 to 32,767</span></span>|<span data-ttu-id="8b790-118">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8b790-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="8b790-119">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="8b790-119">0 to 65,535</span></span>|<span data-ttu-id="8b790-120">16bitové celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="8b790-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="8b790-121">-2 147 483 648 až 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="8b790-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="8b790-122">Podepsané 32 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8b790-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="8b790-123">0 až 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="8b790-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="8b790-124">Celé číslo bez znaménka 32-bit</span><span class="sxs-lookup"><span data-stu-id="8b790-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="8b790-125">– 9223372036854775808 na 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="8b790-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="8b790-126">Podepsané 64 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8b790-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="8b790-127">0 až 18446744073709551615</span><span class="sxs-lookup"><span data-stu-id="8b790-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="8b790-128">Celé číslo bez znaménka 64-bit</span><span class="sxs-lookup"><span data-stu-id="8b790-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="8b790-129">V předchozí tabulce je každé C# klíčové slovo Type ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="8b790-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="8b790-130">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="8b790-130">They are interchangeable.</span></span> <span data-ttu-id="8b790-131">Například následující deklarace deklaruje proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="8b790-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="8b790-132">Výchozí hodnota každého integrálního typu je nula, `0`.</span><span class="sxs-lookup"><span data-stu-id="8b790-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="8b790-133">Každý celočíselný typ má `MinValue` a `MaxValue` konstanty, které poskytují minimální a maximální hodnotu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="8b790-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="8b790-134">Pomocí <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury reprezentovat celé číslo se znaménkem bez horních nebo dolních mezí.</span><span class="sxs-lookup"><span data-stu-id="8b790-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="8b790-135">Celočíselné literály</span><span class="sxs-lookup"><span data-stu-id="8b790-135">Integer literals</span></span>

<span data-ttu-id="8b790-136">Celočíselné literály mohou být</span><span class="sxs-lookup"><span data-stu-id="8b790-136">Integer literals can be</span></span>

- <span data-ttu-id="8b790-137">*Decimal*: bez předpony</span><span class="sxs-lookup"><span data-stu-id="8b790-137">*decimal*: without any prefix</span></span>
- <span data-ttu-id="8b790-138">*šestnáctková*: s předponou `0x` nebo `0X`</span><span class="sxs-lookup"><span data-stu-id="8b790-138">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="8b790-139">*binární*: s předponou `0b` nebo `0B` (k dispozici v C# 7,0 a novějším)</span><span class="sxs-lookup"><span data-stu-id="8b790-139">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="8b790-140">Následující kód ukazuje příklad každé z nich:</span><span class="sxs-lookup"><span data-stu-id="8b790-140">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="8b790-141">Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="8b790-141">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="8b790-142">Oddělovač číslic se dá použít u všech druhů číselných literálů.</span><span class="sxs-lookup"><span data-stu-id="8b790-142">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="8b790-143">Typ celočíselného literálu je určen jeho příponou takto:</span><span class="sxs-lookup"><span data-stu-id="8b790-143">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="8b790-144">Pokud literál nemá žádnou příponu, je jeho typ prvním z následujících typů, ve kterém může být jeho hodnota reprezentovaná: `int`, `uint`, `long` `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8b790-144">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="8b790-145">Je-li literál určen `U` nebo `u`, je jeho typ prvním z následujících typů, ve kterém lze jeho hodnotu reprezentovat: `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8b790-145">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="8b790-146">Je-li literál určen `L` nebo `l`, je jeho typ prvním z následujících typů, ve kterém lze jeho hodnotu reprezentovat: `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8b790-146">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8b790-147">Jako příponu můžete použít malé písmeno `l`.</span><span class="sxs-lookup"><span data-stu-id="8b790-147">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="8b790-148">Tím se však vygeneruje upozornění kompilátoru, protože písmeno `l` může být zaměněno pomocí číslice `1`.</span><span class="sxs-lookup"><span data-stu-id="8b790-148">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="8b790-149">Pro přehlednost použijte `L`.</span><span class="sxs-lookup"><span data-stu-id="8b790-149">Use `L` for clarity.</span></span>

- <span data-ttu-id="8b790-150">Pokud má literál příponu `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` nebo `lu`, jeho typ je `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8b790-150">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="8b790-151">Pokud hodnota reprezentovaná celočíselným literálem překračuje <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilátoru [CS1021](../../misc/cs1021.md) .</span><span class="sxs-lookup"><span data-stu-id="8b790-151">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="8b790-152">Hodnota reprezentovaná celočíselným literálem se dá implicitně převést na typ s menším rozsahem, než je určený typ literálu.</span><span class="sxs-lookup"><span data-stu-id="8b790-152">The value represented by an integer literal can be implicitly converted to a type with a smaller range than the determined type of the literal.</span></span> <span data-ttu-id="8b790-153">To je možné, pokud je hodnota v rozsahu cílového typu:</span><span class="sxs-lookup"><span data-stu-id="8b790-153">That's possible when the value is within the range of the destination type:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="8b790-154">Jak ukazuje předchozí příklad, pokud hodnota literálu není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031](../../misc/cs0031.md) .</span><span class="sxs-lookup"><span data-stu-id="8b790-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="8b790-155">Můžete také použít přetypování k převodu hodnoty reprezentované celočíselným literálem na jiný typ, než je určený typ literálu:</span><span class="sxs-lookup"><span data-stu-id="8b790-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="8b790-156">Převody</span><span class="sxs-lookup"><span data-stu-id="8b790-156">Conversions</span></span>

<span data-ttu-id="8b790-157">Existuje implicitní převod (nazývaný *rozšiřující převod*) mezi dvěma celočíselnými typy, kde cílový typ může ukládat všechny hodnoty zdrojového typu.</span><span class="sxs-lookup"><span data-stu-id="8b790-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="8b790-158">Například existuje implicitní převod z `int` na `long`, protože rozsah hodnot `int` je správná podmnožina `long`.</span><span class="sxs-lookup"><span data-stu-id="8b790-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="8b790-159">Existují implicitní převody z menšího integrálního typu bez znaménka na větší typ se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="8b790-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="8b790-160">Je také implicitní převod z libovolného integrálního typu na libovolný typ s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="8b790-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="8b790-161">Neexistuje žádný implicitní převod z žádného typu se znaménkem na celočíselný typ bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="8b790-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="8b790-162">Je nutné použít explicitní přetypování pro převod jednoho celočíselného typu na jiný integrálový typ, pokud implicitní převod není definován ze zdrojového typu na cílový typ.</span><span class="sxs-lookup"><span data-stu-id="8b790-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="8b790-163">Tato metoda se nazývá *zužující převod*.</span><span class="sxs-lookup"><span data-stu-id="8b790-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="8b790-164">Explicitní případ je vyžadován, protože převod může mít za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="8b790-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8b790-165">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b790-165">C# language specification</span></span>

<span data-ttu-id="8b790-166">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8b790-166">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8b790-167">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="8b790-167">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="8b790-168">Celočíselné literály</span><span class="sxs-lookup"><span data-stu-id="8b790-168">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="8b790-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b790-169">See also</span></span>

- [<span data-ttu-id="8b790-170">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="8b790-170">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8b790-171">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="8b790-171">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="8b790-172">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="8b790-172">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="8b790-173">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="8b790-173">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="8b790-174">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="8b790-174">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="8b790-175">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="8b790-175">Numerics in .NET</span></span>](../../../standard/numerics.md)
