---
title: Bitwise and shift operators - C# reference
description: Learn about C# operators that perform bitwise logical or shift operations with operands of integral types.
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
ms.openlocfilehash: 27f7cf46bd3e344503f74527df34506d38ad4545
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428445"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="9f9db-103">Bitwise and shift operators (C# reference)</span><span class="sxs-lookup"><span data-stu-id="9f9db-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="9f9db-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span><span class="sxs-lookup"><span data-stu-id="9f9db-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="9f9db-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span><span class="sxs-lookup"><span data-stu-id="9f9db-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="9f9db-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span><span class="sxs-lookup"><span data-stu-id="9f9db-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="9f9db-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span><span class="sxs-lookup"><span data-stu-id="9f9db-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="9f9db-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span><span class="sxs-lookup"><span data-stu-id="9f9db-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="9f9db-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span><span class="sxs-lookup"><span data-stu-id="9f9db-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="9f9db-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span><span class="sxs-lookup"><span data-stu-id="9f9db-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="9f9db-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9f9db-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="9f9db-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span><span class="sxs-lookup"><span data-stu-id="9f9db-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="9f9db-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9f9db-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="9f9db-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span><span class="sxs-lookup"><span data-stu-id="9f9db-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="9f9db-115">Bitwise complement operator ~</span><span class="sxs-lookup"><span data-stu-id="9f9db-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="9f9db-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span><span class="sxs-lookup"><span data-stu-id="9f9db-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="9f9db-117">You can also use the `~` symbol to declare finalizers.</span><span class="sxs-lookup"><span data-stu-id="9f9db-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="9f9db-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="9f9db-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="9f9db-119">Left-shift operator \<\<</span><span class="sxs-lookup"><span data-stu-id="9f9db-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="9f9db-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span><span class="sxs-lookup"><span data-stu-id="9f9db-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="9f9db-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span><span class="sxs-lookup"><span data-stu-id="9f9db-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="9f9db-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span><span class="sxs-lookup"><span data-stu-id="9f9db-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="9f9db-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span><span class="sxs-lookup"><span data-stu-id="9f9db-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="9f9db-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span><span class="sxs-lookup"><span data-stu-id="9f9db-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="9f9db-125">Right-shift operator >></span><span class="sxs-lookup"><span data-stu-id="9f9db-125">Right-shift operator >></span></span>

<span data-ttu-id="9f9db-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span><span class="sxs-lookup"><span data-stu-id="9f9db-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="9f9db-127">The right-shift operation discards the low-order bits, as the following example shows:</span><span class="sxs-lookup"><span data-stu-id="9f9db-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="9f9db-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span><span class="sxs-lookup"><span data-stu-id="9f9db-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="9f9db-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span><span class="sxs-lookup"><span data-stu-id="9f9db-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="9f9db-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span><span class="sxs-lookup"><span data-stu-id="9f9db-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="9f9db-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span><span class="sxs-lookup"><span data-stu-id="9f9db-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="9f9db-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span><span class="sxs-lookup"><span data-stu-id="9f9db-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="9f9db-133">Logical AND operator &amp;</span><span class="sxs-lookup"><span data-stu-id="9f9db-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="9f9db-134">The `&` operator computes the bitwise logical AND of its operands:</span><span class="sxs-lookup"><span data-stu-id="9f9db-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="9f9db-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span><span class="sxs-lookup"><span data-stu-id="9f9db-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="9f9db-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="9f9db-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="9f9db-137">Logical exclusive OR operator ^</span><span class="sxs-lookup"><span data-stu-id="9f9db-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="9f9db-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span><span class="sxs-lookup"><span data-stu-id="9f9db-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="9f9db-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span><span class="sxs-lookup"><span data-stu-id="9f9db-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="9f9db-140">Logical OR operator |</span><span class="sxs-lookup"><span data-stu-id="9f9db-140">Logical OR operator |</span></span>

<span data-ttu-id="9f9db-141">The `|` operator computes the bitwise logical OR of its operands:</span><span class="sxs-lookup"><span data-stu-id="9f9db-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="9f9db-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span><span class="sxs-lookup"><span data-stu-id="9f9db-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="9f9db-143">Compound assignment</span><span class="sxs-lookup"><span data-stu-id="9f9db-143">Compound assignment</span></span>

<span data-ttu-id="9f9db-144">For a binary operator `op`, a compound assignment expression of the form</span><span class="sxs-lookup"><span data-stu-id="9f9db-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="9f9db-145">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="9f9db-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="9f9db-146">except that `x` is only evaluated once.</span><span class="sxs-lookup"><span data-stu-id="9f9db-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="9f9db-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span><span class="sxs-lookup"><span data-stu-id="9f9db-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="9f9db-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span><span class="sxs-lookup"><span data-stu-id="9f9db-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="9f9db-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span><span class="sxs-lookup"><span data-stu-id="9f9db-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="9f9db-150">The following example demonstrates that behavior:</span><span class="sxs-lookup"><span data-stu-id="9f9db-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="9f9db-151">Operator precedence</span><span class="sxs-lookup"><span data-stu-id="9f9db-151">Operator precedence</span></span>

<span data-ttu-id="9f9db-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span><span class="sxs-lookup"><span data-stu-id="9f9db-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="9f9db-153">Bitwise complement operator `~`</span><span class="sxs-lookup"><span data-stu-id="9f9db-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="9f9db-154">Shift operators `<<` and `>>`</span><span class="sxs-lookup"><span data-stu-id="9f9db-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="9f9db-155">Logical AND operator `&`</span><span class="sxs-lookup"><span data-stu-id="9f9db-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="9f9db-156">Logical exclusive OR operator `^`</span><span class="sxs-lookup"><span data-stu-id="9f9db-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="9f9db-157">Logical OR operator `|`</span><span class="sxs-lookup"><span data-stu-id="9f9db-157">Logical OR operator `|`</span></span>

<span data-ttu-id="9f9db-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span><span class="sxs-lookup"><span data-stu-id="9f9db-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="9f9db-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span><span class="sxs-lookup"><span data-stu-id="9f9db-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="9f9db-160">Shift count of the shift operators</span><span class="sxs-lookup"><span data-stu-id="9f9db-160">Shift count of the shift operators</span></span>

<span data-ttu-id="9f9db-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span><span class="sxs-lookup"><span data-stu-id="9f9db-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="9f9db-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span><span class="sxs-lookup"><span data-stu-id="9f9db-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="9f9db-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span><span class="sxs-lookup"><span data-stu-id="9f9db-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="9f9db-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="9f9db-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="9f9db-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span><span class="sxs-lookup"><span data-stu-id="9f9db-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="9f9db-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="9f9db-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="9f9db-167">The following example demonstrates that behavior:</span><span class="sxs-lookup"><span data-stu-id="9f9db-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="9f9db-168">Enumeration logical operators</span><span class="sxs-lookup"><span data-stu-id="9f9db-168">Enumeration logical operators</span></span>

<span data-ttu-id="9f9db-169">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../keywords/enum.md) type.</span><span class="sxs-lookup"><span data-stu-id="9f9db-169">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="9f9db-170">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span><span class="sxs-lookup"><span data-stu-id="9f9db-170">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="9f9db-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span><span class="sxs-lookup"><span data-stu-id="9f9db-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="9f9db-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span><span class="sxs-lookup"><span data-stu-id="9f9db-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="9f9db-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span><span class="sxs-lookup"><span data-stu-id="9f9db-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="9f9db-174">Operator overloadability</span><span class="sxs-lookup"><span data-stu-id="9f9db-174">Operator overloadability</span></span>

<span data-ttu-id="9f9db-175">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span><span class="sxs-lookup"><span data-stu-id="9f9db-175">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="9f9db-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span><span class="sxs-lookup"><span data-stu-id="9f9db-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="9f9db-177">A user-defined type cannot explicitly overload a compound assignment operator.</span><span class="sxs-lookup"><span data-stu-id="9f9db-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="9f9db-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span><span class="sxs-lookup"><span data-stu-id="9f9db-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9f9db-179">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9f9db-179">C# language specification</span></span>

<span data-ttu-id="9f9db-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="9f9db-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="9f9db-181">Bitwise complement operator</span><span class="sxs-lookup"><span data-stu-id="9f9db-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="9f9db-182">Shift operators</span><span class="sxs-lookup"><span data-stu-id="9f9db-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="9f9db-183">Logical operators</span><span class="sxs-lookup"><span data-stu-id="9f9db-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="9f9db-184">Compound assignment</span><span class="sxs-lookup"><span data-stu-id="9f9db-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="9f9db-185">Numeric promotions</span><span class="sxs-lookup"><span data-stu-id="9f9db-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="9f9db-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f9db-186">See also</span></span>

- [<span data-ttu-id="9f9db-187">C# reference</span><span class="sxs-lookup"><span data-stu-id="9f9db-187">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9f9db-188">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9f9db-188">C# operators</span></span>](index.md)
- [<span data-ttu-id="9f9db-189">Boolean logical operators</span><span class="sxs-lookup"><span data-stu-id="9f9db-189">Boolean logical operators</span></span>](boolean-logical-operators.md)
