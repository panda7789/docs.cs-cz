---
title: Integrální číselné typy – odkaz jazyka C#
description: Seznamte se s rozsahem, velikostí úložiště a použitím pro každý z integrovaných číselných typů.
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
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093198"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="3c884-103">Integrální číselné typy (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="3c884-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="3c884-104">*Integrální číselné typy* představují celá čísla.</span><span class="sxs-lookup"><span data-stu-id="3c884-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="3c884-105">Všechny integrální číselné typy jsou [typy hodnot](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="3c884-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="3c884-106">Jsou to také [jednoduché typy](value-types.md#built-in-value-types) a mohou být inicializovány [literály](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="3c884-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="3c884-107">Všechny integrální číselné typy podporují [aritmetické](../operators/arithmetic-operators.md), [bitové logické](../operators/bitwise-and-shift-operators.md), [porovnávací](../operators/comparison-operators.md)a [rovnoprávné](../operators/equality-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="3c884-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="3c884-108">Charakteristika integrálních typů</span><span class="sxs-lookup"><span data-stu-id="3c884-108">Characteristics of the integral types</span></span>

<span data-ttu-id="3c884-109">C# podporuje následující předdefinované integrální typy:</span><span class="sxs-lookup"><span data-stu-id="3c884-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="3c884-110">C# typ/klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="3c884-110">C# type/keyword</span></span>|<span data-ttu-id="3c884-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3c884-111">Range</span></span>|<span data-ttu-id="3c884-112">Velikost</span><span class="sxs-lookup"><span data-stu-id="3c884-112">Size</span></span>|<span data-ttu-id="3c884-113">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="3c884-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="3c884-114">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="3c884-114">-128 to 127</span></span>|<span data-ttu-id="3c884-115">Podepsané osmibitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="3c884-116">0 až 255</span><span class="sxs-lookup"><span data-stu-id="3c884-116">0 to 255</span></span>|<span data-ttu-id="3c884-117">Nepodepsané osmibitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="3c884-118">-32 768 až 32 767</span><span class="sxs-lookup"><span data-stu-id="3c884-118">-32,768 to 32,767</span></span>|<span data-ttu-id="3c884-119">Podepsané 16bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="3c884-120">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="3c884-120">0 to 65,535</span></span>|<span data-ttu-id="3c884-121">Nepodepsané 16bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="3c884-122">-2 147 483 648 až 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="3c884-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="3c884-123">Podepsané 32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="3c884-124">0 až 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="3c884-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="3c884-125">Nepodepsané 32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="3c884-126">-9 223 372 036 854 775 808 až 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="3c884-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="3c884-127">Podepsané 64bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="3c884-128">0 až 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="3c884-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="3c884-129">Nepodepsané 64bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3c884-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="3c884-130">V předchozí tabulce je každé klíčové slovo typu C# ze sloupce zcela vlevo aliasem odpovídajícího typu .NET.</span><span class="sxs-lookup"><span data-stu-id="3c884-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="3c884-131">Jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="3c884-131">They are interchangeable.</span></span> <span data-ttu-id="3c884-132">Například následující deklarace deklarují proměnné stejného typu:</span><span class="sxs-lookup"><span data-stu-id="3c884-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="3c884-133">Výchozí hodnota každého integrálního `0`typu je nula .</span><span class="sxs-lookup"><span data-stu-id="3c884-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="3c884-134">Každý z integrální typy má `MinValue` konstanty a, `MaxValue` které poskytují minimální a maximální hodnotu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="3c884-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="3c884-135">Pomocí <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury reprezentujte podepsané celé číslo bez horních nebo dolních hranic.</span><span class="sxs-lookup"><span data-stu-id="3c884-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="3c884-136">Celé číslo literály</span><span class="sxs-lookup"><span data-stu-id="3c884-136">Integer literals</span></span>

<span data-ttu-id="3c884-137">Celé literály lze</span><span class="sxs-lookup"><span data-stu-id="3c884-137">Integer literals can be</span></span>

- <span data-ttu-id="3c884-138">*desítkové*: bez předpony</span><span class="sxs-lookup"><span data-stu-id="3c884-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="3c884-139">*hexadecimální*: `0x` `0X` s předponou nebo</span><span class="sxs-lookup"><span data-stu-id="3c884-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="3c884-140">*binární*: `0b` s `0B` předponou nebo (k dispozici v C# 7.0 a novější)</span><span class="sxs-lookup"><span data-stu-id="3c884-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="3c884-141">Následující kód ukazuje příklad každého z nich:</span><span class="sxs-lookup"><span data-stu-id="3c884-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="3c884-142">Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován počínaje C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="3c884-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="3c884-143">Oddělovač číslic můžete použít se všemi druhy číselných literál.</span><span class="sxs-lookup"><span data-stu-id="3c884-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="3c884-144">Typ literálu celého čísla je určen jeho příponou takto:</span><span class="sxs-lookup"><span data-stu-id="3c884-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="3c884-145">Pokud literál nemá žádnou příponu, jeho typ je první z následujících `uint` `long`typů, ve kterých může být jeho hodnota reprezentována: `int`, , , `ulong`.</span><span class="sxs-lookup"><span data-stu-id="3c884-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="3c884-146">Pokud je literál doplněn `U` nebo `u`, jeho typ je prvním z následujících typů, `uint` `ulong`ve kterém může být jeho hodnota reprezentována: , .</span><span class="sxs-lookup"><span data-stu-id="3c884-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="3c884-147">Pokud je literál doplněn `L` nebo `l`, jeho typ je prvním z následujících typů, `long` `ulong`ve kterém může být jeho hodnota reprezentována: , .</span><span class="sxs-lookup"><span data-stu-id="3c884-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3c884-148">Malé písmeno `l` můžete použít jako příponu.</span><span class="sxs-lookup"><span data-stu-id="3c884-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="3c884-149">To však generuje upozornění kompilátoru, protože písmeno `l` může být zaměněno s číslicí `1`.</span><span class="sxs-lookup"><span data-stu-id="3c884-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="3c884-150">Použití `L` pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="3c884-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="3c884-151">Pokud je literál doplněn `UL`, `Ul` `uL`, `ul` `LU`, `Lu` `lU`, `lu`, , `ulong`, nebo , jeho typ je .</span><span class="sxs-lookup"><span data-stu-id="3c884-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="3c884-152">Pokud hodnota reprezentovaná literálem celé číslo překročí <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilátoru [CS1021.](../../misc/cs1021.md)</span><span class="sxs-lookup"><span data-stu-id="3c884-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="3c884-153">Pokud je `int` určený typ celého literálu a hodnota reprezentovaná literálem je v rozsahu cílového `sbyte` `byte`typu, může být hodnota implicitně převedena na `short`, , , `ushort`, `uint`, nebo `ulong`:</span><span class="sxs-lookup"><span data-stu-id="3c884-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="3c884-154">Jak ukazuje předchozí příklad, pokud hodnota literálu není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031.](../../misc/cs0031.md)</span><span class="sxs-lookup"><span data-stu-id="3c884-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="3c884-155">Přetypovat můžete také převést hodnotu reprezentovanou literálem celéčíslo na typ jiný než určený typ literálu:</span><span class="sxs-lookup"><span data-stu-id="3c884-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="3c884-156">Převody</span><span class="sxs-lookup"><span data-stu-id="3c884-156">Conversions</span></span>

<span data-ttu-id="3c884-157">Libovolný integrální číselný typ můžete převést na jakýkoli jiný integrální číselný typ.</span><span class="sxs-lookup"><span data-stu-id="3c884-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="3c884-158">Pokud cílový typ může uložit všechny hodnoty typu zdroje, převod je implicitní.</span><span class="sxs-lookup"><span data-stu-id="3c884-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="3c884-159">V opačném případě je nutné použít [operátor `()` přetypádka](../operators/type-testing-and-cast.md#cast-operator-) k vyvolání explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="3c884-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="3c884-160">Další informace naleznete [v tématu Předdefinované číselné převody](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="3c884-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3c884-161">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3c884-161">C# language specification</span></span>

<span data-ttu-id="3c884-162">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="3c884-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="3c884-163">Integrální typy</span><span class="sxs-lookup"><span data-stu-id="3c884-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="3c884-164">Celé číslo literály</span><span class="sxs-lookup"><span data-stu-id="3c884-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="3c884-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c884-165">See also</span></span>

- [<span data-ttu-id="3c884-166">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="3c884-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3c884-167">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="3c884-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="3c884-168">Typy s plovoucí desetinnou tálicí</span><span class="sxs-lookup"><span data-stu-id="3c884-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="3c884-169">Standardní číselné formátovací řetězce</span><span class="sxs-lookup"><span data-stu-id="3c884-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="3c884-170">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="3c884-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
