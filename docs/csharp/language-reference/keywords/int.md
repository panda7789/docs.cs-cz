---
title: int – C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 6cabc2c6d4930c5d5fc88e76a17c1a6425ddd1bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661383"
---
# <a name="int-c-reference"></a><span data-ttu-id="9c1e1-102">int (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9c1e1-102">int (C# Reference)</span></span>

<span data-ttu-id="9c1e1-103">`int` označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="9c1e1-104">Type</span><span class="sxs-lookup"><span data-stu-id="9c1e1-104">Type</span></span>|<span data-ttu-id="9c1e1-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9c1e1-105">Range</span></span>|<span data-ttu-id="9c1e1-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="9c1e1-106">Size</span></span>|<span data-ttu-id="9c1e1-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="9c1e1-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`int`|<span data-ttu-id="9c1e1-108">-2 147 483 648 do 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="9c1e1-108">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="9c1e1-109">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9c1e1-109">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="9c1e1-110">Literály</span><span class="sxs-lookup"><span data-stu-id="9c1e1-110">Literals</span></span>

<span data-ttu-id="9c1e1-111">Můžete deklarovat a inicializovat `int` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-111">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="9c1e1-112">Pokud celočíselný literál je mimo rozsah `int` (tj. Pokud je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-112">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="9c1e1-113">V následujícím příkladu celých čísel je rovno 90,946, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `int` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-113">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]

> [!NOTE]
> <span data-ttu-id="9c1e1-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="9c1e1-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9c1e1-116">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>
- <span data-ttu-id="9c1e1-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="9c1e1-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="9c1e1-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="9c1e1-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-120">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]

<span data-ttu-id="9c1e1-121">Literály celých čísel může také obsahovat příponu, která označuje typ., ačkoli neexistuje žádné příponu, která označuje `int` typu.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="9c1e1-122">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="9c1e1-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
2. [<span data-ttu-id="9c1e1-123">uint</span><span class="sxs-lookup"><span data-stu-id="9c1e1-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="9c1e1-124">long</span><span class="sxs-lookup"><span data-stu-id="9c1e1-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="9c1e1-125">ulong</span><span class="sxs-lookup"><span data-stu-id="9c1e1-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)

<span data-ttu-id="9c1e1-126">V těchto příkladech je literál 90946 typu `int`.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-126">In these examples, the literal 90946 is of type `int`.</span></span>

## <a name="conversions"></a><span data-ttu-id="9c1e1-127">Převody</span><span class="sxs-lookup"><span data-stu-id="9c1e1-127">Conversions</span></span>

<span data-ttu-id="9c1e1-128">Není předdefinovanou implicitní převod z `int` k [dlouhé](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="9c1e1-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="9c1e1-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9c1e1-129">For example:</span></span>

```csharp
// '123' is an int, so an implicit conversion takes place here:
float f = 123;
```

<span data-ttu-id="9c1e1-130">Není předdefinovanou implicitní převod z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátký](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `int`.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="9c1e1-131">Přiřazovací příkaz například způsobí chybu kompilace bez přetypování:</span><span class="sxs-lookup"><span data-stu-id="9c1e1-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>

```csharp
long aLong = 22;
int i1 = aLong;       // Error: no implicit conversion from long.
int i2 = (int)aLong;  // OK: explicit conversion.
```

<span data-ttu-id="9c1e1-132">Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `int`.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="9c1e1-133">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="9c1e1-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
int x = 3.0;         // Error: no implicit conversion from double.
int y = (int)3.0;    // OK: explicit conversion.
```

<span data-ttu-id="9c1e1-134">Další informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="9c1e1-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9c1e1-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c1e1-135">C# Language Specification</span></span>

<span data-ttu-id="9c1e1-136">Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c1e1-136">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="9c1e1-137">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9c1e1-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c1e1-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c1e1-138">See also</span></span>

- <xref:System.Int32>
- [<span data-ttu-id="9c1e1-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c1e1-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="9c1e1-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9c1e1-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9c1e1-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c1e1-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="9c1e1-142">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="9c1e1-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="9c1e1-143">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="9c1e1-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="9c1e1-144">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="9c1e1-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="9c1e1-145">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="9c1e1-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
