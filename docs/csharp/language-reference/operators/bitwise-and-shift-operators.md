---
title: Bitové operátory and Shift – C# referenční informace
description: Přečtěte C# si o operátorech, které provádějí bitové logické nebo posunuté operace s operandy integrálních typů.
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
ms.openlocfilehash: a6319cbbbe8a691f5d2a01a13a5abfa2550b3705
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239518"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="098bf-103">Operátory bitových a posunutí (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="098bf-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="098bf-104">Následující operátory provádějí operace bitového nebo posunutí s operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) nebo typu [znaku](../builtin-types/char.md) :</span><span class="sxs-lookup"><span data-stu-id="098bf-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="098bf-105">Unární operátor [`~` (bitový doplněk)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="098bf-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="098bf-106">Binární [`<<` (levý SHIFT)](#left-shift-operator-) a [`>>` (posunutí doprava)](#right-shift-operator-) – operátory posunu</span><span class="sxs-lookup"><span data-stu-id="098bf-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="098bf-107">Binární [`&` (Logical and)](#logical-and-operator-), [`|` (Logical or)](#logical-or-operator-)a [`^` (Logical or)](#logical-exclusive-or-operator-) Operators</span><span class="sxs-lookup"><span data-stu-id="098bf-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="098bf-108">Tyto operátory jsou definovány pro typy `int`, `uint`, `long`a `ulong`.</span><span class="sxs-lookup"><span data-stu-id="098bf-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="098bf-109">Pokud jsou oba operandy jiných integrálních typů (`sbyte`, `byte`, `short`, `ushort`nebo `char`), jejich hodnoty jsou převedeny na typ `int`, což je také výsledný typ operace.</span><span class="sxs-lookup"><span data-stu-id="098bf-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="098bf-110">Pokud jsou operandy různých integrálních typů, jejich hodnoty jsou převedeny na nejbližší obsahující celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="098bf-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="098bf-111">Další informace naleznete v části [Číselná propagace](~/_csharplang/spec/expressions.md#numeric-promotions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="098bf-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="098bf-112">Operátory `&`, `|`a `^` jsou definovány také pro operandy `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="098bf-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="098bf-113">Další informace naleznete v tématu logické [logické operátory](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="098bf-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="098bf-114">Operace bitového a posunutí nikdy nezpůsobí přetečení a vytvářejí stejné výsledky v [zaškrtnutých a nekontrolovaných](../keywords/checked-and-unchecked.md) kontextech.</span><span class="sxs-lookup"><span data-stu-id="098bf-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="098bf-115">Operátor bitového doplňku ~</span><span class="sxs-lookup"><span data-stu-id="098bf-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="098bf-116">Operátor `~` vytvoří bitový doplněk svého operandu převrácením každého bitu:</span><span class="sxs-lookup"><span data-stu-id="098bf-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="098bf-117">K deklaraci finalizační metody můžete použít také symbol `~`.</span><span class="sxs-lookup"><span data-stu-id="098bf-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="098bf-118">Další informace naleznete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="098bf-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="098bf-119">Operátor posunutí doleva \<\<</span><span class="sxs-lookup"><span data-stu-id="098bf-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="098bf-120">Operátor `<<` posune levý operand vlevo o [počet bitů definovaných operandem na pravé straně](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="098bf-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="098bf-121">Operace Left posunutí zahodí horních bitů, které jsou mimo rozsah výsledného typu, a nastavuje prázdné bitové pozice v dolním pořadí na nulu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="098bf-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="098bf-122">Protože operátory posunutí jsou definovány pouze pro `int`, `uint`, `long`a `ulong` typy, výsledek operace vždy obsahuje alespoň 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="098bf-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="098bf-123">Pokud je levý operand jiného integrálního typu (`sbyte`, `byte`, `short`, `ushort`nebo `char`), jeho hodnota je převedena na typ `int`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="098bf-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="098bf-124">Informace o tom, jak operand pravého operátoru `<<` definuje počet posunutí, naleznete v části [posunutí operátorů Shift](#shift-count-of-the-shift-operators) .</span><span class="sxs-lookup"><span data-stu-id="098bf-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="098bf-125">Operátor pravého posunutí > ></span><span class="sxs-lookup"><span data-stu-id="098bf-125">Right-shift operator >></span></span>

<span data-ttu-id="098bf-126">Operátor `>>` posune levý operand vpravo o [počet bitů definovaných operandem na pravé straně](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="098bf-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="098bf-127">Operace pravého posunutí zahodí bity nízkého řádu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="098bf-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="098bf-128">Horní pořadí prázdných bitových pozic je nastaveno na základě typu levého operandu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="098bf-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="098bf-129">Pokud je levý operand typu `int` nebo `long`, operátor pravého posunutí provede *aritmetický* posun: hodnota nejvýznamnějšího bitu (bit znaménka) levého operandu je rozšířena na horní pořadí prázdných bitových pozic.</span><span class="sxs-lookup"><span data-stu-id="098bf-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="098bf-130">To znamená, že horní pozice prázdných pozic je nastavena na hodnotu nula, je-li operand na levé straně nezáporný a je-li záporná, nastavte na jeden.</span><span class="sxs-lookup"><span data-stu-id="098bf-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="098bf-131">Pokud je levý operand typu `uint` nebo `ulong`, provede operátor pravého posunutí *logický* posun: vysoké prázdné bitové pozice jsou vždy nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="098bf-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="098bf-132">Informace o tom, jak operand pravého operátoru `>>` definuje počet posunutí, naleznete v části [posunutí operátorů Shift](#shift-count-of-the-shift-operators) .</span><span class="sxs-lookup"><span data-stu-id="098bf-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="098bf-133">Logický operátor AND &amp;</span><span class="sxs-lookup"><span data-stu-id="098bf-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="098bf-134">Operátor `&` vypočítá bitovou logickou a jeho operandy:</span><span class="sxs-lookup"><span data-stu-id="098bf-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="098bf-135">Pro `bool` operandy vypočítá operátor `&` [logickou a](boolean-logical-operators.md#logical-and-operator-) jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="098bf-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="098bf-136">Unární operátor `&` je [operátor address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="098bf-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="098bf-137">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="098bf-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="098bf-138">Operátor `^` Vypočítá bitový logický operátor exclusive OR, také označovaný jako bitový logický operátor XOR, z jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="098bf-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="098bf-139">Pro `bool` operandy vypočítá operátor `^` [logickou výhradní nebo](boolean-logical-operators.md#logical-exclusive-or-operator-) jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="098bf-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="098bf-140">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="098bf-140">Logical OR operator |</span></span>

<span data-ttu-id="098bf-141">Operátor `|` vypočítá bitovou logickou nebo jeho operandy:</span><span class="sxs-lookup"><span data-stu-id="098bf-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="098bf-142">Pro `bool` operandy vypočítá operátor `|` [logickou nebo](boolean-logical-operators.md#logical-or-operator-) jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="098bf-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="098bf-143">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="098bf-143">Compound assignment</span></span>

<span data-ttu-id="098bf-144">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="098bf-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="098bf-145">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="098bf-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="098bf-146">s výjimkou `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="098bf-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="098bf-147">Následující příklad ukazuje použití složeného přiřazení s bitovým operátorem and Shift:</span><span class="sxs-lookup"><span data-stu-id="098bf-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="098bf-148">Z důvodu [numerických propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions)nemusí být výsledek operace `op` implicitně převoditelný na typ `T` `x`.</span><span class="sxs-lookup"><span data-stu-id="098bf-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="098bf-149">V takovém případě, pokud je `op` předdefinovaným operátorem a výsledek operace je explicitně převoditelné na typ `T` `x`, výraz složeného přiřazení `x op= y` formuláře je ekvivalentní `x = (T)(x op y)`, s tím rozdílem, že `x` vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="098bf-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="098bf-150">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="098bf-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="098bf-151">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="098bf-151">Operator precedence</span></span>

<span data-ttu-id="098bf-152">Následující seznam řadí operátory bitových operátorů and Shift počínaje nejvyšší prioritou až nejnižší:</span><span class="sxs-lookup"><span data-stu-id="098bf-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="098bf-153">Operátor bitového doplňku `~`</span><span class="sxs-lookup"><span data-stu-id="098bf-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="098bf-154">Operátory posunutí `<<` a `>>`</span><span class="sxs-lookup"><span data-stu-id="098bf-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="098bf-155">Logický operátor AND `&`</span><span class="sxs-lookup"><span data-stu-id="098bf-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="098bf-156">`^` logický exkluzivní operátor OR</span><span class="sxs-lookup"><span data-stu-id="098bf-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="098bf-157">Logický operátor OR `|`</span><span class="sxs-lookup"><span data-stu-id="098bf-157">Logical OR operator `|`</span></span>

<span data-ttu-id="098bf-158">Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů, použijte závorky `()`.</span><span class="sxs-lookup"><span data-stu-id="098bf-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="098bf-159">Úplný seznam C# operátorů seřazených podle priority najdete v části [Priorita operátorů](index.md#operator-precedence) [ C# v článku věnovaném operátorům](index.md) .</span><span class="sxs-lookup"><span data-stu-id="098bf-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="098bf-160">Počet posunutí operátorů Shift</span><span class="sxs-lookup"><span data-stu-id="098bf-160">Shift count of the shift operators</span></span>

<span data-ttu-id="098bf-161">Pro operátory Shift `<<` a `>>`musí být typ operandu na pravé straně `int` nebo typ, který má [předdefinovaný implicitní číselný převod](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) na `int`.</span><span class="sxs-lookup"><span data-stu-id="098bf-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="098bf-162">Pro výrazy `x << count` a `x >> count` závisí skutečný počet posunutí na typ `x` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="098bf-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="098bf-163">Pokud je typ `x` `int` nebo `uint`, je počet posunutí definováno *pěti* bity pravého operandu.</span><span class="sxs-lookup"><span data-stu-id="098bf-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="098bf-164">To znamená, že počet posunutí je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="098bf-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="098bf-165">Pokud je typ `x` `long` nebo `ulong`, je počet posunutí definován v dolním *šesti* bitech operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="098bf-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="098bf-166">To znamená, že počet posunutí je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="098bf-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="098bf-167">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="098bf-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="098bf-168">Jak ukazuje předchozí příklad, výsledek operace posunutí může být nenulový, i když hodnota operandu na pravé straně je větší než počet bitů v operandu na levé straně.</span><span class="sxs-lookup"><span data-stu-id="098bf-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="098bf-169">Logické operátory výčtu</span><span class="sxs-lookup"><span data-stu-id="098bf-169">Enumeration logical operators</span></span>

<span data-ttu-id="098bf-170">Operátory `~`, `&`, `|`a `^` jsou podporovány také jakýmkoli [výčtovým](../builtin-types/enum.md) typem.</span><span class="sxs-lookup"><span data-stu-id="098bf-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="098bf-171">Pro operandy se stejným výčtovým typem je logická operace provedena na odpovídajících hodnotách základního integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="098bf-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="098bf-172">Například pro jakékoli `x` a `y` typu výčtu `T` s podkladovým typem `U`výraz `x & y` vytvoří stejný výsledek jako výraz `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="098bf-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="098bf-173">Obvykle používáte bitové logické operátory s výčtovým typem, který je definován pomocí atributu [Flags](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="098bf-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="098bf-174">Další informace naleznete v části [výčtové typy jako bitové příznaky](../builtin-types/enum.md#enumeration-types-as-bit-flags) v článku [výčtové typy](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="098bf-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="098bf-175">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="098bf-175">Operator overloadability</span></span>

<span data-ttu-id="098bf-176">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `~`, `<<`, `>>`, `&`, `|`a `^`.</span><span class="sxs-lookup"><span data-stu-id="098bf-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="098bf-177">Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="098bf-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="098bf-178">Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="098bf-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="098bf-179">Pokud uživatelsky definovaný typ `T` přetížení operátoru `<<` nebo `>>`, musí být typ operandu na levé straně `T` a typ operandu na pravé straně musí být `int`.</span><span class="sxs-lookup"><span data-stu-id="098bf-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="098bf-180">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="098bf-180">C# language specification</span></span>

<span data-ttu-id="098bf-181">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="098bf-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="098bf-182">Operátor bitového doplňku</span><span class="sxs-lookup"><span data-stu-id="098bf-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="098bf-183">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="098bf-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="098bf-184">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="098bf-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="098bf-185">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="098bf-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="098bf-186">Číselné propagační akce</span><span class="sxs-lookup"><span data-stu-id="098bf-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="098bf-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="098bf-187">See also</span></span>

- [<span data-ttu-id="098bf-188">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="098bf-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="098bf-189">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="098bf-189">C# operators</span></span>](index.md)
- [<span data-ttu-id="098bf-190">Logické logické operátory</span><span class="sxs-lookup"><span data-stu-id="098bf-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
