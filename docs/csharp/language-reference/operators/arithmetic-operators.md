---
title: Aritmetické operátory – reference jazyka C#
description: Přečtěte si o operátorech jazyka C#, které provádějí operace násobení, dělení, zbytku, sčítání a odčítání s číselnými typy.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
- '%=_CSharpKeyword'
- '*=_CSharpKeyword'
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 4ddd71e41ff70d4287f474cc91255a5aae51b132
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855241"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="01142-103">Aritmetické operátory (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="01142-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="01142-104">Následující operátory provádějí aritmetické operace s operandy číselných typů:</span><span class="sxs-lookup"><span data-stu-id="01142-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="01142-105">Unární [ `++` (přírůstek)](#increment-operator-), [ `--` (snížená)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)a [ `-` (mínus)](#unary-plus-and-minus-operators) operátory</span><span class="sxs-lookup"><span data-stu-id="01142-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="01142-106">Binary [ `*` (násobení)](#multiplication-operator-), [ `/` (dělení)](#division-operator-), [ `%` (zbytek](#remainder-operator-)), [ `+` (sčítání](#addition-operator-)) a [ `-` (odčítání)](#subtraction-operator--) operátorů</span><span class="sxs-lookup"><span data-stu-id="01142-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="01142-107">Tyto operátory jsou podporovány všemi [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou.</span><span class="sxs-lookup"><span data-stu-id="01142-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

<span data-ttu-id="01142-108">V případě integrálních typů jsou operátory (s výjimkou `++` `--` operátorů a) definovány pro `int` `uint` typy,, `long` a `ulong` .</span><span class="sxs-lookup"><span data-stu-id="01142-108">In the case of integral types, those operators (except the `++` and `--` operators) are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="01142-109">Pokud jsou operandy jiných integrálních typů ( `sbyte` , `byte` , `short` , `ushort` , nebo `char` ), jejich hodnoty jsou převedeny na `int` typ, což je také výsledný typ operace.</span><span class="sxs-lookup"><span data-stu-id="01142-109">When operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="01142-110">Pokud jsou operandy různých typů integrálního nebo plovoucího bodu, jejich hodnoty jsou převedeny na nejbližší nadřazený typ, pokud takový typ existuje.</span><span class="sxs-lookup"><span data-stu-id="01142-110">When operands are of different integral or floating-point types, their values are converted to the closest containing type, if such a type exists.</span></span> <span data-ttu-id="01142-111">Další informace naleznete v části [numerické propagace](~/_csharplang/spec/expressions.md#numeric-promotions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="01142-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="01142-112">`++`Operátory a `--` jsou definovány pro všechny číselné typy integrálních a plovoucí desetinné čárky a typ [znaku](../builtin-types/char.md) .</span><span class="sxs-lookup"><span data-stu-id="01142-112">The `++` and `--` operators are defined for all integral and floating-point numeric types and the [char](../builtin-types/char.md) type.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="01142-113">Operátor přírůstku + +</span><span class="sxs-lookup"><span data-stu-id="01142-113">Increment operator ++</span></span>

<span data-ttu-id="01142-114">Operátor unárního přírůstku `++` zvyšuje svůj operand o 1.</span><span class="sxs-lookup"><span data-stu-id="01142-114">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="01142-115">Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="01142-115">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="01142-116">Operátor přírůstku je podporován ve dvou formách: operátor přírůstku přípony, `x++` a operátor přírůstku předpony, `++x` .</span><span class="sxs-lookup"><span data-stu-id="01142-116">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="01142-117">Příponový operátor inkrementace</span><span class="sxs-lookup"><span data-stu-id="01142-117">Postfix increment operator</span></span>

<span data-ttu-id="01142-118">Výsledek `x++` je hodnota `x` *před* operací, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="01142-118">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="01142-119">Operátor přírůstku předpony</span><span class="sxs-lookup"><span data-stu-id="01142-119">Prefix increment operator</span></span>

<span data-ttu-id="01142-120">Výsledek `++x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="01142-120">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="01142-121">Operátor snížení--</span><span class="sxs-lookup"><span data-stu-id="01142-121">Decrement operator --</span></span>

<span data-ttu-id="01142-122">Operátor unárního snížení `--` snižuje svůj operand o 1.</span><span class="sxs-lookup"><span data-stu-id="01142-122">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="01142-123">Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="01142-123">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="01142-124">Operátor snížení je podporován ve dvou formách: operátor snížení přípony, `x--` a operátor snížení předpony `--x` .</span><span class="sxs-lookup"><span data-stu-id="01142-124">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="01142-125">Příponový operátor dekrementace</span><span class="sxs-lookup"><span data-stu-id="01142-125">Postfix decrement operator</span></span>

<span data-ttu-id="01142-126">Výsledek `x--` je hodnota `x` *před* operací, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="01142-126">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="01142-127">Operátor snížení předpony</span><span class="sxs-lookup"><span data-stu-id="01142-127">Prefix decrement operator</span></span>

<span data-ttu-id="01142-128">Výsledek `--x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="01142-128">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="01142-129">Unární operátory plus a mínus</span><span class="sxs-lookup"><span data-stu-id="01142-129">Unary plus and minus operators</span></span>

<span data-ttu-id="01142-130">Unární `+` operátor vrátí hodnotu jeho operandu.</span><span class="sxs-lookup"><span data-stu-id="01142-130">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="01142-131">Unární `-` operátor vypočítá číselnou negaci svého operandu.</span><span class="sxs-lookup"><span data-stu-id="01142-131">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="01142-132">Typ [ulong](../builtin-types/integral-numeric-types.md) nepodporuje unární `-` operátor.</span><span class="sxs-lookup"><span data-stu-id="01142-132">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="01142-133">Operátor násobení \*</span><span class="sxs-lookup"><span data-stu-id="01142-133">Multiplication operator \*</span></span>

<span data-ttu-id="01142-134">Operátor násobení `*` Vypočítá součin jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="01142-134">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="01142-135">Unární `*` operátor je [operátor dereference ukazatele](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="01142-135">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="01142-136">Operátor dělení/</span><span class="sxs-lookup"><span data-stu-id="01142-136">Division operator /</span></span>

<span data-ttu-id="01142-137">Operátor dělení `/` rozdělí svůj operand na levou stranu operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="01142-137">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="01142-138">Dělení celého čísla</span><span class="sxs-lookup"><span data-stu-id="01142-138">Integer division</span></span>

<span data-ttu-id="01142-139">U operandů typu Integer `/` je výsledkem operátoru typ Integer a rovná se podíl dvou operandů zaokrouhlených směrem k nule:</span><span class="sxs-lookup"><span data-stu-id="01142-139">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="01142-140">Chcete-li získat podíl dvou operandů jako číslo s plovoucí desetinnou čárkou, použijte operátor `float` , `double` nebo `decimal` :</span><span class="sxs-lookup"><span data-stu-id="01142-140">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="01142-141">Dělení plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="01142-141">Floating-point division</span></span>

<span data-ttu-id="01142-142">Pro `float` typy, `double` a `decimal` `/` je výsledkem operátoru podíl dvou operandů:</span><span class="sxs-lookup"><span data-stu-id="01142-142">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="01142-143">Pokud je jeden z operandů `decimal` , jiný operand nemůže být `float` ani `double` , protože ani `float` `double` není implicitně převoditelné na `decimal` .</span><span class="sxs-lookup"><span data-stu-id="01142-143">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="01142-144">Je nutné explicitně převést `float` operand nebo na `double` `decimal` typ.</span><span class="sxs-lookup"><span data-stu-id="01142-144">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="01142-145">Další informace o převodech mezi číselnými typy naleznete v tématu [vestavěné číselné převody](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="01142-145">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="01142-146">Operátor zbývajícího%</span><span class="sxs-lookup"><span data-stu-id="01142-146">Remainder operator %</span></span>

<span data-ttu-id="01142-147">Operátor zbytek `%` vypočítá zbytek po dělení jeho levého operandu pomocí jeho pravého operandu.</span><span class="sxs-lookup"><span data-stu-id="01142-147">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="01142-148">Celočíselný zbytek</span><span class="sxs-lookup"><span data-stu-id="01142-148">Integer remainder</span></span>

<span data-ttu-id="01142-149">U operandů typu Integer `a % b` je výsledkem hodnota hodnotu vytvořenou hodnotou `a - (a / b) * b` .</span><span class="sxs-lookup"><span data-stu-id="01142-149">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="01142-150">Znaménko nenulového zbytku je stejné jako u levého operandu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="01142-150">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="01142-151">Použijte <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metodu pro výpočet celočíselného dělení i zbývajících výsledků.</span><span class="sxs-lookup"><span data-stu-id="01142-151">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="01142-152">Zbytek s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="01142-152">Floating-point remainder</span></span>

<span data-ttu-id="01142-153">Pro `float` `double` operandy a `x % y` je výsledkem pro konečnou `x` `y` hodnotu a hodnota `z` , například</span><span class="sxs-lookup"><span data-stu-id="01142-153">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="01142-154">Znaménko `z` , pokud není nula, je stejné jako znaménko `x` .</span><span class="sxs-lookup"><span data-stu-id="01142-154">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="01142-155">Absolutní hodnota `z` je hodnota vytvořená v `|x| - n * |y|` místě, kde `n` je největší možné celé číslo, které je menší než nebo rovno `|x| / |y|` a `|x|` a `|y|` jsou absolutními hodnotami `x` a v `y` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="01142-155">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="01142-156">Tato metoda výpočtu zbytku je podobná, jako by se použila pro celočíselné operandy, ale liší se od specifikace IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="01142-156">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="01142-157">Pokud potřebujete zbývající operaci, která je v souladu se specifikací IEEE 754, použijte <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="01142-157">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="01142-158">Informace o chování `%` operátoru s nekonečnými operandy naleznete v části [operátor zbylé](~/_csharplang/spec/expressions.md#remainder-operator) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="01142-158">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="01142-159">U `decimal` operandů je operátor zbytku `%` ekvivalentní k [operátoru zbývajícího](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="01142-159">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="01142-160">Následující příklad ukazuje chování operátoru zbytek s operandy s plovoucí desetinnou čárkou:</span><span class="sxs-lookup"><span data-stu-id="01142-160">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="01142-161">Operátor sčítání +</span><span class="sxs-lookup"><span data-stu-id="01142-161">Addition operator +</span></span>

<span data-ttu-id="01142-162">Operátor sčítání `+` vypočítá součet jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="01142-162">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="01142-163">Můžete také použít `+` operátor pro kombinaci řetězení řetězců a delegátů.</span><span class="sxs-lookup"><span data-stu-id="01142-163">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="01142-164">Další informace naleznete v článku [ `+` `+=` operátory a](addition-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="01142-164">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="01142-165">Operátor odčítání –</span><span class="sxs-lookup"><span data-stu-id="01142-165">Subtraction operator -</span></span>

<span data-ttu-id="01142-166">Operátor odčítání `-` odečte svůj pravý operand od jeho levého operandu:</span><span class="sxs-lookup"><span data-stu-id="01142-166">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="01142-167">`-`K odebrání delegáta můžete také použít operátora.</span><span class="sxs-lookup"><span data-stu-id="01142-167">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="01142-168">Další informace naleznete v článku [ `-` `-=` operátory a](subtraction-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="01142-168">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="01142-169">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="01142-169">Compound assignment</span></span>

<span data-ttu-id="01142-170">Pro binární operátor `op` , výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="01142-170">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="01142-171">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="01142-171">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="01142-172">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="01142-172">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="01142-173">Následující příklad ukazuje použití složeného přiřazení s aritmetickými operátory:</span><span class="sxs-lookup"><span data-stu-id="01142-173">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="01142-174">Z důvodu [numerických propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions) `op` nemusí být výsledek operace implicitně převoditelný na typ `T` `x` .</span><span class="sxs-lookup"><span data-stu-id="01142-174">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="01142-175">V takovém případě, pokud `op` je předdefinovaný operátor a výsledek operace je explicitně převoditelné na typ `T` `x` , je složený výraz přiřazení formuláře `x op= y` ekvivalentní s `x = (T)(x op y)` tím rozdílem, že `x` je pouze vyhodnocen pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="01142-175">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="01142-176">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="01142-176">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="01142-177">Pomocí `+=` operátorů a můžete také `-=` Přihlásit odběr a zrušit odběr [události](../keywords/event.md)v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="01142-177">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="01142-178">Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.</span><span class="sxs-lookup"><span data-stu-id="01142-178">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="01142-179">Priorita operátorů a asociativita</span><span class="sxs-lookup"><span data-stu-id="01142-179">Operator precedence and associativity</span></span>

<span data-ttu-id="01142-180">Následující seznam řadí aritmetické operátory počínaje od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="01142-180">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="01142-181">Operátory přírůstku `x++` a snížení přípony `x--`</span><span class="sxs-lookup"><span data-stu-id="01142-181">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="01142-182">Zvýšení a snížení prefixu a `++x` `--x` unární `+` `-` operátory a</span><span class="sxs-lookup"><span data-stu-id="01142-182">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="01142-183">Multiplikativní `*` `/` operátory, a `%`</span><span class="sxs-lookup"><span data-stu-id="01142-183">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="01142-184">Doplňková `+` a `-` operátor</span><span class="sxs-lookup"><span data-stu-id="01142-184">Additive `+` and `-` operators</span></span>

<span data-ttu-id="01142-185">Binární aritmetické operátory jsou asociativní zleva.</span><span class="sxs-lookup"><span data-stu-id="01142-185">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="01142-186">To znamená, že operátory se stejnou úrovní priority jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="01142-186">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="01142-187">Pomocí závorek `()` můžete změnit pořadí vyhodnocování stanovené prioritou operátoru a asociativita.</span><span class="sxs-lookup"><span data-stu-id="01142-187">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="01142-188">Úplný seznam operátorů jazyka C# seřazených podle priority úrovně naleznete v části [Priorita operátorů](index.md#operator-precedence) v článku [operátory jazyka c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="01142-188">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="01142-189">Aritmetické přetečení a dělení nulou</span><span class="sxs-lookup"><span data-stu-id="01142-189">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="01142-190">Pokud je výsledek aritmetické operace mimo rozsah možných konečných hodnot typu, který je součástí daného číselného typu, chování aritmetického operátoru závisí na typu jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="01142-190">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="01142-191">Aritmetické přetečení typu Integer</span><span class="sxs-lookup"><span data-stu-id="01142-191">Integer arithmetic overflow</span></span>

<span data-ttu-id="01142-192">Dělení celého čísla nulou vždy vyvolá <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="01142-192">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="01142-193">V případě celočíselného přetečení aritmetického přetečení, které může být [zaškrtnuto nebo nezaškrtnuto](../keywords/checked-and-unchecked.md), ovládací prvky výsledného chování:</span><span class="sxs-lookup"><span data-stu-id="01142-193">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="01142-194">V kontrolovaném kontextu dojde k chybě při kompilaci, pokud dojde k přetečení v konstantním výrazu.</span><span class="sxs-lookup"><span data-stu-id="01142-194">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="01142-195">V opačném případě, je-li operace provedena v době běhu, <xref:System.OverflowException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="01142-195">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="01142-196">V nekontrolovaném kontextu se výsledek zkrátí tak, že zahodí jakékoli bity s vysokým pořadím, které se nevejdou do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="01142-196">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="01142-197">Spolu s [zaškrtnutými a nekontrolovanými](../keywords/checked-and-unchecked.md) příkazy lze pomocí `checked` `unchecked` operátorů a řídit kontext kontroly přetečení, ve kterém je výraz vyhodnocen:</span><span class="sxs-lookup"><span data-stu-id="01142-197">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="01142-198">Ve výchozím nastavení se aritmetické operace vyskytují v nekontrolovaném *kontextu.*</span><span class="sxs-lookup"><span data-stu-id="01142-198">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="01142-199">Aritmetické přetečení s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="01142-199">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="01142-200">Aritmetické operace s `float` `double` typy a nikdy nevyvolávají výjimku.</span><span class="sxs-lookup"><span data-stu-id="01142-200">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="01142-201">Výsledkem aritmetických operací s těmito typy může být jedna z speciálních hodnot, které reprezentují nekonečno a nikoli-a-číslo:</span><span class="sxs-lookup"><span data-stu-id="01142-201">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="01142-202">U operandů `decimal` typu aritmetické přetečení vždy vyvolá výjimku <xref:System.OverflowException> a dělení nulou vždy vyvolá <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="01142-202">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="01142-203">Chyby zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="01142-203">Round-off errors</span></span>

<span data-ttu-id="01142-204">Z důvodu obecného omezení reprezentace reálných čísel s plovoucí desetinnou čárkou a aritmetických operací s plovoucí desetinnou čárkou mohou být při výpočtech s typy s plovoucí desetinnou čárkou zjištěny chyby zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="01142-204">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="01142-205">To znamená, že získaný výsledek výrazu se může lišit od očekávaného matematického výsledku.</span><span class="sxs-lookup"><span data-stu-id="01142-205">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="01142-206">Následující příklad ukazuje několik takových případů:</span><span class="sxs-lookup"><span data-stu-id="01142-206">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="01142-207">Další informace najdete v tématu poznámky na referenčních stránkách [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)nebo [System. Decimal](/dotnet/api/system.decimal#remarks) .</span><span class="sxs-lookup"><span data-stu-id="01142-207">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="01142-208">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="01142-208">Operator overloadability</span></span>

<span data-ttu-id="01142-209">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) unární `++` `--` `+` aritmetické operátory (,,, a `-` ) a binární ( `*` ,,,, `/` `%` `+` a `-` ).</span><span class="sxs-lookup"><span data-stu-id="01142-209">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="01142-210">Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="01142-210">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="01142-211">Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="01142-211">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="01142-212">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01142-212">C# language specification</span></span>

<span data-ttu-id="01142-213">Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="01142-213">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="01142-214">Operátory přírůstku a snížení přípony</span><span class="sxs-lookup"><span data-stu-id="01142-214">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="01142-215">Operátory inkrementace a dekrementace předpony</span><span class="sxs-lookup"><span data-stu-id="01142-215">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="01142-216">Unární operátor plus</span><span class="sxs-lookup"><span data-stu-id="01142-216">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="01142-217">Operátor unární minus</span><span class="sxs-lookup"><span data-stu-id="01142-217">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="01142-218">Operátor násobení</span><span class="sxs-lookup"><span data-stu-id="01142-218">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="01142-219">Operátor dělení</span><span class="sxs-lookup"><span data-stu-id="01142-219">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="01142-220">Operátor zbývající</span><span class="sxs-lookup"><span data-stu-id="01142-220">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="01142-221">Operátor sčítání</span><span class="sxs-lookup"><span data-stu-id="01142-221">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="01142-222">Operátor odčítání</span><span class="sxs-lookup"><span data-stu-id="01142-222">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="01142-223">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="01142-223">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="01142-224">Kontrolované a nezaškrtnuté operátory</span><span class="sxs-lookup"><span data-stu-id="01142-224">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="01142-225">Číselné propagační akce</span><span class="sxs-lookup"><span data-stu-id="01142-225">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="01142-226">Viz také</span><span class="sxs-lookup"><span data-stu-id="01142-226">See also</span></span>

- [<span data-ttu-id="01142-227">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="01142-227">C# reference</span></span>](../index.md)
- [<span data-ttu-id="01142-228">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="01142-228">C# operators and expressions</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="01142-229">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="01142-229">Numerics in .NET</span></span>](../../../standard/numerics.md)
