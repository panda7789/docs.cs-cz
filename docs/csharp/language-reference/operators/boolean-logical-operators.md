---
title: Logické logické operátory – C# referenční informace
description: Přečtěte C# si o operátorech, které provádějí logické negace, spojení (a) a včetně a exkluzivní operace disjunkce (nebo) s logickými operandy.
ms.date: 09/27/2019
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
ms.openlocfilehash: 4a3e6986060b8e22d49110b8b9f275f41b743af2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036396"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="a6153-103">Logické logické operátory (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="a6153-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="a6153-104">Následující operátory provádějí logické [operace s](../keywords/bool.md) logickými operandy:</span><span class="sxs-lookup"><span data-stu-id="a6153-104">The following operators perform logical operations with [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="a6153-105">Unární operátor [`!` (logická negace)](#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="a6153-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="a6153-106">Binární [`&` (Logical and)](#logical-and-operator-), [`|` (Logical or)](#logical-or-operator-)a [`^` (Logical or)](#logical-exclusive-or-operator-) Operators.</span><span class="sxs-lookup"><span data-stu-id="a6153-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="a6153-107">Tyto operátory vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="a6153-108">Binární [`&&` (podmíněný logický operátor and)](#conditional-logical-and-operator-) a [`||` (Podmíněné logické OR)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="a6153-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="a6153-109">Tyto operátory vyhodnotí operand na pravé straně, pokud je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="a6153-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="a6153-110">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)provádí operátory `&`, `|`a `^` bitové logické operace.</span><span class="sxs-lookup"><span data-stu-id="a6153-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="a6153-111">Další informace naleznete v tématu [operátory bitových a posunutí](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a6153-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="a6153-112">Logický operátor negace!</span><span class="sxs-lookup"><span data-stu-id="a6153-112">Logical negation operator !</span></span>

<span data-ttu-id="a6153-113">Unární předpona `!` vypočítá logickou negaci svého operandu.</span><span class="sxs-lookup"><span data-stu-id="a6153-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="a6153-114">To znamená, že vytváří `true`, pokud je operand vyhodnocen jako `false` a `false`, pokud je operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="a6153-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="a6153-115">Počínaje C# 8,0, unární přípona`!`operátor je [operátor null-striktní](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="a6153-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="a6153-116">Logický operátor AND &amp;</span><span class="sxs-lookup"><span data-stu-id="a6153-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="a6153-117">Operátor `&` vypočítá logickou hodnotu a její operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="a6153-118">Výsledek `x & y` je `true`, pokud `x` a `y` se vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a6153-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="a6153-119">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="a6153-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="a6153-120">Operátor `&` vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen jako `false`, aby byl výsledek operace `false` bez ohledu na hodnotu operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="a6153-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="a6153-121">V následujícím příkladu je pravý operand operátoru `&` volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:</span><span class="sxs-lookup"><span data-stu-id="a6153-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="a6153-122">[Podmíněný logický operátor and](#conditional-logical-and-operator-) `&&` také vypočítá logickou a jeho operandy, ale nevyhodnotí pravý operand, pokud je levý operand vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="a6153-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="a6153-123">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)operátor `&` vypočítá [bitovou logickou a](bitwise-and-shift-operators.md#logical-and-operator-) jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="a6153-124">Unární operátor `&` je [operátor address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="a6153-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="a6153-125">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="a6153-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="a6153-126">Operátor `^` vypočítá logickou exkluzivní nebo, označovanou také jako logická XOR, z jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="a6153-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="a6153-127">Výsledek `x ^ y` je `true`, pokud `x` vyhodnocuje `true` a `y` vyhodnocuje jako `false`, nebo `x` vyhodnocuje `false` a `y` vyhodnocuje `true`.</span><span class="sxs-lookup"><span data-stu-id="a6153-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="a6153-128">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="a6153-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="a6153-129">To znamená, že pro operandy `bool` `^` operátor vypočítá stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="a6153-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="a6153-130">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)operátor `^` vypočítá [bitový logický typ Exclusive nebo](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="a6153-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="a6153-131">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="a6153-131">Logical OR operator |</span></span>

<span data-ttu-id="a6153-132">Operátor `|` vypočítá logické nebo jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="a6153-133">Výsledek `x | y` je `true`, pokud je `x` nebo `y` vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a6153-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="a6153-134">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="a6153-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="a6153-135">Operátor `|` vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen jako `true`, aby byl výsledek operace `true` bez ohledu na hodnotu operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="a6153-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="a6153-136">V následujícím příkladu je pravý operand operátoru `|` volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:</span><span class="sxs-lookup"><span data-stu-id="a6153-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="a6153-137">[Podmíněný logický operátor or](#conditional-logical-or-operator-) `||` také vypočítá logickou nebo jeho operandy, ale nevyhodnotí pravý operand, pokud je levý operand vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a6153-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="a6153-138">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)operátor `|` vypočítá [bitovou logickou nebo](bitwise-and-shift-operators.md#logical-or-operator-) jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="a6153-139">Podmíněný &amp;logický operátor AND&amp;</span><span class="sxs-lookup"><span data-stu-id="a6153-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="a6153-140">Podmíněný logický operátor AND `&&`, označovaný také jako "" krátkodobého okruhu ", je vypočítán logický operátor a jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="a6153-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="a6153-141">Výsledek `x && y` je `true`, pokud `x` a `y` se vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a6153-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="a6153-142">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="a6153-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="a6153-143">Pokud `x` se vyhodnotí jako `false`, `y` se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="a6153-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="a6153-144">V následujícím příkladu je pravý operand operátoru `&&` volání metody, které není provedeno, je-li levý operand vyhodnocen jako `false`:</span><span class="sxs-lookup"><span data-stu-id="a6153-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="a6153-145">[Logický operátor and](#logical-and-operator-) `&` také vypočítá logickou a jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="a6153-146">Podmíněný logický operátor OR | |</span><span class="sxs-lookup"><span data-stu-id="a6153-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="a6153-147">Podmíněný logický operátor OR `||`, označovaný také jako "" krátkodobého "logického" operátoru "nebo", vypočítává logickou nebo jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="a6153-148">Výsledek `x || y` je `true`, pokud je `x` nebo `y` vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a6153-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="a6153-149">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="a6153-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="a6153-150">Pokud `x` se vyhodnotí jako `true`, `y` se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="a6153-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="a6153-151">V následujícím příkladu je pravý operand operátoru `||` volání metody, které není provedeno, je-li levý operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="a6153-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="a6153-152">[Logický operátor or](#logical-or-operator-) `|` také VYPOČÍTÁ logické nebo jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="a6153-153">Logické operátory s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="a6153-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="a6153-154">U operandů `bool?` operátor `&` a `|` podporuje logiku se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="a6153-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="a6153-155">Sémantika těchto operátorů je definována v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a6153-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="a6153-156">x</span><span class="sxs-lookup"><span data-stu-id="a6153-156">x</span></span>|<span data-ttu-id="a6153-157">y</span><span class="sxs-lookup"><span data-stu-id="a6153-157">y</span></span>|<span data-ttu-id="a6153-158">x & y</span><span class="sxs-lookup"><span data-stu-id="a6153-158">x&y</span></span>|<span data-ttu-id="a6153-159">×&#124;y</span><span class="sxs-lookup"><span data-stu-id="a6153-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="a6153-160">true</span><span class="sxs-lookup"><span data-stu-id="a6153-160">true</span></span>|<span data-ttu-id="a6153-161">true</span><span class="sxs-lookup"><span data-stu-id="a6153-161">true</span></span>|<span data-ttu-id="a6153-162">true</span><span class="sxs-lookup"><span data-stu-id="a6153-162">true</span></span>|<span data-ttu-id="a6153-163">true</span><span class="sxs-lookup"><span data-stu-id="a6153-163">true</span></span>|  
|<span data-ttu-id="a6153-164">true</span><span class="sxs-lookup"><span data-stu-id="a6153-164">true</span></span>|<span data-ttu-id="a6153-165">false</span><span class="sxs-lookup"><span data-stu-id="a6153-165">false</span></span>|<span data-ttu-id="a6153-166">false</span><span class="sxs-lookup"><span data-stu-id="a6153-166">false</span></span>|<span data-ttu-id="a6153-167">true</span><span class="sxs-lookup"><span data-stu-id="a6153-167">true</span></span>|  
|<span data-ttu-id="a6153-168">true</span><span class="sxs-lookup"><span data-stu-id="a6153-168">true</span></span>|<span data-ttu-id="a6153-169">null</span><span class="sxs-lookup"><span data-stu-id="a6153-169">null</span></span>|<span data-ttu-id="a6153-170">null</span><span class="sxs-lookup"><span data-stu-id="a6153-170">null</span></span>|<span data-ttu-id="a6153-171">true</span><span class="sxs-lookup"><span data-stu-id="a6153-171">true</span></span>|  
|<span data-ttu-id="a6153-172">false</span><span class="sxs-lookup"><span data-stu-id="a6153-172">false</span></span>|<span data-ttu-id="a6153-173">true</span><span class="sxs-lookup"><span data-stu-id="a6153-173">true</span></span>|<span data-ttu-id="a6153-174">false</span><span class="sxs-lookup"><span data-stu-id="a6153-174">false</span></span>|<span data-ttu-id="a6153-175">true</span><span class="sxs-lookup"><span data-stu-id="a6153-175">true</span></span>|  
|<span data-ttu-id="a6153-176">false</span><span class="sxs-lookup"><span data-stu-id="a6153-176">false</span></span>|<span data-ttu-id="a6153-177">false</span><span class="sxs-lookup"><span data-stu-id="a6153-177">false</span></span>|<span data-ttu-id="a6153-178">false</span><span class="sxs-lookup"><span data-stu-id="a6153-178">false</span></span>|<span data-ttu-id="a6153-179">false</span><span class="sxs-lookup"><span data-stu-id="a6153-179">false</span></span>|  
|<span data-ttu-id="a6153-180">false</span><span class="sxs-lookup"><span data-stu-id="a6153-180">false</span></span>|<span data-ttu-id="a6153-181">null</span><span class="sxs-lookup"><span data-stu-id="a6153-181">null</span></span>|<span data-ttu-id="a6153-182">false</span><span class="sxs-lookup"><span data-stu-id="a6153-182">false</span></span>|<span data-ttu-id="a6153-183">null</span><span class="sxs-lookup"><span data-stu-id="a6153-183">null</span></span>|  
|<span data-ttu-id="a6153-184">null</span><span class="sxs-lookup"><span data-stu-id="a6153-184">null</span></span>|<span data-ttu-id="a6153-185">true</span><span class="sxs-lookup"><span data-stu-id="a6153-185">true</span></span>|<span data-ttu-id="a6153-186">null</span><span class="sxs-lookup"><span data-stu-id="a6153-186">null</span></span>|<span data-ttu-id="a6153-187">true</span><span class="sxs-lookup"><span data-stu-id="a6153-187">true</span></span>|  
|<span data-ttu-id="a6153-188">null</span><span class="sxs-lookup"><span data-stu-id="a6153-188">null</span></span>|<span data-ttu-id="a6153-189">false</span><span class="sxs-lookup"><span data-stu-id="a6153-189">false</span></span>|<span data-ttu-id="a6153-190">false</span><span class="sxs-lookup"><span data-stu-id="a6153-190">false</span></span>|<span data-ttu-id="a6153-191">null</span><span class="sxs-lookup"><span data-stu-id="a6153-191">null</span></span>|  
|<span data-ttu-id="a6153-192">null</span><span class="sxs-lookup"><span data-stu-id="a6153-192">null</span></span>|<span data-ttu-id="a6153-193">null</span><span class="sxs-lookup"><span data-stu-id="a6153-193">null</span></span>|<span data-ttu-id="a6153-194">null</span><span class="sxs-lookup"><span data-stu-id="a6153-194">null</span></span>|<span data-ttu-id="a6153-195">null</span><span class="sxs-lookup"><span data-stu-id="a6153-195">null</span></span>|  

<span data-ttu-id="a6153-196">Chování těchto operátorů se liší od typického chování operátoru s typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a6153-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="a6153-197">Obvykle operátor, který je definován pro operandy typu hodnoty, lze také použít s operandy odpovídajícího typu hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a6153-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="a6153-198">Takový operátor vytvoří `null`, pokud se některý z jeho operandů vyhodnocuje jako `null`.</span><span class="sxs-lookup"><span data-stu-id="a6153-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="a6153-199">Operátory `&` a `|` však mohou vygenerovat jinou hodnotu než null, i když je jeden z operandů vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="a6153-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="a6153-200">Další informace o chování operátora s typy hodnot s možnou hodnotou null naleznete v části [operátory](../../programming-guide/nullable-types/using-nullable-types.md#operators) v článku [použití hodnot s možnou hodnotou null](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="a6153-200">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="a6153-201">Můžete také použít operátory `!` a `^` s `bool?` operandy, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a6153-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="a6153-202">Podmíněné logické operátory `&&` a `||` nepodporují `bool?` operandy.</span><span class="sxs-lookup"><span data-stu-id="a6153-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="a6153-203">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="a6153-203">Compound assignment</span></span>

<span data-ttu-id="a6153-204">Pro binární operátor `op` se složený výraz přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="a6153-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="a6153-205">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="a6153-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="a6153-206">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a6153-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="a6153-207">Operátory `&`, `|`a `^` podporují složené přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a6153-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="a6153-208">Podmíněné logické operátory `&&` a `||` nepodporují složené přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a6153-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="a6153-209">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="a6153-209">Operator precedence</span></span>

<span data-ttu-id="a6153-210">Následující seznam uvádí logické operátory od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="a6153-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="a6153-211">Logický operátor negace `!`</span><span class="sxs-lookup"><span data-stu-id="a6153-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="a6153-212">Logický operátor AND `&`</span><span class="sxs-lookup"><span data-stu-id="a6153-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="a6153-213">`^` logický exkluzivní operátor OR</span><span class="sxs-lookup"><span data-stu-id="a6153-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="a6153-214">Logický operátor OR `|`</span><span class="sxs-lookup"><span data-stu-id="a6153-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="a6153-215">Podmíněný `&&` logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="a6153-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="a6153-216">Podmíněný logický operátor OR `||`</span><span class="sxs-lookup"><span data-stu-id="a6153-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="a6153-217">Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů, použijte závorky `()`:</span><span class="sxs-lookup"><span data-stu-id="a6153-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="a6153-218">Úplný seznam C# operátorů seřazených podle priority najdete v části [Priorita operátorů](index.md#operator-precedence) [ C# v článku věnovaném operátorům](index.md) .</span><span class="sxs-lookup"><span data-stu-id="a6153-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a6153-219">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="a6153-219">Operator overloadability</span></span>

<span data-ttu-id="a6153-220">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `!`, `&`, `|`a `^`.</span><span class="sxs-lookup"><span data-stu-id="a6153-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="a6153-221">Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a6153-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="a6153-222">Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a6153-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="a6153-223">Uživatelsky definovaný typ nemůže přetížit Podmíněné logické operátory `&&` a `||`.</span><span class="sxs-lookup"><span data-stu-id="a6153-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="a6153-224">Pokud však uživatelsky definovaný typ přetěžuje [operátory true a false](true-false-operators.md) a `&` nebo `|` nějakým způsobem, může být pro operandy daného typu vyhodnocena operace `&&` nebo `||`.</span><span class="sxs-lookup"><span data-stu-id="a6153-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="a6153-225">Další informace naleznete v části [uživatelsky definované Podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a6153-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a6153-226">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a6153-226">C# language specification</span></span>

<span data-ttu-id="a6153-227">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a6153-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a6153-228">Logický operátor negace</span><span class="sxs-lookup"><span data-stu-id="a6153-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="a6153-229">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="a6153-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="a6153-230">Podmíněné logické operátory</span><span class="sxs-lookup"><span data-stu-id="a6153-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="a6153-231">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="a6153-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="a6153-232">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6153-232">See also</span></span>

- [<span data-ttu-id="a6153-233">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="a6153-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a6153-234">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a6153-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="a6153-235">Bitové operátory a posunutí</span><span class="sxs-lookup"><span data-stu-id="a6153-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
