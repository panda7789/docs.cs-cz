---
title: Booleovské logické operátory – reference jazyka C#
description: Přečtěte si o operátorech jazyka C#, které provádějí logické negace, spojení (a) a včetně a exkluzivní operace disjunkce (nebo) s logickými operandy.
ms.date: 06/29/2020
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
- '|=_CSharpKeyword'
- ^=_CSharpKeyword
- '&=_CSharpKeyword'
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
ms.openlocfilehash: 2a67542e25ddb258602b4005a71b565cf6522917
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855137"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="20221-103">Logické logické operátory (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="20221-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="20221-104">Následující operátory provádějí logické [operace s](../builtin-types/bool.md) logickými operandy:</span><span class="sxs-lookup"><span data-stu-id="20221-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="20221-105">Unární operátor [ `!` (logická negace)](#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="20221-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="20221-106">Binary [ `&` (Logical and)](#logical-and-operator-), [ `|` (Logical or)](#logical-or-operator-)a [ `^` (Logical or)](#logical-exclusive-or-operator-) Operators.</span><span class="sxs-lookup"><span data-stu-id="20221-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="20221-107">Tyto operátory vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="20221-108">Binární [ `&&` (Podmíněné logické a)](#conditional-logical-and-operator-) a [ `||` (Podmíněné logické OR)](#conditional-logical-or-operator-) operátory.</span><span class="sxs-lookup"><span data-stu-id="20221-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="20221-109">Tyto operátory vyhodnotí operand na pravé straně, pokud je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="20221-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="20221-110">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md), `&` operátory, `|` a `^` provádějí bitové logické operace.</span><span class="sxs-lookup"><span data-stu-id="20221-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="20221-111">Další informace naleznete v tématu [operátory bitových a posunutí](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="20221-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="20221-112">Logický operátor negace!</span><span class="sxs-lookup"><span data-stu-id="20221-112">Logical negation operator !</span></span>

<span data-ttu-id="20221-113">Unární operátor prefixu `!` vypočítá logickou negaci svého operandu.</span><span class="sxs-lookup"><span data-stu-id="20221-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="20221-114">To znamená, že je `true` -li operand vyhodnocen `false` , a `false` , pokud je operand vyhodnocen jako `true` :</span><span class="sxs-lookup"><span data-stu-id="20221-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="20221-115">Počínaje jazykem C# 8,0, unární příponový `!` operátor je [operátor null-striktní](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="20221-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="20221-116">Logický operátor AND&amp;</span><span class="sxs-lookup"><span data-stu-id="20221-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="20221-117">`&`Operátor vypočítá logickou a jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="20221-118">Výsledek je, `x & y` `true` Pokud je `x` a `y` vyhodnocen jako `true` .</span><span class="sxs-lookup"><span data-stu-id="20221-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="20221-119">V opačném případě je výsledkem `false` .</span><span class="sxs-lookup"><span data-stu-id="20221-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="20221-120">`&`Operátor vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen tak `false` , aby výsledek operace byl `false` bez ohledu na hodnotu operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="20221-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="20221-121">V následujícím příkladu je pravý operand `&` operátoru volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:</span><span class="sxs-lookup"><span data-stu-id="20221-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="20221-122">[Podmíněný logický operátor and](#conditional-logical-and-operator-) `&&` také VYPOČÍTÁ logickou a jeho operandy, ale nevyhodnotí pravý operand, pokud je levý operand vyhodnocen jako `false` .</span><span class="sxs-lookup"><span data-stu-id="20221-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="20221-123">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `&` operátor vypočítá [bitovou logickou a](bitwise-and-shift-operators.md#logical-and-operator-) jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="20221-124">Unární `&` operátor je [operátor address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="20221-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="20221-125">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="20221-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="20221-126">`^`Operátor vypočítá logickou výlučnou nebo, označovanou také jako logická XOR, z operandů.</span><span class="sxs-lookup"><span data-stu-id="20221-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="20221-127">Výsledkem `x ^ y` je `true` , pokud je `x` vyhodnocena jako `true` a `y` `false` `x` `false` `y` `true` vyhodnocena jako nebo vyhodnocena jako a vyhodnocena jako.</span><span class="sxs-lookup"><span data-stu-id="20221-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="20221-128">V opačném případě je výsledkem `false` .</span><span class="sxs-lookup"><span data-stu-id="20221-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="20221-129">To znamená, že pro `bool` operandy `^` vypočítá operátor stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=` .</span><span class="sxs-lookup"><span data-stu-id="20221-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="20221-130">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `^` operátor vypočítá [BITOVÝ logický typ Exclusive nebo](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="20221-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="20221-131">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="20221-131">Logical OR operator |</span></span>

<span data-ttu-id="20221-132">`|`Operátor vypočítá logický nebo jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="20221-133">Výsledek je v `x | y` případě, že je `true` buď `x` nebo `y` vyhodnocen jako `true` .</span><span class="sxs-lookup"><span data-stu-id="20221-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="20221-134">V opačném případě je výsledkem `false` .</span><span class="sxs-lookup"><span data-stu-id="20221-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="20221-135">`|`Operátor vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen tak `true` , aby výsledek operace byl `true` bez ohledu na hodnotu operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="20221-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="20221-136">V následujícím příkladu je pravý operand `|` operátoru volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:</span><span class="sxs-lookup"><span data-stu-id="20221-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="20221-137">[Podmíněný logický operátor OR](#conditional-logical-or-operator-) `||` také vypočítá logické nebo jeho operandy, ale nevyhodnotí operand pravého operandu, je-li operand na levé straně vyhodnocen `true` .</span><span class="sxs-lookup"><span data-stu-id="20221-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="20221-138">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `|` operátor vypočítá [bitovou logickou nebo](bitwise-and-shift-operators.md#logical-or-operator-) jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a><span data-ttu-id="20221-139">Podmíněný logický operátor AND&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="20221-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="20221-140">Podmíněný logický operátor AND `&&` , označovaný také jako "" krátkodobého okruhu ", je vypočítán logický operátor a jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="20221-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="20221-141">Výsledek je, `x && y` `true` Pokud je `x` a `y` vyhodnocen jako `true` .</span><span class="sxs-lookup"><span data-stu-id="20221-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="20221-142">V opačném případě je výsledkem `false` .</span><span class="sxs-lookup"><span data-stu-id="20221-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="20221-143">Pokud se `x` vyhodnotí jako `false` , `y` nevyhodnotí se.</span><span class="sxs-lookup"><span data-stu-id="20221-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="20221-144">V následujícím příkladu je pravý operand `&&` operátoru volání metody, které není provedeno, je-li operand na levé straně vyhodnocen jako `false` :</span><span class="sxs-lookup"><span data-stu-id="20221-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="20221-145">[Logický operátor and](#logical-and-operator-) `&` také VYPOČÍTÁ logickou a jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="20221-146">Podmíněný logický operátor OR | |</span><span class="sxs-lookup"><span data-stu-id="20221-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="20221-147">Podmíněný logický operátor OR `||` , označovaný také jako "" krátkodobého "logického okruhu, vypočítá logické nebo jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="20221-148">Výsledek je v `x || y` případě, že je `true` buď `x` nebo `y` vyhodnocen jako `true` .</span><span class="sxs-lookup"><span data-stu-id="20221-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="20221-149">V opačném případě je výsledkem `false` .</span><span class="sxs-lookup"><span data-stu-id="20221-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="20221-150">Pokud se `x` vyhodnotí jako `true` , `y` nevyhodnotí se.</span><span class="sxs-lookup"><span data-stu-id="20221-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="20221-151">V následujícím příkladu je pravý operand `||` operátoru volání metody, které není provedeno, je-li operand na levé straně vyhodnocen jako `true` :</span><span class="sxs-lookup"><span data-stu-id="20221-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="20221-152">[Logický operátor OR](#logical-or-operator-) `|` také vypočítá logické nebo jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="20221-153">Logické operátory s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="20221-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="20221-154">U `bool?` operandů operátory [ `&` (Logical a)](#logical-and-operator-) a [ `|` (Logical a)](#logical-or-operator-) podporují logiku se třemi hodnotami takto:</span><span class="sxs-lookup"><span data-stu-id="20221-154">For `bool?` operands, the [`&` (logical AND)](#logical-and-operator-) and [`|` (logical OR)](#logical-or-operator-) operators support the three-valued logic as follows:</span></span>

- <span data-ttu-id="20221-155">`&`Operátor vytvoří `true` pouze v případě, že se na jeho operandy vyhodnotí `true` .</span><span class="sxs-lookup"><span data-stu-id="20221-155">The `&` operator produces `true` only if both its operands evaluate to `true`.</span></span> <span data-ttu-id="20221-156">Pokud je `x` nebo `y` vyhodnocena jako `false` , `x & y` vytvoří (i když se `false` jiný operand vyhodnocuje `null` ).</span><span class="sxs-lookup"><span data-stu-id="20221-156">If either `x` or `y` evaluates to `false`, `x & y` produces `false` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="20221-157">V opačném případě výsledek `x & y` je `null` .</span><span class="sxs-lookup"><span data-stu-id="20221-157">Otherwise, the result of `x & y` is `null`.</span></span>

- <span data-ttu-id="20221-158">`|`Operátor vytvoří `false` pouze v případě, že se na jeho operandy vyhodnotí `false` .</span><span class="sxs-lookup"><span data-stu-id="20221-158">The `|` operator produces `false` only if both its operands evaluate to `false`.</span></span> <span data-ttu-id="20221-159">Pokud je `x` nebo `y` vyhodnocena jako `true` , `x | y` vytvoří (i když se `true` jiný operand vyhodnocuje `null` ).</span><span class="sxs-lookup"><span data-stu-id="20221-159">If either `x` or `y` evaluates to `true`, `x | y` produces `true` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="20221-160">V opačném případě výsledek `x | y` je `null` .</span><span class="sxs-lookup"><span data-stu-id="20221-160">Otherwise, the result of `x | y` is `null`.</span></span>

<span data-ttu-id="20221-161">Následující tabulka uvádí sémantiku:</span><span class="sxs-lookup"><span data-stu-id="20221-161">The following table presents that semantics:</span></span>

|<span data-ttu-id="20221-162">x</span><span class="sxs-lookup"><span data-stu-id="20221-162">x</span></span>|<span data-ttu-id="20221-163">y</span><span class="sxs-lookup"><span data-stu-id="20221-163">y</span></span>|<span data-ttu-id="20221-164">x&y</span><span class="sxs-lookup"><span data-stu-id="20221-164">x&y</span></span>|<span data-ttu-id="20221-165">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="20221-165">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="20221-166">true</span><span class="sxs-lookup"><span data-stu-id="20221-166">true</span></span>|<span data-ttu-id="20221-167">true</span><span class="sxs-lookup"><span data-stu-id="20221-167">true</span></span>|<span data-ttu-id="20221-168">true</span><span class="sxs-lookup"><span data-stu-id="20221-168">true</span></span>|<span data-ttu-id="20221-169">true</span><span class="sxs-lookup"><span data-stu-id="20221-169">true</span></span>|  
|<span data-ttu-id="20221-170">true</span><span class="sxs-lookup"><span data-stu-id="20221-170">true</span></span>|<span data-ttu-id="20221-171">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-171">false</span></span>|<span data-ttu-id="20221-172">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-172">false</span></span>|<span data-ttu-id="20221-173">true</span><span class="sxs-lookup"><span data-stu-id="20221-173">true</span></span>|  
|<span data-ttu-id="20221-174">true</span><span class="sxs-lookup"><span data-stu-id="20221-174">true</span></span>|<span data-ttu-id="20221-175">null</span><span class="sxs-lookup"><span data-stu-id="20221-175">null</span></span>|<span data-ttu-id="20221-176">null</span><span class="sxs-lookup"><span data-stu-id="20221-176">null</span></span>|<span data-ttu-id="20221-177">true</span><span class="sxs-lookup"><span data-stu-id="20221-177">true</span></span>|  
|<span data-ttu-id="20221-178">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-178">false</span></span>|<span data-ttu-id="20221-179">true</span><span class="sxs-lookup"><span data-stu-id="20221-179">true</span></span>|<span data-ttu-id="20221-180">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-180">false</span></span>|<span data-ttu-id="20221-181">true</span><span class="sxs-lookup"><span data-stu-id="20221-181">true</span></span>|  
|<span data-ttu-id="20221-182">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-182">false</span></span>|<span data-ttu-id="20221-183">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-183">false</span></span>|<span data-ttu-id="20221-184">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-184">false</span></span>|<span data-ttu-id="20221-185">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-185">false</span></span>|  
|<span data-ttu-id="20221-186">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-186">false</span></span>|<span data-ttu-id="20221-187">null</span><span class="sxs-lookup"><span data-stu-id="20221-187">null</span></span>|<span data-ttu-id="20221-188">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-188">false</span></span>|<span data-ttu-id="20221-189">null</span><span class="sxs-lookup"><span data-stu-id="20221-189">null</span></span>|  
|<span data-ttu-id="20221-190">null</span><span class="sxs-lookup"><span data-stu-id="20221-190">null</span></span>|<span data-ttu-id="20221-191">true</span><span class="sxs-lookup"><span data-stu-id="20221-191">true</span></span>|<span data-ttu-id="20221-192">null</span><span class="sxs-lookup"><span data-stu-id="20221-192">null</span></span>|<span data-ttu-id="20221-193">true</span><span class="sxs-lookup"><span data-stu-id="20221-193">true</span></span>|  
|<span data-ttu-id="20221-194">null</span><span class="sxs-lookup"><span data-stu-id="20221-194">null</span></span>|<span data-ttu-id="20221-195">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-195">false</span></span>|<span data-ttu-id="20221-196">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="20221-196">false</span></span>|<span data-ttu-id="20221-197">null</span><span class="sxs-lookup"><span data-stu-id="20221-197">null</span></span>|  
|<span data-ttu-id="20221-198">null</span><span class="sxs-lookup"><span data-stu-id="20221-198">null</span></span>|<span data-ttu-id="20221-199">null</span><span class="sxs-lookup"><span data-stu-id="20221-199">null</span></span>|<span data-ttu-id="20221-200">null</span><span class="sxs-lookup"><span data-stu-id="20221-200">null</span></span>|<span data-ttu-id="20221-201">null</span><span class="sxs-lookup"><span data-stu-id="20221-201">null</span></span>|  

<span data-ttu-id="20221-202">Chování těchto operátorů se liší od typického chování operátoru s typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="20221-202">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="20221-203">Obvykle operátor, který je definován pro operandy typu hodnoty, lze také použít s operandy odpovídajícího typu hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="20221-203">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="20221-204">Takový operátor vytvoří, `null` Pokud se některý z jeho operandů vyhodnotí jako `null` .</span><span class="sxs-lookup"><span data-stu-id="20221-204">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="20221-205">Nicméně `&` `|` operátory a mohou vygenerovat jinou hodnotu než null, i když je jeden z operandů vyhodnocen jako `null` .</span><span class="sxs-lookup"><span data-stu-id="20221-205">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="20221-206">Další informace o chování operátora s povolenými typy hodnot s možnou hodnotou null naleznete v části "předané [operátory](../builtin-types/nullable-value-types.md#lifted-operators) " v článku [typy s možnou hodnotou null](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="20221-206">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="20221-207">Operátory a lze také použít `!` `^` s `bool?` operandy, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="20221-207">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="20221-208">Podmíněné logické operátory `&&` a `||` nepodporují `bool?` operandy.</span><span class="sxs-lookup"><span data-stu-id="20221-208">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="20221-209">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="20221-209">Compound assignment</span></span>

<span data-ttu-id="20221-210">Pro binární operátor `op` , výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="20221-210">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="20221-211">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="20221-211">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="20221-212">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="20221-212">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="20221-213">`&`Operátory, `|` a `^` podporují složené přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="20221-213">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="20221-214">Podmíněné logické operátory `&&` a `||` nepodporují složené přiřazení.</span><span class="sxs-lookup"><span data-stu-id="20221-214">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="20221-215">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="20221-215">Operator precedence</span></span>

<span data-ttu-id="20221-216">Následující seznam uvádí logické operátory od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="20221-216">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="20221-217">Logický operátor negace`!`</span><span class="sxs-lookup"><span data-stu-id="20221-217">Logical negation operator `!`</span></span>
- <span data-ttu-id="20221-218">Logický operátor AND`&`</span><span class="sxs-lookup"><span data-stu-id="20221-218">Logical AND operator `&`</span></span>
- <span data-ttu-id="20221-219">Logický exkluzivní operátor OR`^`</span><span class="sxs-lookup"><span data-stu-id="20221-219">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="20221-220">Logický operátor OR`|`</span><span class="sxs-lookup"><span data-stu-id="20221-220">Logical OR operator `|`</span></span>
- <span data-ttu-id="20221-221">Podmíněný logický operátor AND`&&`</span><span class="sxs-lookup"><span data-stu-id="20221-221">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="20221-222">Podmíněný logický operátor OR`||`</span><span class="sxs-lookup"><span data-stu-id="20221-222">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="20221-223">Pomocí závorek `()` můžete změnit pořadí vyhodnocování stanovené předností operátorů:</span><span class="sxs-lookup"><span data-stu-id="20221-223">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="20221-224">Úplný seznam operátorů jazyka C# seřazených podle priority úrovně naleznete v části [Priorita operátorů](index.md#operator-precedence) v článku [operátory jazyka c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="20221-224">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="20221-225">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="20221-225">Operator overloadability</span></span>

<span data-ttu-id="20221-226">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `!` `&` operátory,, a `|` `^` .</span><span class="sxs-lookup"><span data-stu-id="20221-226">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="20221-227">Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="20221-227">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="20221-228">Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="20221-228">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="20221-229">Uživatelsky definovaný typ nemůže přetížit Podmíněné logické operátory `&&` a `||` .</span><span class="sxs-lookup"><span data-stu-id="20221-229">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="20221-230">Pokud však uživatelsky definovaný typ přetěžuje [operátory true a false](true-false-operators.md) a `&` `|` operátor OR určitým způsobem, `&&` `||` může být operace nebo v uvedeném pořadí vyhodnocena pro operandy daného typu.</span><span class="sxs-lookup"><span data-stu-id="20221-230">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="20221-231">Další informace naleznete v části [Podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="20221-231">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="20221-232">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="20221-232">C# language specification</span></span>

<span data-ttu-id="20221-233">Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="20221-233">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="20221-234">Logický operátor negace</span><span class="sxs-lookup"><span data-stu-id="20221-234">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="20221-235">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="20221-235">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="20221-236">Podmíněné logické operátory</span><span class="sxs-lookup"><span data-stu-id="20221-236">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="20221-237">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="20221-237">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="20221-238">Viz také</span><span class="sxs-lookup"><span data-stu-id="20221-238">See also</span></span>

- [<span data-ttu-id="20221-239">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="20221-239">C# reference</span></span>](../index.md)
- [<span data-ttu-id="20221-240">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="20221-240">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="20221-241">Bitové operátory a operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="20221-241">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
