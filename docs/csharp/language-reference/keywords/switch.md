---
title: C#příkaz switch
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
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345391"
---
# <a name="switch-c-reference"></a><span data-ttu-id="3f207-102">přepínač (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="3f207-102">switch (C# reference)</span></span>

<span data-ttu-id="3f207-103">`switch` je příkaz výběru, který zvolí oddíl s jedním *přepínačem* , který se má provést ze seznamu kandidátů na základě porovnávání vzorů s *výrazem shody*.</span><span class="sxs-lookup"><span data-stu-id="3f207-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="3f207-104">Příkaz `switch` se často používá jako alternativa k konstruktoru [if-else](if-else.md) , pokud je jeden výraz testován proti třem nebo více podmínkám.</span><span class="sxs-lookup"><span data-stu-id="3f207-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="3f207-105">Například následující příkaz `switch` určuje, zda proměnná typu `Color` má jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="3f207-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="3f207-106">Je ekvivalentní s následujícím příkladem, který používá `if`-`else` konstrukce.</span><span class="sxs-lookup"><span data-stu-id="3f207-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="3f207-107">Výraz shody</span><span class="sxs-lookup"><span data-stu-id="3f207-107">The match expression</span></span>

<span data-ttu-id="3f207-108">Výraz Match poskytuje hodnotu odpovídající vzorům v `case` popisky.</span><span class="sxs-lookup"><span data-stu-id="3f207-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="3f207-109">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="3f207-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="3f207-110">V C# 6 a starších verzích výraz porovnávání musí být výraz, který vrací hodnotu následujících typů:</span><span class="sxs-lookup"><span data-stu-id="3f207-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="3f207-111">[znak](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="3f207-111">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="3f207-112">[řetězec](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="3f207-112">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="3f207-113">[logická](../builtin-types/bool.md)hodnota.</span><span class="sxs-lookup"><span data-stu-id="3f207-113">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="3f207-114">[celočíselná](../builtin-types/integral-numeric-types.md) hodnota, například `int` nebo `long`.</span><span class="sxs-lookup"><span data-stu-id="3f207-114">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="3f207-115">hodnota [výčtu](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="3f207-115">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="3f207-116">Počínaje C# 7,0 se výraz shody může jednat o libovolný výraz, který není null.</span><span class="sxs-lookup"><span data-stu-id="3f207-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="3f207-117">Oddíl Switch</span><span class="sxs-lookup"><span data-stu-id="3f207-117">The switch section</span></span>

<span data-ttu-id="3f207-118">Příkaz `switch` obsahuje jeden nebo více oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="3f207-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="3f207-119">Každý oddíl přepínače obsahuje jeden nebo více *popisků Case* (buď označení Case nebo Default) následovaný jedním nebo více příkazy.</span><span class="sxs-lookup"><span data-stu-id="3f207-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="3f207-120">Příkaz `switch` může zahrnovat maximálně jeden výchozí popisek umístěný v jakémkoli oddílu přepínače.</span><span class="sxs-lookup"><span data-stu-id="3f207-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="3f207-121">Následující příklad ukazuje jednoduchý příkaz `switch`, který má tři oddíly přepínače, z nichž každý obsahuje dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="3f207-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="3f207-122">Oddíl druhého přepínače obsahuje popisky `case 2:` a `case 3:`.</span><span class="sxs-lookup"><span data-stu-id="3f207-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="3f207-123">Příkaz `switch` může obsahovat libovolný počet oddílů přepínače a každý oddíl může obsahovat jeden nebo více popisků případu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3f207-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="3f207-124">Nicméně žádné dva popisky case nemůžou obsahovat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="3f207-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="3f207-125">Provede se pouze jeden oddíl Switch v příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="3f207-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="3f207-126">C#neumožňuje pokračování v provádění jednoho oddílu přepínače na další.</span><span class="sxs-lookup"><span data-stu-id="3f207-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="3f207-127">Z tohoto důvodu následující kód vygeneruje chybu kompilátoru, CS0163: "ovládací prvek nemůže přejít z jednoho popisku Case (\<popisek případu >) do jiného."</span><span class="sxs-lookup"><span data-stu-id="3f207-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="3f207-128">Tento požadavek se obvykle splní explicitním ukončením oddílu přepínače pomocí příkazu [Break](break.md), [goto](goto.md)nebo [return](return.md) .</span><span class="sxs-lookup"><span data-stu-id="3f207-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="3f207-129">Následující kód je však také platný, protože zajišťuje, že řízení programu nemůže přejít do oddílu `default` Switch.</span><span class="sxs-lookup"><span data-stu-id="3f207-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="3f207-130">Vykonání seznamu příkazů v oddílu switch s popiskem Case, který odpovídá výrazu shody, začíná prvním příkazem a pokračuje přes seznam příkazů, obvykle dokud není dosaženo příkazu skok, jako je `break`, `goto case`, `goto label`, `return`nebo `throw`.</span><span class="sxs-lookup"><span data-stu-id="3f207-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="3f207-131">V tomto okamžiku se ovládací prvek přenáší mimo příkaz `switch` nebo na jiný popisek případu.</span><span class="sxs-lookup"><span data-stu-id="3f207-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="3f207-132">Příkaz `goto`, pokud se používá, musí přenést řízení na konstantní popisek.</span><span class="sxs-lookup"><span data-stu-id="3f207-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="3f207-133">Toto omezení je nezbytné, protože při pokusu o přenos řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, například přenáší řízení na nezamýšlené umístění v kódu nebo vytvoření nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="3f207-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="3f207-134">Popisky případů</span><span class="sxs-lookup"><span data-stu-id="3f207-134">Case labels</span></span>

<span data-ttu-id="3f207-135">Každý popisek případu určuje vzor, který se má porovnat s výrazem shody (`caseSwitch` proměnnou v předchozích příkladech).</span><span class="sxs-lookup"><span data-stu-id="3f207-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="3f207-136">Pokud se shodují, ovládací prvek se přenese do oddílu Switch, který obsahuje **první** odpovídající popisek případu.</span><span class="sxs-lookup"><span data-stu-id="3f207-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="3f207-137">Pokud žádný vzor popisku případu neodpovídá výrazu shody, ovládací prvek se přenese do oddílu pomocí popisku `default` případu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="3f207-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="3f207-138">Pokud není k dispozici žádný `default` případ, nejsou provedeny žádné příkazy v žádném oddílu přepínače a ovládací prvek se přenese mimo příkaz `switch`.</span><span class="sxs-lookup"><span data-stu-id="3f207-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="3f207-139">Informace o příkazu `switch` a porovnávání vzorů naleznete v části [porovnávání vzorů pomocí příkazu `switch`](#pattern) .</span><span class="sxs-lookup"><span data-stu-id="3f207-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="3f207-140">Vzhledem C# k tomu, že 6 podporuje pouze konstantní vzor a neumožňuje opakování konstantních hodnot, popisky case definují vzájemně se vylučující hodnoty a pouze jeden vzor může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="3f207-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="3f207-141">V důsledku toho je pořadí, ve kterém jsou `case` příkazy, neimportované.</span><span class="sxs-lookup"><span data-stu-id="3f207-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="3f207-142">V C# 7,0, protože jsou však podporovány jiné modely, popisky case nemusí definovat vzájemně se vylučující hodnoty a více vzorů se může shodovat s výrazem shody.</span><span class="sxs-lookup"><span data-stu-id="3f207-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="3f207-143">Vzhledem k tomu, že jsou spuštěny pouze příkazy v prvním oddílu přepínače, který obsahuje odpovídající vzor, je nyní důležité pořadí, v jakém jsou `case` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3f207-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="3f207-144">Pokud C# zjistí oddíl Switch, jehož příkaz Case nebo příkazy jsou ekvivalentní nebo jsou podmnožinou předchozích příkazů, vygeneruje chybu kompilátoru, CS8120, "případ přepínače již byl zpracován předchozím případem".</span><span class="sxs-lookup"><span data-stu-id="3f207-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="3f207-145">Následující příklad ukazuje příkaz `switch`, který používá celou řadu nevzájemně se vylučujících vzorů.</span><span class="sxs-lookup"><span data-stu-id="3f207-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="3f207-146">Pokud přesunete oddíl `case 0:` přepínač tak, že již není prvním oddílem v příkazu `switch`, vygeneruje chybu C# kompilátoru, protože celé číslo, jehož hodnota je nula, je podmnožina všech celých čísel, což je vzor definovaný pomocí příkazu `case int val`.</span><span class="sxs-lookup"><span data-stu-id="3f207-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="3f207-147">Tento problém můžete vyřešit a odstranit upozornění kompilátoru jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="3f207-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="3f207-148">Změnou pořadí oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="3f207-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="3f207-149">Pomocí [klauzule when](#when) v popisku `case`.</span><span class="sxs-lookup"><span data-stu-id="3f207-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="3f207-150">Případ `default`</span><span class="sxs-lookup"><span data-stu-id="3f207-150">The `default` case</span></span>

<span data-ttu-id="3f207-151">`default` případ určuje oddíl Switch, který se má provést, pokud výraz shody neodpovídá žádnému jinému popisku `case`.</span><span class="sxs-lookup"><span data-stu-id="3f207-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="3f207-152">Pokud není přítomen případ `default` a výraz shody neodpovídá žádnému jinému popisku `case`, tok programu spadá do příkazu `switch`.</span><span class="sxs-lookup"><span data-stu-id="3f207-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="3f207-153">`default` případ se může v příkazu `switch` zobrazit v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3f207-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="3f207-154">Bez ohledu na pořadí ve zdrojovém kódu je vždy vyhodnoceno jako poslední, po vyhodnocení všech `case`ch popisků.</span><span class="sxs-lookup"><span data-stu-id="3f207-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="3f207-155"><a name="pattern" /> porovnávání vzorů s příkazem `switch`</span><span class="sxs-lookup"><span data-stu-id="3f207-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="3f207-156">Každý příkaz `case` definuje vzor, který, pokud se shoduje s výrazem shody, způsobí, že obsahuje oddíl obsahujícího přepínače, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3f207-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="3f207-157">Všechny verze nástroje C# podporují konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="3f207-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="3f207-158">Zbývající vzorce jsou podporovány od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="3f207-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="3f207-159">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="3f207-159">Constant pattern</span></span>

<span data-ttu-id="3f207-160">Konstantní vzor testuje, zda se výraz shody rovná zadané konstantě.</span><span class="sxs-lookup"><span data-stu-id="3f207-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="3f207-161">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="3f207-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="3f207-162">kde *konstanta* je hodnota, která má být testována.</span><span class="sxs-lookup"><span data-stu-id="3f207-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="3f207-163">*konstanta* může být libovolný z následujících konstantních výrazů:</span><span class="sxs-lookup"><span data-stu-id="3f207-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="3f207-164">Literál [bool](../builtin-types/bool.md) : buď `true`, nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="3f207-164">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="3f207-165">Jakákoli [integrální](../builtin-types/integral-numeric-types.md) konstanta, například `int`, `long`nebo `byte`.</span><span class="sxs-lookup"><span data-stu-id="3f207-165">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="3f207-166">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="3f207-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="3f207-167">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="3f207-167">An enumeration constant.</span></span>
- <span data-ttu-id="3f207-168">Literál [znaků](../builtin-types/char.md) .</span><span class="sxs-lookup"><span data-stu-id="3f207-168">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="3f207-169">[Řetězcový](../builtin-types/reference-types.md) literál.</span><span class="sxs-lookup"><span data-stu-id="3f207-169">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="3f207-170">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3f207-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="3f207-171">Je *-li výraz* a *konstanta* integrální typy C# , operátor rovnosti určuje, zda výraz vrátí hodnotu `true` (tj. zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="3f207-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="3f207-172">V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .</span><span class="sxs-lookup"><span data-stu-id="3f207-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="3f207-173">V následujícím příkladu je použit model konstanty k určení, zda je konkrétní datum víkend, první den pracovního týdne, poslední den pracovního týdne nebo uprostřed pracovního týdne.</span><span class="sxs-lookup"><span data-stu-id="3f207-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="3f207-174">Vyhodnocuje vlastnost <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> aktuálního dne proti členům <xref:System.DayOfWeek> výčtu.</span><span class="sxs-lookup"><span data-stu-id="3f207-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="3f207-175">Následující příklad používá konstantní vzorek pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje automatický kavárnový počítač.</span><span class="sxs-lookup"><span data-stu-id="3f207-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="3f207-176">Vzor typu</span><span class="sxs-lookup"><span data-stu-id="3f207-176">Type pattern</span></span>

<span data-ttu-id="3f207-177">Vzor typu umožňuje napsat a převést stručný typ hodnocení.</span><span class="sxs-lookup"><span data-stu-id="3f207-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="3f207-178">Při použití s příkazem `switch` k provedení porovnávání se vzorem testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="3f207-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="3f207-179">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="3f207-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="3f207-180">kde *Type* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud je shoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="3f207-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="3f207-181">Typ *výrazu* v čase kompilace může být parametr obecného typu, počínaje C# 7,1.</span><span class="sxs-lookup"><span data-stu-id="3f207-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="3f207-182">Výraz `case` je `true`, pokud platí některá z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="3f207-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="3f207-183">*výraz* je instancí stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="3f207-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="3f207-184">*expr* je instance typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="3f207-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="3f207-185">Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="3f207-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="3f207-186">*výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*.</span><span class="sxs-lookup"><span data-stu-id="3f207-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="3f207-187">*Typ proměnné doby kompilace* proměnné je typ proměnné definovaný v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="3f207-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="3f207-188">*Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.</span><span class="sxs-lookup"><span data-stu-id="3f207-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="3f207-189">*expr* je instance typu, který implementuje rozhraní *typu* .</span><span class="sxs-lookup"><span data-stu-id="3f207-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="3f207-190">Pokud *je výraz Case pravdivý, má* jednoznačně přiřazený a má místní rozsah jenom v rámci oddílu Switch.</span><span class="sxs-lookup"><span data-stu-id="3f207-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="3f207-191">Všimněte si, že `null` neodpovídá typu.</span><span class="sxs-lookup"><span data-stu-id="3f207-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="3f207-192">Aby se shodovala s `null`, použijte následující `case` popisek:</span><span class="sxs-lookup"><span data-stu-id="3f207-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="3f207-193">V následujícím příkladu je použit vzor typu k poskytnutí informací o různých typech kolekcí.</span><span class="sxs-lookup"><span data-stu-id="3f207-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="3f207-194">Místo `object`můžete vytvořit obecnou metodu pomocí typu kolekce jako parametru typu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="3f207-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="3f207-195">Obecná verze se liší od první ukázky dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="3f207-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="3f207-196">Nejdříve nemůžete použít případ `null`.</span><span class="sxs-lookup"><span data-stu-id="3f207-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="3f207-197">Nemůžete použít žádný konstantní případ, protože kompilátor nemůže převést libovolný typ `T` na jiný typ než `object`.</span><span class="sxs-lookup"><span data-stu-id="3f207-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="3f207-198">Co byl `default` případ nyní testuje `object`, která není null.</span><span class="sxs-lookup"><span data-stu-id="3f207-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="3f207-199">To znamená, že `default` testy případu pouze pro `null`.</span><span class="sxs-lookup"><span data-stu-id="3f207-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="3f207-200">Bez porovnávání vzorů může být tento kód napsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3f207-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="3f207-201">Použití porovnávání vzorů typů vytváří více kompaktních a čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null` nebo aby prováděl opakované přetypování.</span><span class="sxs-lookup"><span data-stu-id="3f207-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="3f207-202"><a name="when" /> příkazu `case` a klauzule `when`</span><span class="sxs-lookup"><span data-stu-id="3f207-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="3f207-203">Počínaje C# 7,0, protože příkazy Case nemusejí být vzájemně exkluzivní, můžete přidat klauzuli `when` pro určení další podmínky, která musí být splněna, aby se příkaz Case vyhodnotil na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="3f207-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="3f207-204">Klauzule `when` může být libovolný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3f207-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="3f207-205">Následující příklad definuje základní třídu `Shape`, `Rectangle` třídu odvozenou z `Shape`a třídu `Square`, která je odvozena z `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="3f207-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="3f207-206">Používá klauzuli `when`, aby se zajistilo, že `ShowShapeInfo` zachází s objektem `Rectangle`, kterému byla přiřazena shodná délka a šířka jako `Square` i v případě, že nebyla vytvořena instance objektu `Square`.</span><span class="sxs-lookup"><span data-stu-id="3f207-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="3f207-207">Metoda se nepokusí zobrazit informace buď s objektem, který je `null` nebo tvar, jehož oblast je nula.</span><span class="sxs-lookup"><span data-stu-id="3f207-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="3f207-208">Všimněte si, že klauzule `when` v příkladu, která se pokouší otestovat, zda je objekt `Shape` `null` není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3f207-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="3f207-209">`case null:`je správný vzor typu pro otestování `null`.</span><span class="sxs-lookup"><span data-stu-id="3f207-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3f207-210">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f207-210">C# language specification</span></span>

<span data-ttu-id="3f207-211">Další informace naleznete v [příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="3f207-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="3f207-212">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3f207-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f207-213">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f207-213">See also</span></span>

- [<span data-ttu-id="3f207-214">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="3f207-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f207-215">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3f207-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3f207-216">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f207-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3f207-217">if-else</span><span class="sxs-lookup"><span data-stu-id="3f207-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="3f207-218">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="3f207-218">Pattern Matching</span></span>](../../pattern-matching.md)
