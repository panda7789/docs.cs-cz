---
title: Aritmetické operátory - odkaz C#
description: Další informace o operátorech jazyka C#, které provádějí operace násobení, dělení, zbytek, sčítání a odčítání s číselnými typy.
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
ms.openlocfilehash: f03084fa611c35c5504190b28fab79563d560d03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399257"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="1791b-103">Aritmetické operátory (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="1791b-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="1791b-104">Následující operátory provádějí aritmetické operace s operandy číselných typů:</span><span class="sxs-lookup"><span data-stu-id="1791b-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="1791b-105">Unární [ `++` (přírůstek)](#increment-operator-), [ `--` (snížení)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)a [ `-` (minus)](#unary-plus-and-minus-operators) operátory</span><span class="sxs-lookup"><span data-stu-id="1791b-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="1791b-106">Binární [ `*` (násobení)](#multiplication-operator-), [ `/` (dělení)](#division-operator-), [ `%` (zbytek)](#remainder-operator-), [ `+` (sčítání)](#addition-operator-)a [ `-` (odčítání)](#subtraction-operator--) operátory</span><span class="sxs-lookup"><span data-stu-id="1791b-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="1791b-107">Tyto operátory jsou podporovány všechny [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) desetinnou hodnotu číselné typy.</span><span class="sxs-lookup"><span data-stu-id="1791b-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="1791b-108">Operátor přírůstek ++</span><span class="sxs-lookup"><span data-stu-id="1791b-108">Increment operator ++</span></span>

<span data-ttu-id="1791b-109">Unární přírůstek `++` operátor urychluje jeho operand o 1.</span><span class="sxs-lookup"><span data-stu-id="1791b-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="1791b-110">Operand musí být proměnná, přístup k [vlastnostem](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="1791b-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="1791b-111">Operátor přírůstek je podporován ve dvou formách: operátor `x++`přípona přírůstek , `++x`a operátor přírůstek předpony, .</span><span class="sxs-lookup"><span data-stu-id="1791b-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="1791b-112">Příponový operátor inkrementace</span><span class="sxs-lookup"><span data-stu-id="1791b-112">Postfix increment operator</span></span>

<span data-ttu-id="1791b-113">Výsledkem `x++` je hodnota `x` *před* operací, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1791b-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="1791b-114">Operátor přírůstek předpony</span><span class="sxs-lookup"><span data-stu-id="1791b-114">Prefix increment operator</span></span>

<span data-ttu-id="1791b-115">Výsledkem `++x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1791b-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="1791b-116">Operátor snížení --</span><span class="sxs-lookup"><span data-stu-id="1791b-116">Decrement operator --</span></span>

<span data-ttu-id="1791b-117">Unární snížení operátor `--` sníží jeho operand o 1.</span><span class="sxs-lookup"><span data-stu-id="1791b-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="1791b-118">Operand musí být proměnná, přístup k [vlastnostem](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="1791b-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="1791b-119">Operátor snížení je podporován ve dvou formách: operátor snížení `x--`přípony a operátor snížení `--x`předpony .</span><span class="sxs-lookup"><span data-stu-id="1791b-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="1791b-120">Příponový operátor dekrementace</span><span class="sxs-lookup"><span data-stu-id="1791b-120">Postfix decrement operator</span></span>

<span data-ttu-id="1791b-121">Výsledkem `x--` je hodnota `x` *před* operací, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1791b-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="1791b-122">Operátor snížení předpony</span><span class="sxs-lookup"><span data-stu-id="1791b-122">Prefix decrement operator</span></span>

<span data-ttu-id="1791b-123">Výsledkem `--x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1791b-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="1791b-124">Unární plus a minus operátory</span><span class="sxs-lookup"><span data-stu-id="1791b-124">Unary plus and minus operators</span></span>

<span data-ttu-id="1791b-125">Unární `+` operátor vrátí hodnotu jeho operand.</span><span class="sxs-lookup"><span data-stu-id="1791b-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="1791b-126">Unární `-` operátor vypočítá číselné negace jeho operandu.</span><span class="sxs-lookup"><span data-stu-id="1791b-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="1791b-127">Typ [ulong](../builtin-types/integral-numeric-types.md) nepodporuje unární `-` operátor.</span><span class="sxs-lookup"><span data-stu-id="1791b-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="1791b-128">Operátor násobení \*</span><span class="sxs-lookup"><span data-stu-id="1791b-128">Multiplication operator \*</span></span>

<span data-ttu-id="1791b-129">Operátor `*` násobení vypočítá součin svých operandů:</span><span class="sxs-lookup"><span data-stu-id="1791b-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="1791b-130">Unární `*` operátor je [operátor dereference ukazatele](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="1791b-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="1791b-131">Provozovatel divize /</span><span class="sxs-lookup"><span data-stu-id="1791b-131">Division operator /</span></span>

<span data-ttu-id="1791b-132">Operátor `/` divize rozděluje svůj levý operand pravostrannou obsluhou.</span><span class="sxs-lookup"><span data-stu-id="1791b-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="1791b-133">Celá divize</span><span class="sxs-lookup"><span data-stu-id="1791b-133">Integer division</span></span>

<span data-ttu-id="1791b-134">Pro operandy typů celé číslo je výsledek `/` operátoru celého typu a rovná se podílu dvou operandů zaokrouhlených na nulu:</span><span class="sxs-lookup"><span data-stu-id="1791b-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="1791b-135">Chcete-li získat podíl obou operandů jako číslo s plovoucí `float` `double`desetinnou tácek, použijte typ , nebo `decimal` zadejte:</span><span class="sxs-lookup"><span data-stu-id="1791b-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="1791b-136">Divize s plovoucí desetinnou desetinnou desetinnou desetin</span><span class="sxs-lookup"><span data-stu-id="1791b-136">Floating-point division</span></span>

<span data-ttu-id="1791b-137">Pro `float`, `double`, `decimal` a typy je `/` výsledkem operátoru podíl obou operandů:</span><span class="sxs-lookup"><span data-stu-id="1791b-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="1791b-138">`decimal`Pokud je jeden z operandů , může `float` být `double`jiný operand `double` ani jeden `decimal`, protože ani `float` není implicitně převoditelný na .</span><span class="sxs-lookup"><span data-stu-id="1791b-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="1791b-139">Je nutné explicitně `double` převést `decimal` `float` nebo operand na typ.</span><span class="sxs-lookup"><span data-stu-id="1791b-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="1791b-140">Další informace o převodech mezi číselnými typy naleznete [v tématu Předdefinované číselné převody](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="1791b-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="1791b-141">Zůstatek operátor %</span><span class="sxs-lookup"><span data-stu-id="1791b-141">Remainder operator %</span></span>

<span data-ttu-id="1791b-142">Zbývající operátor `%` vypočítá zbytek po vydělením jeho levého operandu jeho pravostranným operandem.</span><span class="sxs-lookup"><span data-stu-id="1791b-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="1791b-143">Zbytek celého čísla</span><span class="sxs-lookup"><span data-stu-id="1791b-143">Integer remainder</span></span>

<span data-ttu-id="1791b-144">Pro operandy celého čísla `a % b` typů, výsledkem je `a - (a / b) * b`hodnota produkovaná .</span><span class="sxs-lookup"><span data-stu-id="1791b-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="1791b-145">Znaménko nenulového zbytku je stejné jako u levého operandu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1791b-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="1791b-146">Pomocí <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metody můžete vypočítat výsledky dělení celého čísla i zbytku.</span><span class="sxs-lookup"><span data-stu-id="1791b-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="1791b-147">Zbytek s plovoucí desetinnou tísní</span><span class="sxs-lookup"><span data-stu-id="1791b-147">Floating-point remainder</span></span>

<span data-ttu-id="1791b-148">Pro `float` a `double` operandy, výsledek `x % y` pro konečný `x` a `y` je `z` hodnota taková, že</span><span class="sxs-lookup"><span data-stu-id="1791b-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="1791b-149">Znaménko `z`, pokud je nenulové, `x`je stejné jako znaménko .</span><span class="sxs-lookup"><span data-stu-id="1791b-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="1791b-150">Absolutní hodnota `z` je hodnota produkovaná místem, `|x| - n * |y|` `n` kde je největší možné `|x| / |y|` celé `|x|` `|y|` číslo, které `x` je `y`menší nebo rovno a jsou absolutní hodnoty a , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1791b-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="1791b-151">Tato metoda výpočtu zbytek je obdobou, která se používá pro celé číslo operandy, ale liší se od specifikace IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="1791b-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="1791b-152">Pokud potřebujete zbývající operaci, která je v souladu se specifikací IEEE 754, použijte metodu. <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1791b-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1791b-153">Informace o chování operátoru `%` s neomezenýmými operandy naleznete v části Operátor [Zbytek](~/_csharplang/spec/expressions.md#remainder-operator) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1791b-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="1791b-154">Pro `decimal` operandy je operátor `%` zbytek ekvivalentní [zbytku operátoru](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="1791b-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="1791b-155">Následující příklad ukazuje chování operátoru zbytek s operandy s plovoucí desetinnou desetinnou desetinnou táhou:</span><span class="sxs-lookup"><span data-stu-id="1791b-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="1791b-156">Operátor sčítání +</span><span class="sxs-lookup"><span data-stu-id="1791b-156">Addition operator +</span></span>

<span data-ttu-id="1791b-157">Operátor `+` sčítání vypočítá součet jeho operandů:</span><span class="sxs-lookup"><span data-stu-id="1791b-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="1791b-158">Můžete také použít `+` operátor pro zřetězení řetězce a delegát kombinaci.</span><span class="sxs-lookup"><span data-stu-id="1791b-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="1791b-159">Další informace naleznete [ `+` v `+=` článku a operátory.](addition-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1791b-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="1791b-160">Operátor odčítání -</span><span class="sxs-lookup"><span data-stu-id="1791b-160">Subtraction operator -</span></span>

<span data-ttu-id="1791b-161">Operátor `-` odčítání odečte svůj pravostranný operand od levého operandu:</span><span class="sxs-lookup"><span data-stu-id="1791b-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="1791b-162">Můžete také použít `-` operátor pro odebrání delegáta.</span><span class="sxs-lookup"><span data-stu-id="1791b-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="1791b-163">Další informace naleznete [ `-` v `-=` článku a operátory.](subtraction-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1791b-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="1791b-164">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="1791b-164">Compound assignment</span></span>

<span data-ttu-id="1791b-165">Pro binární `op`operátor , složený výraz přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="1791b-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="1791b-166">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="1791b-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="1791b-167">kromě `x` toho, že se vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="1791b-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="1791b-168">Následující příklad ukazuje použití složené přiřazení s aritmetické operátory:</span><span class="sxs-lookup"><span data-stu-id="1791b-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="1791b-169">Z důvodu [číselných propagačních](~/_csharplang/spec/expressions.md#numeric-promotions) `op` akcí nemusí být výsledek operace `T` implicitně převoditelný na typ . `x`</span><span class="sxs-lookup"><span data-stu-id="1791b-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="1791b-170">V takovém případě, `op` pokud je předdefinovaný operátor a výsledek operace je `T` `x`explicitně převoditelný na `x op= y` typ `x = (T)(x op y)`, složený `x` výraz přiřazení formuláře je ekvivalentní , s výjimkou, že je vyhodnocenpouze jednou.</span><span class="sxs-lookup"><span data-stu-id="1791b-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="1791b-171">Následující příklad ukazuje, že chování:</span><span class="sxs-lookup"><span data-stu-id="1791b-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="1791b-172">Můžete také `+=` použít `-=` a operátory přihlásit a odhlásit z [akce](../keywords/event.md), resp.</span><span class="sxs-lookup"><span data-stu-id="1791b-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="1791b-173">Další informace naleznete v tématu [Jak se přihlásit k odběru a odhlásit z odběru událostí](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="1791b-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="1791b-174">Priorita operátora a asociativita</span><span class="sxs-lookup"><span data-stu-id="1791b-174">Operator precedence and associativity</span></span>

<span data-ttu-id="1791b-175">Následující seznam seřazuje aritmetické operátory od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="1791b-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="1791b-176">Operátory přípona přírůstek `x++` a snížení `x--`</span><span class="sxs-lookup"><span data-stu-id="1791b-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="1791b-177">Přírůstek `++x` a snížení předpony `--x` a `+` `-` unární a operátory</span><span class="sxs-lookup"><span data-stu-id="1791b-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="1791b-178">Multiplikativní `*`, `/`a `%` operátory</span><span class="sxs-lookup"><span data-stu-id="1791b-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="1791b-179">Doplňkové `+` `-` látky a obsluha</span><span class="sxs-lookup"><span data-stu-id="1791b-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="1791b-180">Binární aritmetické operátory jsou levosociativní.</span><span class="sxs-lookup"><span data-stu-id="1791b-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="1791b-181">To znamená, že operátory se stejnou úrovní priority jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="1791b-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="1791b-182">Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru a asociativitou operátora.</span><span class="sxs-lookup"><span data-stu-id="1791b-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="1791b-183">Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="1791b-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="1791b-184">Aritmetické přetečení a dělení nulou</span><span class="sxs-lookup"><span data-stu-id="1791b-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="1791b-185">Pokud je výsledek aritmetické operace mimo rozsah možných konečných hodnot zapojeného číselného typu, závisí chování aritmetického operátoru na typu jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="1791b-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="1791b-186">Integer aritmetický přetečení</span><span class="sxs-lookup"><span data-stu-id="1791b-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="1791b-187">Dělení celého čísla nulou <xref:System.DivideByZeroException>vždy vyvolá .</span><span class="sxs-lookup"><span data-stu-id="1791b-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="1791b-188">V případě integer aritmetické přetečení, přetečení kontrolní kontext, který lze [zkontrolovat nebo nezaškrtnuté](../keywords/checked-and-unchecked.md), řídí výsledné chování:</span><span class="sxs-lookup"><span data-stu-id="1791b-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="1791b-189">V kontrolovaném kontextu, pokud dojde k přetečení v konstantním výrazu, dojde k chybě v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="1791b-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="1791b-190">V opačném případě při operaci se <xref:System.OverflowException> provádí v době běhu, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="1791b-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="1791b-191">V nekontrolovaném kontextu je výsledek zkrácen zahozením všech bitů vyššího řádu, které se nevejdou do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="1791b-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="1791b-192">Spolu s [zaškrtnuté a nezaškrtnuté příkazy,](../keywords/checked-and-unchecked.md) můžete použít `checked` a `unchecked` operátory k řízení kontextu kontroly přetečení, ve kterém je vyhodnocován výraz:</span><span class="sxs-lookup"><span data-stu-id="1791b-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="1791b-193">Ve výchozím nastavení aritmetické operace dojít v *nekontrolovaném* kontextu.</span><span class="sxs-lookup"><span data-stu-id="1791b-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="1791b-194">Přetečení aritmetiky s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou tísní</span><span class="sxs-lookup"><span data-stu-id="1791b-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="1791b-195">Aritmetické operace `float` s `double` a typy nikdy vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="1791b-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="1791b-196">Výsledkem aritmetické operace s těmito typy může být jedna ze zvláštních hodnot, které představují nekonečno a ne-a-číslo:</span><span class="sxs-lookup"><span data-stu-id="1791b-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="1791b-197">Pro operandy `decimal` typu aritmetické přetečení vždy <xref:System.OverflowException> vyvolá a dělení nulou <xref:System.DivideByZeroException>vždy vyvolá .</span><span class="sxs-lookup"><span data-stu-id="1791b-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="1791b-198">Chyby zaokrouhlení</span><span class="sxs-lookup"><span data-stu-id="1791b-198">Round-off errors</span></span>

<span data-ttu-id="1791b-199">Z důvodu obecných omezení reprezentace s plovoucí desetinnou desetinnou rovinou reálných čísel a aritmetických aritmetických čísel s plovoucí desetinnou desetinnou, mohou při výpočtech s typy s plovoucí desetinnou desetinnou rovinou dojít k chybám zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="1791b-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="1791b-200">To znamená, že vytvořený výsledek výrazu se může lišit od očekávaného matematického výsledku.</span><span class="sxs-lookup"><span data-stu-id="1791b-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="1791b-201">Následující příklad ukazuje několik takových případů:</span><span class="sxs-lookup"><span data-stu-id="1791b-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="1791b-202">Další informace naleznete v poznámkách na referenčních stránkách [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks)nebo [System.Decimal.](/dotnet/api/system.decimal#remarks)</span><span class="sxs-lookup"><span data-stu-id="1791b-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1791b-203">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="1791b-203">Operator overloadability</span></span>

<span data-ttu-id="1791b-204">Uživatelem definovaný typ může [přetížit](operator-overloading.md) `+`unární `-`(`++`, `--`, `%` `+`, `-`a ) a binární (`*`, `/`, , a ) aritmetické operátory.</span><span class="sxs-lookup"><span data-stu-id="1791b-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="1791b-205">Když je přetížený binární operátor, odpovídající složený operátor přiřazení je také implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="1791b-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="1791b-206">Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1791b-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1791b-207">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1791b-207">C# language specification</span></span>

<span data-ttu-id="1791b-208">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="1791b-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="1791b-209">Operátory přípona přírůstek a snížení</span><span class="sxs-lookup"><span data-stu-id="1791b-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="1791b-210">Operátory přírůstek a snížení předpona</span><span class="sxs-lookup"><span data-stu-id="1791b-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="1791b-211">Jednočlenný operátor plus</span><span class="sxs-lookup"><span data-stu-id="1791b-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="1791b-212">Unární minus operátor</span><span class="sxs-lookup"><span data-stu-id="1791b-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="1791b-213">Operátor násobení</span><span class="sxs-lookup"><span data-stu-id="1791b-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="1791b-214">Provozovatel divize</span><span class="sxs-lookup"><span data-stu-id="1791b-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="1791b-215">Operátor zbytek</span><span class="sxs-lookup"><span data-stu-id="1791b-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="1791b-216">Operátor sčítání</span><span class="sxs-lookup"><span data-stu-id="1791b-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="1791b-217">Operátor odčítání</span><span class="sxs-lookup"><span data-stu-id="1791b-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="1791b-218">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="1791b-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="1791b-219">Kontrolované a nekontrolované operátory</span><span class="sxs-lookup"><span data-stu-id="1791b-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="1791b-220">Číselné propagační akce</span><span class="sxs-lookup"><span data-stu-id="1791b-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="1791b-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="1791b-221">See also</span></span>

- [<span data-ttu-id="1791b-222">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="1791b-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1791b-223">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1791b-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="1791b-224">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="1791b-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
