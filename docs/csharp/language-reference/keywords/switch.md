---
title: Příkaz switch jazyka C#
ms.date: 08/14/2018
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
ms.openlocfilehash: 08b63d67b6175d18bee1317cc8908d876fbb4039
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394814"
---
# <a name="switch-c-reference"></a><span data-ttu-id="00980-102">Přepnout (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="00980-102">switch (C# reference)</span></span>

<span data-ttu-id="00980-103">`switch` je příkaz výběru, který vybere jeden *oddíl přepínání* ke spuštění ze seznamu kandidátů podle porovnávání s *odpovídat výrazu*.</span><span class="sxs-lookup"><span data-stu-id="00980-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="00980-104">`switch` Příkazu se často používá jako alternativu k [if-else](if-else.md) sestavit, pokud jeden výraz je testován vůči tři nebo více podmínek.</span><span class="sxs-lookup"><span data-stu-id="00980-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="00980-105">Například následující `switch` příkaz určuje, zda proměnná typu `Color` obsahuje jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="00980-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="00980-106">Je ekvivalentní v následujícím příkladu, který používá `if` - `else` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="00980-106">It is equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="00980-107">Výraz shody</span><span class="sxs-lookup"><span data-stu-id="00980-107">The match expression</span></span>

<span data-ttu-id="00980-108">Výrazy poskytuje hodnotu k porovnání vzorů v `case` popisky.</span><span class="sxs-lookup"><span data-stu-id="00980-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="00980-109">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="00980-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="00980-110">V jazyce C# 6 shoda výraz musí být výraz, který vrací hodnotu z těchto typů:</span><span class="sxs-lookup"><span data-stu-id="00980-110">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="00980-111">[char](char.md).</span><span class="sxs-lookup"><span data-stu-id="00980-111">a [char](char.md).</span></span>
- <span data-ttu-id="00980-112">[řetězec](string.md).</span><span class="sxs-lookup"><span data-stu-id="00980-112">a [string](string.md).</span></span>
- <span data-ttu-id="00980-113">[bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="00980-113">a [bool](bool.md).</span></span>
- <span data-ttu-id="00980-114">integrální hodnotu, například [int](int.md) nebo [dlouhé](long.md).</span><span class="sxs-lookup"><span data-stu-id="00980-114">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="00980-115">[výčtu](enum.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="00980-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="00980-116">Od verze C# 7.0, výrazu shody může být libovolný výraz jinou hodnotu než null.</span><span class="sxs-lookup"><span data-stu-id="00980-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="00980-117">Oddíl přepínače</span><span class="sxs-lookup"><span data-stu-id="00980-117">The switch section</span></span>

<span data-ttu-id="00980-118">A `switch` výpis obsahuje jeden nebo více oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="00980-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="00980-119">Každý oddíl přepínače obsahuje jednu nebo více *malá a velká popisky* (popisek případu nebo výchozí), za nímž následuje jedna nebo více příkazů.</span><span class="sxs-lookup"><span data-stu-id="00980-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="00980-120">`switch` Příkaz může obsahovat maximálně jednu výchozí popisek, umístěn v jakékoli části přepínače.</span><span class="sxs-lookup"><span data-stu-id="00980-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="00980-121">Následující příklad ukazuje jednoduchý `switch` příkaz, který obsahuje tři části přepínače, každá obsahuje dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="00980-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="00980-122">Druhý oddíl přepínače obsahuje `case 2:` a `case 3:` popisky.</span><span class="sxs-lookup"><span data-stu-id="00980-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="00980-123">A `switch` příkaz může obsahovat libovolný počet oddílů přepínače a každý oddíl může obsahovat jeden nebo více štítků případu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="00980-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="00980-124">Žádné dva popisky případů však může obsahovat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="00980-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="00980-125">Provede přepínači pouze jeden oddíl v příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="00980-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="00980-126">C# neumožňuje spuštění pokračovat z jednoho oddílu přepnutí na další.</span><span class="sxs-lookup"><span data-stu-id="00980-126">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="00980-127">Proto následující kód vygeneruje chybu kompilátoru CS0163: "ovládací prvek nemůže být předáno z jednoho návěstí příkazu case (<case label>) do jiného."</span><span class="sxs-lookup"><span data-stu-id="00980-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>

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

<span data-ttu-id="00980-128">Tento požadavek obvykle splněn explicitně ukončením oddíl přepínače s použitím [přerušení](break.md), [goto](goto.md), nebo [vrátit](return.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="00980-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="00980-129">Následující kód je však také platný, protože zajistí, že ovládací prvek programu nemůže být předáno `default` přepnutí oddílu.</span><span class="sxs-lookup"><span data-stu-id="00980-129">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="00980-130">Spuštění seznamu příkazů ve oddíl přepínače case popiskem, který odpovídá výrazu match začíná prvním příkazem a pokračuje přes seznam příkazů, obvykle dokud výpisu odkazů, jako například `break`, `goto case`, `goto label`, `return`, nebo `throw`, je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="00980-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="00980-131">V tomto okamžiku je ovládací prvek převeden mimo `switch` příkaz nebo jiný popisek případu.</span><span class="sxs-lookup"><span data-stu-id="00980-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="00980-132">A `goto` příkazu, pokud se používá, musí řízení je převedeno na konstantní popisek.</span><span class="sxs-lookup"><span data-stu-id="00980-132">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="00980-133">Toto omezení je nezbytné, protože pokus o předání řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, takový přenos řízení na neúmyslnému umístění v kódu nebo vytváření nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="00980-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="00980-134">Popisky případu</span><span class="sxs-lookup"><span data-stu-id="00980-134">Case labels</span></span>

<span data-ttu-id="00980-135">Každý popisek případu určuje vzor k porovnání s výrazu match ( `caseSwitch` proměnné v předchozích příkladech).</span><span class="sxs-lookup"><span data-stu-id="00980-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="00980-136">Pokud se shodují, ovládací prvek bude převeden do části přepínač, který obsahuje **první** odpovídající popisek případu.</span><span class="sxs-lookup"><span data-stu-id="00980-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="00980-137">Pokud žádný popisek případu vzor odpovídá výrazu shody, ovládací prvek bude převeden do části s `default` popisek příkazu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="00980-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="00980-138">Pokud není žádný `default` případu, jsou provedeny žádné příkazy v jakékoli části přepínače a ovládací prvek bude převeden mimo `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="00980-138">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="00980-139">Informace o tom, `switch` příkazu a porovnávání vzorů, najdete v článku [porovnávání vzorů s `switch` příkaz](#pattern) oddílu.</span><span class="sxs-lookup"><span data-stu-id="00980-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="00980-140">Protože C# 6 podporuje pouze konstantní vzorek a nepovoluje opakování konstantní hodnoty, popisky případu definovat vzájemně se vylučuje hodnoty a pouze jeden vzor odpovídá výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="00980-140">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="00980-141">V důsledku toho pořadí, ve kterém `case` příkazy se zobrazí, nedůležité.</span><span class="sxs-lookup"><span data-stu-id="00980-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="00980-142">V jazyce C# 7.0 ale protože jsou podporována další způsoby, popisky případů není nutné definovat vzájemně se vylučuje hodnoty a více vzorům může odpovídat výrazu match.</span><span class="sxs-lookup"><span data-stu-id="00980-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="00980-143">Protože jsou spouštěny příkazy v části přepínače, který obsahuje první odpovídající vzor, pořadí, ve kterém `case` příkazy se zobrazí, je důležité.</span><span class="sxs-lookup"><span data-stu-id="00980-143">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="00980-144">Pokud C# zjistí části přepínače, jejichž case – příkaz nebo příkazy jsou ekvivalentní, nebo jsou podmnožinou tohoto předchozích příkazů, vygeneruje chybu kompilátoru, CS8120, "případ přepínače se už zpracovala předchozí větví."</span><span class="sxs-lookup"><span data-stu-id="00980-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="00980-145">Následující příklad ukazuje `switch` příkaz, který používá celou řadu jiných vzájemně se vylučující vzory.</span><span class="sxs-lookup"><span data-stu-id="00980-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="00980-146">Pokud přesunete `case 0:` oddíl přepínání tak, aby se už v první části `switch` prohlášení, C# vygeneruje chybu kompilátoru, protože celé číslo, jehož hodnota je nula je podmnožinou všech celých čísel, který je definován vzor podle `case int val` příkaz.</span><span class="sxs-lookup"><span data-stu-id="00980-146">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="00980-147">Můžete tento problém vyřešit a vyloučit upozornění kompilátoru v jednom ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="00980-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="00980-148">Změnou pořadí oddílů přepínače.</span><span class="sxs-lookup"><span data-stu-id="00980-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="00980-149">Pomocí < /a name = "kdy" > při klauzule</a> v `case` popisek.</span><span class="sxs-lookup"><span data-stu-id="00980-149">By using a </a name="when">when clause</a> in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="00980-150">`default` Případ</span><span class="sxs-lookup"><span data-stu-id="00980-150">The `default` case</span></span>

<span data-ttu-id="00980-151">`default` Případu určuje části přepínače, které budou spuštěny, pokud výrazu shody se neshoduje s jinými `case` popisek.</span><span class="sxs-lookup"><span data-stu-id="00980-151">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="00980-152">Pokud `default` případ není k dispozici a výrazu shody se neshoduje s jinými `case` popisek, nepropadla tok programu `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="00980-152">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="00980-153">`default` Případu se mohou objevit v libovolném pořadí, v `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="00980-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="00980-154">Bez ohledu na jeho pořadí ve zdrojovém kódu, je vždy vyhodnocen poslední koneckonců `case` popisky vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="00980-154">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="00980-155"><a name="pattern" /> Porovnávání vzorů s `switch` – příkaz</span><span class="sxs-lookup"><span data-stu-id="00980-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="00980-156">Každý `case` prohlášení definuje vzor, který, pokud odpovídá výrazu shody způsobí, že jeho nadřazený oddíl přepínače má být proveden.</span><span class="sxs-lookup"><span data-stu-id="00980-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="00980-157">Všechny verze jazyka C# podporují konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="00980-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="00980-158">Zbývající vzory jsou podporované od verze C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="00980-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="00980-159">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="00980-159">Constant pattern</span></span>

<span data-ttu-id="00980-160">Konstantní vzorek testuje, jestli výrazu shody rovná zadané – konstanta.</span><span class="sxs-lookup"><span data-stu-id="00980-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="00980-161">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="00980-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="00980-162">kde *konstantní* je hodnota pro testování.</span><span class="sxs-lookup"><span data-stu-id="00980-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="00980-163">*konstantní* může být následující konstantní výrazy:</span><span class="sxs-lookup"><span data-stu-id="00980-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="00980-164">A [bool](bool.md) literálu, buď `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="00980-164">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="00980-165">Všech integrálového konstantní, například [int](int.md), [dlouhé](long.md), nebo [bajtů](byte.md).</span><span class="sxs-lookup"><span data-stu-id="00980-165">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span>
- <span data-ttu-id="00980-166">Název deklarovanou `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="00980-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="00980-167">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="00980-167">An enumeration constant.</span></span>
- <span data-ttu-id="00980-168">A [char](char.md) literálu.</span><span class="sxs-lookup"><span data-stu-id="00980-168">A [char](char.md) literal.</span></span>
- <span data-ttu-id="00980-169">A [řetězec](string.md) literálu.</span><span class="sxs-lookup"><span data-stu-id="00980-169">A [string](string.md) literal.</span></span>

<span data-ttu-id="00980-170">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="00980-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="00980-171">Pokud *expr* a *konstantní* integrální typy jsou operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="00980-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="00980-172">V opačném případě je hodnota výrazu určena voláním statické [funkci Object.Equals (expr, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="00980-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="00980-173">Následující příklad používá konstantní vzorek k určení, zda je určitý den víkendu, první den v týdnu práce, poslední den v týdnu pracovní nebo střední pracovního týdne.</span><span class="sxs-lookup"><span data-stu-id="00980-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="00980-174">Je vyhodnocen jako <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuálního dne na členech <xref:System.DayOfWeek> výčtu.</span><span class="sxs-lookup"><span data-stu-id="00980-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="00980-175">Následující příklad používá pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje počítače s automatickou kávy konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="00980-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="00980-176">Vzorek typu</span><span class="sxs-lookup"><span data-stu-id="00980-176">Type pattern</span></span>

<span data-ttu-id="00980-177">Model typu umožňuje stručný typ vyhodnocení a převodu.</span><span class="sxs-lookup"><span data-stu-id="00980-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="00980-178">Při použití s `switch` příkaz k provedení porovnávání vzorů, testuje výraz lze převést na zadaný typ a zda může být, přetypování pro proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="00980-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="00980-179">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="00980-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="00980-180">kde *typ* je název typu, na který výsledek *expr* se má převést, a *název_proměnné* je objekt, na který výsledek *expr*je převeden v případě, že porovnání se zdaří.</span><span class="sxs-lookup"><span data-stu-id="00980-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span>

<span data-ttu-id="00980-181">`case` Výraz je `true` Pokud je splněna některá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="00980-181">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="00980-182">*výraz* je instance stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="00980-182">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="00980-183">*výraz* je instance typu, který je odvozen od *typ*.</span><span class="sxs-lookup"><span data-stu-id="00980-183">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="00980-184">Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.</span><span class="sxs-lookup"><span data-stu-id="00980-184">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="00980-185">*výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*.</span><span class="sxs-lookup"><span data-stu-id="00980-185">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="00980-186">*Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="00980-186">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="00980-187">*Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="00980-187">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="00980-188">*výraz* je instance typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00980-188">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="00980-189">Pokud je hodnota true, výraz case *název_proměnné* je jednoznačně přiřazovat a má místní rozsah v rámci části přepínače.</span><span class="sxs-lookup"><span data-stu-id="00980-189">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="00980-190">Všimněte si, že `null` se neshoduje s typem.</span><span class="sxs-lookup"><span data-stu-id="00980-190">Note that `null` does not match a type.</span></span> <span data-ttu-id="00980-191">Tak, aby odpovídaly `null`, použijte následující `case` popisku:</span><span class="sxs-lookup"><span data-stu-id="00980-191">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="00980-192">Následující příklad používá vzor typu k poskytnutí informací o různé druhy typů kolekce.</span><span class="sxs-lookup"><span data-stu-id="00980-192">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="00980-193">Bez porovnávání vzorů, může být napsán takto následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="00980-193">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="00980-194">Použití porovnávání vzorů typu produkuje kompaktnějším čitelné kódu pomocí tím eliminuje nutnost otestovat, jestli je výsledek převodu `null` nebo provádět opakované přetypování.</span><span class="sxs-lookup"><span data-stu-id="00980-194">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="00980-195"><a name="when" /> `case` Příkazu a `when` – klauzule</span><span class="sxs-lookup"><span data-stu-id="00980-195"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="00980-196">Od verze C# 7.0, protože příkazy case musí být vzájemně se vylučující, můžete přidat `when` klauzule zadejte další podmínky, které musí být splněny pro příkaz case vyhodnotit na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="00980-196">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="00980-197">`when` Klauzule může být libovolný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="00980-197">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="00980-198">Následující příklad definuje základní `Shape` třídy, `Rectangle` třídu odvozenou od `Shape`a `Square` třídu odvozenou od `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="00980-198">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="00980-199">Používá `when` klauzule zajistěte, aby `ShowShapeInfo` zpracovává `Rectangle` objekt, který má přiřazenou stejné délky a šířky jako `Square` i v případě, že nebyla inicializována jako `Square` objektu.</span><span class="sxs-lookup"><span data-stu-id="00980-199">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="00980-200">Metoda se nepokusí k zobrazení informací o objektu, který je buď `null` nebo tvar, jehož obsah je nula.</span><span class="sxs-lookup"><span data-stu-id="00980-200">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="00980-201">Všimněte si, že `when` klauzule v příkladu, která se pokusí otestovat, jestli `Shape` objekt `null` nespustí.</span><span class="sxs-lookup"><span data-stu-id="00980-201">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="00980-202">Vzor správný typ pro testování `null` je `case null:`.</span><span class="sxs-lookup"><span data-stu-id="00980-202">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="00980-203">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="00980-203">C# language specification</span></span>

<span data-ttu-id="00980-204">Další informace najdete v tématu [příkazu switch](/dotnet/csharp/language-reference/language-specification/statements#the-switch-statement) v [specifikace jazyka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="00980-204">For more information, see [The switch statement](/dotnet/csharp/language-reference/language-specification/statements#the-switch-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="00980-205">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="00980-205">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="00980-206">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00980-206">See also</span></span>

- [<span data-ttu-id="00980-207">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="00980-207">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="00980-208">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="00980-208">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="00980-209">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="00980-209">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="00980-210">if-else</span><span class="sxs-lookup"><span data-stu-id="00980-210">if-else</span></span>](if-else.md)
- [<span data-ttu-id="00980-211">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="00980-211">Pattern Matching</span></span>](../../pattern-matching.md)