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
ms.openlocfilehash: 141475c4d92278be02d6a832a93cd8553a4bcbd8
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661128"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="d195b-103">Integrální číselné typy (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="d195b-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="d195b-104">**Integrální číselné typy** jsou podmnožinou **jednoduché typy** a mohou být inicializovány pomocí [ *literály*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="d195b-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="d195b-105">Typy hodnot jsou také všechny celočíselné typy.</span><span class="sxs-lookup"><span data-stu-id="d195b-105">All integral types are also value types.</span></span>

<span data-ttu-id="d195b-106">Všechny integrální číselné typy. podpora [aritmetické](../operators/arithmetic-operators.md), [bitový logický](../operators/bitwise-and-shift-operators.md), [porovnání a rovnost](../operators/equality-operators.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="d195b-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="sizes-and-ranges"></a><span data-ttu-id="d195b-107">Velikosti a oblasti</span><span class="sxs-lookup"><span data-stu-id="d195b-107">Sizes and ranges</span></span>

<span data-ttu-id="d195b-108">V následující tabulce jsou uvedeny velikosti a rozsah celočíselných typů:</span><span class="sxs-lookup"><span data-stu-id="d195b-108">The following table shows the sizes and ranges of the integral types:</span></span>

|<span data-ttu-id="d195b-109">type</span><span class="sxs-lookup"><span data-stu-id="d195b-109">Type</span></span>|<span data-ttu-id="d195b-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d195b-110">Range</span></span>|<span data-ttu-id="d195b-111">Velikost</span><span class="sxs-lookup"><span data-stu-id="d195b-111">Size</span></span>|  
|----------|-----------|----------|  
|`sbyte`|<span data-ttu-id="d195b-112">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="d195b-112">-128 to 127</span></span>|<span data-ttu-id="d195b-113">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d195b-113">Signed 8-bit integer</span></span>|  
|`byte`|<span data-ttu-id="d195b-114">0 až 255</span><span class="sxs-lookup"><span data-stu-id="d195b-114">0 to 255</span></span>|<span data-ttu-id="d195b-115">Celé číslo bez znaménka 8 bitů</span><span class="sxs-lookup"><span data-stu-id="d195b-115">Unsigned 8-bit integer</span></span>|  
|`short`|<span data-ttu-id="d195b-116">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="d195b-116">-32,768 to 32,767</span></span>|<span data-ttu-id="d195b-117">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d195b-117">Signed 16-bit integer</span></span>|  
|`ushort`|<span data-ttu-id="d195b-118">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="d195b-118">0 to 65,535</span></span>|<span data-ttu-id="d195b-119">Celé číslo bez znaménka 16 bitů</span><span class="sxs-lookup"><span data-stu-id="d195b-119">Unsigned 16-bit integer</span></span>|  
|`int`|<span data-ttu-id="d195b-120">-2 147 483 648 do 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="d195b-120">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="d195b-121">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d195b-121">Signed 32-bit integer</span></span>|  
|`uint`|<span data-ttu-id="d195b-122">0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="d195b-122">0 to 4,294,967,295</span></span>|<span data-ttu-id="d195b-123">Nepodepsané 32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="d195b-123">Unsigned 32-bit integer</span></span>|  
|`long`|<span data-ttu-id="d195b-124">-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="d195b-124">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="d195b-125">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d195b-125">Signed 64-bit integer</span></span>|  
|`ulong`|<span data-ttu-id="d195b-126">0 na 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="d195b-126">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="d195b-127">64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="d195b-127">Unsigned 64-bit integer</span></span>|  

<span data-ttu-id="d195b-128">Výchozí hodnota pro všechny celočíselné typy je `0`.</span><span class="sxs-lookup"><span data-stu-id="d195b-128">The default value for all integral types is `0`.</span></span> <span data-ttu-id="d195b-129">Každá z celočíselných typů obsahuje konstanty s názvem `MinValue` a `MaxValue` pro minimální a maximální hodnotu daného typu.</span><span class="sxs-lookup"><span data-stu-id="d195b-129">Each of the integral types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span>

<span data-ttu-id="d195b-130">Použití <xref:System.Numerics.BigInteger?displayProperty=nameWithType> strukturu představující celé číslo se znaménkem s žádná horní nebo dolní meze.</span><span class="sxs-lookup"><span data-stu-id="d195b-130">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="d195b-131">Integrální literály</span><span class="sxs-lookup"><span data-stu-id="d195b-131">Integral literals</span></span>

<span data-ttu-id="d195b-132">Integrální literály lze zadat jako *desítkové literály*, *šestnáctkové literály*, nebo *binární literály:* .</span><span class="sxs-lookup"><span data-stu-id="d195b-132">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="d195b-133">Níže je uveden příklad každé:</span><span class="sxs-lookup"><span data-stu-id="d195b-133">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="d195b-134">Desítkové literály nevyžadují jakoukoli předponu.</span><span class="sxs-lookup"><span data-stu-id="d195b-134">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="d195b-135">`x` Nebo `X` označuje, že předpona *šestnáctkové literál*.</span><span class="sxs-lookup"><span data-stu-id="d195b-135">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="d195b-136">`b` Nebo `B` označuje, že předpona *binární literál*.</span><span class="sxs-lookup"><span data-stu-id="d195b-136">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="d195b-137">Deklarace `binaryLiteral` demonstruje použití `_` jako *oddělovač číslic*.</span><span class="sxs-lookup"><span data-stu-id="d195b-137">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="d195b-138">Oddělovač číslic jde použít s všechny číselné literály.</span><span class="sxs-lookup"><span data-stu-id="d195b-138">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="d195b-139">Binární literály a oddělovače číslic `_` podporuje workflowy C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="d195b-139">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

## <a name="literal-suffixes"></a><span data-ttu-id="d195b-140">Přípony literálu</span><span class="sxs-lookup"><span data-stu-id="d195b-140">Literal suffixes</span></span> 

<span data-ttu-id="d195b-141">`l` Nebo `L` příponu Určuje, že by měl být celočíselný literál `long` typu.</span><span class="sxs-lookup"><span data-stu-id="d195b-141">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="d195b-142">`ul` Nebo `UL` Určuje příponu `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="d195b-142">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="d195b-143">Pokud `L` přípona se používá na literál, který je větší než 9,223,372,036,854,775,807 (maximální hodnota `long`), hodnota převedená na `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="d195b-143">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="d195b-144">Pokud se překročí Hodnota reprezentovaná celočíselného literálu <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, chybu kompilátoru [CS1021](../../misc/cs1021.md) vyvolá.</span><span class="sxs-lookup"><span data-stu-id="d195b-144">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="d195b-145">Malé písmeno "l" můžete použít jako příponu.</span><span class="sxs-lookup"><span data-stu-id="d195b-145">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="d195b-146">Nicméně tím se vygeneruje upozornění kompilátoru protože písmeno "l" je snadno zaměnitelná s číslicí "1".</span><span class="sxs-lookup"><span data-stu-id="d195b-146">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="d195b-147">Pro přehlednost použijte "L".</span><span class="sxs-lookup"><span data-stu-id="d195b-147">Use "L" for clarity.</span></span>

## <a name="type-of-an-integral-literal"></a><span data-ttu-id="d195b-148">Typ celočíselný literál</span><span class="sxs-lookup"><span data-stu-id="d195b-148">Type of an integral literal</span></span>

<span data-ttu-id="d195b-149">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="d195b-149">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="d195b-150">Celočíselný literál lze převést na typ s menší rozsah, než je výchozí přiřazení nebo výraz přetypování:</span><span class="sxs-lookup"><span data-stu-id="d195b-150">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="d195b-151">Celočíselný literál lze převést na typ s větším než výchozí, pomocí přiřazení, přetypování nebo příponu na literál:</span><span class="sxs-lookup"><span data-stu-id="d195b-151">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="d195b-152">Převody</span><span class="sxs-lookup"><span data-stu-id="d195b-152">Conversions</span></span>

<span data-ttu-id="d195b-153">Je implicitní převod (volá se *rozšiřující převod*) mezi dvou celočíselných typů kde cílový typ můžete uložit všechny hodnoty typu zdroje.</span><span class="sxs-lookup"><span data-stu-id="d195b-153">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="d195b-154">Například je implicitní převod z `int` k `long` protože rozsah `int` hodnoty jsou správné podmnožinou `long`.</span><span class="sxs-lookup"><span data-stu-id="d195b-154">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="d195b-155">Nejsou k dispozici implicitní převod z menší celočíselný typ bez znaménka větší celočíselný typ se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="d195b-155">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="d195b-156">Existuje také implicitní převod z libovolný integrální typ na libovolný typ s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="d195b-156">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="d195b-157">Neexistuje žádný implicitní převod z libovolný integrální typ se znaménkem na libovolný integrální typ bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="d195b-157">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="d195b-158">Pro převod jedné celočíselného typu na jiný celočíselný typ při implicitní převod není definován zdrojový typ pro cílový typ je nutné použít explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="d195b-158">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="d195b-159">Jedná se *zužující převod*.</span><span class="sxs-lookup"><span data-stu-id="d195b-159">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="d195b-160">Explicitní případu se totiž převod může dojít ke ztrátě.</span><span class="sxs-lookup"><span data-stu-id="d195b-160">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="d195b-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d195b-161">See also</span></span>

- [<span data-ttu-id="d195b-162">C#Specifikace jazyka - integrální typy</span><span class="sxs-lookup"><span data-stu-id="d195b-162">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="d195b-163">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="d195b-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d195b-164">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="d195b-164">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="d195b-165">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="d195b-165">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="d195b-166">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="d195b-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="d195b-167">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="d195b-167">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="d195b-168">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="d195b-168">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
