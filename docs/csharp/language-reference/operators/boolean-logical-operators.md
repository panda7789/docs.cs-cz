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
ms.openlocfilehash: cc25d4bfd444dc0acb30fc1c6e6c3c9918af537c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698685"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="c4ccd-103">Logické logické operátory (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="c4ccd-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="c4ccd-104">Následující operátory provádějí logické operace [s logickými operandy](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="c4ccd-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="c4ccd-105">Unární operátor [`!` (logická negace)](#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="c4ccd-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="c4ccd-106">Binary [`&` (Logical and)](#logical-and-operator-), [`|` (Logical or)](#logical-or-operator-)a [`^` (logické vyhrazené operátory OR)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="c4ccd-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="c4ccd-107">Tyto operátory vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="c4ccd-108">Binární [`&&` (podmíněný logický operátor and)](#conditional-logical-and-operator-) a [`||` (Podmíněné logické OR)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="c4ccd-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="c4ccd-109">Tyto operátory vyhodnotí operand na pravé straně, pokud je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="c4ccd-110">Pro operandy [integrálních](../builtin-types/integral-numeric-types.md) typů provádí operátory `&`, `|` a `^` bitové logické operace.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="c4ccd-111">Další informace naleznete v tématu [operátory bitových a posunutí](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c4ccd-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="c4ccd-112">Logický operátor negace!</span><span class="sxs-lookup"><span data-stu-id="c4ccd-112">Logical negation operator !</span></span>

<span data-ttu-id="c4ccd-113">Operátor `!` vypočítá logickou negaci svého operandu.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="c4ccd-114">To znamená, že vytváří `true`, pokud je operand vyhodnocen jako `false` a `false`, pokud je operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="c4ccd-115">Počínaje C# 8,0, unární přípona @no__t operátor-1 je operátor null-striktní.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-115">Starting with C# 8.0, the unary postfix `!` operator is a null-forgiving operator.</span></span> <span data-ttu-id="c4ccd-116">V povoleném kontextu anotace s možnou hodnotou null je použit k deklaraci, že výraz `x` typu odkazu s možnou hodnotou null není null: `x!`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-116">In an enabled nullable annotation context, you use it to declare that expression `x` of a nullable reference type isn't null: `x!`.</span></span> <span data-ttu-id="c4ccd-117">Další informace naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="c4ccd-117">For more information, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="c4ccd-118">Logický operátor AND &amp;</span><span class="sxs-lookup"><span data-stu-id="c4ccd-118">Logical AND operator &amp;</span></span>

<span data-ttu-id="c4ccd-119">Operátor `&` vypočítá logickou hodnotu a její operandy.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-119">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="c4ccd-120">Výsledek `x & y` je `true`, pokud `x` a `y` se vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-120">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="c4ccd-121">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-121">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="c4ccd-122">Operátor `&` vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen jako `false`, takže výsledek musí být `false` bez ohledu na hodnotu operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-122">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="c4ccd-123">V následujícím příkladu je pravý operand operátoru `&` volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-123">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="c4ccd-124">[Podmíněný logický operátor and](#conditional-logical-and-operator-) `&&` také vypočítá logickou a jeho operandy, ale nevyhodnotí pravý operand, pokud je levý operand vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-124">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="c4ccd-125">Pro operandy integrálních typů operátor `&` vypočítá [bitovou logickou hodnotu a](bitwise-and-shift-operators.md#logical-and-operator-) její operandy.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-125">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="c4ccd-126">Unární operátor `&` je [operátor address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="c4ccd-126">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="c4ccd-127">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="c4ccd-127">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="c4ccd-128">Operátor `^` vypočítá logickou hodnotu Exclusive nebo, také známou jako logická XOR, z jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-128">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="c4ccd-129">Výsledek `x ^ y` je `true`, pokud `x` vyhodnotí na `true` a `y` se vyhodnotí jako `false` nebo `x` se vyhodnotí na `true` a `y` se vyhodnotí jako .</span><span class="sxs-lookup"><span data-stu-id="c4ccd-129">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="c4ccd-130">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-130">Otherwise, the result is `false`.</span></span> <span data-ttu-id="c4ccd-131">To znamená, že pro operandy `bool` vypočítá operátor `^` stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-131">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="c4ccd-132">Pro operandy integrálních typů operátor `^` vypočítá [bitový logický typ Exclusive nebo](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-132">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="c4ccd-133">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="c4ccd-133">Logical OR operator |</span></span>

<span data-ttu-id="c4ccd-134">Operátor `|` vypočítá logické nebo jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-134">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="c4ccd-135">Výsledek `x | y` je `true`, pokud je `x` nebo `y` vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-135">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="c4ccd-136">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-136">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="c4ccd-137">Operátor `|` vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen jako `true`, takže výsledek musí být `true` bez ohledu na hodnotu operandu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-137">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="c4ccd-138">V následujícím příkladu je pravý operand operátoru `|` volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-138">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="c4ccd-139">[Podmíněný logický operátor or](#conditional-logical-or-operator-) `||` také vypočítá logickou nebo jeho operandy, ale nevyhodnotí pravý operand, pokud je levý operand vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-139">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="c4ccd-140">Pro operandy integrálních typů operátor `|` vypočítá [bitový logický operátor nebo](bitwise-and-shift-operators.md#logical-or-operator-) jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-140">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="c4ccd-141">Podmíněný logický operátor AND &amp; @ no__t-2</span><span class="sxs-lookup"><span data-stu-id="c4ccd-141">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="c4ccd-142">Podmíněný logický operátor AND `&&`, označovaný také jako "" krátkodobého okruhu ", je vypočítán logický operátor a jeho operandů.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-142">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="c4ccd-143">Výsledek `x && y` je `true`, pokud `x` a `y` se vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-143">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="c4ccd-144">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-144">Otherwise, the result is `false`.</span></span> <span data-ttu-id="c4ccd-145">Pokud `x` se vyhodnotí jako `false`, `y` se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-145">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="c4ccd-146">V následujícím příkladu je pravý operand operátoru `&&` volání metody, které není provedeno, je-li levý operand vyhodnocen jako `false`:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-146">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="c4ccd-147">[Logický operátor and](#logical-and-operator-) `&` také vypočítá logickou a jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-147">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="c4ccd-148">Podmíněný logický operátor OR | |</span><span class="sxs-lookup"><span data-stu-id="c4ccd-148">Conditional logical OR operator ||</span></span>

<span data-ttu-id="c4ccd-149">Podmíněný logický operátor OR `||`, označovaný také jako "" krátkodobého "logického" operátoru "nebo", vypočítává logickou nebo jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-149">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="c4ccd-150">Výsledek `x || y` je `true`, pokud je `x` nebo `y` vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-150">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="c4ccd-151">V opačném případě je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-151">Otherwise, the result is `false`.</span></span> <span data-ttu-id="c4ccd-152">Pokud `x` se vyhodnotí jako `true`, `y` se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-152">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="c4ccd-153">V následujícím příkladu je pravý operand operátoru `||` volání metody, které není provedeno, je-li levý operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-153">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="c4ccd-154">[Logický operátor or](#logical-or-operator-) `|` také VYPOČÍTÁ logické nebo jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-154">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="c4ccd-155">Logické operátory s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-155">Nullable Boolean logical operators</span></span>

<span data-ttu-id="c4ccd-156">U operandů `bool?` podporují operátory `&` a `|` logiku se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-156">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="c4ccd-157">Sémantika těchto operátorů je definována v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-157">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="c4ccd-158">x</span><span class="sxs-lookup"><span data-stu-id="c4ccd-158">x</span></span>|<span data-ttu-id="c4ccd-159">y</span><span class="sxs-lookup"><span data-stu-id="c4ccd-159">y</span></span>|<span data-ttu-id="c4ccd-160">x & y</span><span class="sxs-lookup"><span data-stu-id="c4ccd-160">x&y</span></span>|<span data-ttu-id="c4ccd-161">×&#124;y</span><span class="sxs-lookup"><span data-stu-id="c4ccd-161">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="c4ccd-162">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-162">true</span></span>|<span data-ttu-id="c4ccd-163">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-163">true</span></span>|<span data-ttu-id="c4ccd-164">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-164">true</span></span>|<span data-ttu-id="c4ccd-165">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-165">true</span></span>|  
|<span data-ttu-id="c4ccd-166">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-166">true</span></span>|<span data-ttu-id="c4ccd-167">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-167">false</span></span>|<span data-ttu-id="c4ccd-168">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-168">false</span></span>|<span data-ttu-id="c4ccd-169">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-169">true</span></span>|  
|<span data-ttu-id="c4ccd-170">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-170">true</span></span>|<span data-ttu-id="c4ccd-171">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-171">null</span></span>|<span data-ttu-id="c4ccd-172">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-172">null</span></span>|<span data-ttu-id="c4ccd-173">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-173">true</span></span>|  
|<span data-ttu-id="c4ccd-174">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-174">false</span></span>|<span data-ttu-id="c4ccd-175">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-175">true</span></span>|<span data-ttu-id="c4ccd-176">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-176">false</span></span>|<span data-ttu-id="c4ccd-177">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-177">true</span></span>|  
|<span data-ttu-id="c4ccd-178">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-178">false</span></span>|<span data-ttu-id="c4ccd-179">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-179">false</span></span>|<span data-ttu-id="c4ccd-180">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-180">false</span></span>|<span data-ttu-id="c4ccd-181">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-181">false</span></span>|  
|<span data-ttu-id="c4ccd-182">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-182">false</span></span>|<span data-ttu-id="c4ccd-183">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-183">null</span></span>|<span data-ttu-id="c4ccd-184">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-184">false</span></span>|<span data-ttu-id="c4ccd-185">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-185">null</span></span>|  
|<span data-ttu-id="c4ccd-186">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-186">null</span></span>|<span data-ttu-id="c4ccd-187">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-187">true</span></span>|<span data-ttu-id="c4ccd-188">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-188">null</span></span>|<span data-ttu-id="c4ccd-189">true</span><span class="sxs-lookup"><span data-stu-id="c4ccd-189">true</span></span>|  
|<span data-ttu-id="c4ccd-190">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-190">null</span></span>|<span data-ttu-id="c4ccd-191">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-191">false</span></span>|<span data-ttu-id="c4ccd-192">false</span><span class="sxs-lookup"><span data-stu-id="c4ccd-192">false</span></span>|<span data-ttu-id="c4ccd-193">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-193">null</span></span>|  
|<span data-ttu-id="c4ccd-194">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-194">null</span></span>|<span data-ttu-id="c4ccd-195">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-195">null</span></span>|<span data-ttu-id="c4ccd-196">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-196">null</span></span>|<span data-ttu-id="c4ccd-197">null</span><span class="sxs-lookup"><span data-stu-id="c4ccd-197">null</span></span>|  

<span data-ttu-id="c4ccd-198">Chování těchto operátorů se liší od typického chování operátoru s typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-198">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="c4ccd-199">Obvykle operátor, který je definován pro operandy typu hodnoty, lze také použít s operandy odpovídajícího typu hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-199">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="c4ccd-200">Takový operátor vytvoří `null`, pokud je kterýkoli z jeho operandů `null`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-200">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="c4ccd-201">Operátory `&` a `|` však mohou vydávat hodnotu, která není null, i když je jeden z operandů `null`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-201">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="c4ccd-202">Další informace o chování operátora s typy hodnot s možnou hodnotou null naleznete v části [operátory](../../programming-guide/nullable-types/using-nullable-types.md#operators) v článku [použití hodnot s možnou hodnotou null](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="c4ccd-202">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="c4ccd-203">Můžete také použít operátory `!` a `^` s operandy `bool?`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-203">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="c4ccd-204">Podmíněné logické operátory `&&` a `||` nepodporují operandy `bool?`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-204">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="c4ccd-205">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="c4ccd-205">Compound assignment</span></span>

<span data-ttu-id="c4ccd-206">Pro binární operátor `op` se složený výraz přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="c4ccd-206">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="c4ccd-207">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="c4ccd-207">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="c4ccd-208">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-208">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="c4ccd-209">Operátory `&`, `|` a `^` podporují složené přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-209">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="c4ccd-210">Podmíněné logické operátory `&&` a `||` nepodporují složené přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-210">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="c4ccd-211">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="c4ccd-211">Operator precedence</span></span>

<span data-ttu-id="c4ccd-212">Následující seznam uvádí logické operátory od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-212">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="c4ccd-213">Logický operátor negace `!`</span><span class="sxs-lookup"><span data-stu-id="c4ccd-213">Logical negation operator `!`</span></span>
- <span data-ttu-id="c4ccd-214">Logický operátor AND `&`</span><span class="sxs-lookup"><span data-stu-id="c4ccd-214">Logical AND operator `&`</span></span>
- <span data-ttu-id="c4ccd-215">Logický exkluzivní operátor OR `^`</span><span class="sxs-lookup"><span data-stu-id="c4ccd-215">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="c4ccd-216">Logický operátor OR @no__t – 0</span><span class="sxs-lookup"><span data-stu-id="c4ccd-216">Logical OR operator `|`</span></span>
- <span data-ttu-id="c4ccd-217">Podmíněný logický operátor AND @no__t – 0</span><span class="sxs-lookup"><span data-stu-id="c4ccd-217">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="c4ccd-218">Podmíněný logický operátor OR `||`</span><span class="sxs-lookup"><span data-stu-id="c4ccd-218">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="c4ccd-219">Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů, použijte závorky `()`:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-219">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="c4ccd-220">Úplný seznam C# operátorů seřazených podle priority úrovně naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="c4ccd-220">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c4ccd-221">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="c4ccd-221">Operator overloadability</span></span>

<span data-ttu-id="c4ccd-222">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `!`, `&`, `|` a `^`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-222">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="c4ccd-223">Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-223">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="c4ccd-224">Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-224">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="c4ccd-225">Uživatelsky definovaný typ nemůže přetížit Podmíněné logické operátory `&&` a `||`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-225">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="c4ccd-226">Pokud však uživatelsky definovaný typ přetěžuje [operátory true a false](true-false-operators.md) a `&` nebo `|` nějakým způsobem, může být pro operandy daného typu vyhodnocena operace `&&` nebo `||`.</span><span class="sxs-lookup"><span data-stu-id="c4ccd-226">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="c4ccd-227">Další informace naleznete v části [uživatelsky definované Podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c4ccd-227">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c4ccd-228">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c4ccd-228">C# language specification</span></span>

<span data-ttu-id="c4ccd-229">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="c4ccd-229">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c4ccd-230">Logický operátor negace</span><span class="sxs-lookup"><span data-stu-id="c4ccd-230">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="c4ccd-231">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="c4ccd-231">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="c4ccd-232">Podmíněné logické operátory</span><span class="sxs-lookup"><span data-stu-id="c4ccd-232">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="c4ccd-233">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="c4ccd-233">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="c4ccd-234">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4ccd-234">See also</span></span>

- [<span data-ttu-id="c4ccd-235">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="c4ccd-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c4ccd-236">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c4ccd-236">C# operators</span></span>](index.md)
- [<span data-ttu-id="c4ccd-237">Bitové operátory a posunutí</span><span class="sxs-lookup"><span data-stu-id="c4ccd-237">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
