---
title: Long - C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: a3c2dc725d5747c638acba9311ae78272cf63de0
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186010"
---
# <a name="long-c-reference"></a><span data-ttu-id="2d972-102">long (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2d972-102">long (C# Reference)</span></span>

<span data-ttu-id="2d972-103">`long` označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2d972-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="2d972-104">Typ</span><span class="sxs-lookup"><span data-stu-id="2d972-104">Type</span></span>|<span data-ttu-id="2d972-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2d972-105">Range</span></span>|<span data-ttu-id="2d972-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="2d972-106">Size</span></span>|<span data-ttu-id="2d972-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="2d972-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`long`|<span data-ttu-id="2d972-108">-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="2d972-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="2d972-109">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2d972-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="2d972-110">Literály</span><span class="sxs-lookup"><span data-stu-id="2d972-110">Literals</span></span>

<span data-ttu-id="2d972-111">Můžete deklarovat a inicializovat `long` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="2d972-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>

<span data-ttu-id="2d972-112">V následujícím příkladu celých čísel rovnat do 4 294 967 296 jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `long` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2d972-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]

> [!NOTE]
> <span data-ttu-id="2d972-113">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="2d972-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="2d972-114">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="2d972-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2d972-115">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="2d972-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>
- <span data-ttu-id="2d972-116">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="2d972-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="2d972-117">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="2d972-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="2d972-118">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="2d972-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="2d972-119">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="2d972-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

<span data-ttu-id="2d972-120">Literály celých čísel může také obsahovat příponu, která označuje typ.</span><span class="sxs-lookup"><span data-stu-id="2d972-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="2d972-121">Přípona `L` označuje `long`.</span><span class="sxs-lookup"><span data-stu-id="2d972-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="2d972-122">V následujícím příkladu `L` příponu k označení dlouhé celé číslo:</span><span class="sxs-lookup"><span data-stu-id="2d972-122">The following example uses the `L` suffix to denote a long integer:</span></span>

```csharp
long value = 4294967296L;
```

> [!NOTE]
> <span data-ttu-id="2d972-123">Malé písmeno "l" můžete také použít jako příponu.</span><span class="sxs-lookup"><span data-stu-id="2d972-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="2d972-124">Nicméně tím se vygeneruje upozornění kompilátoru protože písmeno "l" je snadno zaměnitelná s číslicí "1".</span><span class="sxs-lookup"><span data-stu-id="2d972-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="2d972-125">Pro přehlednost použijte "L".</span><span class="sxs-lookup"><span data-stu-id="2d972-125">Use "L" for clarity.</span></span>

<span data-ttu-id="2d972-126">Pokud použijete tuto příponu `L`, vyhodnotí typu literál celého čísla buď `long` nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), v závislosti na jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="2d972-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="2d972-127">V takovém případě je `long` vzhledem k tomu je méně než rozsah [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="2d972-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>

<span data-ttu-id="2d972-128">Běžné použití přípona je volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="2d972-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="2d972-129">Například následující přetížené metody mít parametry typu `long` a [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="2d972-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(long l) {}
```

<span data-ttu-id="2d972-130">`L` Přípona zaručuje, že je volána správné přetížení:</span><span class="sxs-lookup"><span data-stu-id="2d972-130">The `L` suffix guarantees that the correct overload is called:</span></span>

```csharp
SampleMethod(5);    // Calls the method with the int parameter
SampleMethod(5L);   // Calls the method with the long parameter
```
<span data-ttu-id="2d972-131">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="2d972-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="2d972-132">int</span><span class="sxs-lookup"><span data-stu-id="2d972-132">int</span></span>](int.md)
2. [<span data-ttu-id="2d972-133">uint</span><span class="sxs-lookup"><span data-stu-id="2d972-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="2d972-134">ulong</span><span class="sxs-lookup"><span data-stu-id="2d972-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)

<span data-ttu-id="2d972-135">Typ je literál 4294967296 v předchozích příkladech `long`, protože překračuje rozsah [uint](../../../csharp/language-reference/keywords/uint.md) (naleznete v tématu [integrální typy tabulky](../../../csharp/language-reference/keywords/integral-types-table.md) pro velikosti úložiště celočíselných typů).</span><span class="sxs-lookup"><span data-stu-id="2d972-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>

<span data-ttu-id="2d972-136">Pokud používáte `long` typ s jiné typy celých čísel ve stejném výrazu, výrazu je vyhodnoceno jako `long` (nebo [bool](../../../csharp/language-reference/keywords/bool.md) v případě relační nebo logické výrazy).</span><span class="sxs-lookup"><span data-stu-id="2d972-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="2d972-137">Například následující výraz se vyhodnocuje jako `long`:</span><span class="sxs-lookup"><span data-stu-id="2d972-137">For example, the following expression evaluates as `long`:</span></span>

```csharp
898L + 88
```

<span data-ttu-id="2d972-138">Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="2d972-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="2d972-139">Převody</span><span class="sxs-lookup"><span data-stu-id="2d972-139">Conversions</span></span>

<span data-ttu-id="2d972-140">Není předdefinovanou implicitní převod z `long` k [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="2d972-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="2d972-141">V opačném případě se musí použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="2d972-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="2d972-142">Například následující příkaz vytvoří chybu kompilace bez explicitního přetypování:</span><span class="sxs-lookup"><span data-stu-id="2d972-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>

```csharp
int x = 8L;        // Error: no implicit conversion from long to int
int y = (int)8L;   // OK: explicit conversion to int
```

<span data-ttu-id="2d972-143">Není předdefinovanou implicitní převod z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátký](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `long`.</span><span class="sxs-lookup"><span data-stu-id="2d972-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>

<span data-ttu-id="2d972-144">Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `long`.</span><span class="sxs-lookup"><span data-stu-id="2d972-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="2d972-145">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="2d972-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
long x = 3.0;         // Error: no implicit conversion from double
long y = (long)3.0;   // OK: explicit conversion
```

## <a name="c-language-specification"></a><span data-ttu-id="2d972-146">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d972-146">C# Language Specification</span></span>

<span data-ttu-id="2d972-147">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d972-147">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="2d972-148">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2d972-148">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d972-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d972-149">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="2d972-150">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d972-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="2d972-151">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2d972-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2d972-152">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d972-152">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="2d972-153">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="2d972-153">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="2d972-154">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="2d972-154">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="2d972-155">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="2d972-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="2d972-156">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="2d972-156">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
