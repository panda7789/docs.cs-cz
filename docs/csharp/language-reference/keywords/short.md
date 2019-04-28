---
title: short – C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 8c38a4158f627f41d1667eb96478cd499de78772
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660648"
---
# <a name="short-c-reference"></a><span data-ttu-id="5ef8b-102">short (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5ef8b-102">short (C# Reference)</span></span>

<span data-ttu-id="5ef8b-103">`short` označuje integrální datový typ, který uchovává hodnoty podle velikosti a oblasti, které jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="5ef8b-104">Type</span><span class="sxs-lookup"><span data-stu-id="5ef8b-104">Type</span></span>|<span data-ttu-id="5ef8b-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="5ef8b-105">Range</span></span>|<span data-ttu-id="5ef8b-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="5ef8b-106">Size</span></span>|<span data-ttu-id="5ef8b-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="5ef8b-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`short`|<span data-ttu-id="5ef8b-108">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="5ef8b-108">-32,768 to 32,767</span></span>|<span data-ttu-id="5ef8b-109">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="5ef8b-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="5ef8b-110">Literály</span><span class="sxs-lookup"><span data-stu-id="5ef8b-110">Literals</span></span>

<span data-ttu-id="5ef8b-111">Můžete deklarovat a inicializovat `short` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="5ef8b-112">Pokud celočíselný literál je mimo rozsah `short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="5ef8b-113">V následujícím příkladu celých čísel je rovno 1,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](int.md) k `short` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `short` values.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> <span data-ttu-id="5ef8b-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="5ef8b-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5ef8b-116">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>

- <span data-ttu-id="5ef8b-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="5ef8b-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="5ef8b-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="5ef8b-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-120">Some examples are shown below.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="5ef8b-121">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="5ef8b-121">Compiler overload resolution</span></span>

<span data-ttu-id="5ef8b-122">Přetypování musí být použito při volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="5ef8b-123">Zvažte například následující přetížené metody, které používají `short` a [int](int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="5ef8b-123">Consider, for example, the following overloaded methods that use `short` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

<span data-ttu-id="5ef8b-124">Použití `short` přetypování zaručuje, že správný typ název, například:</span><span class="sxs-lookup"><span data-stu-id="5ef8b-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a><span data-ttu-id="5ef8b-125">Převody</span><span class="sxs-lookup"><span data-stu-id="5ef8b-125">Conversions</span></span>

<span data-ttu-id="5ef8b-126">Není předdefinovanou implicitní převod z `short` k [int](int.md), [dlouhé](long.md), [float](float.md), [double](double.md), nebo [ desetinné](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="5ef8b-126">There is a predefined implicit conversion from `short` to [int](int.md), [long](long.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="5ef8b-127">Nelze implicitně převést neliterální číselné typy větší velikosti úložiště `short` (naleznete v tématu [integrální typy tabulky](integral-types-table.md) pro velikosti úložiště celočíselných typů).</span><span class="sxs-lookup"><span data-stu-id="5ef8b-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="5ef8b-128">Zvažte například následující dva `short` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="5ef8b-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>

```csharp
short x = 5, y = 12;
```

<span data-ttu-id="5ef8b-129">Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako [int](int.md) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](int.md) by default.</span></span>

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

<span data-ttu-id="5ef8b-130">Pokud chcete tento problém vyřešit, použijte přetypování:</span><span class="sxs-lookup"><span data-stu-id="5ef8b-130">To fix this problem, use a cast:</span></span>

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

<span data-ttu-id="5ef8b-131">Je také možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="5ef8b-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="5ef8b-132">Neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `short`.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="5ef8b-133">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="5ef8b-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

<span data-ttu-id="5ef8b-134">Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="5ef8b-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="5ef8b-135">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="5ef8b-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5ef8b-136">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5ef8b-136">C# language specification</span></span>

<span data-ttu-id="5ef8b-137">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5ef8b-137">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="5ef8b-138">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="5ef8b-138">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef8b-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ef8b-139">See also</span></span>

- <xref:System.Int16>
- [<span data-ttu-id="5ef8b-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5ef8b-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5ef8b-141">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5ef8b-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5ef8b-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5ef8b-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5ef8b-143">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="5ef8b-143">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="5ef8b-144">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="5ef8b-144">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="5ef8b-145">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="5ef8b-145">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="5ef8b-146">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="5ef8b-146">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)