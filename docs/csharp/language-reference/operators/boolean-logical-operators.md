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
ms.openlocfilehash: de621b26334bbc9679ba7e48a9d5a0cbaec67eab
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427315"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="ca955-103">Logická logické operátory (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="ca955-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="ca955-104">Následující operátory provádí logické operace s [bool](../keywords/bool.md) operandy:</span><span class="sxs-lookup"><span data-stu-id="ca955-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="ca955-105">Unární [ `!` (Logická negace)](#logical-negation-operator-) operátor.</span><span class="sxs-lookup"><span data-stu-id="ca955-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="ca955-106">Binární [ `&` (logický operátor a)](#logical-and-operator-), [ `|` (logický operátor nebo)](#logical-or-operator-), a [ `^` (logické XOR)](#logical-exclusive-or-operator-) operátory.</span><span class="sxs-lookup"><span data-stu-id="ca955-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="ca955-107">Tyto operátory jsou vždy vyhodnoceny oba operandy.</span><span class="sxs-lookup"><span data-stu-id="ca955-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="ca955-108">Binární [ `&&` (logický operátor podmíněného AND)](#conditional-logical-and-operator-) a [ `||` (logický operátor podmíněného OR)](#conditional-logical-or-operator-) operátory.</span><span class="sxs-lookup"><span data-stu-id="ca955-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="ca955-109">Tyto operátory vyhodnocení druhého operandu, pouze pokud je nutné.</span><span class="sxs-lookup"><span data-stu-id="ca955-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="ca955-110">Pro operandy [integrální](../keywords/integral-types-table.md) typy, `&`, `|`, a `^` operátory provádějí operace bitový logický.</span><span class="sxs-lookup"><span data-stu-id="ca955-110">For the operands of [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="ca955-111">Logický operátor negace!</span><span class="sxs-lookup"><span data-stu-id="ca955-111">Logical negation operator !</span></span>

<span data-ttu-id="ca955-112">`!` Vypočítá operátor logické negace svého operandu.</span><span class="sxs-lookup"><span data-stu-id="ca955-112">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="ca955-113">To znamená, vytvoří `true`, pokud je operand vyhodnocen jako `false`, a `false`, pokud je operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="ca955-113">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="ca955-114">Logický operátor AND &amp;</span><span class="sxs-lookup"><span data-stu-id="ca955-114">Logical AND operator &amp;</span></span>

<span data-ttu-id="ca955-115">`&` Operátor vypočítá logický operátor AND operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-115">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="ca955-116">Výsledek `x & y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`.</span><span class="sxs-lookup"><span data-stu-id="ca955-116">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="ca955-117">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="ca955-117">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="ca955-118">`&` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `false`tak, aby výsledek musí být `false` bez ohledu na hodnotu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="ca955-118">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="ca955-119">V následujícím příkladu, druhý operand `&` operátor je volání metody, která se provádí bez ohledu na hodnotu prvního operandu:</span><span class="sxs-lookup"><span data-stu-id="ca955-119">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="ca955-120">[Podmíněné logického operátoru AND](#conditional-logical-and-operator-) `&&` také vypočítá logický operátor a jeho operandy, ale nebude vyhodnocení druhého operandu, jestli je první operand vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="ca955-120">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="ca955-121">Pro operandy integrální typy `&` operátor výpočetní [bitové logické AND](and-operator.md#integer-logical-bitwise-and-operator) z operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-121">For the operands of integral types, the `&` operator computes [bitwise logical AND](and-operator.md#integer-logical-bitwise-and-operator) of its operands.</span></span> <span data-ttu-id="ca955-122">Unární `&` operátor je [operátoru address-of](and-operator.md#unary-address-of-operator).</span><span class="sxs-lookup"><span data-stu-id="ca955-122">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="ca955-123">Logický exkluzivní operátor OR ^</span><span class="sxs-lookup"><span data-stu-id="ca955-123">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="ca955-124">`^` Operátor vypočítá logické exkluzivní OR označované také jako logický operátor XOR z operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-124">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="ca955-125">Výsledek `x ^ y` je `true` Pokud `x` vyhodnotí jako `true` a `y` vyhodnotí jako `false`, nebo `x` vyhodnotí jako `false` a `y` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="ca955-125">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="ca955-126">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="ca955-126">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ca955-127">To znamená pro `bool` operandy, `^` operátor vypočítá stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="ca955-127">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="ca955-128">Pro operandy integrální typy `^` operátor výpočetní [logický bitový exkluzivní operátor OR](xor-operator.md) z operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-128">For the operands of integral types, the `^` operator computes [bitwise logical exclusive OR](xor-operator.md) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="ca955-129">Logický operátor OR |</span><span class="sxs-lookup"><span data-stu-id="ca955-129">Logical OR operator |</span></span>

<span data-ttu-id="ca955-130">`|` Operátor vypočítá logický operátor OR operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-130">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="ca955-131">Výsledek `x | y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="ca955-131">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="ca955-132">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="ca955-132">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="ca955-133">`|` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `true`tak, aby výsledek musí být `true` bez ohledu na hodnotu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="ca955-133">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="ca955-134">V následujícím příkladu, druhý operand `|` operátor je volání metody, která se provádí bez ohledu na hodnotu prvního operandu:</span><span class="sxs-lookup"><span data-stu-id="ca955-134">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="ca955-135">[Podmíněné logického operátoru OR](#conditional-logical-or-operator-) `||` také vypočítá logický operátor OR jeho operandy, ale nebude vyhodnocení druhého operandu, jestli je první operand vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="ca955-135">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="ca955-136">Pro operandy integrální typy `|` operátor výpočetní [bitové logické OR](or-operator.md) z operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-136">For the operands of integral types, the `|` operator computes [bitwise logical OR](or-operator.md) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="ca955-137">Podmíněné logického operátoru AND &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="ca955-137">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="ca955-138">Podmíněné logického operátoru AND `&&`, označované také jako "krátký cyklus" logického operátoru AND, vypočítá logický operátor AND operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-138">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="ca955-139">Výsledek `x && y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`.</span><span class="sxs-lookup"><span data-stu-id="ca955-139">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="ca955-140">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="ca955-140">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ca955-141">Pokud je první operand vyhodnocen jako `false`, není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="ca955-141">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="ca955-142">V následujícím příkladu, druhý operand `&&` operátor je volání metody, které se neprovádí, pokud je první operand vyhodnocen jako `false`:</span><span class="sxs-lookup"><span data-stu-id="ca955-142">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="ca955-143">[Logického operátoru AND](#logical-and-operator-) `&` také vypočítá logický operátor a jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="ca955-143">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="ca955-144">Podmíněné logického operátoru OR ||</span><span class="sxs-lookup"><span data-stu-id="ca955-144">Conditional logical OR operator ||</span></span>

<span data-ttu-id="ca955-145">Podmíněné logického operátoru OR `||`, označované také jako "krátký cyklus" logického operátoru OR, vypočítá logický operátor OR operandů.</span><span class="sxs-lookup"><span data-stu-id="ca955-145">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="ca955-146">Výsledek `x || y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="ca955-146">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="ca955-147">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="ca955-147">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ca955-148">Pokud je první operand vyhodnocen jako `true`, není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="ca955-148">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="ca955-149">V následujícím příkladu, druhý operand `||` operátor je volání metody, které se neprovádí, pokud je první operand vyhodnocen jako `true`:</span><span class="sxs-lookup"><span data-stu-id="ca955-149">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="ca955-150">[Logického operátoru OR](#logical-or-operator-) `|` také vypočítá logický operátor OR jeho operandy, ale vždy vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="ca955-150">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="ca955-151">Logická logické operátory s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="ca955-151">Nullable Boolean logical operators</span></span>

<span data-ttu-id="ca955-152">Pro `bool?` operandy, `&` a `|` operátory podporu logiky s hodnotou tři.</span><span class="sxs-lookup"><span data-stu-id="ca955-152">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="ca955-153">Sémantika těchto operátorů je definována v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="ca955-153">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="ca955-154">x</span><span class="sxs-lookup"><span data-stu-id="ca955-154">x</span></span>|<span data-ttu-id="ca955-155">y</span><span class="sxs-lookup"><span data-stu-id="ca955-155">y</span></span>|<span data-ttu-id="ca955-156">x & y</span><span class="sxs-lookup"><span data-stu-id="ca955-156">x&y</span></span>|<span data-ttu-id="ca955-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="ca955-157">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="ca955-158">true</span><span class="sxs-lookup"><span data-stu-id="ca955-158">true</span></span>|<span data-ttu-id="ca955-159">true</span><span class="sxs-lookup"><span data-stu-id="ca955-159">true</span></span>|<span data-ttu-id="ca955-160">true</span><span class="sxs-lookup"><span data-stu-id="ca955-160">true</span></span>|<span data-ttu-id="ca955-161">true</span><span class="sxs-lookup"><span data-stu-id="ca955-161">true</span></span>|  
|<span data-ttu-id="ca955-162">true</span><span class="sxs-lookup"><span data-stu-id="ca955-162">true</span></span>|<span data-ttu-id="ca955-163">false</span><span class="sxs-lookup"><span data-stu-id="ca955-163">false</span></span>|<span data-ttu-id="ca955-164">false</span><span class="sxs-lookup"><span data-stu-id="ca955-164">false</span></span>|<span data-ttu-id="ca955-165">true</span><span class="sxs-lookup"><span data-stu-id="ca955-165">true</span></span>|  
|<span data-ttu-id="ca955-166">true</span><span class="sxs-lookup"><span data-stu-id="ca955-166">true</span></span>|<span data-ttu-id="ca955-167">null</span><span class="sxs-lookup"><span data-stu-id="ca955-167">null</span></span>|<span data-ttu-id="ca955-168">null</span><span class="sxs-lookup"><span data-stu-id="ca955-168">null</span></span>|<span data-ttu-id="ca955-169">true</span><span class="sxs-lookup"><span data-stu-id="ca955-169">true</span></span>|  
|<span data-ttu-id="ca955-170">false</span><span class="sxs-lookup"><span data-stu-id="ca955-170">false</span></span>|<span data-ttu-id="ca955-171">true</span><span class="sxs-lookup"><span data-stu-id="ca955-171">true</span></span>|<span data-ttu-id="ca955-172">false</span><span class="sxs-lookup"><span data-stu-id="ca955-172">false</span></span>|<span data-ttu-id="ca955-173">true</span><span class="sxs-lookup"><span data-stu-id="ca955-173">true</span></span>|  
|<span data-ttu-id="ca955-174">false</span><span class="sxs-lookup"><span data-stu-id="ca955-174">false</span></span>|<span data-ttu-id="ca955-175">false</span><span class="sxs-lookup"><span data-stu-id="ca955-175">false</span></span>|<span data-ttu-id="ca955-176">false</span><span class="sxs-lookup"><span data-stu-id="ca955-176">false</span></span>|<span data-ttu-id="ca955-177">false</span><span class="sxs-lookup"><span data-stu-id="ca955-177">false</span></span>|  
|<span data-ttu-id="ca955-178">false</span><span class="sxs-lookup"><span data-stu-id="ca955-178">false</span></span>|<span data-ttu-id="ca955-179">null</span><span class="sxs-lookup"><span data-stu-id="ca955-179">null</span></span>|<span data-ttu-id="ca955-180">false</span><span class="sxs-lookup"><span data-stu-id="ca955-180">false</span></span>|<span data-ttu-id="ca955-181">null</span><span class="sxs-lookup"><span data-stu-id="ca955-181">null</span></span>|  
|<span data-ttu-id="ca955-182">null</span><span class="sxs-lookup"><span data-stu-id="ca955-182">null</span></span>|<span data-ttu-id="ca955-183">true</span><span class="sxs-lookup"><span data-stu-id="ca955-183">true</span></span>|<span data-ttu-id="ca955-184">null</span><span class="sxs-lookup"><span data-stu-id="ca955-184">null</span></span>|<span data-ttu-id="ca955-185">true</span><span class="sxs-lookup"><span data-stu-id="ca955-185">true</span></span>|  
|<span data-ttu-id="ca955-186">null</span><span class="sxs-lookup"><span data-stu-id="ca955-186">null</span></span>|<span data-ttu-id="ca955-187">false</span><span class="sxs-lookup"><span data-stu-id="ca955-187">false</span></span>|<span data-ttu-id="ca955-188">false</span><span class="sxs-lookup"><span data-stu-id="ca955-188">false</span></span>|<span data-ttu-id="ca955-189">null</span><span class="sxs-lookup"><span data-stu-id="ca955-189">null</span></span>|  
|<span data-ttu-id="ca955-190">null</span><span class="sxs-lookup"><span data-stu-id="ca955-190">null</span></span>|<span data-ttu-id="ca955-191">null</span><span class="sxs-lookup"><span data-stu-id="ca955-191">null</span></span>|<span data-ttu-id="ca955-192">null</span><span class="sxs-lookup"><span data-stu-id="ca955-192">null</span></span>|<span data-ttu-id="ca955-193">null</span><span class="sxs-lookup"><span data-stu-id="ca955-193">null</span></span>|  

<span data-ttu-id="ca955-194">Tyto operátory chování se liší od chování typické operátor s typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="ca955-194">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="ca955-195">Obvykle operátor, který je definován pro operandy typu hodnoty je také možné s operandy odpovídající typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="ca955-195">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="ca955-196">Takové operátor vytvoří `null` Pokud kterýkoli z operandů `null`.</span><span class="sxs-lookup"><span data-stu-id="ca955-196">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="ca955-197">Ale `&` a `|` operátory lze vytvořit jinou hodnotu než null, i v případě, že jeden z operandů je `null`.</span><span class="sxs-lookup"><span data-stu-id="ca955-197">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="ca955-198">Další informace o chování operátoru s typy s možnou hodnotou Null, najdete v článku [operátory](../../programming-guide/nullable-types/using-nullable-types.md#operators) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="ca955-198">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="ca955-199">Můžete také použít `!` a `^` operátory se `bool?` operandy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca955-199">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="ca955-200">Podmíněné logické operátory `&&` a `||` nepodporují `bool?` operandy.</span><span class="sxs-lookup"><span data-stu-id="ca955-200">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ca955-201">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="ca955-201">Compound assignment</span></span>

<span data-ttu-id="ca955-202">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="ca955-202">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ca955-203">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="ca955-203">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ca955-204">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="ca955-204">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ca955-205">`&`, `|`, A `^` podporují operátory složeného přiřazení jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca955-205">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="ca955-206">Podmíněné logické operátory `&&` a `||` nepodporují složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ca955-206">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="ca955-207">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="ca955-207">Operator precedence</span></span>

<span data-ttu-id="ca955-208">V následujícím seznamu objednávek od nejvyšší priority k nejnižší logické operátory:</span><span class="sxs-lookup"><span data-stu-id="ca955-208">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="ca955-209">Logický operátor negace</span><span class="sxs-lookup"><span data-stu-id="ca955-209">Logical negation operator</span></span> `!`
- <span data-ttu-id="ca955-210">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="ca955-210">Logical AND operator</span></span> `&`
- <span data-ttu-id="ca955-211">Logické exkluzivní OR – operátor</span><span class="sxs-lookup"><span data-stu-id="ca955-211">Logical exclusive OR operator</span></span> `^`
- <span data-ttu-id="ca955-212">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="ca955-212">Logical OR operator</span></span> `|`
- <span data-ttu-id="ca955-213">Podmíněné logického operátoru AND</span><span class="sxs-lookup"><span data-stu-id="ca955-213">Conditional logical AND operator</span></span> `&&`
- <span data-ttu-id="ca955-214">Podmíněné logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="ca955-214">Conditional logical OR operator</span></span> `||`

<span data-ttu-id="ca955-215">Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů:</span><span class="sxs-lookup"><span data-stu-id="ca955-215">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="ca955-216">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="ca955-216">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ca955-217">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="ca955-217">Operator overloadability</span></span>

<span data-ttu-id="ca955-218">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `!`, `&`, `|`, a `^` operátory.</span><span class="sxs-lookup"><span data-stu-id="ca955-218">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="ca955-219">Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ca955-219">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="ca955-220">Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ca955-220">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="ca955-221">Uživatelem definovaný typ nejde přetížit podmíněné logické operátory `&&` a `||`.</span><span class="sxs-lookup"><span data-stu-id="ca955-221">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="ca955-222">Ale pokud přetížení uživatelem definovaného typu [operátory true a false](../keywords/true-false-operators.md) a `&` nebo `|` operátor určitým způsobem, `&&` nebo `||` operace, respektive, může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="ca955-222">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="ca955-223">Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ca955-223">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ca955-224">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ca955-224">C# language specification</span></span>

<span data-ttu-id="ca955-225">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="ca955-225">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="ca955-226">Logický operátor negace</span><span class="sxs-lookup"><span data-stu-id="ca955-226">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="ca955-227">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="ca955-227">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="ca955-228">Podmíněné logické operátory</span><span class="sxs-lookup"><span data-stu-id="ca955-228">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)

## <a name="see-also"></a><span data-ttu-id="ca955-229">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca955-229">See also</span></span>

- [<span data-ttu-id="ca955-230">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ca955-230">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ca955-231">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ca955-231">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ca955-232">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ca955-232">C# Operators</span></span>](index.md)
