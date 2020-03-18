---
title: Příkaz c# switch
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
ms.openlocfilehash: e5580e81b9175cd95491fdba724bacbffa692a5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345391"
---
# <a name="switch-c-reference"></a><span data-ttu-id="f2fb4-102">přepínač (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="f2fb4-102">switch (C# reference)</span></span>

<span data-ttu-id="f2fb4-103">`switch`je příkaz výběru, který vybere *jeden oddíl přepínače,* který se provede ze seznamu kandidátů na základě shody vzoru s *výrazem shody*.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="f2fb4-104">Příkaz `switch` se často používá jako alternativa k [if-else](if-else.md) konstrukce, pokud jeden výraz je testován proti tři nebo více podmínek.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="f2fb4-105">Například následující `switch` příkaz určuje, zda proměnná typu `Color` má jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="f2fb4-106">Je ekvivalentní následující příklad, který `if` - `else` používá konstrukci.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="f2fb4-107">Výraz shody</span><span class="sxs-lookup"><span data-stu-id="f2fb4-107">The match expression</span></span>

<span data-ttu-id="f2fb4-108">Výraz shody poskytuje hodnotu, která `case` se má shodovat se vzorky v popiscích.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="f2fb4-109">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="f2fb4-110">V c# 6 a starší výraz shody musí být výraz, který vrací hodnotu následujících typů:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="f2fb4-111">[znak](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="f2fb4-111">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="f2fb4-112">[řetězec](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="f2fb4-112">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="f2fb4-113">[bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="f2fb4-113">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="f2fb4-114">[integrální](../builtin-types/integral-numeric-types.md) hodnotu, `int` `long`například a nebo .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-114">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="f2fb4-115">hodnotu [výčtu.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="f2fb4-115">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="f2fb4-116">Počínaje C# 7.0, výraz shody může být libovolný výraz bez null.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="f2fb4-117">Sekce přepínače</span><span class="sxs-lookup"><span data-stu-id="f2fb4-117">The switch section</span></span>

<span data-ttu-id="f2fb4-118">Příkaz `switch` obsahuje jeden nebo více oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="f2fb4-119">Každý oddíl přepínače obsahuje jeden nebo více *popisků případu* (případ nebo výchozí popisek) následovaný jedním nebo více příkazy.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="f2fb4-120">Příkaz `switch` může obsahovat maximálně jeden výchozí popisek umístěný v libovolné mašice přepínače.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="f2fb4-121">Následující příklad ukazuje `switch` jednoduchý příkaz, který má tři oddíly přepínače, z nichž každý obsahuje dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="f2fb4-122">Druhý přepínač sekce `case 2:` obsahuje `case 3:` a popisky.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="f2fb4-123">Příkaz `switch` může obsahovat libovolný počet oddílů přepínače a každý oddíl může mít jeden nebo více popisků případu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="f2fb4-124">Žádné dva popisky případu však nesmí obsahovat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="f2fb4-125">Spustí se pouze jeden oddíl přepínače v příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="f2fb4-126">C# neumožňuje spuštění pokračovat z jednoho oddílu přepínače do další.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="f2fb4-127">Z tohoto důvodu následující kód generuje chybu kompilátoru CS0163: "Ovládací prvek\<nemůže propadnout z jednoho popisku případu (popisek případu>) do jiného."</span><span class="sxs-lookup"><span data-stu-id="f2fb4-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="f2fb4-128">Tento požadavek je obvykle splněn explicitním ukončením oddílu přepínače pomocí příkazu [break](break.md), [goto](goto.md)nebo [return.](return.md)</span><span class="sxs-lookup"><span data-stu-id="f2fb4-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="f2fb4-129">Následující kód je však také platný, protože zajišťuje, že ovládací `default` prvek programu nemůže propadnout do části přepínače.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="f2fb4-130">Spuštění seznamu příkazů v části switch s popiskem případu, který odpovídá výrazu shody, začíná prvním příkazem a `break`pokračuje `goto case` `goto label`v `return`seznamu příkazů, obvykle dokud není dosaženo příkazu skoku, například , , , nebo `throw`, .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="f2fb4-131">V tomto okamžiku je ovládací `switch` prvek převeden mimo příkaz nebo na jiný popisek případu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="f2fb4-132">Příkaz, `goto` pokud se používá, musí přenést řízení na konstantní popisek.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="f2fb4-133">Toto omezení je nezbytné, protože pokus o přenos řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, jako přenos řízení do nezamýšleného umístění v kódu nebo vytvoření nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="f2fb4-134">Popisky případů</span><span class="sxs-lookup"><span data-stu-id="f2fb4-134">Case labels</span></span>

<span data-ttu-id="f2fb4-135">Každý popisek případu určuje vzorek, který má `caseSwitch` být porovnán s výrazem shody (proměnná v předchozích příkladech).</span><span class="sxs-lookup"><span data-stu-id="f2fb4-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="f2fb4-136">Pokud se shodují, ovládací prvek je převeden do oddílu přepínače, který obsahuje **první** odpovídající popisek případu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="f2fb4-137">Pokud žádný vzor popisku případu neodpovídá výrazu shody, ovládací prvek se přenese do oddílu s popiskem `default` případu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="f2fb4-138">Pokud neexistuje žádný `default` případ, žádné příkazy v žádné části přepínače jsou `switch` provedeny a řízení je převedena mimo příkaz.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="f2fb4-139">Informace o `switch` příkazu a porovnávání vzorů naleznete v [části Pattern odpovídající oddílu. `switch` ](#pattern)</span><span class="sxs-lookup"><span data-stu-id="f2fb4-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="f2fb4-140">Vzhledem k tomu, že C# 6 podporuje pouze konstantní vzor a neumožňuje opakování konstantní hodnoty, popisky případu definovat vzájemně se vylučující hodnoty a pouze jeden vzorek může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="f2fb4-141">V důsledku toho pořadí, `case` ve kterém příkazy se zobrazí, není důležité.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="f2fb4-142">V c# 7.0 však protože ostatní vzorky jsou podporovány, popisky případu nemusí definovat vzájemně se vylučující hodnoty a více vzorů může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="f2fb4-143">Vzhledem k tomu, že jsou provedeny pouze příkazy v první `case` části přepínače, která obsahuje odpovídající vzorek, pořadí, ve kterém příkazy se zobrazí, je nyní důležité.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="f2fb4-144">Pokud C# zjistí oddíl přepínače, jehož case prohlášení nebo příkazy jsou rovnocenné nebo jsou podmnožiny předchozí příkazy, generuje chybu kompilátoru, CS8120, "případ přepínače již byla zpracována předchozí případ."</span><span class="sxs-lookup"><span data-stu-id="f2fb4-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="f2fb4-145">Následující příklad ilustruje `switch` příkaz, který používá různé vzory, které se nevylučují.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="f2fb4-146">Pokud přesunete `case 0:` oddíl přepínačtak, že již není první `switch` část v příkazu, C# generuje chybu kompilátoru, protože celé číslo, jehož hodnota je nula je podmnožinou všech celých čísel, což je vzor definovaný příkazem. `case int val`</span><span class="sxs-lookup"><span data-stu-id="f2fb4-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="f2fb4-147">Tento problém můžete opravit a odstranit upozornění kompilátoru jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="f2fb4-148">Změnou pořadí sekcí přepínače.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="f2fb4-149">Pomocí [when klauzule](#when) `case` v popisku.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="f2fb4-150">Případ `default`</span><span class="sxs-lookup"><span data-stu-id="f2fb4-150">The `default` case</span></span>

<span data-ttu-id="f2fb4-151">Případ `default` určuje oddíl přepínače, který má být proveden, `case` pokud výraz shody neodpovídá žádnému jinému popisku.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="f2fb4-152">Pokud `default` případ není k dispozici a výraz shody `case` neodpovídá žádnému `switch` jinému popisku, tok programu spadá do příkazu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="f2fb4-153">Případ `default` se může objevit v `switch` libovolném pořadí v příkazu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="f2fb4-154">Bez ohledu na jeho pořadí ve zdrojovém kódu je `case` vždy vyhodnocena jako poslední, poté, co byly vyhodnoceny všechny popisky.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="f2fb4-155"><a name="pattern" />Porovnávání vzorů `switch` s příkazem</span><span class="sxs-lookup"><span data-stu-id="f2fb4-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="f2fb4-156">Každý `case` příkaz definuje vzor, který, pokud odpovídá výrazu shody, způsobí, že jeho část obsahující přepínač bude spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="f2fb4-157">Všechny verze jazyka C# podporují konstantní vzor.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="f2fb4-158">Zbývající vzorky jsou podporovány počínaje C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="f2fb4-159">Konstantní vzor</span><span class="sxs-lookup"><span data-stu-id="f2fb4-159">Constant pattern</span></span>

<span data-ttu-id="f2fb4-160">Konstantní vzorek testuje, zda se výraz shody rovná zadané konstantě.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="f2fb4-161">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="f2fb4-162">*kde konstanta* je hodnota, pro kterou se má testovat.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="f2fb4-163">*konstanta* může být některý z následujících konstantních výrazů:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="f2fb4-164">[Bool](../builtin-types/bool.md) literál: `true` `false`buď nebo .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-164">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="f2fb4-165">Jakákoli [integrální](../builtin-types/integral-numeric-types.md) `int`konstanta, například , a `long`nebo . `byte`</span><span class="sxs-lookup"><span data-stu-id="f2fb4-165">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="f2fb4-166">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="f2fb4-167">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-167">An enumeration constant.</span></span>
- <span data-ttu-id="f2fb4-168">[Char](../builtin-types/char.md) doslovný.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-168">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="f2fb4-169">[Řetězcový](../builtin-types/reference-types.md) literál.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-169">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="f2fb4-170">Konstantní výraz je vyhodnocen takto:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="f2fb4-171">Pokud *expr* a *konstanta* jsou integrální typy, c# operátor rovnosti určuje, zda výraz vrátí `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="f2fb4-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="f2fb4-172">Jinak je hodnota výrazu určena voláním statické [metody Object.Equals(expr, constant).](xref:System.Object.Equals(System.Object,System.Object))</span><span class="sxs-lookup"><span data-stu-id="f2fb4-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="f2fb4-173">Následující příklad používá konstantní vzor k určení, zda je určité datum víkend, první den pracovního týdne, poslední den pracovního týdne nebo uprostřed pracovního týdne.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="f2fb4-174">Vyhodnotí <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuální ho dne proti <xref:System.DayOfWeek> členům výčtu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="f2fb4-175">Následující příklad používá konstantní vzor pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje automatický kávovar.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="f2fb4-176">Vzor typu</span><span class="sxs-lookup"><span data-stu-id="f2fb4-176">Type pattern</span></span>

<span data-ttu-id="f2fb4-177">Vzorek typu umožňuje stručné hodnocení typu a převod.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="f2fb4-178">Při použití `switch` s příkazem provádět porovnávání vzorů, testuje, zda výraz lze převést na zadaný typ, a pokud může být, přetypování do proměnné tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="f2fb4-179">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="f2fb4-180">kde *type* je název typu, na který má být převeden výsledek *expr,* a *varname* je objekt, na který je výsledek *expr* převeden, pokud je shoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="f2fb4-181">Typ *expr* v době kompilace může být parametr obecného typu, počínaje C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="f2fb4-182">Výraz `case` je, `true` pokud je splněna některá z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="f2fb4-183">*expr* je instancí stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="f2fb4-184">*expr* je instancí typu, který je odvozen od *typu*.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="f2fb4-185">Jinými slovy, výsledek *expr* může být upcast na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="f2fb4-186">*expr* má typ kompilace, který je základní třídou *typu*, a *expr* má typ runtime, který je *typu* nebo je odvozen od *typu*.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="f2fb4-187">Typ proměnné v *době kompilace* je typ proměnné, jak je definován v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="f2fb4-188">*Typ runtime* proměnné je typ instance, která je přiřazena k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="f2fb4-189">*expr* je instancí třídy typu, který implementuje *rozhraní typu.*</span><span class="sxs-lookup"><span data-stu-id="f2fb4-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="f2fb4-190">Pokud je výraz případu true, *varname* je jednoznačně přiřazena a má místní obor v rámci oddílu switch.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="f2fb4-191">Všimněte `null` si, že neodpovídá typu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="f2fb4-192">Chcete-li `null`odpovídat , `case` použijte následující popisek:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="f2fb4-193">Následující příklad používá vzor typu k poskytnutí informací o různých typech typů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="f2fb4-194">Místo `object`, můžete provést obecnou metodu pomocí typu kolekce jako parametr typu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f2fb4-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="f2fb4-195">Obecná verze se liší od první ukázky dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="f2fb4-196">Za prvé, nemůžete použít `null` případ.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="f2fb4-197">Nelze použít žádný konstantní případ, protože kompilátor nelze převést libovolný `T` typ `object`na jiný typ než .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="f2fb4-198">Co bylo `default` v případě nyní testuje `object`pro non-null .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="f2fb4-199">To znamená, `default` že `null`případ testy pouze pro .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="f2fb4-200">Bez porovnávání vzorů může být tento kód zapsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="f2fb4-201">Použití odpovídající typ vzorku vytváří kompaktnější, čitelný kód tím, že eliminuje potřebu `null` otestovat, zda je výsledkem převodu nebo provádět opakované přetypování.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="f2fb4-202"><a name="when" />Prohlášení `case` a `when` doložka</span><span class="sxs-lookup"><span data-stu-id="f2fb4-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="f2fb4-203">Počínaje C# 7.0, protože case příkazy nemusí být vzájemně `when` vylučovat, můžete přidat klauzule určit další podmínku, která musí být splněna pro případ prohlášení vyhodnotit na true.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="f2fb4-204">Klauzule `when` může být libovolný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="f2fb4-205">Následující příklad definuje základní `Shape` třídu, `Rectangle` třídu, `Shape`která `Square` je odvozena `Rectangle`od , a třídu, která je odvozena z .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="f2fb4-206">`when` Používá klauzuli k zajištění, že `ShowShapeInfo` zachází `Rectangle` objekt, který byl přiřazen stejné `Square` délky a šířky jako i `Square` v případě, že nebyl anas unátřizován jako objekt.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="f2fb4-207">Metoda se nepokouší zobrazit informace o objektu, který je, `null` nebo obrazec, jehož plocha je nula.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="f2fb4-208">Všimněte `when` si, že klauzule v příkladu, který se pokusí otestovat, zda `Shape` je `null` objekt neprovede.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="f2fb4-209">Správný vzorek typu pro `null` testování `case null:`je .</span><span class="sxs-lookup"><span data-stu-id="f2fb4-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2fb4-210">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2fb4-210">C# language specification</span></span>

<span data-ttu-id="f2fb4-211">Další informace naleznete [v příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="f2fb4-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f2fb4-212">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f2fb4-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2fb4-213">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2fb4-213">See also</span></span>

- [<span data-ttu-id="f2fb4-214">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2fb4-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2fb4-215">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2fb4-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2fb4-216">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f2fb4-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f2fb4-217">if-else</span><span class="sxs-lookup"><span data-stu-id="f2fb4-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="f2fb4-218">Porovnávání</span><span class="sxs-lookup"><span data-stu-id="f2fb4-218">Pattern Matching</span></span>](../../pattern-matching.md)
