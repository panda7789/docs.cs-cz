---
title: C# switch statement
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 012fa5b4d5f39b4dfa4d1c77bc3d6fbe181e78a6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428491"
---
# <a name="switch-c-reference"></a><span data-ttu-id="8b22d-102">switch (C# reference)</span><span class="sxs-lookup"><span data-stu-id="8b22d-102">switch (C# reference)</span></span>

<span data-ttu-id="8b22d-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span><span class="sxs-lookup"><span data-stu-id="8b22d-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="8b22d-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span><span class="sxs-lookup"><span data-stu-id="8b22d-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="8b22d-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span><span class="sxs-lookup"><span data-stu-id="8b22d-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="8b22d-106">It's equivalent to the following example that uses an `if`-`else` construct.</span><span class="sxs-lookup"><span data-stu-id="8b22d-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="8b22d-107">The match expression</span><span class="sxs-lookup"><span data-stu-id="8b22d-107">The match expression</span></span>

<span data-ttu-id="8b22d-108">The match expression provides the value to match against the patterns in `case` labels.</span><span class="sxs-lookup"><span data-stu-id="8b22d-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="8b22d-109">Its syntax is:</span><span class="sxs-lookup"><span data-stu-id="8b22d-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="8b22d-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span><span class="sxs-lookup"><span data-stu-id="8b22d-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="8b22d-111">a [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="8b22d-111">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="8b22d-112">a [string](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="8b22d-112">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="8b22d-113">a [bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="8b22d-113">a [bool](bool.md).</span></span>
- <span data-ttu-id="8b22d-114">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-114">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="8b22d-115">an [enum](enum.md) value.</span><span class="sxs-lookup"><span data-stu-id="8b22d-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="8b22d-116">Starting with C# 7.0, the match expression can be any non-null expression.</span><span class="sxs-lookup"><span data-stu-id="8b22d-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="8b22d-117">The switch section</span><span class="sxs-lookup"><span data-stu-id="8b22d-117">The switch section</span></span>

<span data-ttu-id="8b22d-118">A `switch` statement includes one or more switch sections.</span><span class="sxs-lookup"><span data-stu-id="8b22d-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="8b22d-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span><span class="sxs-lookup"><span data-stu-id="8b22d-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="8b22d-120">The `switch` statement may include at most one default label placed in any switch section.</span><span class="sxs-lookup"><span data-stu-id="8b22d-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="8b22d-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span><span class="sxs-lookup"><span data-stu-id="8b22d-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="8b22d-122">The second switch section contains the `case 2:` and `case 3:` labels.</span><span class="sxs-lookup"><span data-stu-id="8b22d-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="8b22d-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="8b22d-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="8b22d-124">However, no two case labels may contain the same expression.</span><span class="sxs-lookup"><span data-stu-id="8b22d-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="8b22d-125">Only one switch section in a switch statement executes.</span><span class="sxs-lookup"><span data-stu-id="8b22d-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="8b22d-126">C# doesn't allow execution to continue from one switch section to the next.</span><span class="sxs-lookup"><span data-stu-id="8b22d-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="8b22d-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span><span class="sxs-lookup"><span data-stu-id="8b22d-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="8b22d-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span><span class="sxs-lookup"><span data-stu-id="8b22d-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="8b22d-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span><span class="sxs-lookup"><span data-stu-id="8b22d-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="8b22d-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span><span class="sxs-lookup"><span data-stu-id="8b22d-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="8b22d-131">At that point, control is transferred outside the `switch` statement or to another case label.</span><span class="sxs-lookup"><span data-stu-id="8b22d-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="8b22d-132">A `goto` statement, if it's used, must transfer control to a constant label.</span><span class="sxs-lookup"><span data-stu-id="8b22d-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="8b22d-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span><span class="sxs-lookup"><span data-stu-id="8b22d-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="8b22d-134">Case labels</span><span class="sxs-lookup"><span data-stu-id="8b22d-134">Case labels</span></span>

<span data-ttu-id="8b22d-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span><span class="sxs-lookup"><span data-stu-id="8b22d-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="8b22d-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span><span class="sxs-lookup"><span data-stu-id="8b22d-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="8b22d-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span><span class="sxs-lookup"><span data-stu-id="8b22d-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="8b22d-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span><span class="sxs-lookup"><span data-stu-id="8b22d-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="8b22d-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span><span class="sxs-lookup"><span data-stu-id="8b22d-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="8b22d-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span><span class="sxs-lookup"><span data-stu-id="8b22d-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="8b22d-141">As a result, the order in which `case` statements appear is unimportant.</span><span class="sxs-lookup"><span data-stu-id="8b22d-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="8b22d-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span><span class="sxs-lookup"><span data-stu-id="8b22d-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="8b22d-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span><span class="sxs-lookup"><span data-stu-id="8b22d-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="8b22d-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span><span class="sxs-lookup"><span data-stu-id="8b22d-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="8b22d-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span><span class="sxs-lookup"><span data-stu-id="8b22d-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="8b22d-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span><span class="sxs-lookup"><span data-stu-id="8b22d-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="8b22d-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span><span class="sxs-lookup"><span data-stu-id="8b22d-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="8b22d-148">By changing the order of the switch sections.</span><span class="sxs-lookup"><span data-stu-id="8b22d-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="8b22d-149">By using a [when clause](#when) in the `case` label.</span><span class="sxs-lookup"><span data-stu-id="8b22d-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="8b22d-150">The `default` case</span><span class="sxs-lookup"><span data-stu-id="8b22d-150">The `default` case</span></span>

<span data-ttu-id="8b22d-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span><span class="sxs-lookup"><span data-stu-id="8b22d-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="8b22d-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span><span class="sxs-lookup"><span data-stu-id="8b22d-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="8b22d-153">The `default` case can appear in any order in the `switch` statement.</span><span class="sxs-lookup"><span data-stu-id="8b22d-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="8b22d-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span><span class="sxs-lookup"><span data-stu-id="8b22d-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="8b22d-155"><a name="pattern" /> Pattern matching with the `switch` statement</span><span class="sxs-lookup"><span data-stu-id="8b22d-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="8b22d-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span><span class="sxs-lookup"><span data-stu-id="8b22d-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="8b22d-157">All versions of C# support the constant pattern.</span><span class="sxs-lookup"><span data-stu-id="8b22d-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="8b22d-158">The remaining patterns are supported beginning with C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="8b22d-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="8b22d-159">Constant pattern</span><span class="sxs-lookup"><span data-stu-id="8b22d-159">Constant pattern</span></span>

<span data-ttu-id="8b22d-160">The constant pattern tests whether the match expression equals a specified constant.</span><span class="sxs-lookup"><span data-stu-id="8b22d-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="8b22d-161">Its syntax is:</span><span class="sxs-lookup"><span data-stu-id="8b22d-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="8b22d-162">where *constant* is the value to test for.</span><span class="sxs-lookup"><span data-stu-id="8b22d-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="8b22d-163">*constant* can be any of the following constant expressions:</span><span class="sxs-lookup"><span data-stu-id="8b22d-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="8b22d-164">A [bool](bool.md) literal, either `true` or `false`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-164">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="8b22d-165">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-165">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="8b22d-166">The name of a declared `const` variable.</span><span class="sxs-lookup"><span data-stu-id="8b22d-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="8b22d-167">An enumeration constant.</span><span class="sxs-lookup"><span data-stu-id="8b22d-167">An enumeration constant.</span></span>
- <span data-ttu-id="8b22d-168">A [char](../builtin-types/char.md) literal.</span><span class="sxs-lookup"><span data-stu-id="8b22d-168">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="8b22d-169">A [string](../builtin-types/reference-types.md) literal.</span><span class="sxs-lookup"><span data-stu-id="8b22d-169">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="8b22d-170">The constant expression is evaluated as follows:</span><span class="sxs-lookup"><span data-stu-id="8b22d-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="8b22d-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="8b22d-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="8b22d-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span><span class="sxs-lookup"><span data-stu-id="8b22d-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="8b22d-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span><span class="sxs-lookup"><span data-stu-id="8b22d-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="8b22d-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span><span class="sxs-lookup"><span data-stu-id="8b22d-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="8b22d-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span><span class="sxs-lookup"><span data-stu-id="8b22d-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="8b22d-176">Type pattern</span><span class="sxs-lookup"><span data-stu-id="8b22d-176">Type pattern</span></span>

<span data-ttu-id="8b22d-177">The type pattern enables concise type evaluation and conversion.</span><span class="sxs-lookup"><span data-stu-id="8b22d-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="8b22d-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span><span class="sxs-lookup"><span data-stu-id="8b22d-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="8b22d-179">Its syntax is:</span><span class="sxs-lookup"><span data-stu-id="8b22d-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="8b22d-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span><span class="sxs-lookup"><span data-stu-id="8b22d-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="8b22d-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="8b22d-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="8b22d-182">The `case` expression is `true` if any of the following is true:</span><span class="sxs-lookup"><span data-stu-id="8b22d-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="8b22d-183">*expr* is an instance of the same type as *type*.</span><span class="sxs-lookup"><span data-stu-id="8b22d-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="8b22d-184">*expr* is an instance of a type that derives from *type*.</span><span class="sxs-lookup"><span data-stu-id="8b22d-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="8b22d-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span><span class="sxs-lookup"><span data-stu-id="8b22d-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="8b22d-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span><span class="sxs-lookup"><span data-stu-id="8b22d-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="8b22d-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span><span class="sxs-lookup"><span data-stu-id="8b22d-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="8b22d-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span><span class="sxs-lookup"><span data-stu-id="8b22d-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="8b22d-189">*expr* is an instance of a type that implements the *type* interface.</span><span class="sxs-lookup"><span data-stu-id="8b22d-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="8b22d-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span><span class="sxs-lookup"><span data-stu-id="8b22d-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="8b22d-191">Note that `null` doesn't match a type.</span><span class="sxs-lookup"><span data-stu-id="8b22d-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="8b22d-192">To match a `null`, you use the following `case` label:</span><span class="sxs-lookup"><span data-stu-id="8b22d-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="8b22d-193">The following example uses the type pattern to provide information about various kinds of collection types.</span><span class="sxs-lookup"><span data-stu-id="8b22d-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="8b22d-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span><span class="sxs-lookup"><span data-stu-id="8b22d-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="8b22d-195">The generic version is different than the first sample in two ways.</span><span class="sxs-lookup"><span data-stu-id="8b22d-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="8b22d-196">First, you can't use the `null` case.</span><span class="sxs-lookup"><span data-stu-id="8b22d-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="8b22d-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="8b22d-198">What had been the `default` case now tests for a non-null `object`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="8b22d-199">That means the `default` case tests only for `null`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="8b22d-200">Without pattern matching, this code might be written as follows.</span><span class="sxs-lookup"><span data-stu-id="8b22d-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="8b22d-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span><span class="sxs-lookup"><span data-stu-id="8b22d-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="8b22d-202"><a name="when" /> The `case` statement and the `when` clause</span><span class="sxs-lookup"><span data-stu-id="8b22d-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="8b22d-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span><span class="sxs-lookup"><span data-stu-id="8b22d-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="8b22d-204">The `when` clause can be any expression that returns a Boolean value.</span><span class="sxs-lookup"><span data-stu-id="8b22d-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="8b22d-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="8b22d-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span><span class="sxs-lookup"><span data-stu-id="8b22d-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="8b22d-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span><span class="sxs-lookup"><span data-stu-id="8b22d-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="8b22d-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span><span class="sxs-lookup"><span data-stu-id="8b22d-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="8b22d-209">The correct type pattern to test for a `null` is `case null:`.</span><span class="sxs-lookup"><span data-stu-id="8b22d-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8b22d-210">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b22d-210">C# language specification</span></span>

<span data-ttu-id="8b22d-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="8b22d-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="8b22d-212">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8b22d-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b22d-213">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b22d-213">See also</span></span>

- [<span data-ttu-id="8b22d-214">C# Reference</span><span class="sxs-lookup"><span data-stu-id="8b22d-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8b22d-215">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8b22d-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8b22d-216">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b22d-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8b22d-217">if-else</span><span class="sxs-lookup"><span data-stu-id="8b22d-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="8b22d-218">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="8b22d-218">Pattern Matching</span></span>](../../pattern-matching.md)
