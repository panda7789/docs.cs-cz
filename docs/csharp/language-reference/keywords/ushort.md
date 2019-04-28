---
title: ushort – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660395"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="b9be0-102">ushort (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b9be0-102">ushort (C# Reference)</span></span>

<span data-ttu-id="b9be0-103">`ushort` – Klíčové slovo určuje celočíselný datový typ, který uchovává hodnoty podle velikosti a oblasti, které jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b9be0-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="b9be0-104">Type</span><span class="sxs-lookup"><span data-stu-id="b9be0-104">Type</span></span>|<span data-ttu-id="b9be0-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b9be0-105">Range</span></span>|<span data-ttu-id="b9be0-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="b9be0-106">Size</span></span>|<span data-ttu-id="b9be0-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="b9be0-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ushort`|<span data-ttu-id="b9be0-108">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="b9be0-108">0 to 65,535</span></span>|<span data-ttu-id="b9be0-109">Celé číslo bez znaménka 16 bitů</span><span class="sxs-lookup"><span data-stu-id="b9be0-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="b9be0-110">Literály</span><span class="sxs-lookup"><span data-stu-id="b9be0-110">Literals</span></span>

<span data-ttu-id="b9be0-111">Můžete deklarovat a inicializovat `ushort` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="b9be0-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="b9be0-112">Pokud celočíselný literál je mimo rozsah `ushort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="b9be0-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="b9be0-113">V následujícím příkladu celých čísel je rovno 65,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](int.md) k `ushort` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b9be0-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `ushort` values.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> <span data-ttu-id="b9be0-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="b9be0-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="b9be0-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="b9be0-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b9be0-116">Počínaje C# 7.0, několik funkce byly přidány za účelem zlepšení čitelnosti:</span><span class="sxs-lookup"><span data-stu-id="b9be0-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="b9be0-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="b9be0-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="b9be0-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="b9be0-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="b9be0-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="b9be0-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="b9be0-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="b9be0-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="b9be0-121">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="b9be0-121">Compiler overload resolution</span></span>

<span data-ttu-id="b9be0-122">Přetypování musí být použito při volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="b9be0-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="b9be0-123">Zvažte například následující přetížené metody, které používají `ushort` a [int](int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="b9be0-123">Consider, for example, the following overloaded methods that use `ushort` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

<span data-ttu-id="b9be0-124">Použití `ushort` přetypování zaručuje, že správný typ název, například:</span><span class="sxs-lookup"><span data-stu-id="b9be0-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a><span data-ttu-id="b9be0-125">Převody</span><span class="sxs-lookup"><span data-stu-id="b9be0-125">Conversions</span></span>

<span data-ttu-id="b9be0-126">Není předdefinovanou implicitní převod z `ushort` k [int](int.md), [uint](uint.md), [dlouhé](long.md), [ulong](ulong.md), [plovoucí desetinnou čárkou ](float.md), [double](double.md), nebo [desítkové](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="b9be0-126">There is a predefined implicit conversion from `ushort` to [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="b9be0-127">Není předdefinovanou implicitní převod z [bajtů](byte.md) nebo [char](char.md) k `ushort`.</span><span class="sxs-lookup"><span data-stu-id="b9be0-127">There is a predefined implicit conversion from [byte](byte.md) or [char](char.md) to `ushort`.</span></span> <span data-ttu-id="b9be0-128">V opačném případě musí být použito k provedení explicitního převodu přetypování.</span><span class="sxs-lookup"><span data-stu-id="b9be0-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="b9be0-129">Zvažte například následující dva `ushort` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="b9be0-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>

```csharp
ushort x = 5, y = 12;
```

<span data-ttu-id="b9be0-130">Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako `int` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="b9be0-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

<span data-ttu-id="b9be0-131">Pokud chcete tento problém vyřešit, použijte přetypování:</span><span class="sxs-lookup"><span data-stu-id="b9be0-131">To fix this problem, use a cast:</span></span>

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

<span data-ttu-id="b9be0-132">Je ale možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="b9be0-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="b9be0-133">Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `ushort`.</span><span class="sxs-lookup"><span data-stu-id="b9be0-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="b9be0-134">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="b9be0-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

<span data-ttu-id="b9be0-135">Informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="b9be0-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="b9be0-136">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="b9be0-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b9be0-137">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9be0-137">C# language specification</span></span>

<span data-ttu-id="b9be0-138">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b9be0-138">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="b9be0-139">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="b9be0-139">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9be0-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9be0-140">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="b9be0-141">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9be0-141">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b9be0-142">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b9be0-142">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b9be0-143">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9be0-143">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b9be0-144">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="b9be0-144">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="b9be0-145">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="b9be0-145">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="b9be0-146">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="b9be0-146">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="b9be0-147">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="b9be0-147">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
