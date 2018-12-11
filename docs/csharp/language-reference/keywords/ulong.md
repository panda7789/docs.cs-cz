---
title: ulong – klíčové slovo (C# odkaz)
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: d0c7df4ebda13a59e51e9599699f6abf4bbf1d71
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143425"
---
# <a name="ulong-c-reference"></a><span data-ttu-id="eb527-102">ulong (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="eb527-102">ulong (C# Reference)</span></span>

<span data-ttu-id="eb527-103">`ulong` – Klíčové slovo označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="eb527-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="eb527-104">Typ</span><span class="sxs-lookup"><span data-stu-id="eb527-104">Type</span></span>|<span data-ttu-id="eb527-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="eb527-105">Range</span></span>|<span data-ttu-id="eb527-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="eb527-106">Size</span></span>|<span data-ttu-id="eb527-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="eb527-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ulong`|<span data-ttu-id="eb527-108">0 na 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="eb527-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="eb527-109">64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="eb527-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="eb527-110">Literály</span><span class="sxs-lookup"><span data-stu-id="eb527-110">Literals</span></span>

<span data-ttu-id="eb527-111">Můžete deklarovat a inicializovat `ulong` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="eb527-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="eb527-112">Pokud celočíselný literál je mimo rozsah `ulong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="eb527-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="eb527-113">V následujícím příkladu celých čísel je rovno 7,934,076,125, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `ulong` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="eb527-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>

[!code-csharp[ulong](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]

> [!NOTE]
> <span data-ttu-id="eb527-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="eb527-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="eb527-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="eb527-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="eb527-116">Počínaje C# 7.0, několik funkce byly přidány za účelem zlepšení čitelnosti:</span><span class="sxs-lookup"><span data-stu-id="eb527-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="eb527-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="eb527-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="eb527-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="eb527-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="eb527-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="eb527-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="eb527-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="eb527-120">Some examples are shown below.</span></span>

[!code-csharp[long](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

<span data-ttu-id="eb527-121">Literály celých čísel může také obsahovat příponu, která označuje typ.</span><span class="sxs-lookup"><span data-stu-id="eb527-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="eb527-122">Přípona `UL` nebo `ul` jednoznačně identifikuje jako číselný literál `ulong` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eb527-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="eb527-123">`L` Označuje příponu `ulong` pokud překročí hodnotu literálu <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb527-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb527-124">A `U` nebo `u` označuje příponu `ulong` pokud překročí hodnotu literálu <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb527-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb527-125">V následujícím příkladu `ul` příponu k označení dlouhé celé číslo:</span><span class="sxs-lookup"><span data-stu-id="eb527-125">The following example uses the `ul` suffix to denote a long integer:</span></span>

[!code-csharp[ulsuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="eb527-126">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="eb527-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="eb527-127">int</span><span class="sxs-lookup"><span data-stu-id="eb527-127">int</span></span>](int.md)
2. [<span data-ttu-id="eb527-128">uint</span><span class="sxs-lookup"><span data-stu-id="eb527-128">uint</span></span>](uint.md)
3. [<span data-ttu-id="eb527-129">long</span><span class="sxs-lookup"><span data-stu-id="eb527-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="eb527-130">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="eb527-130">Compiler overload resolution</span></span>

<span data-ttu-id="eb527-131">Je běžné použití přípony s voláním přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="eb527-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="eb527-132">Zvažte například následující přetížené metody, které používají `ulong` a [int](int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="eb527-132">Consider, for example, the following overloaded methods that use `ulong` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ulong l) {}
```

<span data-ttu-id="eb527-133">Pomocí přípony s `ulong` parametr zaručuje, že správný typ název, například:</span><span class="sxs-lookup"><span data-stu-id="eb527-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);    // Calling the method with the int parameter
SampleMethod(5UL);  // Calling the method with the ulong parameter
```

## <a name="conversions"></a><span data-ttu-id="eb527-134">Převody</span><span class="sxs-lookup"><span data-stu-id="eb527-134">Conversions</span></span>

<span data-ttu-id="eb527-135">Není předdefinovanou implicitní převod z `ulong` k [float](float.md), [double](double.md), nebo [desítkové](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="eb527-135">There is a predefined implicit conversion from `ulong` to [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="eb527-136">Neexistuje žádný implicitní převod z `ulong` na libovolný integrální typ.</span><span class="sxs-lookup"><span data-stu-id="eb527-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="eb527-137">Například následující příkaz vytvoří chybu kompilace bez explicitního přetypování:</span><span class="sxs-lookup"><span data-stu-id="eb527-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>

```csharp
long long1 = 8UL;   // Error: no implicit conversion from ulong
```

<span data-ttu-id="eb527-138">Není předdefinovanou implicitní převod z [bajtů](byte.md), [ushort](ushort.md), [uint](uint.md), nebo [char](char.md) k `ulong`.</span><span class="sxs-lookup"><span data-stu-id="eb527-138">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), [uint](uint.md), or [char](char.md) to `ulong`.</span></span>

<span data-ttu-id="eb527-139">Také, neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `ulong`.</span><span class="sxs-lookup"><span data-stu-id="eb527-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="eb527-140">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="eb527-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ulong x = 3.0;
// OK -- explicit conversion:
ulong y = (ulong)3.0;
```

<span data-ttu-id="eb527-141">Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="eb527-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="eb527-142">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="eb527-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eb527-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eb527-143">C# language specification</span></span>

<span data-ttu-id="eb527-144">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb527-144">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="eb527-145">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="eb527-145">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb527-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb527-146">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="eb527-147">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eb527-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eb527-148">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="eb527-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eb527-149">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eb527-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eb527-150">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="eb527-150">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="eb527-151">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="eb527-151">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="eb527-152">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="eb527-152">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="eb527-153">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="eb527-153">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
