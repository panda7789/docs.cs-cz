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
ms.openlocfilehash: df696b9b9462f1a844d43043b968f30404da586d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660096"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="64ef1-103">Bitový operátor a operátory posunutí (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="64ef1-103">Bitwise and shift operators (C# Reference)</span></span>

<span data-ttu-id="64ef1-104">Následující operátory provádějí operace bitový nebo shift operací s operandy [celočíselných typů](../keywords/integral-types-table.md):</span><span class="sxs-lookup"><span data-stu-id="64ef1-104">The following operators perform bitwise or shift operations with operands of the [integral types](../keywords/integral-types-table.md):</span></span>

- <span data-ttu-id="64ef1-105">Unární [ `~` (bitový doplněk)](#bitwise-complement-operator-) – operátor</span><span class="sxs-lookup"><span data-stu-id="64ef1-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="64ef1-106">Binární [ `<<` (levý shift)](#left-shift-operator-) a [ `>>` (posunutí doprava)](#right-shift-operator-) operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="64ef1-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="64ef1-107">Binární [ `&` (logický operátor a)](#logical-and-operator-), [ `|` (logický operátor nebo)](#logical-or-operator-), a [ `^` (logické XOR)](#logical-exclusive-or-operator-) operátory</span><span class="sxs-lookup"><span data-stu-id="64ef1-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="64ef1-108">Tyto operátory jsou definovány pro `int`, `uint`, `long`, a `ulong` typy.</span><span class="sxs-lookup"><span data-stu-id="64ef1-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="64ef1-109">Pokud jsou oba operandy jiné typy celých čísel (`sbyte`, `byte`, `short`, `ushort`, nebo `char`), jejich hodnoty se převedou na `int` typ, který je také typ výsledku operace.</span><span class="sxs-lookup"><span data-stu-id="64ef1-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="64ef1-110">Když operandy jsou odlišnými typy celých čísel, jejich hodnoty se převedou na nejbližší obsahující integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="64ef1-111">Další informace najdete v tématu [číselné propagace](~/_csharplang/spec/expressions.md#numeric-promotions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="64ef1-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="64ef1-112">`&`, `|`, A `^` operátory jsou také definovány pro operandy `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="64ef1-113">Další informace najdete v tématu [logické logické operátory](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="64ef1-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="64ef1-114">Bitový operátor a operace posunutí nikdy způsobit přetečení a produkuje stejné výsledky v [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) kontexty.</span><span class="sxs-lookup"><span data-stu-id="64ef1-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="64ef1-115">Operátor bitového doplňku ~</span><span class="sxs-lookup"><span data-stu-id="64ef1-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="64ef1-116">`~` Operátor vytvoří bitový doplněk svého operandu přehozením každý bit:</span><span class="sxs-lookup"><span data-stu-id="64ef1-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="64ef1-117">Můžete také použít `~` symbol finalizační metody deklarovat.</span><span class="sxs-lookup"><span data-stu-id="64ef1-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="64ef1-118">Další informace najdete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="64ef1-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="64ef1-119">Operátor posunutí doleva \<\<</span><span class="sxs-lookup"><span data-stu-id="64ef1-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="64ef1-120">`<<` Operátor posune jeho prvního operandu vlevo o počet bitů, které jsou určené svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="64ef1-120">The `<<` operator shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="64ef1-121">Operace levého posunutí zahodí implikovaný bitů, které jsou mimo rozsah typu výsledku a nastaví nižšího řádu prázdný bitové pozice na nulu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="64ef1-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="64ef1-122">Protože operátory posunutí jsou určená jenom pro `int`, `uint`, `long`, a `ulong` obsahuje typy, výsledek operace vždy alespoň 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="64ef1-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="64ef1-123">Pokud je první operand je jiný celočíselný typ (`sbyte`, `byte`, `short`, `ushort`, nebo `char`), jeho hodnota je převedena na `int` typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="64ef1-123">If the first operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="64ef1-124">Informace o druhý operand `<<` operátor definuje počet posunů naleznete v tématu [Shift počet operátory posunutí](#shift-count-of-the-shift-operators) oddílu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-124">For information about how the second operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="64ef1-125">Operátor pravého posunutí >></span><span class="sxs-lookup"><span data-stu-id="64ef1-125">Right-shift operator >></span></span>

<span data-ttu-id="64ef1-126">`>>` Svůj první operand operátoru přímo posune počet bitů, které jsou určené svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="64ef1-126">The `>>` operator shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="64ef1-127">Operace pravého posunutí zahodí bity nižšího řádu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="64ef1-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="64ef1-128">Nejvyšším prázdný bitové pozice jsou nastaveny na základě typu prvního operandu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="64ef1-128">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="64ef1-129">Pokud je první operand je typu [int](../keywords/int.md) nebo [dlouhé](../keywords/long.md), operátor pravého posunutí provádí *aritmetické* shift: hodnota nejvýznamnější bit (bit znaménka) prvního operand je postoupena do nejvyšším prázdný bitové pozice.</span><span class="sxs-lookup"><span data-stu-id="64ef1-129">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="64ef1-130">To znamená, implikovaný prázdný bitové pozice nastavení na hodnotu nula, pokud je první operand je nastaven na nezáporné a nastavit na jednu, pokud je záporné.</span><span class="sxs-lookup"><span data-stu-id="64ef1-130">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="64ef1-131">Pokud je první operand je typu [uint](../keywords/uint.md) nebo [ulong](../keywords/ulong.md), operátor pravého posunutí provádí *logické* shift: nejvyšším prázdný bitové pozice jsou vždy nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="64ef1-131">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="64ef1-132">Informace o druhý operand `>>` operátor definuje počet posunů naleznete v tématu [Shift počet operátory posunutí](#shift-count-of-the-shift-operators) oddílu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-132">For information about how the second operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><span data-ttu-id="64ef1-133">Logický operátor AND &amp;</span><span class="sxs-lookup"><span data-stu-id="64ef1-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="64ef1-134">`&` Vypočítá bitové logické AND jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="64ef1-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="64ef1-135">Pro operandy `bool` typ, `&` operátor výpočetní prostředí [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="64ef1-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="64ef1-136">Unární `&` operátor je [operátoru address-of](and-operator.md#unary-address-of-operator).</span><span class="sxs-lookup"><span data-stu-id="64ef1-136">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="64ef1-137">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="64ef1-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="64ef1-138">`^` Operátor vypočítá bitový logický exkluzivní OR označované také jako bitové logické XOR z operandů:</span><span class="sxs-lookup"><span data-stu-id="64ef1-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="64ef1-139">Pro operandy `bool` typ, `^` operátor výpočetní prostředí [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="64ef1-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="64ef1-140">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="64ef1-140">Logical OR operator |</span></span>

<span data-ttu-id="64ef1-141">`|` Vypočítá bitové logické OR jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="64ef1-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="64ef1-142">Pro operandy `bool` typ, `|` operátor výpočetní prostředí [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="64ef1-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="64ef1-143">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="64ef1-143">Compound assignment</span></span>

<span data-ttu-id="64ef1-144">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="64ef1-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="64ef1-145">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="64ef1-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="64ef1-146">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="64ef1-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="64ef1-147">Následující příklad ukazuje použití složeného přiřazení s bitovým a operátory posunutí:</span><span class="sxs-lookup"><span data-stu-id="64ef1-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="64ef1-148">Z důvodu [číselné propagace](~/_csharplang/spec/expressions.md#numeric-promotions), výsledek `op` operace může být implicitně převést na typ `T` z `x`.</span><span class="sxs-lookup"><span data-stu-id="64ef1-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="64ef1-149">V takovém případě pokud `op` je předdefinovaný operátor a výsledek operace je výslovně převeditelný na typ `T` z `x`, výraz složeného přiřazení formuláře `x op= y` je ekvivalentní `x = (T)(x op y)`, s výjimkou který `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="64ef1-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="64ef1-150">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="64ef1-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="64ef1-151">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="64ef1-151">Operator precedence</span></span>

<span data-ttu-id="64ef1-152">Následující seznam objednávky bitové a operátory posunutí od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="64ef1-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="64ef1-153">Operátor bitového doplňku `~`</span><span class="sxs-lookup"><span data-stu-id="64ef1-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="64ef1-154">Operátory posunutí `<<` a `>>`</span><span class="sxs-lookup"><span data-stu-id="64ef1-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="64ef1-155">Logický operátor AND `&`</span><span class="sxs-lookup"><span data-stu-id="64ef1-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="64ef1-156">Logické exkluzivní OR – operátor `^`</span><span class="sxs-lookup"><span data-stu-id="64ef1-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="64ef1-157">Logický operátor OR `|`</span><span class="sxs-lookup"><span data-stu-id="64ef1-157">Logical OR operator `|`</span></span>

<span data-ttu-id="64ef1-158">Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů:</span><span class="sxs-lookup"><span data-stu-id="64ef1-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="64ef1-159">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="64ef1-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="64ef1-160">Počet posunů operátorů posunutí</span><span class="sxs-lookup"><span data-stu-id="64ef1-160">Shift count of the shift operators</span></span>

<span data-ttu-id="64ef1-161">Pro operátory posunutí `<<` a `>>`, musí být typu druhého operandu [int](../keywords/int.md) nebo typ, který má [předdefinované implicitní převod čísla](../keywords/implicit-numeric-conversions-table.md) k `int`.</span><span class="sxs-lookup"><span data-stu-id="64ef1-161">For the shift operators `<<` and `>>`, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="64ef1-162">Pro `x << count` a `x >> count` výrazy, počet skutečné posunutí závisí na typu `x` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="64ef1-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="64ef1-163">Pokud typ `x` je [int](../keywords/int.md) nebo [uint](../keywords/uint.md), počet posunů je definován nižšího řádu *pět* bits druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-163">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is defined by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="64ef1-164">To znamená, že počet posunů je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="64ef1-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="64ef1-165">Pokud typ `x` je [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md), počet posunů je definován nižšího řádu *šest* bits druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-165">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is defined by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="64ef1-166">To znamená, že počet posunů je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="64ef1-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="64ef1-167">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="64ef1-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="64ef1-168">Výčet logické operátory</span><span class="sxs-lookup"><span data-stu-id="64ef1-168">Enumeration logical operators</span></span>

<span data-ttu-id="64ef1-169">`~`, `&`, `|`, A `^` operátory jsou také definovány pro všechny [výčet](../keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="64ef1-170">Pro operandy stejný typ výčtu se provádí logické operace na odpovídající hodnoty základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="64ef1-171">Například pro všechny `x` a `y` výčtového typu `T` s podkladovým typem `U`, `x & y` výraz vytvoří stejný výsledek jako `(T)((U)x & (U)y)` výrazu.</span><span class="sxs-lookup"><span data-stu-id="64ef1-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="64ef1-172">Obvykle použijete bitové logické operátory s typem výčtu, která je definována s [příznaky](xref:System.FlagsAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="64ef1-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="64ef1-173">Další informace najdete v tématu [výčtové typy jako bitové příznaky](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) část [výčtové typy](../../programming-guide/enumeration-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="64ef1-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="64ef1-174">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="64ef1-174">Operator overloadability</span></span>

<span data-ttu-id="64ef1-175">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `~`, `<<`, `>>`, `&`, `|`, a `^` operátory.</span><span class="sxs-lookup"><span data-stu-id="64ef1-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="64ef1-176">Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="64ef1-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="64ef1-177">Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="64ef1-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="64ef1-178">Pokud uživatelský typ `T` přetížení `<<` nebo `>>` operátoru musí být typu prvního operandu `T` a musí být typu druhého operandu `int`.</span><span class="sxs-lookup"><span data-stu-id="64ef1-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="64ef1-179">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64ef1-179">C# language specification</span></span>

<span data-ttu-id="64ef1-180">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="64ef1-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="64ef1-181">Operátor bitového doplňku</span><span class="sxs-lookup"><span data-stu-id="64ef1-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="64ef1-182">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="64ef1-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="64ef1-183">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="64ef1-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="64ef1-184">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="64ef1-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="64ef1-185">Číselné propagačních akcí</span><span class="sxs-lookup"><span data-stu-id="64ef1-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="64ef1-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64ef1-186">See also</span></span>

- [<span data-ttu-id="64ef1-187">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64ef1-187">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="64ef1-188">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="64ef1-188">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="64ef1-189">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64ef1-189">C# Operators</span></span>](index.md)
- [<span data-ttu-id="64ef1-190">Logická logické operátory</span><span class="sxs-lookup"><span data-stu-id="64ef1-190">Boolean logical operators</span></span>](boolean-logical-operators.md)