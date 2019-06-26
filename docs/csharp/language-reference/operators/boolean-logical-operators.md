---
title: Logické operátory logické - C# odkaz
description: Další informace o C# operátory, které provádějí operace disjunkce výhradními i zahrnutými (nebo) logická operandy, spojení (a) a Logická negace.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 261c3fa2cc2f94e2a3f76a8a41982c21183e973a
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401367"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="a64d9-103">Logická logické operátory (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="a64d9-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="a64d9-104">Následující operátory provádí logické operace s [bool](../keywords/bool.md) operandy:</span><span class="sxs-lookup"><span data-stu-id="a64d9-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="a64d9-105">Unární [ `!` (Logická negace)](#logical-negation-operator-) operátor.</span><span class="sxs-lookup"><span data-stu-id="a64d9-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="a64d9-106">Binární [ `&` (logický operátor a)](#logical-and-operator-), [ `|` (logický operátor nebo)](#logical-or-operator-), a [ `^` (logické XOR)](#logical-exclusive-or-operator-) operátory.</span><span class="sxs-lookup"><span data-stu-id="a64d9-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="a64d9-107">Tyto operátory jsou vždy vyhodnoceny oba operandy.</span><span class="sxs-lookup"><span data-stu-id="a64d9-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="a64d9-108">Binární [ `&&` (logický operátor podmíněného AND)](#conditional-logical-and-operator-) a [ `||` (logický operátor podmíněného OR)](#conditional-logical-or-operator-) operátory.</span><span class="sxs-lookup"><span data-stu-id="a64d9-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="a64d9-109">Tyto operátory vyhodnotit operand pravé strany pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="a64d9-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="a64d9-110">Pro operandy [integrální](../keywords/integral-types-table.md) typy, `&`, `|`, a `^` operátory provádějí operace bitový logický.</span><span class="sxs-lookup"><span data-stu-id="a64d9-110">For the operands of the [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="a64d9-111">Další informace najdete v tématu [operátory bitové a shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a64d9-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="a64d9-112">Logický operátor negace!</span><span class="sxs-lookup"><span data-stu-id="a64d9-112">Logical negation operator !</span></span>

<span data-ttu-id="a64d9-113">`!` Vypočítá operátor logické negace svého operandu.</span><span class="sxs-lookup"><span data-stu-id="a64d9-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="a64d9-114">To znamená, vytvoří `true`, pokud je operand vyhodnocen jako `false`, a `false`, pokud je operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="a64d9-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-"></a> <span data-ttu-id="a64d9-115">Logický operátor AND &amp;</span><span class="sxs-lookup"><span data-stu-id="a64d9-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="a64d9-116">`&` Operátor vypočítá logický operátor AND operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="a64d9-117">Výsledek `x & y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="a64d9-118">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="a64d9-119">`&` Operátor vyhodnotí oba operandy i v případě, že levý operand je vyhodnocen jako `false`tak, aby výsledek musí být `false` bez ohledu na hodnotu operandu pravé.</span><span class="sxs-lookup"><span data-stu-id="a64d9-119">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="a64d9-120">V následujícím příkladu, pravém operand `&` volání metody, která se provádí bez ohledu na hodnotu levý operand je operátor:</span><span class="sxs-lookup"><span data-stu-id="a64d9-120">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="a64d9-121">[Podmíněné logického operátoru AND](#conditional-logical-and-operator-) `&&` také vypočítá logický operátor a jeho operandy, ale nevyhodnocuje zpracovával pravý operand, je-li levý operand je vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="a64d9-122">Pro operandy integrální typy `&` operátor výpočetní prostředí [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="a64d9-123">Unární `&` operátor je [operátoru address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="a64d9-123">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="a64d9-124">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="a64d9-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="a64d9-125">`^` Operátor vypočítá logické exkluzivní OR označované také jako logický operátor XOR z operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="a64d9-126">Výsledek `x ^ y` je `true` Pokud `x` vyhodnotí jako `true` a `y` vyhodnotí jako `false`, nebo `x` vyhodnotí jako `false` a `y` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="a64d9-127">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="a64d9-128">To znamená pro `bool` operandy, `^` operátor vypočítá stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="a64d9-129">Pro operandy integrální typy `^` operátor výpočetní prostředí [logický bitový exkluzivní operátor OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="a64d9-130">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="a64d9-130">Logical OR operator |</span></span>

<span data-ttu-id="a64d9-131">`|` Operátor vypočítá logický operátor OR operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="a64d9-132">Výsledek `x | y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="a64d9-133">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="a64d9-134">`|` Operátor vyhodnotí oba operandy i v případě, že levý operand je vyhodnocen jako `true`tak, aby výsledek musí být `true` bez ohledu na hodnotu operandu pravé.</span><span class="sxs-lookup"><span data-stu-id="a64d9-134">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="a64d9-135">V následujícím příkladu, pravém operand `|` volání metody, která se provádí bez ohledu na hodnotu levý operand je operátor:</span><span class="sxs-lookup"><span data-stu-id="a64d9-135">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="a64d9-136">[Podmíněné logického operátoru OR](#conditional-logical-or-operator-) `||` také vypočítá logický operátor OR jeho operandy, ale nevyhodnocuje zpracovával pravý operand, je-li levý operand je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="a64d9-137">Pro operandy integrální typy `|` operátor výpočetní prostředí [bitové logické OR](bitwise-and-shift-operators.md#logical-or-operator-) z operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="a64d9-138">Podmíněné logického operátoru AND &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="a64d9-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="a64d9-139">Podmíněné logického operátoru AND `&&`, označované také jako "krátký cyklus" logického operátoru AND, vypočítá logický operátor AND operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="a64d9-140">Výsledek `x && y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="a64d9-141">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="a64d9-142">Pokud `x` vyhodnotí jako `false`, `y` , nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="a64d9-142">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="a64d9-143">V následujícím příkladu, pravém operand `&&` operátor je volání metody, které se neprovádí, pokud je levý operand vyhodnocen jako `false`:</span><span class="sxs-lookup"><span data-stu-id="a64d9-143">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="a64d9-144">[Logického operátoru AND](#logical-and-operator-) `&` také vypočítá logický operátor a jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="a64d9-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="a64d9-145">Podmíněné logického operátoru OR ||</span><span class="sxs-lookup"><span data-stu-id="a64d9-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="a64d9-146">Podmíněné logického operátoru OR `||`, označované také jako "krátký cyklus" logického operátoru OR, vypočítá logický operátor OR operandů.</span><span class="sxs-lookup"><span data-stu-id="a64d9-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="a64d9-147">Výsledek `x || y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="a64d9-148">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="a64d9-149">Pokud `x` vyhodnotí jako `true`, `y` , nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="a64d9-149">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="a64d9-150">V následujícím příkladu, pravém operand `||` operátor je volání metody, které se neprovádí, pokud je levý operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="a64d9-150">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="a64d9-151">[Logického operátoru OR](#logical-or-operator-) `|` také vypočítá logický operátor OR jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="a64d9-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="a64d9-152">Logická logické operátory s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a64d9-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="a64d9-153">Pro `bool?` operandy, `&` a `|` operátory podporu logiky s hodnotou tři.</span><span class="sxs-lookup"><span data-stu-id="a64d9-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="a64d9-154">Sémantika těchto operátorů je definována v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a64d9-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="a64d9-155">x</span><span class="sxs-lookup"><span data-stu-id="a64d9-155">x</span></span>|<span data-ttu-id="a64d9-156">y</span><span class="sxs-lookup"><span data-stu-id="a64d9-156">y</span></span>|<span data-ttu-id="a64d9-157">x & y</span><span class="sxs-lookup"><span data-stu-id="a64d9-157">x&y</span></span>|<span data-ttu-id="a64d9-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="a64d9-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="a64d9-159">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-159">true</span></span>|<span data-ttu-id="a64d9-160">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-160">true</span></span>|<span data-ttu-id="a64d9-161">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-161">true</span></span>|<span data-ttu-id="a64d9-162">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-162">true</span></span>|  
|<span data-ttu-id="a64d9-163">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-163">true</span></span>|<span data-ttu-id="a64d9-164">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-164">false</span></span>|<span data-ttu-id="a64d9-165">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-165">false</span></span>|<span data-ttu-id="a64d9-166">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-166">true</span></span>|  
|<span data-ttu-id="a64d9-167">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-167">true</span></span>|<span data-ttu-id="a64d9-168">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-168">null</span></span>|<span data-ttu-id="a64d9-169">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-169">null</span></span>|<span data-ttu-id="a64d9-170">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-170">true</span></span>|  
|<span data-ttu-id="a64d9-171">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-171">false</span></span>|<span data-ttu-id="a64d9-172">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-172">true</span></span>|<span data-ttu-id="a64d9-173">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-173">false</span></span>|<span data-ttu-id="a64d9-174">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-174">true</span></span>|  
|<span data-ttu-id="a64d9-175">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-175">false</span></span>|<span data-ttu-id="a64d9-176">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-176">false</span></span>|<span data-ttu-id="a64d9-177">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-177">false</span></span>|<span data-ttu-id="a64d9-178">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-178">false</span></span>|  
|<span data-ttu-id="a64d9-179">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-179">false</span></span>|<span data-ttu-id="a64d9-180">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-180">null</span></span>|<span data-ttu-id="a64d9-181">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-181">false</span></span>|<span data-ttu-id="a64d9-182">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-182">null</span></span>|  
|<span data-ttu-id="a64d9-183">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-183">null</span></span>|<span data-ttu-id="a64d9-184">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-184">true</span></span>|<span data-ttu-id="a64d9-185">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-185">null</span></span>|<span data-ttu-id="a64d9-186">true</span><span class="sxs-lookup"><span data-stu-id="a64d9-186">true</span></span>|  
|<span data-ttu-id="a64d9-187">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-187">null</span></span>|<span data-ttu-id="a64d9-188">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-188">false</span></span>|<span data-ttu-id="a64d9-189">false</span><span class="sxs-lookup"><span data-stu-id="a64d9-189">false</span></span>|<span data-ttu-id="a64d9-190">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-190">null</span></span>|  
|<span data-ttu-id="a64d9-191">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-191">null</span></span>|<span data-ttu-id="a64d9-192">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-192">null</span></span>|<span data-ttu-id="a64d9-193">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-193">null</span></span>|<span data-ttu-id="a64d9-194">null</span><span class="sxs-lookup"><span data-stu-id="a64d9-194">null</span></span>|  

<span data-ttu-id="a64d9-195">Tyto operátory chování se liší od chování typické operátor s typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="a64d9-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="a64d9-196">Obvykle operátor, který je definován pro operandy typu hodnoty je také možné s operandy odpovídající typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="a64d9-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="a64d9-197">Takové operátor vytvoří `null` Pokud kterýkoli z operandů `null`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="a64d9-198">Ale `&` a `|` operátory lze vytvořit jinou hodnotu než null, i v případě, že jeden z operandů je `null`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="a64d9-199">Další informace o chování operátoru s typy s možnou hodnotou Null, najdete v článku [operátory](../../programming-guide/nullable-types/using-nullable-types.md#operators) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="a64d9-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="a64d9-200">Můžete také použít `!` a `^` operátory se `bool?` operandy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a64d9-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="a64d9-201">Podmíněné logické operátory `&&` a `||` nepodporují `bool?` operandy.</span><span class="sxs-lookup"><span data-stu-id="a64d9-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="a64d9-202">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="a64d9-202">Compound assignment</span></span>

<span data-ttu-id="a64d9-203">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="a64d9-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="a64d9-204">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="a64d9-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="a64d9-205">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="a64d9-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="a64d9-206">`&`, `|`, A `^` podporují operátory složeného přiřazení jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a64d9-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="a64d9-207">Podmíněné logické operátory `&&` a `||` nepodporují složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a64d9-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="a64d9-208">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="a64d9-208">Operator precedence</span></span>

<span data-ttu-id="a64d9-209">V následujícím seznamu objednávek od nejvyšší priority k nejnižší logické operátory:</span><span class="sxs-lookup"><span data-stu-id="a64d9-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="a64d9-210">Logický operátor negace `!`</span><span class="sxs-lookup"><span data-stu-id="a64d9-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="a64d9-211">Logický operátor AND `&`</span><span class="sxs-lookup"><span data-stu-id="a64d9-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="a64d9-212">Logické exkluzivní OR – operátor `^`</span><span class="sxs-lookup"><span data-stu-id="a64d9-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="a64d9-213">Logický operátor OR `|`</span><span class="sxs-lookup"><span data-stu-id="a64d9-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="a64d9-214">Podmíněné logického operátoru AND `&&`</span><span class="sxs-lookup"><span data-stu-id="a64d9-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="a64d9-215">Podmíněné logický operátor OR `||`</span><span class="sxs-lookup"><span data-stu-id="a64d9-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="a64d9-216">Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů:</span><span class="sxs-lookup"><span data-stu-id="a64d9-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="a64d9-217">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="a64d9-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a64d9-218">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="a64d9-218">Operator overloadability</span></span>

<span data-ttu-id="a64d9-219">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `!`, `&`, `|`, a `^` operátory.</span><span class="sxs-lookup"><span data-stu-id="a64d9-219">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="a64d9-220">Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a64d9-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="a64d9-221">Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a64d9-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="a64d9-222">Uživatelem definovaný typ nejde přetížit podmíněné logické operátory `&&` a `||`.</span><span class="sxs-lookup"><span data-stu-id="a64d9-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="a64d9-223">Ale pokud přetížení uživatelem definovaného typu [operátory true a false](true-false-operators.md) a `&` nebo `|` operátor určitým způsobem, `&&` nebo `||` operace, respektive, může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="a64d9-223">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="a64d9-224">Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a64d9-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a64d9-225">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a64d9-225">C# language specification</span></span>

<span data-ttu-id="a64d9-226">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a64d9-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a64d9-227">Logický operátor negace</span><span class="sxs-lookup"><span data-stu-id="a64d9-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="a64d9-228">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="a64d9-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="a64d9-229">Podmíněné logické operátory</span><span class="sxs-lookup"><span data-stu-id="a64d9-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="a64d9-230">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="a64d9-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="a64d9-231">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a64d9-231">See also</span></span>

- [<span data-ttu-id="a64d9-232">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="a64d9-232">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a64d9-233">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a64d9-233">C# operators</span></span>](index.md)
- [<span data-ttu-id="a64d9-234">Bitový operátor a operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="a64d9-234">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
