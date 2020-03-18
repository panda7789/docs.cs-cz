---
title: Bitové a směny operátory - C# odkaz
description: Další informace o operátorech jazyka C#, které provádějí bitové logické operace nebo operace směny s operandy integrálních typů.
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
ms.openlocfilehash: 54198368672e0c9324210a232c7851b5a90402cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399264"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="c94a8-103">Bitové operátory a operátory směny (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="c94a8-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="c94a8-104">Následující operátory provádějí bitové operace nebo operace směny s operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) nebo typu [znaku:](../builtin-types/char.md)</span><span class="sxs-lookup"><span data-stu-id="c94a8-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="c94a8-105">Operátor Unární [ `~` (bitový doplněk)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="c94a8-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="c94a8-106">Binární [ `<<` (levý posun)](#left-shift-operator-) a [ `>>` (posun vpravo)](#right-shift-operator-) operátory posunu</span><span class="sxs-lookup"><span data-stu-id="c94a8-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="c94a8-107">Binární [ `&` (logické OPERÁTOR)](#logical-and-operator-) [ `|` , (logické OR)](#logical-or-operator-)a [ `^` (logické výhradní OPERÁTORy OR)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="c94a8-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="c94a8-108">Tyto hospodářské subjekty `int` `uint`jsou `long`definovány pro , , , a `ulong` typy.</span><span class="sxs-lookup"><span data-stu-id="c94a8-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="c94a8-109">Pokud jsou oba operandy jiných`sbyte` `byte`integrálních typů ( , , `short`, `ushort`, nebo `char`), jejich hodnoty jsou převedeny na `int` typ, který je také typ výsledku operace.</span><span class="sxs-lookup"><span data-stu-id="c94a8-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="c94a8-110">Pokud operandy jsou různé integrální typy, jejich hodnoty jsou převedeny na nejbližší obsahující integrální typ.</span><span class="sxs-lookup"><span data-stu-id="c94a8-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="c94a8-111">Další informace naleznete v části [Numerické propagační akce](~/_csharplang/spec/expressions.md#numeric-promotions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c94a8-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="c94a8-112">V `&` `|`, `^` a operátory jsou také definovány pro operandy `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="c94a8-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="c94a8-113">Další informace naleznete v [tématu Logické operátory logické .](boolean-logical-operators.md)</span><span class="sxs-lookup"><span data-stu-id="c94a8-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="c94a8-114">Bitové operace a operace posunu nikdy nezpůsobí přetečení a v [kontrolovaných a nekontrolovaných](../keywords/checked-and-unchecked.md) kontextech vytvoří stejné výsledky.</span><span class="sxs-lookup"><span data-stu-id="c94a8-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="c94a8-115">Bitový operátor komplementu ~</span><span class="sxs-lookup"><span data-stu-id="c94a8-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="c94a8-116">Operátor `~` vytváří bitový doplněk svého operandu obrácením každého bitu:</span><span class="sxs-lookup"><span data-stu-id="c94a8-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="c94a8-117">`~` Symbol můžete také použít k deklarování finalizačních metod.</span><span class="sxs-lookup"><span data-stu-id="c94a8-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="c94a8-118">Další informace naleznete v tématu [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="c94a8-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="c94a8-119">Operátor posunu doleva\<\<</span><span class="sxs-lookup"><span data-stu-id="c94a8-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="c94a8-120">Operátor `<<` posune svůj levý operand doleva podle [počtu bitů definovaných jeho pravostranný operand](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="c94a8-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="c94a8-121">Operace po sazí po levém posunu zahodí bity vyššího řádu, které jsou mimo rozsah typu výsledek, a nastaví prázdné bitové pozice nízkého řádu na nulu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c94a8-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="c94a8-122">Vzhledem k tomu, že `int` `uint`operátory směny jsou definovány pouze pro , , `long`a `ulong` typy, výsledek operace vždy obsahuje alespoň 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="c94a8-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="c94a8-123">Pokud je levostranný operand jiného `byte` `short`integrálního typu (`sbyte`, `int` , , `ushort`, nebo `char`), jeho hodnota je převedena na typ, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c94a8-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="c94a8-124">Informace o tom, jak pravostranný `<<` operand operátordefinuje počet směn, naleznete v části [Počet směn operátorů směny.](#shift-count-of-the-shift-operators)</span><span class="sxs-lookup"><span data-stu-id="c94a8-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="c94a8-125"> >> operátora s pravou směnou</span><span class="sxs-lookup"><span data-stu-id="c94a8-125">Right-shift operator >></span></span>

<span data-ttu-id="c94a8-126">Obsluha `>>` posune svůj levý operand doprava o [počet bitů definovaný jeho pravostranný operand](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="c94a8-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="c94a8-127">Operace pravého posunu zahodí bity nižšího řádu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c94a8-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="c94a8-128">Pozice prázdných bitů vyššího řádu jsou nastaveny na základě typu levého operandu takto:</span><span class="sxs-lookup"><span data-stu-id="c94a8-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="c94a8-129">Pokud je levá operand `int` typu `long`nebo , operátor pravého posunu provede *aritmetický* posun: hodnota nejvýznamnějšího bitu (znaménkový bit) levého operandu je rozšířena do prázdných bitových pozic vyššího řádu.</span><span class="sxs-lookup"><span data-stu-id="c94a8-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="c94a8-130">To znamená, že pozice prázdného bitu vyššího řádu jsou nastaveny na nulu, pokud je levá operand nezáporná a nastavena na hodnotu jedna, pokud je záporná.</span><span class="sxs-lookup"><span data-stu-id="c94a8-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="c94a8-131">Pokud je levostranný operand typu `uint` nebo `ulong`, operátor pravého posunu provede *logický* posun: pozice prázdných bitů vyššího řádu jsou vždy nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="c94a8-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="c94a8-132">Informace o tom, jak pravostranný `>>` operand operátordefinuje počet směn, naleznete v části [Počet směn operátorů směny.](#shift-count-of-the-shift-operators)</span><span class="sxs-lookup"><span data-stu-id="c94a8-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="c94a8-133">Logický operátor AND&amp;</span><span class="sxs-lookup"><span data-stu-id="c94a8-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="c94a8-134">Operátor `&` vypočítá bitové logické and jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="c94a8-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="c94a8-135">Pro `bool` operandy `&` operátor vypočítá [logické AND](boolean-logical-operators.md#logical-and-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="c94a8-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="c94a8-136">Unární `&` operátor je [operátor adresy](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="c94a8-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="c94a8-137">Logický výhradní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="c94a8-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="c94a8-138">Operátor `^` vypočítá bitové logické výhradní OR, také známý jako bitové logické XOR, jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="c94a8-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="c94a8-139">Pro `bool` operandy `^` operátor vypočítá [logické výhradní OR](boolean-logical-operators.md#logical-exclusive-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="c94a8-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="c94a8-140">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="c94a8-140">Logical OR operator |</span></span>

<span data-ttu-id="c94a8-141">Operátor `|` vypočítá bitové logické OR jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="c94a8-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="c94a8-142">Pro `bool` operandy `|` operátor vypočítá [logické NEBO](boolean-logical-operators.md#logical-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="c94a8-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="c94a8-143">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="c94a8-143">Compound assignment</span></span>

<span data-ttu-id="c94a8-144">Pro binární `op`operátor , složený výraz přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="c94a8-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="c94a8-145">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="c94a8-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="c94a8-146">kromě `x` toho, že se vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c94a8-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="c94a8-147">Následující příklad ukazuje použití složené přiřazení s bitové a shift operátory:</span><span class="sxs-lookup"><span data-stu-id="c94a8-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="c94a8-148">Z důvodu [číselných propagačních](~/_csharplang/spec/expressions.md#numeric-promotions) `op` akcí nemusí být výsledek operace `T` implicitně převoditelný na typ . `x`</span><span class="sxs-lookup"><span data-stu-id="c94a8-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="c94a8-149">V takovém případě, `op` pokud je předdefinovaný operátor a výsledek operace je `T` `x`explicitně převoditelný na `x op= y` typ `x = (T)(x op y)`, složený `x` výraz přiřazení formuláře je ekvivalentní , s výjimkou, že je vyhodnocenpouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c94a8-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="c94a8-150">Následující příklad ukazuje, že chování:</span><span class="sxs-lookup"><span data-stu-id="c94a8-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="c94a8-151">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="c94a8-151">Operator precedence</span></span>

<span data-ttu-id="c94a8-152">Následující seznam objednává bitové a operátory směny od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="c94a8-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="c94a8-153">Bitový operátor komplementu`~`</span><span class="sxs-lookup"><span data-stu-id="c94a8-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="c94a8-154">Operátory `<<` směn a`>>`</span><span class="sxs-lookup"><span data-stu-id="c94a8-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="c94a8-155">Logický operátor AND`&`</span><span class="sxs-lookup"><span data-stu-id="c94a8-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="c94a8-156">Logický výhradní operátor OR`^`</span><span class="sxs-lookup"><span data-stu-id="c94a8-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="c94a8-157">Logický operátor OR`|`</span><span class="sxs-lookup"><span data-stu-id="c94a8-157">Logical OR operator `|`</span></span>

<span data-ttu-id="c94a8-158">Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru:</span><span class="sxs-lookup"><span data-stu-id="c94a8-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="c94a8-159">Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="c94a8-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="c94a8-160">Počet směn operátorů směn</span><span class="sxs-lookup"><span data-stu-id="c94a8-160">Shift count of the shift operators</span></span>

<span data-ttu-id="c94a8-161">Pro operátory `<<` `>>`směny a , typ pravéoperand `int` musí být nebo typ, který `int`má [předdefinovaný implicitní číselný převod](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) na .</span><span class="sxs-lookup"><span data-stu-id="c94a8-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="c94a8-162">`x << count` Pro `x >> count` a výrazy skutečný počet směn závisí `x` na typu následujícím:</span><span class="sxs-lookup"><span data-stu-id="c94a8-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="c94a8-163">Pokud `x` je typ `int` `uint`nebo , počet směn je definován low-order *pět* bitů pravé operand.</span><span class="sxs-lookup"><span data-stu-id="c94a8-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="c94a8-164">To znamená, že počet směn `count & 0x1F` se `count & 0b_1_1111`vypočítá z (nebo).</span><span class="sxs-lookup"><span data-stu-id="c94a8-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="c94a8-165">Pokud `x` je typ `long` `ulong`nebo , počet směn je definován low-order *šest* bitů pravé operand.</span><span class="sxs-lookup"><span data-stu-id="c94a8-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="c94a8-166">To znamená, že počet směn `count & 0x3F` se `count & 0b_11_1111`vypočítá z (nebo).</span><span class="sxs-lookup"><span data-stu-id="c94a8-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="c94a8-167">Následující příklad ukazuje, že chování:</span><span class="sxs-lookup"><span data-stu-id="c94a8-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="c94a8-168">Jak ukazuje předchozí příklad, výsledek operace posunu může být nenulový i v případě, že hodnota pravostranného operandu je větší než počet bitů v levém operandu.</span><span class="sxs-lookup"><span data-stu-id="c94a8-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="c94a8-169">Logické operátory výčtu</span><span class="sxs-lookup"><span data-stu-id="c94a8-169">Enumeration logical operators</span></span>

<span data-ttu-id="c94a8-170">Všechny `~` `&`typy `|`výčtů jsou podporovány také libovolným typem `^` [výčtu](../builtin-types/enum.md) , , a operátory.</span><span class="sxs-lookup"><span data-stu-id="c94a8-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="c94a8-171">Pro operandy stejného typu výčtu se provádí logická operace na odpovídající hodnoty základního integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="c94a8-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="c94a8-172">Například pro `x` všechny `y` a typu `T` výčtu s `U`podkladovým typem `x & y` výraz vytváří `(T)((U)x & (U)y)` stejný výsledek jako výraz.</span><span class="sxs-lookup"><span data-stu-id="c94a8-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="c94a8-173">Obvykle používáte bitové logické operátory s typem výčtu, který je definován atributem [Flags.](xref:System.FlagsAttribute)</span><span class="sxs-lookup"><span data-stu-id="c94a8-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="c94a8-174">Další informace naleznete v části [Výčet jako bitové příznaky](../builtin-types/enum.md#enumeration-types-as-bit-flags) v článku [Typy výčtu.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="c94a8-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c94a8-175">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="c94a8-175">Operator overloadability</span></span>

<span data-ttu-id="c94a8-176">Uživatelem definovaný typ může `~` `<<` [přetížit](operator-overloading.md) operátory , , `>>` `&`, `|`, a. `^`</span><span class="sxs-lookup"><span data-stu-id="c94a8-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="c94a8-177">Když je přetížený binární operátor, odpovídající složený operátor přiřazení je také implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="c94a8-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="c94a8-178">Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c94a8-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="c94a8-179">Pokud uživatelem definovaný `T` typ `<<` přetíží operátor nebo, `>>` musí být `T` typ levého operandu a typ `int`pravostranného operandu .</span><span class="sxs-lookup"><span data-stu-id="c94a8-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c94a8-180">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c94a8-180">C# language specification</span></span>

<span data-ttu-id="c94a8-181">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="c94a8-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c94a8-182">Bitový operátor komplementu</span><span class="sxs-lookup"><span data-stu-id="c94a8-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="c94a8-183">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="c94a8-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="c94a8-184">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="c94a8-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="c94a8-185">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="c94a8-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="c94a8-186">Číselné propagační akce</span><span class="sxs-lookup"><span data-stu-id="c94a8-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="c94a8-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="c94a8-187">See also</span></span>

- [<span data-ttu-id="c94a8-188">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="c94a8-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c94a8-189">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c94a8-189">C# operators</span></span>](index.md)
- [<span data-ttu-id="c94a8-190">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="c94a8-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
