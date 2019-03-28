---
title: 'Aritmetické operátory: - C# odkaz'
description: Další informace o C# operátory, které provádějí operace násobení, dělení, zbývající, sčítání a odčítání s číselnými typy.
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
ms.openlocfilehash: aaa6af8067707162a440ab69b46f08b612eae9b3
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545504"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="17305-103">Aritmetické operátory (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="17305-103">Arithmetic operators (C# Reference)</span></span>

<span data-ttu-id="17305-104">Následující operátory provádění aritmetických operací s číselnými typy:</span><span class="sxs-lookup"><span data-stu-id="17305-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="17305-105">Unární [ `++` (přírůstek)](#increment-operator-), [ `--` (snížení)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators), a [ `-` (minus)](#unary-plus-and-minus-operators) operátory.</span><span class="sxs-lookup"><span data-stu-id="17305-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators.</span></span>
- <span data-ttu-id="17305-106">Binární [ `*` (násobení)](#multiplication-operator-), [ `/` (dělení)](#division-operator-), [ `%` (zbytek)](#remainder-operator-), [ `+` () Přidání)](#addition-operator-), a [ `-` (odčítání)](#subtraction-operator-) operátory.</span><span class="sxs-lookup"><span data-stu-id="17305-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator-) operators.</span></span>

<span data-ttu-id="17305-107">Tyto operátory podporují všechny [integrální](../keywords/integral-types-table.md) a [s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md) číselné typy.</span><span class="sxs-lookup"><span data-stu-id="17305-107">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="17305-108">Operátor Inkrementace ++</span><span class="sxs-lookup"><span data-stu-id="17305-108">Increment operator ++</span></span>

<span data-ttu-id="17305-109">Unární operátor Inkrementace `++` svého operandu zvýší o hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="17305-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="17305-110">Operand musí být proměnná [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="17305-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="17305-111">Operátor Inkrementace se podporuje ve dvou formách: příponového operátoru Inkrementace `x++`a prefixový operátor Inkrementace `++x`.</span><span class="sxs-lookup"><span data-stu-id="17305-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="17305-112">Příponový operátor inkrementace</span><span class="sxs-lookup"><span data-stu-id="17305-112">Postfix increment operator</span></span>

<span data-ttu-id="17305-113">Výsledek `x++` je hodnota `x` *před* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="17305-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="17305-114">Prefixový operátor Inkrementace</span><span class="sxs-lookup"><span data-stu-id="17305-114">Prefix increment operator</span></span>

<span data-ttu-id="17305-115">Výsledek `++x` je hodnota `x` *po* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="17305-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="17305-116">Operátor dekrementace--</span><span class="sxs-lookup"><span data-stu-id="17305-116">Decrement operator --</span></span>

<span data-ttu-id="17305-117">Unární operátor dekrementace `--` sníží svého operandu o 1.</span><span class="sxs-lookup"><span data-stu-id="17305-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="17305-118">Operand musí být proměnná [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="17305-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="17305-119">Operátor dekrementace je podporován ve dvou formách: příponového operátoru dekrementace `x--`a operátor dekrementace předpony `--x`.</span><span class="sxs-lookup"><span data-stu-id="17305-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="17305-120">Příponový operátor dekrementace</span><span class="sxs-lookup"><span data-stu-id="17305-120">Postfix decrement operator</span></span>

<span data-ttu-id="17305-121">Výsledek `x--` je hodnota `x` *před* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="17305-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="17305-122">Operátor dekrementace předpony</span><span class="sxs-lookup"><span data-stu-id="17305-122">Prefix decrement operator</span></span>

<span data-ttu-id="17305-123">Výsledek `--x` je hodnota `x` *po* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="17305-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="17305-124">Unární plus a minus operátory</span><span class="sxs-lookup"><span data-stu-id="17305-124">Unary plus and minus operators</span></span>

<span data-ttu-id="17305-125">Unární `+` operátor vrátí hodnotu svého operandu.</span><span class="sxs-lookup"><span data-stu-id="17305-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="17305-126">Unární `-` operátor vypočítá negaci číselného svého operandu.</span><span class="sxs-lookup"><span data-stu-id="17305-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="17305-127">Unární `-` operátor nepodporuje [ulong](../keywords/ulong.md) typu.</span><span class="sxs-lookup"><span data-stu-id="17305-127">The unary `-` operator doesn't support the [ulong](../keywords/ulong.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="17305-128">Operátor násobení \*</span><span class="sxs-lookup"><span data-stu-id="17305-128">Multiplication operator \*</span></span>

<span data-ttu-id="17305-129">Operátor násobení `*` vypočítá součin z operandů:</span><span class="sxs-lookup"><span data-stu-id="17305-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="17305-130">Unární `*` operátor je [operátor dereference ukazatele](multiplication-operator.md#pointer-indirection-operator).</span><span class="sxs-lookup"><span data-stu-id="17305-130">The unary `*` operator is a [pointer indirection operator](multiplication-operator.md#pointer-indirection-operator).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="17305-131">Operátor dělení /</span><span class="sxs-lookup"><span data-stu-id="17305-131">Division operator /</span></span>

<span data-ttu-id="17305-132">Operátor dělení `/` rozděluje svůj první operand tak svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="17305-132">The division operator `/` divides its first operand by its second operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="17305-133">Celočíselné dělení</span><span class="sxs-lookup"><span data-stu-id="17305-133">Integer division</span></span>

<span data-ttu-id="17305-134">Pro operandy typy celých čísel, výsledek `/` operátor je typu integer a rovnosti podílu dvou operandů zaokrouhlena směrem k nule.:</span><span class="sxs-lookup"><span data-stu-id="17305-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="17305-135">Chcete-li získat podílu dvou operandů jako číslo s plovoucí desetinnou čárkou, použijte `float`, `double`, nebo `decimal` typu:</span><span class="sxs-lookup"><span data-stu-id="17305-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="17305-136">S plovoucí desetinnou čárkou dělení</span><span class="sxs-lookup"><span data-stu-id="17305-136">Floating-point division</span></span>

<span data-ttu-id="17305-137">Pro `float`, `double`, a `decimal` typy, výsledek `/` operátor odpovídá podílu dvou operandů:</span><span class="sxs-lookup"><span data-stu-id="17305-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="17305-138">Pokud jeden z operandů je `decimal`, může být jiný operand ani `float` ani `double`, protože ani `float` ani `double` implicitně převést na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="17305-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="17305-139">Je nutné explicitně převést `float` nebo `double` operand `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="17305-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="17305-140">Další informace o implicitní převody mezi číselnými typy najdete v tématu [tabulka implicitních číselných převodů](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="17305-140">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="17305-141">Zbývající % – operátor</span><span class="sxs-lookup"><span data-stu-id="17305-141">Remainder operator %</span></span>

<span data-ttu-id="17305-142">Operátor zbytku `%` vypočítá zbytek po dělení svůj první operand tak svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="17305-142">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="17305-143">Zbývající celé číslo</span><span class="sxs-lookup"><span data-stu-id="17305-143">Integer remainder</span></span>
  
<span data-ttu-id="17305-144">Pro operandy typy celých čísel, výsledek `a % b` hodnota vytvořil `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="17305-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="17305-145">Znaménko nenulové zbývající je stejný jako první operand, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="17305-145">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="17305-146">Použití <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metodu za účelem výpočtu dělení celého čísla a zbytek výsledky.</span><span class="sxs-lookup"><span data-stu-id="17305-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="17305-147">Zbytek s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="17305-147">Floating-point remainder</span></span>

<span data-ttu-id="17305-148">Pro `float` a `double` operandy, výsledek `x % y` pro omezenou `x` a `y` je hodnota `z` tak, aby</span><span class="sxs-lookup"><span data-stu-id="17305-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="17305-149">Znaménko `z`nenulová, pokud je stejný jako znaménko `x`.</span><span class="sxs-lookup"><span data-stu-id="17305-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="17305-150">absolutní hodnota `z` hodnota vytvořil `|x| - n * |y|` kde `n` je největší možné číslo, které je menší než nebo rovna hodnotě `|x| / |y|` a `|x|` a `|y|` jsou absolutní hodnoty `x` a `y`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="17305-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="17305-151">Tato metoda výpočetních zbytek je obdobou, který používá pro celočíselné operandy, ale se liší od IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="17305-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="17305-152">Pokud potřebujete zbývající operace, která splňuje IEEE 754, použijte <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="17305-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="17305-153">Informace o chování `%` operátor s nekonečnou operandy, najdete v článku [operátor zbytku](~/_csharplang/spec/expressions.md#remainder-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="17305-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="17305-154">Pro `decimal` operandy, operátor zbytku `%` odpovídá [operátor zbytku](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="17305-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="17305-155">Následující příklad ukazuje chování operátoru zbytek s plovoucí desetinnou čárkou operandy:</span><span class="sxs-lookup"><span data-stu-id="17305-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="17305-156">Operátor sčítání +</span><span class="sxs-lookup"><span data-stu-id="17305-156">Addition operator +</span></span>

<span data-ttu-id="17305-157">Operátor sčítání `+` kód vypočítá součet operandů:</span><span class="sxs-lookup"><span data-stu-id="17305-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="17305-158">Můžete také použít `+` operátoru pro zřetězení a delegátem kombinaci řetězec.</span><span class="sxs-lookup"><span data-stu-id="17305-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="17305-159">Další informace najdete v tématu [ `+` operátor](addition-operator.md) článku.</span><span class="sxs-lookup"><span data-stu-id="17305-159">For more information, see the [`+` operator](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="17305-160">Operátor odčítání-</span><span class="sxs-lookup"><span data-stu-id="17305-160">Subtraction operator -</span></span>

<span data-ttu-id="17305-161">Operátor odčítání `-` odečte jeho druhého operandu od jeho prvního operandu:</span><span class="sxs-lookup"><span data-stu-id="17305-161">The subtraction operator `-` subtracts its second operand from its first operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="17305-162">Můžete také použít `-` operátor pro odebrání delegátů.</span><span class="sxs-lookup"><span data-stu-id="17305-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="17305-163">Další informace najdete v tématu [ `-` operátor](subtraction-operator.md) článku.</span><span class="sxs-lookup"><span data-stu-id="17305-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="17305-164">Priorita a asociativita operátora</span><span class="sxs-lookup"><span data-stu-id="17305-164">Operator precedence and associativity</span></span>

<span data-ttu-id="17305-165">V následujícím seznamu objednávek od nejvyšší priority k nejnižší aritmetické operátory:</span><span class="sxs-lookup"><span data-stu-id="17305-165">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="17305-166">Zvýšení příponového operátora `x++` a dekrementace `x--` operátory.</span><span class="sxs-lookup"><span data-stu-id="17305-166">Postfix increment `x++` and decrement `x--` operators.</span></span>
- <span data-ttu-id="17305-167">Předponového `++x` a dekrementace `--x` a unární `+` a `-` operátory.</span><span class="sxs-lookup"><span data-stu-id="17305-167">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators.</span></span>
- <span data-ttu-id="17305-168">Multiplikativní `*`, `/`, a `%` operátory.</span><span class="sxs-lookup"><span data-stu-id="17305-168">Multiplicative `*`, `/`, and `%` operators.</span></span>
- <span data-ttu-id="17305-169">Additive `+` a `-` operátory.</span><span class="sxs-lookup"><span data-stu-id="17305-169">Additive `+` and `-` operators.</span></span>

<span data-ttu-id="17305-170">Binární aritmetické operátory jsou asociativní zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="17305-170">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="17305-171">To znamená, že operátory se stejnou úrovní priority jsou vyhodnoceny zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="17305-171">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="17305-172">Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů a asociativity.</span><span class="sxs-lookup"><span data-stu-id="17305-172">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="17305-173">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="17305-173">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="17305-174">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="17305-174">Compound assignment</span></span>

<span data-ttu-id="17305-175">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="17305-175">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="17305-176">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="17305-176">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="17305-177">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="17305-177">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="17305-178">Následující příklad ukazuje použití aritmetické operátory složeného přiřazení:</span><span class="sxs-lookup"><span data-stu-id="17305-178">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="17305-179">Můžete také použít `+=` a `-=` operátorů sloužící k přihlášení a odhlášení [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="17305-179">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="17305-180">Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="17305-180">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="17305-181">Aritmetické přetečení a dělení nulou</span><span class="sxs-lookup"><span data-stu-id="17305-181">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="17305-182">Když výsledek aritmetické operace je mimo rozsah možných hodnot omezené zahrnutých číselného typu, chování aritmetickém operátoru závisí na typu operandů.</span><span class="sxs-lookup"><span data-stu-id="17305-182">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="17305-183">Aritmetické přetečení celého čísla</span><span class="sxs-lookup"><span data-stu-id="17305-183">Integer arithmetic overflow</span></span>

<span data-ttu-id="17305-184">Dělení celého čísla nulou vždy vyvolá <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="17305-184">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="17305-185">V případě aritmetické přetečení celého čísla, přetečení kontrola kontextu, což může být [zaškrtnuté nebo nezaškrtnuté](../keywords/checked-and-unchecked.md), řídí výsledné chování:</span><span class="sxs-lookup"><span data-stu-id="17305-185">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="17305-186">Ve zkontrolovaném kontextu Pokud v konstantním výrazu se stane přetečení, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="17305-186">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="17305-187">Jinak, pokud se operace provádí za běhu, <xref:System.OverflowException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="17305-187">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="17305-188">V nekontrolovaném kontextu výsledek je rozdělená do se zahodí všechny bity nejvyšším, které se nehodí do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="17305-188">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="17305-189">Spolu s [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) příkazy, můžete použít `checked` a `unchecked` operátory ovládající kontroly kontext, ve kterém je výraz vyhodnocen přetečení:</span><span class="sxs-lookup"><span data-stu-id="17305-189">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="17305-190">Ve výchozím nastavení, aritmetické operace prováděny v *Nekontrolovaná* kontextu.</span><span class="sxs-lookup"><span data-stu-id="17305-190">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="17305-191">Plovoucí aritmetické přetečení</span><span class="sxs-lookup"><span data-stu-id="17305-191">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="17305-192">Aritmetické operace s `float` a `double` typy nikdy nevyvolají výjimku.</span><span class="sxs-lookup"><span data-stu-id="17305-192">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="17305-193">Výsledek aritmetické operace s těmito typy může být jedna z speciálními hodnotami, které představují nekonečno a not-a-number:</span><span class="sxs-lookup"><span data-stu-id="17305-193">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="17305-194">Pro operandy `decimal` typ aritmetické přetečení vždy vyvolá výjimku <xref:System.OverflowException> a dělení nulou vždy vyvolá výjimku <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="17305-194">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="17305-195">Zaokrouhlovací chyby</span><span class="sxs-lookup"><span data-stu-id="17305-195">Round-off errors</span></span>

<span data-ttu-id="17305-196">Z důvodu obecné omezení reprezentace plovoucí desetinné čárky reálná čísla a aritmetické operace s plovoucí desetinnou čárkou může dojít k chybám zaokrouhlovací ve výpočtech s typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="17305-196">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="17305-197">Vyprodukované výsledek výrazu tedy mohou lišit od očekávaný výsledek matematické.</span><span class="sxs-lookup"><span data-stu-id="17305-197">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="17305-198">Následující příklad ukazuje několik těchto případech:</span><span class="sxs-lookup"><span data-stu-id="17305-198">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

## <a name="operator-overloadability"></a><span data-ttu-id="17305-199">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="17305-199">Operator overloadability</span></span>

<span data-ttu-id="17305-200">Uživatelem definované typy lze [přetížení](../keywords/operator.md) unární (`++`, `--`, `+`, a `-`) a binární (`*`, `/`, `%`, `+`a `-`) aritmetické operátory.</span><span class="sxs-lookup"><span data-stu-id="17305-200">User-defined types can [overload](../keywords/operator.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="17305-201">Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="17305-201">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="17305-202">Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="17305-202">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17305-203">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="17305-203">C# language specification</span></span>

<span data-ttu-id="17305-204">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="17305-204">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="17305-205">Příponové operátory Inkrementace a dekrementace operátory</span><span class="sxs-lookup"><span data-stu-id="17305-205">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="17305-206">Předpona Inkrementace a dekrementace operátory</span><span class="sxs-lookup"><span data-stu-id="17305-206">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="17305-207">Unárního operátoru plus</span><span class="sxs-lookup"><span data-stu-id="17305-207">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="17305-208">Unární operátor minus</span><span class="sxs-lookup"><span data-stu-id="17305-208">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="17305-209">Operátor násobení</span><span class="sxs-lookup"><span data-stu-id="17305-209">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="17305-210">Operátor dělení</span><span class="sxs-lookup"><span data-stu-id="17305-210">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="17305-211">Operátor zbytku</span><span class="sxs-lookup"><span data-stu-id="17305-211">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="17305-212">Operátor sčítání</span><span class="sxs-lookup"><span data-stu-id="17305-212">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="17305-213">Operátor odčítání</span><span class="sxs-lookup"><span data-stu-id="17305-213">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="17305-214">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="17305-214">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="17305-215">Operátory zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="17305-215">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)

## <a name="see-also"></a><span data-ttu-id="17305-216">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17305-216">See also</span></span>

- [<span data-ttu-id="17305-217">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="17305-217">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="17305-218">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="17305-218">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="17305-219">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="17305-219">C# Operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="17305-220">Číslovky v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="17305-220">Numerics in .NET</span></span>](../../../standard/numerics.md)