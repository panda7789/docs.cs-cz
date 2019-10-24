---
title: Aritmetické operátory C# – referenční informace
description: Přečtěte C# si o operátorech, které provádějí operace násobení, dělení, zbytku, sčítání a odčítání s číselnými typy.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
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
ms.openlocfilehash: 9760be0fcfe29d2c11cbb1f4d4d81c5a79261a0d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771737"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="02191-103">Aritmetické operátoryC# (referenční)</span><span class="sxs-lookup"><span data-stu-id="02191-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="02191-104">Následující operátory provádějí aritmetické operace s číselnými typy:</span><span class="sxs-lookup"><span data-stu-id="02191-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="02191-105">Unární operátory [`++` (přírůstek)](#increment-operator-), [`--` (snížení)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators)a [`-` (mínus)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="02191-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="02191-106">Binární [`*` (násobení)](#multiplication-operator-), [`/` (dělení)](#division-operator-), [`%` (zbytek)](#remainder-operator-), [`+` (sčítání](#addition-operator-)) a [`-`ch (odčítání)](#subtraction-operator--) operátorů</span><span class="sxs-lookup"><span data-stu-id="02191-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="02191-107">Tyto operátory podporují všechny číselné typy [integrálních](../builtin-types/integral-numeric-types.md) a [plovoucích bodů](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="02191-107">Those operators support all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="02191-108">Operátor přírůstku + +</span><span class="sxs-lookup"><span data-stu-id="02191-108">Increment operator ++</span></span>

<span data-ttu-id="02191-109">Unární operátor přírůstku `++` zvyšuje svůj operand o 1.</span><span class="sxs-lookup"><span data-stu-id="02191-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="02191-110">Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="02191-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="02191-111">Operátor přírůstku je podporován ve dvou formách: operátor přírůstku přípony, `x++` a operátor přírůstku předpony `++x`.</span><span class="sxs-lookup"><span data-stu-id="02191-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="02191-112">Příponový operátor inkrementace</span><span class="sxs-lookup"><span data-stu-id="02191-112">Postfix increment operator</span></span>

<span data-ttu-id="02191-113">Výsledek `x++` je hodnota `x` *před* operací, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="02191-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="02191-114">Operátor přírůstku předpony</span><span class="sxs-lookup"><span data-stu-id="02191-114">Prefix increment operator</span></span>

<span data-ttu-id="02191-115">Výsledek `++x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="02191-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="02191-116">Operátor snížení--</span><span class="sxs-lookup"><span data-stu-id="02191-116">Decrement operator --</span></span>

<span data-ttu-id="02191-117">Operátor unárního snížení `--` sníží svůj operand o 1.</span><span class="sxs-lookup"><span data-stu-id="02191-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="02191-118">Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="02191-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="02191-119">Operátor snížení je podporován ve dvou formulářích: operátor snížení přípony, `x--` a operátor snížení prefixu `--x`.</span><span class="sxs-lookup"><span data-stu-id="02191-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="02191-120">Příponový operátor dekrementace</span><span class="sxs-lookup"><span data-stu-id="02191-120">Postfix decrement operator</span></span>

<span data-ttu-id="02191-121">Výsledek `x--` je hodnota `x` *před* operací, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="02191-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="02191-122">Operátor snížení předpony</span><span class="sxs-lookup"><span data-stu-id="02191-122">Prefix decrement operator</span></span>

<span data-ttu-id="02191-123">Výsledek `--x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="02191-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="02191-124">Unární operátory plus a mínus</span><span class="sxs-lookup"><span data-stu-id="02191-124">Unary plus and minus operators</span></span>

<span data-ttu-id="02191-125">Unární operátor `+` vrací hodnotu jeho operandu.</span><span class="sxs-lookup"><span data-stu-id="02191-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="02191-126">Operátor unární `-` vypočítá číselnou negaci svého operandu.</span><span class="sxs-lookup"><span data-stu-id="02191-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="02191-127">Unární operátor `-` nepodporuje typ [ulong](../builtin-types/integral-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="02191-127">The unary `-` operator doesn't support the [ulong](../builtin-types/integral-numeric-types.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="02191-128">Operátor násobení \*</span><span class="sxs-lookup"><span data-stu-id="02191-128">Multiplication operator \*</span></span>

<span data-ttu-id="02191-129">Operátor násobení `*` Vypočítá součin jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="02191-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="02191-130">Unární operátor `*` je [operátor dereference ukazatele](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="02191-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="02191-131">Operátor dělení/</span><span class="sxs-lookup"><span data-stu-id="02191-131">Division operator /</span></span>

<span data-ttu-id="02191-132">Operátor dělení `/` rozdělí svůj operand na levé straně svým operandem na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="02191-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="02191-133">Dělení celého čísla</span><span class="sxs-lookup"><span data-stu-id="02191-133">Integer division</span></span>

<span data-ttu-id="02191-134">U operandů typu integer je výsledkem operátoru `/` celočíselný typ a rovná se podíl dvou operandů zaokrouhlených směrem k nule:</span><span class="sxs-lookup"><span data-stu-id="02191-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="02191-135">Chcete-li získat podíl dvou operandů jako číslo s plovoucí desetinnou čárkou, použijte `float`, `double` nebo `decimal` typ:</span><span class="sxs-lookup"><span data-stu-id="02191-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="02191-136">Dělení plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="02191-136">Floating-point division</span></span>

<span data-ttu-id="02191-137">V případě typů `float`, `double` a `decimal` je výsledkem operátoru `/` podíl dvou operandů:</span><span class="sxs-lookup"><span data-stu-id="02191-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="02191-138">Pokud je jeden z operandů `decimal`, jiný operand nemůže být `float` ani `double`, protože ani `float` ani `double` není implicitně převoditelná na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="02191-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="02191-139">Je nutné explicitně převést `float` nebo operand `double` na typ `decimal`.</span><span class="sxs-lookup"><span data-stu-id="02191-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="02191-140">Další informace o převodech mezi číselnými typy naleznete v tématu [vestavěné číselné převody](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="02191-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="02191-141">Operátor zbývajícího%</span><span class="sxs-lookup"><span data-stu-id="02191-141">Remainder operator %</span></span>

<span data-ttu-id="02191-142">Operátor zbývající `%` vypočítá zbytek po dělení jeho levého operandu jeho pravým operandem.</span><span class="sxs-lookup"><span data-stu-id="02191-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="02191-143">Celočíselný zbytek</span><span class="sxs-lookup"><span data-stu-id="02191-143">Integer remainder</span></span>
  
<span data-ttu-id="02191-144">U operandů typu integer je výsledkem `a % b` hodnota vytvořená `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="02191-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="02191-145">Znaménko nenulového zbytku je stejné jako u levého operandu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="02191-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="02191-146">Použijte metodu <xref:System.Math.DivRem%2A?displayProperty=nameWithType> k výpočtu celočíselného dělení i zbývajících výsledků.</span><span class="sxs-lookup"><span data-stu-id="02191-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="02191-147">Zbytek s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="02191-147">Floating-point remainder</span></span>

<span data-ttu-id="02191-148">U operandů `float` a `double` je výsledkem `x % y` pro konečnou `x` a `y` hodnota `z` tak, aby</span><span class="sxs-lookup"><span data-stu-id="02191-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="02191-149">Znaménko `z`, pokud není nula, je stejné jako znaménko `x`.</span><span class="sxs-lookup"><span data-stu-id="02191-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="02191-150">Absolutní hodnota `z` je hodnota vytvořená `|x| - n * |y|`, kde `n` je největší možné celé číslo, které je menší nebo rovno `|x| / |y|` a `|x|` a `|y|` jsou absolutními hodnotami `x` a `y` přestup.</span><span class="sxs-lookup"><span data-stu-id="02191-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="02191-151">Tato metoda výpočetního zbytku je podobná, jako se používá pro celočíselné operandy, ale liší se od IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="02191-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="02191-152">Pokud potřebujete zbývající operaci, která je v souladu s NORMou IEEE 754, použijte metodu <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02191-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="02191-153">Informace o chování operátoru `%` s nekonečnými operandy naleznete v části [operátor zbytek](~/_csharplang/spec/expressions.md#remainder-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="02191-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="02191-154">U operandů `decimal` je operátor zbývající `%` ekvivalentní k [operátoru zbývajícího](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) typu <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02191-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="02191-155">Následující příklad ukazuje chování operátoru zbytek s operandy s plovoucí desetinnou čárkou:</span><span class="sxs-lookup"><span data-stu-id="02191-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="02191-156">Operátor sčítání +</span><span class="sxs-lookup"><span data-stu-id="02191-156">Addition operator +</span></span>

<span data-ttu-id="02191-157">Operátor sčítání `+` vypočítá součet jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="02191-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="02191-158">Můžete také použít operátor `+` pro kombinaci řetězení řetězců a delegáta.</span><span class="sxs-lookup"><span data-stu-id="02191-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="02191-159">Další informace najdete v článku [operátory `+` a `+=`](addition-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="02191-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="02191-160">Operátor odčítání –</span><span class="sxs-lookup"><span data-stu-id="02191-160">Subtraction operator -</span></span>

<span data-ttu-id="02191-161">Operátor odčítání `-` odečte svůj pravý operand od jeho levého operandu:</span><span class="sxs-lookup"><span data-stu-id="02191-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="02191-162">K odebrání delegáta můžete také použít operátor `-`.</span><span class="sxs-lookup"><span data-stu-id="02191-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="02191-163">Další informace najdete v článku o [operátoru `-`](subtraction-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="02191-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="02191-164">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="02191-164">Compound assignment</span></span>

<span data-ttu-id="02191-165">Pro binární operátor `op` se složený výraz přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="02191-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="02191-166">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="02191-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="02191-167">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="02191-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="02191-168">Následující příklad ukazuje použití složeného přiřazení s aritmetickými operátory:</span><span class="sxs-lookup"><span data-stu-id="02191-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="02191-169">Z důvodu [numerických propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions)nemusí být výsledek operace `op` implicitně převoditelný na typ `T` `x`.</span><span class="sxs-lookup"><span data-stu-id="02191-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="02191-170">V takovém případě, pokud je `op` předdefinovaným operátorem a výsledek operace je explicitně převoditelné na typ `T` `x`, výraz složeného přiřazení `x op= y` formuláře je ekvivalentní `x = (T)(x op y)` , s výjimkou toho, že `x` vyhodnocována pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="02191-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="02191-171">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="02191-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="02191-172">K přihlášení a odhlášení odběru [událostí](../keywords/event.md)můžete použít také operátory `+=` a `-=`.</span><span class="sxs-lookup"><span data-stu-id="02191-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="02191-173">Další informace najdete v tématu [Postup: přihlášení a](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)odhlášení odběru událostí.</span><span class="sxs-lookup"><span data-stu-id="02191-173">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="02191-174">Priorita operátorů a asociativita</span><span class="sxs-lookup"><span data-stu-id="02191-174">Operator precedence and associativity</span></span>

<span data-ttu-id="02191-175">Následující seznam řadí aritmetické operátory počínaje od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="02191-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="02191-176">Přírůstek přípony `x++` a snížení `x--` operátory</span><span class="sxs-lookup"><span data-stu-id="02191-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="02191-177">Zvýšení prefixu `++x` a snížení `--x` a unární operátory `+` a `-`</span><span class="sxs-lookup"><span data-stu-id="02191-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="02191-178">Multiplikativní operátory `*`, `/` a `%`</span><span class="sxs-lookup"><span data-stu-id="02191-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="02191-179">Aditivní `+` a `-` operátory</span><span class="sxs-lookup"><span data-stu-id="02191-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="02191-180">Binární aritmetické operátory jsou asociativní zleva.</span><span class="sxs-lookup"><span data-stu-id="02191-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="02191-181">To znamená, že operátory se stejnou úrovní priority jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="02191-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="02191-182">Pomocí závorek, `()` můžete změnit pořadí vyhodnocování stanovené prioritou operátora a asociativita.</span><span class="sxs-lookup"><span data-stu-id="02191-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="02191-183">Úplný seznam C# operátorů seřazených podle priority úrovně naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="02191-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="02191-184">Aritmetické přetečení a dělení nulou</span><span class="sxs-lookup"><span data-stu-id="02191-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="02191-185">Pokud je výsledek aritmetické operace mimo rozsah možných konečných hodnot typu, který je součástí daného číselného typu, chování aritmetického operátoru závisí na typu jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="02191-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="02191-186">Aritmetické přetečení typu Integer</span><span class="sxs-lookup"><span data-stu-id="02191-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="02191-187">Celočíselné dělení nulou vždy vyvolá <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="02191-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="02191-188">V případě celočíselného přetečení aritmetického přetečení, které může být [zaškrtnuto nebo nezaškrtnuto](../keywords/checked-and-unchecked.md), ovládací prvky výsledného chování:</span><span class="sxs-lookup"><span data-stu-id="02191-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="02191-189">V kontrolovaném kontextu dojde k chybě při kompilaci, pokud dojde k přetečení v konstantním výrazu.</span><span class="sxs-lookup"><span data-stu-id="02191-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="02191-190">V opačném případě, pokud je operace provedena v době běhu, je vyvolána <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="02191-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="02191-191">V nekontrolovaném kontextu se výsledek zkrátí tak, že zahodí jakékoli bity s vysokým pořadím, které se nevejdou do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="02191-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="02191-192">Spolu s [zaškrtnutými a nekontrolovanými](../keywords/checked-and-unchecked.md) příkazy můžete použít operátory `checked` a `unchecked` k řízení kontextu kontroly přetečení, ve kterém je výraz vyhodnocen:</span><span class="sxs-lookup"><span data-stu-id="02191-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="02191-193">Ve výchozím nastavení se aritmetické operace vyskytují v nekontrolovaném *kontextu.*</span><span class="sxs-lookup"><span data-stu-id="02191-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="02191-194">Aritmetické přetečení s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="02191-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="02191-195">Aritmetické operace s typy `float` a `double` nikdy nevyvolávají výjimku.</span><span class="sxs-lookup"><span data-stu-id="02191-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="02191-196">Výsledkem aritmetických operací s těmito typy může být jedna z speciálních hodnot, které reprezentují nekonečno a nikoli-a-číslo:</span><span class="sxs-lookup"><span data-stu-id="02191-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="02191-197">Pro operandy typu `decimal` aritmetické přetečení vždy vyvolá <xref:System.OverflowException> a dělení nulou vždy vyvolá <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="02191-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="02191-198">Chyby zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="02191-198">Round-off errors</span></span>

<span data-ttu-id="02191-199">Z důvodu obecného omezení reprezentace reálných čísel s plovoucí desetinnou čárkou a aritmetických operací s plovoucí desetinnou čárkou může dojít k chybám zaokrouhlení ve výpočtech s typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="02191-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="02191-200">To znamená, že získaný výsledek výrazu se může lišit od očekávaného matematického výsledku.</span><span class="sxs-lookup"><span data-stu-id="02191-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="02191-201">Následující příklad ukazuje několik takových případů:</span><span class="sxs-lookup"><span data-stu-id="02191-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="02191-202">Další informace najdete v tématu poznámky na referenčních stránkách [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)nebo [System. Decimal](/dotnet/api/system.decimal#remarks) .</span><span class="sxs-lookup"><span data-stu-id="02191-202">For more information, see remarks at [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="02191-203">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="02191-203">Operator overloadability</span></span>

<span data-ttu-id="02191-204">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) unární operátory (`++`, `--`, `+` a `-`) a binární (`*`, `/`, `%`, `+` a `-`).</span><span class="sxs-lookup"><span data-stu-id="02191-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="02191-205">Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="02191-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="02191-206">Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="02191-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="02191-207">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="02191-207">C# language specification</span></span>

<span data-ttu-id="02191-208">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="02191-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="02191-209">Operátory přírůstku a snížení přípony</span><span class="sxs-lookup"><span data-stu-id="02191-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="02191-210">Operátory přírůstku a snížení předpony</span><span class="sxs-lookup"><span data-stu-id="02191-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="02191-211">Unární operátor plus</span><span class="sxs-lookup"><span data-stu-id="02191-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="02191-212">Unární operátor minus</span><span class="sxs-lookup"><span data-stu-id="02191-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="02191-213">Operátor násobení</span><span class="sxs-lookup"><span data-stu-id="02191-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="02191-214">Operátor dělení</span><span class="sxs-lookup"><span data-stu-id="02191-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="02191-215">Operátor zbývající</span><span class="sxs-lookup"><span data-stu-id="02191-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="02191-216">Operátor sčítání</span><span class="sxs-lookup"><span data-stu-id="02191-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="02191-217">Operátor odčítání</span><span class="sxs-lookup"><span data-stu-id="02191-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="02191-218">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="02191-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="02191-219">Kontrolované a nezaškrtnuté operátory</span><span class="sxs-lookup"><span data-stu-id="02191-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="02191-220">Číselné propagační akce</span><span class="sxs-lookup"><span data-stu-id="02191-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="02191-221">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02191-221">See also</span></span>

- [<span data-ttu-id="02191-222">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="02191-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="02191-223">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="02191-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="02191-224">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="02191-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
