---
title: Celočíselné číselné typy C# – referenční informace
description: Seznamte se s rozsahem, velikostí úložiště a s využitím pro každý celočíselný numerický typ.
ms.date: 10/22/2019
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
ms.openlocfilehash: c255711e4b165fdca27d50c6bd0f2debfe15ae25
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773871"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="2dcbc-103">Integrální číselné typy (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="2dcbc-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="2dcbc-104">**Integrální číselné typy** jsou podmnožinou **jednoduchých typů** a lze je inicializovat pomocí [*literálů*](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="2dcbc-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integer-literals).</span></span> <span data-ttu-id="2dcbc-105">Všechny celočíselné typy jsou také typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-105">All integral types are also value types.</span></span> <span data-ttu-id="2dcbc-106">Všechny integrální číselné typy podporují [aritmetické](../operators/arithmetic-operators.md)a [logické](../operators/bitwise-and-shift-operators.md)operátory, [porovnání](../operators/comparison-operators.md)a [rovnost](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="2dcbc-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="2dcbc-107">Charakteristiky integrálních typů</span><span class="sxs-lookup"><span data-stu-id="2dcbc-107">Characteristics of the integral types</span></span>

<span data-ttu-id="2dcbc-108">C#podporuje následující předdefinované celočíselné typy:</span><span class="sxs-lookup"><span data-stu-id="2dcbc-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="2dcbc-109">C#typ/klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="2dcbc-109">C# type/keyword</span></span>|<span data-ttu-id="2dcbc-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2dcbc-110">Range</span></span>|<span data-ttu-id="2dcbc-111">Velikost</span><span class="sxs-lookup"><span data-stu-id="2dcbc-111">Size</span></span>|<span data-ttu-id="2dcbc-112">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="2dcbc-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="2dcbc-113">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="2dcbc-113">-128 to 127</span></span>|<span data-ttu-id="2dcbc-114">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2dcbc-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="2dcbc-115">0 až 255</span><span class="sxs-lookup"><span data-stu-id="2dcbc-115">0 to 255</span></span>|<span data-ttu-id="2dcbc-116">8bitové celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="2dcbc-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="2dcbc-117">-32 768 až 32 767</span><span class="sxs-lookup"><span data-stu-id="2dcbc-117">-32,768 to 32,767</span></span>|<span data-ttu-id="2dcbc-118">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2dcbc-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="2dcbc-119">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="2dcbc-119">0 to 65,535</span></span>|<span data-ttu-id="2dcbc-120">16bitové celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="2dcbc-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="2dcbc-121">-2 147 483 648 až 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="2dcbc-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="2dcbc-122">Podepsané 32 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2dcbc-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="2dcbc-123">0 až 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="2dcbc-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="2dcbc-124">Celé číslo bez znaménka 32-bit</span><span class="sxs-lookup"><span data-stu-id="2dcbc-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="2dcbc-125">– 9223372036854775808 na 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="2dcbc-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="2dcbc-126">Podepsané 64 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2dcbc-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="2dcbc-127">0 až 18446744073709551615</span><span class="sxs-lookup"><span data-stu-id="2dcbc-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="2dcbc-128">Celé číslo bez znaménka 64-bit</span><span class="sxs-lookup"><span data-stu-id="2dcbc-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="2dcbc-129">V předchozí tabulce je každé C# klíčové slovo Type ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="2dcbc-130">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-130">They are interchangeable.</span></span> <span data-ttu-id="2dcbc-131">Například následující deklarace deklaruje proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="2dcbc-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="2dcbc-132">Výchozí hodnota každého integrálního typu je nula, `0`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="2dcbc-133">Každý celočíselný typ má `MinValue` a `MaxValue` konstanty, které poskytují minimální a maximální hodnotu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="2dcbc-134">Pomocí <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury reprezentovat celé číslo se znaménkem bez horních nebo dolních mezí.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="2dcbc-135">Celočíselné literály</span><span class="sxs-lookup"><span data-stu-id="2dcbc-135">Integer literals</span></span>

<span data-ttu-id="2dcbc-136">Celočíselné literály mohou být</span><span class="sxs-lookup"><span data-stu-id="2dcbc-136">Integer literals can be</span></span>

- <span data-ttu-id="2dcbc-137">*Decimal*: bez předpony</span><span class="sxs-lookup"><span data-stu-id="2dcbc-137">*decimal*: without any prefix</span></span>
- <span data-ttu-id="2dcbc-138">*šestnáctková*: s předponou `0x` nebo `0X`</span><span class="sxs-lookup"><span data-stu-id="2dcbc-138">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="2dcbc-139">*binární*: s předponou `0b` nebo `0B` (k dispozici v C# 7,0 a novějším)</span><span class="sxs-lookup"><span data-stu-id="2dcbc-139">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="2dcbc-140">Následující kód ukazuje příklad každé z nich:</span><span class="sxs-lookup"><span data-stu-id="2dcbc-140">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="2dcbc-141">Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-141">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="2dcbc-142">Oddělovač číslic se dá použít u všech druhů číselných literálů.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-142">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="2dcbc-143">Typ celočíselného literálu je určen jeho příponou takto:</span><span class="sxs-lookup"><span data-stu-id="2dcbc-143">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="2dcbc-144">Pokud literál nemá žádnou příponu, je jeho typ prvním z následujících typů, ve kterém může být jeho hodnota reprezentovaná: `int`, `uint`, `long` `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-144">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="2dcbc-145">Je-li literál určen `U` nebo `u`, je jeho typ prvním z následujících typů, ve kterém lze jeho hodnotu reprezentovat: `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-145">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="2dcbc-146">Je-li literál určen `L` nebo `l`, je jeho typ prvním z následujících typů, ve kterém lze jeho hodnotu reprezentovat: `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-146">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2dcbc-147">Jako příponu můžete použít malé písmeno `l`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-147">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="2dcbc-148">Tím se však vygeneruje upozornění kompilátoru, protože písmeno `l` může být zaměněno pomocí číslice `1`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-148">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="2dcbc-149">Pro přehlednost použijte `L`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-149">Use `L` for clarity.</span></span>

- <span data-ttu-id="2dcbc-150">Pokud má literál příponu `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` nebo `lu`, jeho typ je `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-150">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="2dcbc-151">Pokud hodnota reprezentovaná celočíselným literálem překračuje <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilátoru [CS1021](../../misc/cs1021.md) .</span><span class="sxs-lookup"><span data-stu-id="2dcbc-151">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="2dcbc-152">Pokud je určený typ celočíselného literálu `int` a hodnota spadá do rozsahu cílového typu, hodnota reprezentovaná literálem se může implicitně převést na `sbyte`, `byte`, `short`, `ushort`, `uint`nebo `ulong`:</span><span class="sxs-lookup"><span data-stu-id="2dcbc-152">If the determined type of an integer literal is `int` and the value is within the range of the destination type, the value represented by the literal can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="2dcbc-153">Jak ukazuje předchozí příklad, pokud hodnota literálu není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031](../../misc/cs0031.md) .</span><span class="sxs-lookup"><span data-stu-id="2dcbc-153">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="2dcbc-154">Můžete také použít přetypování k převodu hodnoty reprezentované celočíselným literálem na jiný typ, než je určený typ literálu:</span><span class="sxs-lookup"><span data-stu-id="2dcbc-154">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="2dcbc-155">Převody</span><span class="sxs-lookup"><span data-stu-id="2dcbc-155">Conversions</span></span>

<span data-ttu-id="2dcbc-156">Libovolný celočíselný numerický typ můžete převést na jakýkoliv jiný integrální číselný typ.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-156">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="2dcbc-157">Pokud cílový typ může ukládat všechny hodnoty zdrojového typu, je převod implicitní.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-157">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="2dcbc-158">V opačném případě je nutné použít [operátor přetypování `()`](../operators/type-testing-and-cast.md#cast-operator-) k vyvolání explicitního převodu.</span><span class="sxs-lookup"><span data-stu-id="2dcbc-158">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="2dcbc-159">Další informace najdete v tématu [integrované číselné převody](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="2dcbc-159">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2dcbc-160">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2dcbc-160">C# language specification</span></span>

<span data-ttu-id="2dcbc-161">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="2dcbc-161">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2dcbc-162">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="2dcbc-162">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="2dcbc-163">Celočíselné literály</span><span class="sxs-lookup"><span data-stu-id="2dcbc-163">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="2dcbc-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dcbc-164">See also</span></span>

- [<span data-ttu-id="2dcbc-165">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="2dcbc-165">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2dcbc-166">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="2dcbc-166">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="2dcbc-167">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="2dcbc-167">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="2dcbc-168">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="2dcbc-168">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="2dcbc-169">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="2dcbc-169">Numerics in .NET</span></span>](../../../standard/numerics.md)
