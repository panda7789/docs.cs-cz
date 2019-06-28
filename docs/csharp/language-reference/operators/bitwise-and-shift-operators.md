---
title: Bitové operátory a operátory posunutí - C# odkaz
description: Další informace o C# operátory, které provádějí operace bitový logický nebo operace posunutí se operandy integrální typy.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 8068ec09f0c7d05d6d711e4e7a607b6183727b41
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424001"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="5f825-103">Bitový operátor a operátory posunutí (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="5f825-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="5f825-104">Následující operátory provádějí operace bitový nebo shift operací s operandy [celočíselných typů](../builtin-types/integral-numeric-types.md):</span><span class="sxs-lookup"><span data-stu-id="5f825-104">The following operators perform bitwise or shift operations with operands of the [integral types](../builtin-types/integral-numeric-types.md):</span></span>

- <span data-ttu-id="5f825-105">Unární [ `~` (bitový doplněk)](#bitwise-complement-operator-) – operátor</span><span class="sxs-lookup"><span data-stu-id="5f825-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="5f825-106">Binární [ `<<` (levý shift)](#left-shift-operator-) a [ `>>` (posunutí doprava)](#right-shift-operator-) operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="5f825-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="5f825-107">Binární [ `&` (logický operátor a)](#logical-and-operator-), [ `|` (logický operátor nebo)](#logical-or-operator-), a [ `^` (logické XOR)](#logical-exclusive-or-operator-) operátory</span><span class="sxs-lookup"><span data-stu-id="5f825-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="5f825-108">Tyto operátory jsou definovány pro `int`, `uint`, `long`, a `ulong` typy.</span><span class="sxs-lookup"><span data-stu-id="5f825-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="5f825-109">Pokud jsou oba operandy jiné typy celých čísel (`sbyte`, `byte`, `short`, `ushort`, nebo `char`), jejich hodnoty se převedou na `int` typ, který je také typ výsledku operace.</span><span class="sxs-lookup"><span data-stu-id="5f825-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="5f825-110">Když operandy jsou odlišnými typy celých čísel, jejich hodnoty se převedou na nejbližší obsahující integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="5f825-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="5f825-111">Další informace najdete v tématu [číselné propagace](~/_csharplang/spec/expressions.md#numeric-promotions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5f825-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="5f825-112">`&`, `|`, A `^` operátory jsou také definovány pro operandy `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="5f825-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="5f825-113">Další informace najdete v tématu [logické logické operátory](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5f825-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="5f825-114">Bitový operátor a operace posunutí nikdy způsobit přetečení a produkuje stejné výsledky v [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) kontexty.</span><span class="sxs-lookup"><span data-stu-id="5f825-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="5f825-115">Operátor bitového doplňku ~</span><span class="sxs-lookup"><span data-stu-id="5f825-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="5f825-116">`~` Operátor vytvoří bitový doplněk svého operandu přehozením každý bit:</span><span class="sxs-lookup"><span data-stu-id="5f825-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="5f825-117">Můžete také použít `~` symbol finalizační metody deklarovat.</span><span class="sxs-lookup"><span data-stu-id="5f825-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="5f825-118">Další informace najdete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="5f825-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="5f825-119">Operátor posunutí doleva \<\<</span><span class="sxs-lookup"><span data-stu-id="5f825-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="5f825-120">`<<` Operátor posune jeho levý operand doleva o počet bitů, které jsou určené jeho operand pravé strany.</span><span class="sxs-lookup"><span data-stu-id="5f825-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="5f825-121">Operace levého posunutí zahodí implikovaný bitů, které jsou mimo rozsah typu výsledku a nastaví nižšího řádu prázdný bitové pozice na nulu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5f825-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="5f825-122">Protože operátory posunutí jsou určená jenom pro `int`, `uint`, `long`, a `ulong` obsahuje typy, výsledek operace vždy alespoň 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="5f825-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="5f825-123">Pokud levý operand je jiný celočíselný typ (`sbyte`, `byte`, `short`, `ushort`, nebo `char`), jeho hodnota je převedena na `int` typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="5f825-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="5f825-124">Informace o tom, pravém operand `<<` operátor definuje počet posunů naleznete v tématu [Shift počet operátory posunutí](#shift-count-of-the-shift-operators) oddílu.</span><span class="sxs-lookup"><span data-stu-id="5f825-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="5f825-125">Operátor pravého posunutí >></span><span class="sxs-lookup"><span data-stu-id="5f825-125">Right-shift operator >></span></span>

<span data-ttu-id="5f825-126">`>>` Jeho levý operand operátoru přímo posune počet bitů, které jsou určené jeho zpracovával pravý operand.</span><span class="sxs-lookup"><span data-stu-id="5f825-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="5f825-127">Operace pravého posunutí zahodí bity nižšího řádu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5f825-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="5f825-128">Nejvyšším prázdný bitové pozice jsou nastavena na základě typu levý operand následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5f825-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="5f825-129">Pokud levý operand je typu [int](../builtin-types/integral-numeric-types.md) nebo [dlouhé](../builtin-types/integral-numeric-types.md), operátor pravého posunutí provádí *aritmetické* shift: hodnota nejvýznamnější bit (bit znaménka) Levý operand je postoupena do nejvyšším prázdný bitové pozice.</span><span class="sxs-lookup"><span data-stu-id="5f825-129">If the left-hand operand is of type [int](../builtin-types/integral-numeric-types.md) or [long](../builtin-types/integral-numeric-types.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="5f825-130">To znamená, implikovaný prázdný bitové pozice jsou nastaveny na nulu pokud levý operand je nastaven na nezáporné a nastavit na jednu, pokud je záporné.</span><span class="sxs-lookup"><span data-stu-id="5f825-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="5f825-131">Pokud levý operand je typu [uint](../builtin-types/integral-numeric-types.md) nebo [ulong](../builtin-types/integral-numeric-types.md), operátor pravého posunutí provádí *logické* shift: nejvyšším prázdný bitové pozice jsou vždy nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="5f825-131">If the left-hand operand is of type [uint](../builtin-types/integral-numeric-types.md) or [ulong](../builtin-types/integral-numeric-types.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="5f825-132">Informace o tom, pravém operand `>>` operátor definuje počet posunů naleznete v tématu [Shift počet operátory posunutí](#shift-count-of-the-shift-operators) oddílu.</span><span class="sxs-lookup"><span data-stu-id="5f825-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="5f825-133">Logický operátor AND &amp;</span><span class="sxs-lookup"><span data-stu-id="5f825-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="5f825-134">`&` Vypočítá bitové logické AND jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="5f825-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="5f825-135">Pro operandy `bool` typ, `&` operátor výpočetní prostředí [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="5f825-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="5f825-136">Unární `&` operátor je [operátoru address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="5f825-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="5f825-137">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="5f825-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="5f825-138">`^` Operátor vypočítá bitový logický exkluzivní OR označované také jako bitové logické XOR z operandů:</span><span class="sxs-lookup"><span data-stu-id="5f825-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="5f825-139">Pro operandy `bool` typ, `^` operátor výpočetní prostředí [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="5f825-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="5f825-140">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="5f825-140">Logical OR operator |</span></span>

<span data-ttu-id="5f825-141">`|` Vypočítá bitové logické OR jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="5f825-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="5f825-142">Pro operandy `bool` typ, `|` operátor výpočetní prostředí [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="5f825-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="5f825-143">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="5f825-143">Compound assignment</span></span>

<span data-ttu-id="5f825-144">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="5f825-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="5f825-145">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="5f825-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="5f825-146">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="5f825-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="5f825-147">Následující příklad ukazuje použití složeného přiřazení s bitovým a operátory posunutí:</span><span class="sxs-lookup"><span data-stu-id="5f825-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="5f825-148">Z důvodu [číselné propagace](~/_csharplang/spec/expressions.md#numeric-promotions), výsledek `op` operace může být implicitně převést na typ `T` z `x`.</span><span class="sxs-lookup"><span data-stu-id="5f825-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="5f825-149">V takovém případě pokud `op` je předdefinovaný operátor a výsledek operace je výslovně převeditelný na typ `T` z `x`, výraz složeného přiřazení formuláře `x op= y` je ekvivalentní `x = (T)(x op y)`, s výjimkou který `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="5f825-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="5f825-150">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="5f825-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="5f825-151">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="5f825-151">Operator precedence</span></span>

<span data-ttu-id="5f825-152">Následující seznam objednávky bitové a operátory posunutí od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="5f825-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="5f825-153">Operátor bitového doplňku `~`</span><span class="sxs-lookup"><span data-stu-id="5f825-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="5f825-154">Operátory posunutí `<<` a `>>`</span><span class="sxs-lookup"><span data-stu-id="5f825-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="5f825-155">Logický operátor AND `&`</span><span class="sxs-lookup"><span data-stu-id="5f825-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="5f825-156">Logické exkluzivní OR – operátor `^`</span><span class="sxs-lookup"><span data-stu-id="5f825-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="5f825-157">Logický operátor OR `|`</span><span class="sxs-lookup"><span data-stu-id="5f825-157">Logical OR operator `|`</span></span>

<span data-ttu-id="5f825-158">Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů:</span><span class="sxs-lookup"><span data-stu-id="5f825-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="5f825-159">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="5f825-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="5f825-160">Počet posunů operátorů posunutí</span><span class="sxs-lookup"><span data-stu-id="5f825-160">Shift count of the shift operators</span></span>

<span data-ttu-id="5f825-161">Pro operátory posunutí `<<` a `>>`, musí být typu zpracovával pravý operand [int](../builtin-types/integral-numeric-types.md) nebo typ, který má [předdefinované implicitní převod čísla](../keywords/implicit-numeric-conversions-table.md) k `int`.</span><span class="sxs-lookup"><span data-stu-id="5f825-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be [int](../builtin-types/integral-numeric-types.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="5f825-162">Pro `x << count` a `x >> count` výrazy, počet skutečné posunutí závisí na typu `x` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5f825-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="5f825-163">Pokud typ `x` je [int](../builtin-types/integral-numeric-types.md) nebo [uint](../builtin-types/integral-numeric-types.md), počet posunů je definován nižšího řádu *pět* bits operand pravé strany.</span><span class="sxs-lookup"><span data-stu-id="5f825-163">If the type of `x` is [int](../builtin-types/integral-numeric-types.md) or [uint](../builtin-types/integral-numeric-types.md), the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="5f825-164">To znamená, že počet posunů je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="5f825-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="5f825-165">Pokud typ `x` je [dlouhé](../builtin-types/integral-numeric-types.md) nebo [ulong](../builtin-types/integral-numeric-types.md), počet posunů je definován nižšího řádu *šest* bits operand pravé strany.</span><span class="sxs-lookup"><span data-stu-id="5f825-165">If the type of `x` is [long](../builtin-types/integral-numeric-types.md) or [ulong](../builtin-types/integral-numeric-types.md), the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="5f825-166">To znamená, že počet posunů je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="5f825-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="5f825-167">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="5f825-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="5f825-168">Výčet logické operátory</span><span class="sxs-lookup"><span data-stu-id="5f825-168">Enumeration logical operators</span></span>

<span data-ttu-id="5f825-169">`~`, `&`, `|`, A `^` operátory jsou také definovány pro všechny [výčet](../keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="5f825-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="5f825-170">Pro operandy stejný typ výčtu se provádí logické operace na odpovídající hodnoty základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="5f825-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="5f825-171">Například pro všechny `x` a `y` výčtového typu `T` s podkladovým typem `U`, `x & y` výraz vytvoří stejný výsledek jako `(T)((U)x & (U)y)` výrazu.</span><span class="sxs-lookup"><span data-stu-id="5f825-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="5f825-172">Obvykle použijete bitové logické operátory s typem výčtu, která je definována s [příznaky](xref:System.FlagsAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="5f825-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="5f825-173">Další informace najdete v tématu [výčtové typy jako bitové příznaky](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) část [výčtové typy](../../programming-guide/enumeration-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="5f825-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5f825-174">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="5f825-174">Operator overloadability</span></span>

<span data-ttu-id="5f825-175">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `~`, `<<`, `>>`, `&`, `|`, a `^` operátory.</span><span class="sxs-lookup"><span data-stu-id="5f825-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="5f825-176">Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="5f825-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="5f825-177">Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="5f825-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="5f825-178">Pokud uživatelský typ `T` přetížení `<<` nebo `>>` operátoru musí být typu levý operand `T` a musí být typu zpracovával pravý operand `int`.</span><span class="sxs-lookup"><span data-stu-id="5f825-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5f825-179">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f825-179">C# language specification</span></span>

<span data-ttu-id="5f825-180">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5f825-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5f825-181">Operátor bitového doplňku</span><span class="sxs-lookup"><span data-stu-id="5f825-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="5f825-182">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="5f825-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="5f825-183">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="5f825-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="5f825-184">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="5f825-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="5f825-185">Číselné propagačních akcí</span><span class="sxs-lookup"><span data-stu-id="5f825-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="5f825-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f825-186">See also</span></span>

- [<span data-ttu-id="5f825-187">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="5f825-187">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5f825-188">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f825-188">C# operators</span></span>](index.md)
- [<span data-ttu-id="5f825-189">Logická logické operátory</span><span class="sxs-lookup"><span data-stu-id="5f825-189">Boolean logical operators</span></span>](boolean-logical-operators.md)
