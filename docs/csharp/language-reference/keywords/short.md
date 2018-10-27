---
title: short (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 0d90f31da49b94eee490e95f0cdf1d582bb0b059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184150"
---
# <a name="short-c-reference"></a><span data-ttu-id="1382f-102">short (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1382f-102">short (C# Reference)</span></span>

<span data-ttu-id="1382f-103">`short` označuje integrální datový typ, který uchovává hodnoty podle velikosti a oblasti, které jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1382f-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="1382f-104">Typ</span><span class="sxs-lookup"><span data-stu-id="1382f-104">Type</span></span>|<span data-ttu-id="1382f-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1382f-105">Range</span></span>|<span data-ttu-id="1382f-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="1382f-106">Size</span></span>|<span data-ttu-id="1382f-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="1382f-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`short`|<span data-ttu-id="1382f-108">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="1382f-108">-32,768 to 32,767</span></span>|<span data-ttu-id="1382f-109">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="1382f-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="1382f-110">Literály</span><span class="sxs-lookup"><span data-stu-id="1382f-110">Literals</span></span>

<span data-ttu-id="1382f-111">Můžete deklarovat a inicializovat `short` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="1382f-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="1382f-112">Pokud celočíselný literál je mimo rozsah `short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="1382f-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="1382f-113">V následujícím příkladu celých čísel je rovno 1,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](int.md) k `short` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1382f-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `short` values.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> <span data-ttu-id="1382f-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="1382f-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="1382f-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="1382f-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1382f-116">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="1382f-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>

- <span data-ttu-id="1382f-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="1382f-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="1382f-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="1382f-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="1382f-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="1382f-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="1382f-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="1382f-120">Some examples are shown below.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="1382f-121">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="1382f-121">Compiler overload resolution</span></span>

<span data-ttu-id="1382f-122">Přetypování musí být použito při volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="1382f-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="1382f-123">Zvažte například následující přetížené metody, které používají `short` a [int](int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="1382f-123">Consider, for example, the following overloaded methods that use `short` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

<span data-ttu-id="1382f-124">Použití `short` přetypování zaručuje, že správný typ název, například:</span><span class="sxs-lookup"><span data-stu-id="1382f-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a><span data-ttu-id="1382f-125">Převody</span><span class="sxs-lookup"><span data-stu-id="1382f-125">Conversions</span></span>

<span data-ttu-id="1382f-126">Není předdefinovanou implicitní převod z `short` k [int](int.md), [dlouhé](long.md), [float](float.md), [double](double.md), nebo [ desetinné](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="1382f-126">There is a predefined implicit conversion from `short` to [int](int.md), [long](long.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="1382f-127">Nelze implicitně převést neliterální číselné typy větší velikosti úložiště `short` (naleznete v tématu [integrální typy tabulky](integral-types-table.md) pro velikosti úložiště celočíselných typů).</span><span class="sxs-lookup"><span data-stu-id="1382f-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="1382f-128">Zvažte například následující dva `short` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="1382f-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>

```csharp
short x = 5, y = 12;
```

<span data-ttu-id="1382f-129">Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako [int](int.md) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1382f-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](int.md) by default.</span></span>

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

<span data-ttu-id="1382f-130">Pokud chcete tento problém vyřešit, použijte přetypování:</span><span class="sxs-lookup"><span data-stu-id="1382f-130">To fix this problem, use a cast:</span></span>

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

<span data-ttu-id="1382f-131">Je také možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="1382f-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="1382f-132">Neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `short`.</span><span class="sxs-lookup"><span data-stu-id="1382f-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="1382f-133">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="1382f-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

<span data-ttu-id="1382f-134">Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="1382f-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="1382f-135">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="1382f-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1382f-136">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1382f-136">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1382f-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1382f-137">See also</span></span>

- <xref:System.Int16>
- [<span data-ttu-id="1382f-138">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1382f-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1382f-139">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1382f-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1382f-140">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1382f-140">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1382f-141">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="1382f-141">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="1382f-142">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="1382f-142">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="1382f-143">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="1382f-143">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="1382f-144">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="1382f-144">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)