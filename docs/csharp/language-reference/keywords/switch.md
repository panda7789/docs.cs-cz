---
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
ms.openlocfilehash: 9335399be2d4909a02fecbf2959c6f5608664732
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493666"
---
# <a name="switch-c-reference"></a><span data-ttu-id="07479-102">Switch (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="07479-102">switch (C# reference)</span></span>

<span data-ttu-id="07479-103">Tento článek se zabývá `switch` příkazem.</span><span class="sxs-lookup"><span data-stu-id="07479-103">This article covers the `switch` statement.</span></span> <span data-ttu-id="07479-104">Informace o `switch` výrazu (představené v C# 8,0) najdete v článku [ `switch` výrazy](../operators/switch-expression.md) v části [výrazy a operátory](../operators/index.md) .</span><span class="sxs-lookup"><span data-stu-id="07479-104">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="07479-105">`switch`je příkaz výběru, který zvolí oddíl s jedním *přepínačem* , který se má provést ze seznamu kandidátů na základě porovnávání vzorů s *výrazem shody*.</span><span class="sxs-lookup"><span data-stu-id="07479-105">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="07479-106">`switch`Příkaz se často používá jako alternativa k konstruktoru [if-else](if-else.md) , pokud je jeden výraz testován proti třem nebo více podmínkám.</span><span class="sxs-lookup"><span data-stu-id="07479-106">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="07479-107">Například následující `switch` příkaz určuje, zda proměnná typu `Color` má jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="07479-107">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="07479-108">Je ekvivalentní s následujícím příkladem, který používá `if` - `else` konstrukci.</span><span class="sxs-lookup"><span data-stu-id="07479-108">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="07479-109">Výraz shody</span><span class="sxs-lookup"><span data-stu-id="07479-109">The match expression</span></span>

<span data-ttu-id="07479-110">Výraz Match poskytuje hodnotu odpovídající vzorům v `case` popiscích.</span><span class="sxs-lookup"><span data-stu-id="07479-110">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="07479-111">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="07479-111">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="07479-112">V jazyce C# 6 a dřívější výraz porovnávání musí být výraz, který vrací hodnotu následujících typů:</span><span class="sxs-lookup"><span data-stu-id="07479-112">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="07479-113">[znak](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="07479-113">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="07479-114">[řetězec](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="07479-114">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="07479-115">[logická](../builtin-types/bool.md)hodnota.</span><span class="sxs-lookup"><span data-stu-id="07479-115">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="07479-116">[celočíselná](../builtin-types/integral-numeric-types.md) hodnota, například `int` nebo `long` .</span><span class="sxs-lookup"><span data-stu-id="07479-116">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="07479-117">hodnota [výčtu](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="07479-117">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="07479-118">Počínaje jazykem C# 7,0 může výraz porovnávání být libovolný výraz, který není null.</span><span class="sxs-lookup"><span data-stu-id="07479-118">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="07479-119">Oddíl Switch</span><span class="sxs-lookup"><span data-stu-id="07479-119">The switch section</span></span>

<span data-ttu-id="07479-120">`switch`Příkaz obsahuje jeden nebo více oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="07479-120">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="07479-121">Každý oddíl přepínače obsahuje jeden nebo více *popisků Case* (buď označení Case nebo Default) následovaný jedním nebo více příkazy.</span><span class="sxs-lookup"><span data-stu-id="07479-121">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="07479-122">`switch`Příkaz může obsahovat maximálně jeden výchozí popisek umístěný v libovolném oddílu Switch.</span><span class="sxs-lookup"><span data-stu-id="07479-122">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="07479-123">Následující příklad ukazuje jednoduchý `switch` příkaz, který má tři oddíly přepínače, z nichž každý obsahuje dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="07479-123">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="07479-124">Oddíl druhého přepínače obsahuje `case 2:` `case 3:` popisky a.</span><span class="sxs-lookup"><span data-stu-id="07479-124">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="07479-125">`switch`Příkaz může obsahovat libovolný počet oddílů přepínače a každý oddíl může obsahovat jeden nebo více popisků případu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="07479-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="07479-126">Nicméně žádné dva popisky case nemůžou obsahovat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="07479-126">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="07479-127">Provede se pouze jeden oddíl Switch v příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="07479-127">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="07479-128">C# neumožní pokračování v provádění jednoho oddílu přepínače na další.</span><span class="sxs-lookup"><span data-stu-id="07479-128">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="07479-129">Z tohoto důvodu následující kód vygeneruje chybu kompilátoru, CS0163: "řízení nemůže být z jednoho popisku Case ( \<case label> ) do jiného."</span><span class="sxs-lookup"><span data-stu-id="07479-129">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="07479-130">Tento požadavek se obvykle splní explicitním ukončením oddílu přepínače pomocí příkazu [Break](break.md), [goto](goto.md)nebo [return](return.md) .</span><span class="sxs-lookup"><span data-stu-id="07479-130">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="07479-131">Následující kód je však také platný, protože zajišťuje, že řízení programu nemůže `default` Přejít do oddílu Switch.</span><span class="sxs-lookup"><span data-stu-id="07479-131">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="07479-132">Spuštění seznamu příkazů v oddílu switch s popiskem Case, který odpovídá výrazu Match začíná prvním příkazem a pokračuje přes seznam příkazů, obvykle dokud není dosaženo příkazu skok, jako je,,, `break` `goto case` `goto label` `return` nebo `throw` .</span><span class="sxs-lookup"><span data-stu-id="07479-132">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="07479-133">V tomto okamžiku je ovládací prvek převeden mimo `switch` příkaz nebo na jiný popisek případu.</span><span class="sxs-lookup"><span data-stu-id="07479-133">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="07479-134">`goto`Příkaz, pokud se používá, musí přenést řízení na konstantní popisek.</span><span class="sxs-lookup"><span data-stu-id="07479-134">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="07479-135">Toto omezení je nezbytné, protože při pokusu o přenos řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, například přenáší řízení na nezamýšlené umístění v kódu nebo vytvoření nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="07479-135">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="07479-136">Popisky případů</span><span class="sxs-lookup"><span data-stu-id="07479-136">Case labels</span></span>

<span data-ttu-id="07479-137">Každý popisek případu určuje vzor, který se má porovnat s výrazem shody ( `caseSwitch` Proměnná v předchozích příkladech).</span><span class="sxs-lookup"><span data-stu-id="07479-137">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="07479-138">Pokud se shodují, ovládací prvek se přenese do oddílu Switch, který obsahuje **první** odpovídající popisek případu.</span><span class="sxs-lookup"><span data-stu-id="07479-138">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="07479-139">Pokud žádný vzor popisku případu neodpovídá výrazu Match, je ovládací prvek převeden do oddílu s `default` popiskem Case, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="07479-139">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="07479-140">Pokud není žádný `default` případ, nejsou spuštěny žádné příkazy v žádném oddílu přepínače a ovládací prvek se přenese mimo `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="07479-140">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="07479-141">Informace o `switch` příkazu a porovnávání vzorů naleznete v tématu porovnávání [vzorů s oddílem `switch` Statement](#pattern-matching with-the-switch-statement) .</span><span class="sxs-lookup"><span data-stu-id="07479-141">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching with-the-switch-statement) section.</span></span>

<span data-ttu-id="07479-142">Vzhledem k tomu, že C# 6 podporuje pouze konstantní vzor a neumožňuje opakování konstantních hodnot, popisky case definují vzájemně se vylučující hodnoty a pouze jeden vzor může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="07479-142">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="07479-143">V důsledku toho pořadí, ve kterém `case` se zobrazují příkazy, je neimportované.</span><span class="sxs-lookup"><span data-stu-id="07479-143">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="07479-144">V jazyce C# 7,0 však, protože jsou podporovány jiné modely, popisky case nemusí definovat vzájemně se vylučující hodnoty a více vzorů může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="07479-144">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="07479-145">Vzhledem k tomu, že jsou spuštěny pouze příkazy v první části přepínače obsahující odpovídající vzor, je nyní důležité pořadí, ve kterém jsou `case` příkazy zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="07479-145">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="07479-146">Pokud C# detekuje oddíl Switch, jehož příkaz Case nebo příkazy jsou ekvivalentní nebo jsou podmnožinou předchozích příkazů, vygeneruje chybu kompilátoru, CS8120, "případ přepínače již byl zpracován předchozím případem".</span><span class="sxs-lookup"><span data-stu-id="07479-146">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="07479-147">Následující příklad znázorňuje `switch` příkaz, který používá celou řadu nevzájemně se vylučujících vzorů.</span><span class="sxs-lookup"><span data-stu-id="07479-147">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="07479-148">Pokud přesunete `case 0:` oddíl Switch tak, že již není prvním oddílem v `switch` příkazu, C# vygeneruje chybu kompilátoru, protože celé číslo, jehož hodnota je nula, je podmnožina všech celých čísel, což je vzor definovaný `case int val` příkazem.</span><span class="sxs-lookup"><span data-stu-id="07479-148">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="07479-149">Tento problém můžete vyřešit a odstranit upozornění kompilátoru jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="07479-149">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="07479-150">Změnou pořadí oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="07479-150">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="07479-151">Použitím [klauzule when](#the-case-statement-and-the-when-clause) v `case` popisku.</span><span class="sxs-lookup"><span data-stu-id="07479-151">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="07479-152">`default`Případ</span><span class="sxs-lookup"><span data-stu-id="07479-152">The `default` case</span></span>

<span data-ttu-id="07479-153">`default`Parametr Case určuje oddíl přepínače, který se má provést, pokud výraz shody neodpovídá žádnému jinému `case` popisku.</span><span class="sxs-lookup"><span data-stu-id="07479-153">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="07479-154">Pokud není k `default` dispozici případ a výraz shody neodpovídá žádnému jinému `case` popisku, tok programu přepadne do `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="07479-154">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="07479-155">`default`Případ se může objevit v libovolném pořadí `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="07479-155">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="07479-156">Bez ohledu na pořadí ve zdrojovém kódu je vždy vyhodnoceno jako poslední, po `case` vyhodnocení všech popisků.</span><span class="sxs-lookup"><span data-stu-id="07479-156">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="07479-157">Porovnávání vzorů s `switch` příkazem</span><span class="sxs-lookup"><span data-stu-id="07479-157">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="07479-158">Každý `case` příkaz definuje vzor, který, pokud se shoduje s výrazem shody, způsobí, že obsahuje oddíl obsahujícího přepínače, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="07479-158">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="07479-159">Všechny verze jazyka C# podporují konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="07479-159">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="07479-160">Zbývající vzorce jsou podporovány počínaje jazykem C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="07479-160">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="07479-161">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="07479-161">Constant pattern</span></span>

<span data-ttu-id="07479-162">Konstantní vzor testuje, zda se výraz shody rovná zadané konstantě.</span><span class="sxs-lookup"><span data-stu-id="07479-162">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="07479-163">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="07479-163">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="07479-164">kde *konstanta* je hodnota, která má být testována.</span><span class="sxs-lookup"><span data-stu-id="07479-164">where *constant* is the value to test for.</span></span> <span data-ttu-id="07479-165">*konstanta* může být libovolný z následujících konstantních výrazů:</span><span class="sxs-lookup"><span data-stu-id="07479-165">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="07479-166">Literál [bool](../builtin-types/bool.md) : `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="07479-166">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="07479-167">Jakékoli [integrální](../builtin-types/integral-numeric-types.md) konstanty, například `int` , a `long` , nebo `byte` .</span><span class="sxs-lookup"><span data-stu-id="07479-167">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="07479-168">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="07479-168">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="07479-169">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="07479-169">An enumeration constant.</span></span>
- <span data-ttu-id="07479-170">Literál [znaků](../builtin-types/char.md) .</span><span class="sxs-lookup"><span data-stu-id="07479-170">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="07479-171">[Řetězcový](../builtin-types/reference-types.md) literál.</span><span class="sxs-lookup"><span data-stu-id="07479-171">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="07479-172">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="07479-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="07479-173">Pokud je *výraz* a *konstanta* integrální typy, operátor rovnosti jazyka C# určuje, zda výraz vrátí hodnotu `true` (tj `expr == constant` . zda).</span><span class="sxs-lookup"><span data-stu-id="07479-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="07479-174">V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .</span><span class="sxs-lookup"><span data-stu-id="07479-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="07479-175">V následujícím příkladu je použit model konstanty k určení, zda je konkrétní datum víkend, první den pracovního týdne, poslední den pracovního týdne nebo uprostřed pracovního týdne.</span><span class="sxs-lookup"><span data-stu-id="07479-175">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="07479-176">Vyhodnocuje <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuálního dne proti členům <xref:System.DayOfWeek> výčtu.</span><span class="sxs-lookup"><span data-stu-id="07479-176">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="07479-177">Následující příklad používá konstantní vzorek pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje automatický kavárnový počítač.</span><span class="sxs-lookup"><span data-stu-id="07479-177">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="07479-178">Vzor typu</span><span class="sxs-lookup"><span data-stu-id="07479-178">Type pattern</span></span>

<span data-ttu-id="07479-179">Vzor typu umožňuje napsat a převést stručný typ hodnocení.</span><span class="sxs-lookup"><span data-stu-id="07479-179">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="07479-180">Při použití s `switch` příkazem k provedení porovnávání vzorů testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="07479-180">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="07479-181">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="07479-181">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="07479-182">kde *Type* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud je shoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="07479-182">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="07479-183">Typ *výrazu* v čase kompilace může být parametr obecného typu, počínaje jazykem C# 7,1.</span><span class="sxs-lookup"><span data-stu-id="07479-183">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="07479-184">`case`Výraz je v `true` případě, že platí některá z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="07479-184">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="07479-185">*výraz* je instancí stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="07479-185">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="07479-186">*expr* je instance typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="07479-186">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="07479-187">Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="07479-187">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="07479-188">*výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*.</span><span class="sxs-lookup"><span data-stu-id="07479-188">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="07479-189">*Typ proměnné doby kompilace* proměnné je typ proměnné definovaný v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="07479-189">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="07479-190">*Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.</span><span class="sxs-lookup"><span data-stu-id="07479-190">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="07479-191">*expr* je instance typu, který implementuje rozhraní *typu* .</span><span class="sxs-lookup"><span data-stu-id="07479-191">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="07479-192">Pokud *je výraz Case pravdivý, má* jednoznačně přiřazený a má místní rozsah jenom v rámci oddílu Switch.</span><span class="sxs-lookup"><span data-stu-id="07479-192">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="07479-193">Všimněte si, že `null` se neshoduje s typem.</span><span class="sxs-lookup"><span data-stu-id="07479-193">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="07479-194">K vyhledání shody `null` použijte následující `case` popisek:</span><span class="sxs-lookup"><span data-stu-id="07479-194">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="07479-195">V následujícím příkladu je použit vzor typu k poskytnutí informací o různých typech kolekcí.</span><span class="sxs-lookup"><span data-stu-id="07479-195">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="07479-196">Namísto `object` byste mohli vytvořit obecnou metodu pomocí typu kolekce jako parametru typu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="07479-196">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="07479-197">Obecná verze se liší od první ukázky dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="07479-197">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="07479-198">Nejdříve nemůžete použít `null` případ.</span><span class="sxs-lookup"><span data-stu-id="07479-198">First, you can't use the `null` case.</span></span> <span data-ttu-id="07479-199">Nemůžete použít žádný konstantní případ, protože kompilátor nemůže převést libovolný typ `T` na jiný typ než `object` .</span><span class="sxs-lookup"><span data-stu-id="07479-199">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="07479-200">Jaký byl `default` případ nyní testů pro jinou hodnotu než null `object` .</span><span class="sxs-lookup"><span data-stu-id="07479-200">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="07479-201">To znamená, že `default` testy případu jsou pouze pro `null` .</span><span class="sxs-lookup"><span data-stu-id="07479-201">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="07479-202">Bez porovnávání vzorů může být tento kód napsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="07479-202">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="07479-203">Použití porovnávání vzorů typů vytváří více kompaktních čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null` nebo aby prováděl opakované přetypování.</span><span class="sxs-lookup"><span data-stu-id="07479-203">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="07479-204">`case`Příkaz a `when` klauzule</span><span class="sxs-lookup"><span data-stu-id="07479-204">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="07479-205">Počínaje jazykem C# 7,0, protože příkazy Case nemusejí být vzájemně exkluzivní, můžete přidat `when` klauzuli pro určení další podmínky, která musí být splněna, aby příkaz Case vyhodnotil hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="07479-205">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="07479-206">`when`Klauzule může být libovolný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="07479-206">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="07479-207">Následující příklad definuje základní `Shape` třídu, `Rectangle` třídu, která je odvozena z třídy `Shape` , a `Square` třídu, která je odvozena z `Rectangle` .</span><span class="sxs-lookup"><span data-stu-id="07479-207">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="07479-208">Používá `when` klauzuli k zajištění toho, aby `ShowShapeInfo` považovala `Rectangle` objekt, kterému byla přiřazena shodná délka a šířka, a `Square` to i v případě, že nebyla vytvořena instance `Square` objektu.</span><span class="sxs-lookup"><span data-stu-id="07479-208">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="07479-209">Metoda se nepokusí zobrazit informace buď s objektem, který je `null` nebo tvarem, jehož oblast je nula.</span><span class="sxs-lookup"><span data-stu-id="07479-209">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="07479-210">Všimněte si, že `when` klauzule v příkladu, která se pokouší otestovat, zda `Shape` objekt není `null` spuštěn.</span><span class="sxs-lookup"><span data-stu-id="07479-210">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="07479-211">Správný vzor typu, který se má testovat, `null` je `case null:` .</span><span class="sxs-lookup"><span data-stu-id="07479-211">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="07479-212">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07479-212">C# language specification</span></span>

<span data-ttu-id="07479-213">Další informace naleznete v [příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="07479-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="07479-214">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="07479-214">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="07479-215">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07479-215">See also</span></span>

- [<span data-ttu-id="07479-216">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07479-216">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07479-217">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="07479-217">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07479-218">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07479-218">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="07479-219">if-else</span><span class="sxs-lookup"><span data-stu-id="07479-219">if-else</span></span>](if-else.md)
- [<span data-ttu-id="07479-220">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="07479-220">Pattern Matching</span></span>](../../pattern-matching.md)
