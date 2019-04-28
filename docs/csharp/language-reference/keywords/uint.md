---
title: uint – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: e22468eea63ce082f2e9842e6ec307aba1888964
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660434"
---
# <a name="uint-c-reference"></a><span data-ttu-id="3794c-102">uint (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3794c-102">uint (C# Reference)</span></span>

<span data-ttu-id="3794c-103">`uint` – Klíčové slovo označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="3794c-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="3794c-104">Type</span><span class="sxs-lookup"><span data-stu-id="3794c-104">Type</span></span>|<span data-ttu-id="3794c-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3794c-105">Range</span></span>|<span data-ttu-id="3794c-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="3794c-106">Size</span></span>|<span data-ttu-id="3794c-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="3794c-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`uint`|<span data-ttu-id="3794c-108">0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="3794c-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="3794c-109">Nepodepsané 32bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="3794c-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|

<span data-ttu-id="3794c-110">**Poznámka:** `uint` typ není kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="3794c-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="3794c-111">Použití `int` kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="3794c-111">Use `int` whenever possible.</span></span>

## <a name="literals"></a><span data-ttu-id="3794c-112">Literály</span><span class="sxs-lookup"><span data-stu-id="3794c-112">Literals</span></span>

<span data-ttu-id="3794c-113">Můžete deklarovat a inicializovat `uint` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="3794c-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="3794c-114">Pokud celočíselný literál je mimo rozsah `uint` (tj. Pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="3794c-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="3794c-115">V následujícím příkladu celých čísel je rovno 3,000,000,000, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `uint` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3794c-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> <span data-ttu-id="3794c-116">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="3794c-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="3794c-117">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="3794c-117">Decimal literals have no prefix.</span></span>

<span data-ttu-id="3794c-118">Počínaje C# 7.0, několik funkce byly přidány za účelem zlepšení čitelnosti:</span><span class="sxs-lookup"><span data-stu-id="3794c-118">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="3794c-119">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="3794c-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="3794c-120">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="3794c-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="3794c-121">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="3794c-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="3794c-122">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="3794c-122">Some examples are shown below.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

<span data-ttu-id="3794c-123">Literály celých čísel může také obsahovat příponu, která označuje typ.</span><span class="sxs-lookup"><span data-stu-id="3794c-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="3794c-124">Přípona `U` nebo "u" označuje buď `uint` nebo `ulong`, v závislosti na číselnou hodnotu literálu.</span><span class="sxs-lookup"><span data-stu-id="3794c-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="3794c-125">V následujícím příkladu `u` příponu k označení celé číslo bez znaménka obou typů.</span><span class="sxs-lookup"><span data-stu-id="3794c-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="3794c-126">Všimněte si, že je první literál `uint` vzhledem k tomu, že její hodnota je menší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, zatímco druhá je `ulong` vzhledem k tomu, že její hodnota je větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3794c-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

<span data-ttu-id="3794c-127">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="3794c-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="3794c-128">int</span><span class="sxs-lookup"><span data-stu-id="3794c-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="3794c-129">long</span><span class="sxs-lookup"><span data-stu-id="3794c-129">long</span></span>](long.md)
4. [<span data-ttu-id="3794c-130">ulong</span><span class="sxs-lookup"><span data-stu-id="3794c-130">ulong</span></span>](ulong.md)

## <a name="conversions"></a><span data-ttu-id="3794c-131">Převody</span><span class="sxs-lookup"><span data-stu-id="3794c-131">Conversions</span></span>

<span data-ttu-id="3794c-132">Není předdefinovanou implicitní převod z `uint` k [dlouhé](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), nebo [ desetinné](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="3794c-132">There is a predefined implicit conversion from `uint` to [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span> <span data-ttu-id="3794c-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3794c-133">For example:</span></span>

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

<span data-ttu-id="3794c-134">Není předdefinovanou implicitní převod z [bajtů](byte.md), [ushort](ushort.md), nebo [char](char.md) k `uint`.</span><span class="sxs-lookup"><span data-stu-id="3794c-134">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), or [char](char.md) to `uint`.</span></span> <span data-ttu-id="3794c-135">V opačném případě je nutné použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="3794c-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="3794c-136">Přiřazovací příkaz například způsobí chybu kompilace bez přetypování:</span><span class="sxs-lookup"><span data-stu-id="3794c-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

<span data-ttu-id="3794c-137">Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `uint`.</span><span class="sxs-lookup"><span data-stu-id="3794c-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="3794c-138">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="3794c-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

<span data-ttu-id="3794c-139">Informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="3794c-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="3794c-140">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="3794c-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3794c-141">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3794c-141">C# language specification</span></span>

<span data-ttu-id="3794c-142">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3794c-142">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="3794c-143">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3794c-143">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3794c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3794c-144">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="3794c-145">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3794c-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3794c-146">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3794c-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3794c-147">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3794c-147">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3794c-148">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="3794c-148">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="3794c-149">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="3794c-149">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="3794c-150">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="3794c-150">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="3794c-151">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="3794c-151">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)