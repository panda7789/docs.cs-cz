---
description: Switch (Referenční dokumentace jazyka C#)
title: Příkaz přepínače jazyka C#
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
ms.openlocfilehash: 20c1d9786eaa184088500cf1b37d33afc421b5e7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142021"
---
# <a name="switch-c-reference"></a><span data-ttu-id="e2990-103">Switch (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e2990-103">switch (C# reference)</span></span>

<span data-ttu-id="e2990-104">Tento článek se zabývá `switch` příkazem.</span><span class="sxs-lookup"><span data-stu-id="e2990-104">This article covers the `switch` statement.</span></span> <span data-ttu-id="e2990-105">Informace o `switch` výrazu (představené v C# 8,0) najdete v článku [ `switch` výrazy](../operators/switch-expression.md) v části [výrazy a operátory](../operators/index.md) .</span><span class="sxs-lookup"><span data-stu-id="e2990-105">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="e2990-106">`switch` je příkaz výběru, který zvolí oddíl s jedním *přepínačem* , který se má provést ze seznamu kandidátů na základě porovnávání vzorů s *výrazem shody*.</span><span class="sxs-lookup"><span data-stu-id="e2990-106">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="e2990-107">`switch`Příkaz se často používá jako alternativa k konstruktoru [if-else](if-else.md) , pokud je jeden výraz testován proti třem nebo více podmínkám.</span><span class="sxs-lookup"><span data-stu-id="e2990-107">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="e2990-108">Například následující `switch` příkaz určuje, zda proměnná typu `Color` má jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="e2990-108">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="e2990-109">Je ekvivalentní s následujícím příkladem, který používá `if` - `else` konstrukci.</span><span class="sxs-lookup"><span data-stu-id="e2990-109">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="e2990-110">Výraz shody</span><span class="sxs-lookup"><span data-stu-id="e2990-110">The match expression</span></span>

<span data-ttu-id="e2990-111">Výraz Match poskytuje hodnotu odpovídající vzorům v `case` popiscích.</span><span class="sxs-lookup"><span data-stu-id="e2990-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="e2990-112">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="e2990-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="e2990-113">V jazyce C# 6 a dřívější výraz porovnávání musí být výraz, který vrací hodnotu následujících typů:</span><span class="sxs-lookup"><span data-stu-id="e2990-113">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="e2990-114">[znak](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="e2990-114">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="e2990-115">[řetězec](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e2990-115">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="e2990-116">[logická](../builtin-types/bool.md)hodnota.</span><span class="sxs-lookup"><span data-stu-id="e2990-116">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="e2990-117">[celočíselná](../builtin-types/integral-numeric-types.md) hodnota, například `int` nebo `long` .</span><span class="sxs-lookup"><span data-stu-id="e2990-117">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="e2990-118">hodnota [výčtu](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="e2990-118">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="e2990-119">Počínaje jazykem C# 7,0 může výraz porovnávání být libovolný výraz, který není null.</span><span class="sxs-lookup"><span data-stu-id="e2990-119">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="e2990-120">Oddíl Switch</span><span class="sxs-lookup"><span data-stu-id="e2990-120">The switch section</span></span>

<span data-ttu-id="e2990-121">`switch`Příkaz obsahuje jeden nebo více oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="e2990-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="e2990-122">Každý oddíl přepínače obsahuje jeden nebo více *popisků Case* (buď označení Case nebo Default) následovaný jedním nebo více příkazy.</span><span class="sxs-lookup"><span data-stu-id="e2990-122">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="e2990-123">`switch`Příkaz může obsahovat maximálně jeden výchozí popisek umístěný v libovolném oddílu Switch.</span><span class="sxs-lookup"><span data-stu-id="e2990-123">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="e2990-124">Následující příklad ukazuje jednoduchý `switch` příkaz, který má tři oddíly přepínače, z nichž každý obsahuje dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="e2990-124">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="e2990-125">Oddíl druhého přepínače obsahuje `case 2:` `case 3:` popisky a.</span><span class="sxs-lookup"><span data-stu-id="e2990-125">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="e2990-126">`switch`Příkaz může obsahovat libovolný počet oddílů přepínače a každý oddíl může obsahovat jeden nebo více popisků případu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e2990-126">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="e2990-127">Nicméně žádné dva popisky case nemůžou obsahovat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="e2990-127">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="e2990-128">Provede se pouze jeden oddíl Switch v příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="e2990-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="e2990-129">C# neumožní pokračování v provádění jednoho oddílu přepínače na další.</span><span class="sxs-lookup"><span data-stu-id="e2990-129">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="e2990-130">Z tohoto důvodu následující kód vygeneruje chybu kompilátoru, CS0163: "řízení nemůže být z jednoho popisku Case ( \<case label> ) do jiného."</span><span class="sxs-lookup"><span data-stu-id="e2990-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="e2990-131">Tento požadavek se obvykle splní explicitním ukončením oddílu přepínače pomocí příkazu [Break](break.md), [goto](goto.md)nebo [return](return.md) .</span><span class="sxs-lookup"><span data-stu-id="e2990-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="e2990-132">Následující kód je však také platný, protože zajišťuje, že řízení programu nemůže `default` Přejít do oddílu Switch.</span><span class="sxs-lookup"><span data-stu-id="e2990-132">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="e2990-133">Spuštění seznamu příkazů v oddílu switch s popiskem Case, který odpovídá výrazu Match začíná prvním příkazem a pokračuje přes seznam příkazů, obvykle dokud není dosaženo příkazu skok, jako je,,, `break` `goto case` `goto label` `return` nebo `throw` .</span><span class="sxs-lookup"><span data-stu-id="e2990-133">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="e2990-134">V tomto okamžiku je ovládací prvek převeden mimo `switch` příkaz nebo na jiný popisek případu.</span><span class="sxs-lookup"><span data-stu-id="e2990-134">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="e2990-135">`goto`Příkaz, pokud se používá, musí přenést řízení na konstantní popisek.</span><span class="sxs-lookup"><span data-stu-id="e2990-135">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="e2990-136">Toto omezení je nezbytné, protože při pokusu o přenos řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, například přenáší řízení na nezamýšlené umístění v kódu nebo vytvoření nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="e2990-136">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="e2990-137">Popisky případů</span><span class="sxs-lookup"><span data-stu-id="e2990-137">Case labels</span></span>

<span data-ttu-id="e2990-138">Každý popisek případu určuje vzor, který se má porovnat s výrazem shody ( `caseSwitch` Proměnná v předchozích příkladech).</span><span class="sxs-lookup"><span data-stu-id="e2990-138">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="e2990-139">Pokud se shodují, ovládací prvek se přenese do oddílu Switch, který obsahuje **první** odpovídající popisek případu.</span><span class="sxs-lookup"><span data-stu-id="e2990-139">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="e2990-140">Pokud žádný vzor popisku případu neodpovídá výrazu Match, je ovládací prvek převeden do oddílu s `default` popiskem Case, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="e2990-140">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="e2990-141">Pokud není žádný `default` případ, nejsou spuštěny žádné příkazy v žádném oddílu přepínače a ovládací prvek se přenese mimo `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e2990-141">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="e2990-142">Informace o `switch` příkazu a porovnávání vzorů naleznete v tématu porovnávání [vzorů s oddílem `switch` Statement](#pattern-matching with-the-switch-statement) .</span><span class="sxs-lookup"><span data-stu-id="e2990-142">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching with-the-switch-statement) section.</span></span>

<span data-ttu-id="e2990-143">Vzhledem k tomu, že C# 6 podporuje pouze konstantní vzor a neumožňuje opakování konstantních hodnot, popisky case definují vzájemně se vylučující hodnoty a pouze jeden vzor může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="e2990-143">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="e2990-144">V důsledku toho pořadí, ve kterém `case` se zobrazují příkazy, je neimportované.</span><span class="sxs-lookup"><span data-stu-id="e2990-144">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="e2990-145">V jazyce C# 7,0 však, protože jsou podporovány jiné modely, popisky case nemusí definovat vzájemně se vylučující hodnoty a více vzorů může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="e2990-145">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="e2990-146">Vzhledem k tomu, že jsou spuštěny pouze příkazy v první části přepínače obsahující odpovídající vzor, je nyní důležité pořadí, ve kterém jsou `case` příkazy zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="e2990-146">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="e2990-147">Pokud C# detekuje oddíl Switch, jehož příkaz Case nebo příkazy jsou ekvivalentní nebo jsou podmnožinou předchozích příkazů, vygeneruje chybu kompilátoru, CS8120, "případ přepínače již byl zpracován předchozím případem".</span><span class="sxs-lookup"><span data-stu-id="e2990-147">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="e2990-148">Následující příklad znázorňuje `switch` příkaz, který používá celou řadu nevzájemně se vylučujících vzorů.</span><span class="sxs-lookup"><span data-stu-id="e2990-148">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="e2990-149">Pokud přesunete `case 0:` oddíl Switch tak, že již není prvním oddílem v `switch` příkazu, C# vygeneruje chybu kompilátoru, protože celé číslo, jehož hodnota je nula, je podmnožina všech celých čísel, což je vzor definovaný `case int val` příkazem.</span><span class="sxs-lookup"><span data-stu-id="e2990-149">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="e2990-150">Tento problém můžete vyřešit a odstranit upozornění kompilátoru jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="e2990-150">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="e2990-151">Změnou pořadí oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="e2990-151">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="e2990-152">Použitím [klauzule when](#the-case-statement-and-the-when-clause) v `case` popisku.</span><span class="sxs-lookup"><span data-stu-id="e2990-152">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="e2990-153">`default`Případ</span><span class="sxs-lookup"><span data-stu-id="e2990-153">The `default` case</span></span>

<span data-ttu-id="e2990-154">`default`Parametr Case určuje oddíl přepínače, který se má provést, pokud výraz shody neodpovídá žádnému jinému `case` popisku.</span><span class="sxs-lookup"><span data-stu-id="e2990-154">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="e2990-155">Pokud není k `default` dispozici případ a výraz shody neodpovídá žádnému jinému `case` popisku, tok programu přepadne do `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e2990-155">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="e2990-156">`default`Případ se může objevit v libovolném pořadí `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e2990-156">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="e2990-157">Bez ohledu na pořadí ve zdrojovém kódu je vždy vyhodnoceno jako poslední, po `case` vyhodnocení všech popisků.</span><span class="sxs-lookup"><span data-stu-id="e2990-157">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="e2990-158">Porovnávání vzorů s `switch` příkazem</span><span class="sxs-lookup"><span data-stu-id="e2990-158">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="e2990-159">Každý `case` příkaz definuje vzor, který, pokud se shoduje s výrazem shody, způsobí, že obsahuje oddíl obsahujícího přepínače, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="e2990-159">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="e2990-160">Všechny verze jazyka C# podporují konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="e2990-160">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="e2990-161">Zbývající vzorce jsou podporovány počínaje jazykem C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="e2990-161">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="e2990-162">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="e2990-162">Constant pattern</span></span>

<span data-ttu-id="e2990-163">Konstantní vzor testuje, zda se výraz shody rovná zadané konstantě.</span><span class="sxs-lookup"><span data-stu-id="e2990-163">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="e2990-164">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="e2990-164">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="e2990-165">kde *konstanta* je hodnota, která má být testována.</span><span class="sxs-lookup"><span data-stu-id="e2990-165">where *constant* is the value to test for.</span></span> <span data-ttu-id="e2990-166">*konstanta* může být libovolný z následujících konstantních výrazů:</span><span class="sxs-lookup"><span data-stu-id="e2990-166">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="e2990-167">Literál [bool](../builtin-types/bool.md) : `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="e2990-167">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="e2990-168">Jakékoli [integrální](../builtin-types/integral-numeric-types.md) konstanty, například `int` , a `long` , nebo `byte` .</span><span class="sxs-lookup"><span data-stu-id="e2990-168">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="e2990-169">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="e2990-169">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="e2990-170">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="e2990-170">An enumeration constant.</span></span>
- <span data-ttu-id="e2990-171">Literál [znaků](../builtin-types/char.md) .</span><span class="sxs-lookup"><span data-stu-id="e2990-171">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="e2990-172">[Řetězcový](../builtin-types/reference-types.md) literál.</span><span class="sxs-lookup"><span data-stu-id="e2990-172">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="e2990-173">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e2990-173">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="e2990-174">Pokud je *výraz* a *konstanta* integrální typy, operátor rovnosti jazyka C# určuje, zda výraz vrátí hodnotu `true` (tj `expr == constant` . zda).</span><span class="sxs-lookup"><span data-stu-id="e2990-174">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="e2990-175">V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .</span><span class="sxs-lookup"><span data-stu-id="e2990-175">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="e2990-176">V následujícím příkladu je použit model konstanty k určení, zda je konkrétní datum víkend, první den pracovního týdne, poslední den pracovního týdne nebo uprostřed pracovního týdne.</span><span class="sxs-lookup"><span data-stu-id="e2990-176">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="e2990-177">Vyhodnocuje <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuálního dne proti členům <xref:System.DayOfWeek> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e2990-177">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="e2990-178">Následující příklad používá konstantní vzorek pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje automatický kavárnový počítač.</span><span class="sxs-lookup"><span data-stu-id="e2990-178">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="e2990-179">Vzor typu</span><span class="sxs-lookup"><span data-stu-id="e2990-179">Type pattern</span></span>

<span data-ttu-id="e2990-180">Vzor typu umožňuje napsat a převést stručný typ hodnocení.</span><span class="sxs-lookup"><span data-stu-id="e2990-180">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="e2990-181">Při použití s `switch` příkazem k provedení porovnávání vzorů testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="e2990-181">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="e2990-182">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="e2990-182">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="e2990-183">kde *Type* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud je shoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e2990-183">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="e2990-184">Typ *výrazu* v čase kompilace může být parametr obecného typu, počínaje jazykem C# 7,1.</span><span class="sxs-lookup"><span data-stu-id="e2990-184">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="e2990-185">`case`Výraz je v `true` případě, že platí některá z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="e2990-185">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="e2990-186">*výraz* je instancí stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="e2990-186">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="e2990-187">*expr* je instance typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="e2990-187">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="e2990-188">Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="e2990-188">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="e2990-189">*výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*.</span><span class="sxs-lookup"><span data-stu-id="e2990-189">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="e2990-190">*Typ proměnné doby kompilace* proměnné je typ proměnné definovaný v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="e2990-190">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="e2990-191">*Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.</span><span class="sxs-lookup"><span data-stu-id="e2990-191">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="e2990-192">*expr* je instance typu, který implementuje rozhraní *typu* .</span><span class="sxs-lookup"><span data-stu-id="e2990-192">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="e2990-193">Pokud *je výraz Case pravdivý, má* jednoznačně přiřazený a má místní rozsah jenom v rámci oddílu Switch.</span><span class="sxs-lookup"><span data-stu-id="e2990-193">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="e2990-194">Všimněte si, že `null` se neshoduje s typem.</span><span class="sxs-lookup"><span data-stu-id="e2990-194">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="e2990-195">K vyhledání shody `null` použijte následující `case` popisek:</span><span class="sxs-lookup"><span data-stu-id="e2990-195">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="e2990-196">V následujícím příkladu je použit vzor typu k poskytnutí informací o různých typech kolekcí.</span><span class="sxs-lookup"><span data-stu-id="e2990-196">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="e2990-197">Namísto `object` byste mohli vytvořit obecnou metodu pomocí typu kolekce jako parametru typu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="e2990-197">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="e2990-198">Obecná verze se liší od první ukázky dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="e2990-198">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="e2990-199">Nejdříve nemůžete použít `null` případ.</span><span class="sxs-lookup"><span data-stu-id="e2990-199">First, you can't use the `null` case.</span></span> <span data-ttu-id="e2990-200">Nemůžete použít žádný konstantní případ, protože kompilátor nemůže převést libovolný typ `T` na jiný typ než `object` .</span><span class="sxs-lookup"><span data-stu-id="e2990-200">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="e2990-201">Jaký byl `default` případ nyní testů pro jinou hodnotu než null `object` .</span><span class="sxs-lookup"><span data-stu-id="e2990-201">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="e2990-202">To znamená, že `default` testy případu jsou pouze pro `null` .</span><span class="sxs-lookup"><span data-stu-id="e2990-202">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="e2990-203">Bez porovnávání vzorů může být tento kód napsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e2990-203">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="e2990-204">Použití porovnávání vzorů typů vytváří více kompaktních čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null` nebo aby prováděl opakované přetypování.</span><span class="sxs-lookup"><span data-stu-id="e2990-204">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="e2990-205">`case`Příkaz a `when` klauzule</span><span class="sxs-lookup"><span data-stu-id="e2990-205">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="e2990-206">Počínaje jazykem C# 7,0, protože příkazy Case nemusejí být vzájemně exkluzivní, můžete přidat `when` klauzuli pro určení další podmínky, která musí být splněna, aby příkaz Case vyhodnotil hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="e2990-206">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="e2990-207">`when`Klauzule může být libovolný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e2990-207">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="e2990-208">Následující příklad definuje základní `Shape` třídu, `Rectangle` třídu, která je odvozena z třídy `Shape` , a `Square` třídu, která je odvozena z `Rectangle` .</span><span class="sxs-lookup"><span data-stu-id="e2990-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="e2990-209">Používá `when` klauzuli k zajištění toho, aby `ShowShapeInfo` považovala `Rectangle` objekt, kterému byla přiřazena shodná délka a šířka, a `Square` to i v případě, že nebyla vytvořena instance `Square` objektu.</span><span class="sxs-lookup"><span data-stu-id="e2990-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="e2990-210">Metoda se nepokusí zobrazit informace buď s objektem, který je `null` nebo tvarem, jehož oblast je nula.</span><span class="sxs-lookup"><span data-stu-id="e2990-210">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="e2990-211">Všimněte si, že `when` klauzule v příkladu, která se pokouší otestovat, zda `Shape` objekt není `null` spuštěn.</span><span class="sxs-lookup"><span data-stu-id="e2990-211">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="e2990-212">Správný vzor typu, který se má testovat, `null` je `case null:` .</span><span class="sxs-lookup"><span data-stu-id="e2990-212">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e2990-213">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2990-213">C# language specification</span></span>

<span data-ttu-id="e2990-214">Další informace naleznete v [příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="e2990-214">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="e2990-215">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e2990-215">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2990-216">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2990-216">See also</span></span>

- [<span data-ttu-id="e2990-217">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2990-217">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2990-218">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e2990-218">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2990-219">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2990-219">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e2990-220">if-else</span><span class="sxs-lookup"><span data-stu-id="e2990-220">if-else</span></span>](if-else.md)
- [<span data-ttu-id="e2990-221">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="e2990-221">Pattern Matching</span></span>](../../pattern-matching.md)
