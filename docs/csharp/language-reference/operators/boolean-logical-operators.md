---
title: Logické operátory logické hodnoty - odkaz jazyka C#
description: Další informace o operátorech jazyka C#, které provádějí logické negace, konjunkce (AND) a včetně a výhradní chod (OR) operace s logickými operandy.
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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399495"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="ae41d-103">Logické operátory logické položky (odkaz Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ae41d-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="ae41d-104">Následující operátory provádějí logické operace s [buč](../builtin-types/bool.md) operandy:</span><span class="sxs-lookup"><span data-stu-id="ae41d-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="ae41d-105">Unární [ `!` (logické negace)](#logical-negation-operator-) operátor.</span><span class="sxs-lookup"><span data-stu-id="ae41d-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="ae41d-106">Binární [ `&` (logické AND)](#logical-and-operator-) [ `|` , (logické OR)](#logical-or-operator-)a [ `^` (logické výhradní OR)](#logical-exclusive-or-operator-) operátory.</span><span class="sxs-lookup"><span data-stu-id="ae41d-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="ae41d-107">Tyto operátory vždy vyhodnocují oba operandy.</span><span class="sxs-lookup"><span data-stu-id="ae41d-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="ae41d-108">Binární [ `&&` (podmíněné logické OPERÁTORy)](#conditional-logical-and-operator-) a [ `||` (podmíněné logické OPERÁTORy).](#conditional-logical-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="ae41d-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="ae41d-109">Tyto operátory vyhodnocují pravostranný operand pouze v případě, že je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="ae41d-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="ae41d-110">Pro operandy [integrálníčíselné typy](../builtin-types/integral-numeric-types.md), `&`, `|`a `^` operátory provádět bitové logické operace.</span><span class="sxs-lookup"><span data-stu-id="ae41d-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="ae41d-111">Další informace naleznete v tématu [Bitwise and shift operators](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ae41d-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="ae41d-112">Logický operátor negace !</span><span class="sxs-lookup"><span data-stu-id="ae41d-112">Logical negation operator !</span></span>

<span data-ttu-id="ae41d-113">Unární prefix `!` operátor vypočítá logické negace jeho operand.</span><span class="sxs-lookup"><span data-stu-id="ae41d-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="ae41d-114">To znamená, že `true`vytvoří , pokud operand vyhodnotí `false`na , a `false`, pokud operand vyhodnotí: `true`</span><span class="sxs-lookup"><span data-stu-id="ae41d-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="ae41d-115">Počínaje C# 8.0, unární `!` přípona operátor je [null odpouštějící operátor](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="ae41d-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="ae41d-116">Logický operátor AND&amp;</span><span class="sxs-lookup"><span data-stu-id="ae41d-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="ae41d-117">Operátor `&` vypočítá logické AND jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="ae41d-118">Výsledkem `x & y` je `true` if `x` `y` both `true`a vyhodnotit na .</span><span class="sxs-lookup"><span data-stu-id="ae41d-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="ae41d-119">V opačném případě `false`je výsledkem .</span><span class="sxs-lookup"><span data-stu-id="ae41d-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="ae41d-120">Operátor `&` vyhodnotí oba operandy i v případě, `false`že levá operand `false` vyhodnotí do , tak, aby výsledek operace je bez ohledu na hodnotu pravéoperand.</span><span class="sxs-lookup"><span data-stu-id="ae41d-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="ae41d-121">V následujícím příkladu je pravostranný `&` operand operátoru volání metody, které se provádí bez ohledu na hodnotu levého operandu:</span><span class="sxs-lookup"><span data-stu-id="ae41d-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="ae41d-122">[Podmíněný logický operátor](#conditional-logical-and-operator-) `&&` AND také vypočítá logické and jeho operandů, ale nevyhodnotí pravé operand, pokud levá `false`operand vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="ae41d-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="ae41d-123">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `&` operátor vypočítá [bitové logické and](bitwise-and-shift-operators.md#logical-and-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="ae41d-124">Unární `&` operátor je [operátor adresy](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="ae41d-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="ae41d-125">Logický výhradní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="ae41d-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="ae41d-126">Operátor `^` vypočítá logické výhradní NEBO, označované také jako logické XOR, jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="ae41d-127">Výsledkem `x ^ y` `true` je, `x` pokud `true` vyhodnotí `y` a `x` vyhodnotí `false` `y` `false`, nebo `true`vyhodnotí a vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="ae41d-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="ae41d-128">V opačném případě `false`je výsledkem .</span><span class="sxs-lookup"><span data-stu-id="ae41d-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ae41d-129">To znamená, `bool` že pro operandy `^` operátor vypočítá stejný výsledek jako operátor `!=` [nerovnosti](equality-operators.md#inequality-operator-) .</span><span class="sxs-lookup"><span data-stu-id="ae41d-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="ae41d-130">Pro operandy [integrálníčíselné typy](../builtin-types/integral-numeric-types.md)operátor `^` vypočítá [bitové logické exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="ae41d-131">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="ae41d-131">Logical OR operator |</span></span>

<span data-ttu-id="ae41d-132">Operátor `|` vypočítá logické OR jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="ae41d-133">Výsledkem `x | y` `true` je, `x` pokud `y` buď `true`nebo vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="ae41d-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="ae41d-134">V opačném případě `false`je výsledkem .</span><span class="sxs-lookup"><span data-stu-id="ae41d-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="ae41d-135">Operátor `|` vyhodnotí oba operandy i v případě, `true`že levá operand `true` vyhodnotí do , tak, aby výsledek operace je bez ohledu na hodnotu pravéoperand.</span><span class="sxs-lookup"><span data-stu-id="ae41d-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="ae41d-136">V následujícím příkladu je pravostranný `|` operand operátoru volání metody, které se provádí bez ohledu na hodnotu levého operandu:</span><span class="sxs-lookup"><span data-stu-id="ae41d-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="ae41d-137">[Podmíněný logický operátor](#conditional-logical-or-operator-) `||` OR také vypočítá logický operátor OR svých operandů, ale nevyhodnotí pravostranný operand, `true`pokud se levá operand vyhodnotí na .</span><span class="sxs-lookup"><span data-stu-id="ae41d-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="ae41d-138">Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `|` operátor vypočítá [bitové logické OR](bitwise-and-shift-operators.md#logical-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="ae41d-139">Podmíněný logický operátor AND&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="ae41d-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="ae41d-140">Podmíněný logický operátor `&&`AND , označovaný také jako logický operátor AND "short-circuiting", vypočítá logické and jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="ae41d-141">Výsledkem `x && y` je `true` if `x` `y` both `true`a vyhodnotit na .</span><span class="sxs-lookup"><span data-stu-id="ae41d-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="ae41d-142">V opačném případě `false`je výsledkem .</span><span class="sxs-lookup"><span data-stu-id="ae41d-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ae41d-143">Pokud `x` je `false`vyhodnocena do , `y` není vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="ae41d-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="ae41d-144">V následujícím příkladu je pravostranný `&&` operand operátoru volání metody, které se neprovádí, pokud `false`se levá operand vyhodnotí na :</span><span class="sxs-lookup"><span data-stu-id="ae41d-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="ae41d-145">Logický [operátor](#logical-and-operator-) `&` AND také vypočítá logické and jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="ae41d-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="ae41d-146">Podmíněný logický operátor OR ||</span><span class="sxs-lookup"><span data-stu-id="ae41d-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="ae41d-147">Podmíněný logický operátor `||`OR , označovaný také jako logický operátor OR "short-circuiting", vypočítá logický operátor OR jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="ae41d-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="ae41d-148">Výsledkem `x || y` `true` je, `x` pokud `y` buď `true`nebo vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="ae41d-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="ae41d-149">V opačném případě `false`je výsledkem .</span><span class="sxs-lookup"><span data-stu-id="ae41d-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ae41d-150">Pokud `x` je `true`vyhodnocena do , `y` není vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="ae41d-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="ae41d-151">V následujícím příkladu je pravostranný `||` operand operátoru volání metody, které se neprovádí, pokud `true`se levá operand vyhodnotí na :</span><span class="sxs-lookup"><span data-stu-id="ae41d-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="ae41d-152">[Logický operátor](#logical-or-operator-) `|` OR také vypočítá logický operátor OR svých operandů, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="ae41d-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="ae41d-153">Logické operátory logické hodnoty null</span><span class="sxs-lookup"><span data-stu-id="ae41d-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="ae41d-154">Pro `bool?` operandy `&` a `|` operátory podporují logiku se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="ae41d-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="ae41d-155">Sémantiku těchto operátorů je definována následující tabulkou:</span><span class="sxs-lookup"><span data-stu-id="ae41d-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="ae41d-156">x</span><span class="sxs-lookup"><span data-stu-id="ae41d-156">x</span></span>|<span data-ttu-id="ae41d-157">y</span><span class="sxs-lookup"><span data-stu-id="ae41d-157">y</span></span>|<span data-ttu-id="ae41d-158">x&y</span><span class="sxs-lookup"><span data-stu-id="ae41d-158">x&y</span></span>|<span data-ttu-id="ae41d-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="ae41d-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="ae41d-160">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-160">true</span></span>|<span data-ttu-id="ae41d-161">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-161">true</span></span>|<span data-ttu-id="ae41d-162">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-162">true</span></span>|<span data-ttu-id="ae41d-163">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-163">true</span></span>|  
|<span data-ttu-id="ae41d-164">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-164">true</span></span>|<span data-ttu-id="ae41d-165">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-165">false</span></span>|<span data-ttu-id="ae41d-166">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-166">false</span></span>|<span data-ttu-id="ae41d-167">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-167">true</span></span>|  
|<span data-ttu-id="ae41d-168">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-168">true</span></span>|<span data-ttu-id="ae41d-169">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-169">null</span></span>|<span data-ttu-id="ae41d-170">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-170">null</span></span>|<span data-ttu-id="ae41d-171">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-171">true</span></span>|  
|<span data-ttu-id="ae41d-172">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-172">false</span></span>|<span data-ttu-id="ae41d-173">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-173">true</span></span>|<span data-ttu-id="ae41d-174">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-174">false</span></span>|<span data-ttu-id="ae41d-175">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-175">true</span></span>|  
|<span data-ttu-id="ae41d-176">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-176">false</span></span>|<span data-ttu-id="ae41d-177">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-177">false</span></span>|<span data-ttu-id="ae41d-178">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-178">false</span></span>|<span data-ttu-id="ae41d-179">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-179">false</span></span>|  
|<span data-ttu-id="ae41d-180">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-180">false</span></span>|<span data-ttu-id="ae41d-181">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-181">null</span></span>|<span data-ttu-id="ae41d-182">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-182">false</span></span>|<span data-ttu-id="ae41d-183">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-183">null</span></span>|  
|<span data-ttu-id="ae41d-184">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-184">null</span></span>|<span data-ttu-id="ae41d-185">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-185">true</span></span>|<span data-ttu-id="ae41d-186">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-186">null</span></span>|<span data-ttu-id="ae41d-187">true</span><span class="sxs-lookup"><span data-stu-id="ae41d-187">true</span></span>|  
|<span data-ttu-id="ae41d-188">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-188">null</span></span>|<span data-ttu-id="ae41d-189">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-189">false</span></span>|<span data-ttu-id="ae41d-190">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="ae41d-190">false</span></span>|<span data-ttu-id="ae41d-191">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-191">null</span></span>|  
|<span data-ttu-id="ae41d-192">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-192">null</span></span>|<span data-ttu-id="ae41d-193">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-193">null</span></span>|<span data-ttu-id="ae41d-194">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-194">null</span></span>|<span data-ttu-id="ae41d-195">null</span><span class="sxs-lookup"><span data-stu-id="ae41d-195">null</span></span>|  

<span data-ttu-id="ae41d-196">Chování těchto operátorů se liší od typické chování operátoru s typy hodnot s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ae41d-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="ae41d-197">Operátor, který je definován pro operandy typu hodnoty, lze obvykle použít také s operandy odpovídajícího typu hodnoty s možnou hodnotou, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="ae41d-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="ae41d-198">Takový operátor vyprodukuje, `null` pokud některý z `null`jeho operandů vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="ae41d-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="ae41d-199">Však `&` a `|` operátory můžete vyrábět nenull i v případě, `null`že jeden z operandů vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="ae41d-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="ae41d-200">Další informace o chování operátoru s typy hodnot s možnou hodnotou s hodnotou null naleznete v části [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) v článku [Typy hodnot S možnou hodnotou Null.](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="ae41d-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="ae41d-201">Můžete také použít `!` `^` a `bool?` operátory s operandy, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ae41d-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="ae41d-202">Podmíněné logické `&&` `||` operátory a `bool?` nepodporují operandy.</span><span class="sxs-lookup"><span data-stu-id="ae41d-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ae41d-203">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="ae41d-203">Compound assignment</span></span>

<span data-ttu-id="ae41d-204">Pro binární `op`operátor , složený výraz přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="ae41d-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ae41d-205">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="ae41d-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ae41d-206">kromě `x` toho, že se vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="ae41d-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ae41d-207">Složené `&` `|`přiřazení `^` podporují , a operátory, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ae41d-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="ae41d-208">Podmíněné logické `&&` `||` operátory a nepodporují složené přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ae41d-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="ae41d-209">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="ae41d-209">Operator precedence</span></span>

<span data-ttu-id="ae41d-210">Následující seznam seřídí logické operátory od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="ae41d-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="ae41d-211">Logický operátor negace`!`</span><span class="sxs-lookup"><span data-stu-id="ae41d-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="ae41d-212">Logický operátor AND`&`</span><span class="sxs-lookup"><span data-stu-id="ae41d-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="ae41d-213">Logický výhradní operátor OR`^`</span><span class="sxs-lookup"><span data-stu-id="ae41d-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="ae41d-214">Logický operátor OR`|`</span><span class="sxs-lookup"><span data-stu-id="ae41d-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="ae41d-215">Podmíněný logický operátor AND`&&`</span><span class="sxs-lookup"><span data-stu-id="ae41d-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="ae41d-216">Podmíněný logický operátor OR`||`</span><span class="sxs-lookup"><span data-stu-id="ae41d-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="ae41d-217">Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru:</span><span class="sxs-lookup"><span data-stu-id="ae41d-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="ae41d-218">Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="ae41d-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ae41d-219">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="ae41d-219">Operator overloadability</span></span>

<span data-ttu-id="ae41d-220">Uživatelem definovaný typ může `!` `&` `|` [přetížit](operator-overloading.md) , , , a `^` operátory.</span><span class="sxs-lookup"><span data-stu-id="ae41d-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="ae41d-221">Když je přetížený binární operátor, odpovídající složený operátor přiřazení je také implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="ae41d-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="ae41d-222">Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ae41d-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="ae41d-223">Uživatelem definovaný typ nemůže přetížit podmíněné logické operátory `&&` a `||`.</span><span class="sxs-lookup"><span data-stu-id="ae41d-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="ae41d-224">Pokud však uživatelem definovaný typ určitým způsobem přetíží [operátory true a false](true-false-operators.md) a operátor `&` nebo, `|` může být `&&` operace nebo `||` operace vyhodnocena pro operandy tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="ae41d-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="ae41d-225">Další informace naleznete v části [Uživatelem definované podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ae41d-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ae41d-226">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae41d-226">C# language specification</span></span>

<span data-ttu-id="ae41d-227">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="ae41d-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="ae41d-228">Logický operátor negace</span><span class="sxs-lookup"><span data-stu-id="ae41d-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="ae41d-229">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="ae41d-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="ae41d-230">Podmíněné logické operátory</span><span class="sxs-lookup"><span data-stu-id="ae41d-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="ae41d-231">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="ae41d-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="ae41d-232">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae41d-232">See also</span></span>

- [<span data-ttu-id="ae41d-233">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="ae41d-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ae41d-234">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae41d-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="ae41d-235">Bitové operátory a operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="ae41d-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
