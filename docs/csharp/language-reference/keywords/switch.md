---
title: "Switch – klíčové slovo (referenční dokumentace jazyka C#)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c345d0c6c935271600a386752e18c19a25cc389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="switch-c-reference"></a><span data-ttu-id="09e79-102">switch – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="09e79-102">switch (C# Reference)</span></span>
<span data-ttu-id="09e79-103">`switch`je výběr příkaz, který vybere jeden *přepnout oddíl* provést ze seznamu kandidátů na základě vzor shody s *odpovídat výrazu*.</span><span class="sxs-lookup"><span data-stu-id="09e79-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span> 
  
 [!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

<span data-ttu-id="09e79-104">`switch` Příkaz se často používá jako alternativu k [if-else](if-else.md) vytvořit, pokud jeden výraz je testován vůči tři nebo více podmínek.</span><span class="sxs-lookup"><span data-stu-id="09e79-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="09e79-105">Například následující `switch` příkaz určuje, zda proměnná typu `Color` obsahuje jednu ze tří hodnot:</span><span class="sxs-lookup"><span data-stu-id="09e79-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span> 

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

<span data-ttu-id="09e79-106">Je ekvivalentní v následujícím příkladu, který používá `if` - `else` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="09e79-106">It is equivalent to the following example that uses an `if`-`else` construct.</span></span> 

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a><span data-ttu-id="09e79-107">Výrazy</span><span class="sxs-lookup"><span data-stu-id="09e79-107">The match expression</span></span>

<span data-ttu-id="09e79-108">Výrazy poskytuje hodnoty k porovnání vzorů v `case` popisky.</span><span class="sxs-lookup"><span data-stu-id="09e79-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="09e79-109">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="09e79-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="09e79-110">Výrazy jazyka C# 6, musí být výraz, který vrací hodnotu z těchto typů:</span><span class="sxs-lookup"><span data-stu-id="09e79-110">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="09e79-111">[char](char.md).</span><span class="sxs-lookup"><span data-stu-id="09e79-111">a [char](char.md).</span></span>
- <span data-ttu-id="09e79-112">[řetězec](string.md).</span><span class="sxs-lookup"><span data-stu-id="09e79-112">a [string](string.md).</span></span>
- <span data-ttu-id="09e79-113">[bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="09e79-113">a [bool](bool.md).</span></span> 
- <span data-ttu-id="09e79-114">integrální hodnoty, například [int](int.md) nebo [dlouho](long.md).</span><span class="sxs-lookup"><span data-stu-id="09e79-114">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="09e79-115">[výčtu](enum.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09e79-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="09e79-116">Od verze jazyka C# 7, výrazu shody může být jakýkoli výraz nesmí být nulová.</span><span class="sxs-lookup"><span data-stu-id="09e79-116">Starting with C# 7, the match expression can be any non-null expression.</span></span>
 
## <a name="the-switch-section"></a><span data-ttu-id="09e79-117">V části přepínače</span><span class="sxs-lookup"><span data-stu-id="09e79-117">The switch section</span></span>
 
 <span data-ttu-id="09e79-118">A `switch` příkaz obsahuje jeden nebo více oddíly přepínače.</span><span class="sxs-lookup"><span data-stu-id="09e79-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="09e79-119">Každá část přepínač obsahuje jeden nebo více *případ popisky* následuje jeden nebo více příkazů.</span><span class="sxs-lookup"><span data-stu-id="09e79-119">Each switch section contains one or more *case labels* followed by one or more statements.</span></span> <span data-ttu-id="09e79-120">Následující příklad ukazuje jednoduchý `switch` příkaz, který má tři části přepínače.</span><span class="sxs-lookup"><span data-stu-id="09e79-120">The following example shows a simple `switch` statement that has three switch sections.</span></span> <span data-ttu-id="09e79-121">Každý oddíl přepínače má jednoho návěstí, jako například `case 1:`a dvou příkazů.</span><span class="sxs-lookup"><span data-stu-id="09e79-121">Each switch section has one case label, such as `case 1:`, and two statements.</span></span>
 
  <span data-ttu-id="09e79-122">A `switch` příkaz může obsahovat libovolný počet oddílů přepínače, a každé části může mít jeden nebo více štítků případu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="09e79-122">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="09e79-123">Žádné dvě případu popisky však může obsahovat stejný výraz.</span><span class="sxs-lookup"><span data-stu-id="09e79-123">However, no two case labels may contain the same expression.</span></span>  

 [!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 <span data-ttu-id="09e79-124">Přepínač pouze jeden oddíl v příkazu switch provede.</span><span class="sxs-lookup"><span data-stu-id="09e79-124">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="09e79-125">C# neumožňuje spouštění z jednoho oddílu přepínač pokračovat na další.</span><span class="sxs-lookup"><span data-stu-id="09e79-125">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="09e79-126">Z tohoto důvodu se následující kód vygeneruje chybu kompilátoru CS0163: "ovládacího prvku nelze přejít z jednoho návěstí (<case label>) na jiný."</span><span class="sxs-lookup"><span data-stu-id="09e79-126">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>  

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
<span data-ttu-id="09e79-127">Tento požadavek se splní obvykle explicitně ukončení části přepínač pomocí [zalomení](break.md), [goto](goto.md), nebo [vrátit](return.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="09e79-127">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="09e79-128">Následující kód je však také platný, protože zajišťuje, že program řízení nelze přejít ke `default` přepnout oddíl.</span><span class="sxs-lookup"><span data-stu-id="09e79-128">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>
  
 [!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 <span data-ttu-id="09e79-129">Spuštění příkazu seznamu v části přepínače s případu popiskem, který odpovídá výrazu shody začíná první příkaz a pokračuje prostřednictvím seznamu příkaz obvykle dokud výpis přechod, například `break`, `goto case`, `goto label`, `return`, nebo `throw`, je dostupný.</span><span class="sxs-lookup"><span data-stu-id="09e79-129">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="09e79-130">V tomto okamžiku je ovládací prvek přenesen mimo `switch` příkaz nebo na jinou případu štítek.</span><span class="sxs-lookup"><span data-stu-id="09e79-130">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="09e79-131">A `goto` příkaz, pokud se používá, musí přenos řízení na konstantní štítek.</span><span class="sxs-lookup"><span data-stu-id="09e79-131">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="09e79-132">Toto omezení je nutné, protože probíhá pokus o přenos řízení na štítek nekonstantní může mít nežádoucí vedlejší účinky, takový přenos řízení na nezamýšleným umístění v kódu nebo vytváření nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="09e79-132">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="09e79-133">Case popisky</span><span class="sxs-lookup"><span data-stu-id="09e79-133">Case labels</span></span>

 <span data-ttu-id="09e79-134">Každý popisek případu určuje vzor k porovnání shody výrazu ( `caseSwitch` proměnné v předchozích příkladech).</span><span class="sxs-lookup"><span data-stu-id="09e79-134">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="09e79-135">Pokud se shodují, je ovládací prvek přenesen do části přepínač, který obsahuje **první** odpovídající případu popisek.</span><span class="sxs-lookup"><span data-stu-id="09e79-135">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="09e79-136">Pokud žádné návěstí vzor odpovídá výrazu shody, je ovládací prvek přenesen do části s `default` případu štítku, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="09e79-136">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="09e79-137">Pokud neexistuje žádné `default` případě žádné příkazy v žádné části přepínače jsou spouštěny a ovládací prvek je přenesen mimo `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="09e79-137">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

 <span data-ttu-id="09e79-138">Informace o `switch` příkaz a porovnávání vzorů, najdete v článku [porovnávání vzorů s `switch` příkaz](#pattern) části.</span><span class="sxs-lookup"><span data-stu-id="09e79-138">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

 <span data-ttu-id="09e79-139">Protože C# 6 podporuje pouze konstantní vzor a nepovoluje opakování konstantní hodnoty, případu popisky definovat vzájemně se vylučuje hodnoty a pouze jeden vzor může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="09e79-139">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="09e79-140">V důsledku toho, v jakém pořadí `case` příkazy zobrazí, je důležitý.</span><span class="sxs-lookup"><span data-stu-id="09e79-140">As a result, the order in which `case` statements appear is unimportant.</span></span>

 <span data-ttu-id="09e79-141">V jazyce C# 7 ale je podporována dalšími vzory případu popisky nemusíte definovat vzájemně se vylučuje hodnoty a více vzorů může odpovídat výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="09e79-141">In C# 7, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="09e79-142">Protože jsou vykonány pouze příkazy v části přepínač, který obsahuje první odpovídající vzor, v jakém pořadí `case` příkazy zobrazí, je důležité.</span><span class="sxs-lookup"><span data-stu-id="09e79-142">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="09e79-143">Pokud C# zjistí části přepínač, jehož case – příkaz nebo příkazy odpovídají nebo jsou podmnožinou tohoto předchozí příkazy, vygeneruje Chyba kompilátoru, CS8120, "případy switch již byla zpracována předchozí případem."</span><span class="sxs-lookup"><span data-stu-id="09e79-143">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span> 

 <span data-ttu-id="09e79-144">Následující příklad ilustruje `switch` příkaz, který používá celou řadu jiných vzájemně se vylučuje vzory.</span><span class="sxs-lookup"><span data-stu-id="09e79-144">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="09e79-145">Pokud přesunete `case 0:` přepnout oddíl tak, aby se už v první části v `switch` příkaz, C# generuje chybu kompilátoru, protože celé číslo, jehož hodnota je nulová je podmnožinou všechny celá čísla, což je vzoru definována podle `case int val` příkaz.</span><span class="sxs-lookup"><span data-stu-id="09e79-145">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

 [!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

<span data-ttu-id="09e79-146">Můžete opravit tento problém a eliminovat upozornění kompilátoru v jednom ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="09e79-146">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="09e79-147">Změnou pořadí částí přepínače.</span><span class="sxs-lookup"><span data-stu-id="09e79-147">By changing the order of the switch sections.</span></span> 
 
- <span data-ttu-id="09e79-148">Pomocí < /a name = "při" > při klauzule</a> v `case` popisek.</span><span class="sxs-lookup"><span data-stu-id="09e79-148">By using a </a name="when">when clause</a> in the `case` label.</span></span>
 
## <a name="the-default-case"></a><span data-ttu-id="09e79-149">`default` Případu</span><span class="sxs-lookup"><span data-stu-id="09e79-149">The `default` case</span></span>

<span data-ttu-id="09e79-150">`default` Případ určuje oddílu přepínač, který má provést Pokud výrazu shody neodpovídá žádné jiné `case` popisek.</span><span class="sxs-lookup"><span data-stu-id="09e79-150">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="09e79-151">Pokud `default` případu není k dispozici a výrazy neodpovídá žádné jiné `case` štítku, toku programu spadá `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="09e79-151">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="09e79-152">`default` Případ se mohou objevit v libovolném pořadí, v `switch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="09e79-152">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="09e79-153">Bez ohledu na jeho pořadí ve zdrojovém kódu, vždy vyhodnotí poslední, po všech `case` byly vyhodnoceny popisky.</span><span class="sxs-lookup"><span data-stu-id="09e79-153">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="09e79-154"><a name="pattern" />Shoda vzoru se `switch` – příkaz</span><span class="sxs-lookup"><span data-stu-id="09e79-154"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>
  
<span data-ttu-id="09e79-155">Každý `case` příkaz definuje vzor, který odpovídá výrazu shody vede k jeho obsahující části přepínače má být proveden.</span><span class="sxs-lookup"><span data-stu-id="09e79-155">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="09e79-156">Všechny verze jazyka C# podporovat vzoru konstantní.</span><span class="sxs-lookup"><span data-stu-id="09e79-156">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="09e79-157">Zbývající vzory jsou podporované od verze jazyka C# 7.</span><span class="sxs-lookup"><span data-stu-id="09e79-157">The remaining patterns are supported beginning with C# 7.</span></span> 
  
### <a name="constant-pattern"></a><span data-ttu-id="09e79-158">Konstantní vzor</span><span class="sxs-lookup"><span data-stu-id="09e79-158">Constant pattern</span></span> 

<span data-ttu-id="09e79-159">Konstantní vzor ověřuje, zda výrazu shody rovná zadané konstanta.</span><span class="sxs-lookup"><span data-stu-id="09e79-159">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="09e79-160">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="09e79-160">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="09e79-161">kde *konstantní* je hodnota, kterou chcete otestovat.</span><span class="sxs-lookup"><span data-stu-id="09e79-161">where *constant* is the value to test for.</span></span> <span data-ttu-id="09e79-162">*konstantní* může být libovolná z následujících konstantní výrazy:</span><span class="sxs-lookup"><span data-stu-id="09e79-162">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="09e79-163">A [bool](bool.md) literálu, buď `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="09e79-163">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="09e79-164">Všechny integrální konstanta, například [int](int.md), [dlouho](long.md), nebo [bajtů](byte.md).</span><span class="sxs-lookup"><span data-stu-id="09e79-164">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span> 
- <span data-ttu-id="09e79-165">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="09e79-165">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="09e79-166">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="09e79-166">An enumeration constant.</span></span>
- <span data-ttu-id="09e79-167">A [char](char.md) literálu.</span><span class="sxs-lookup"><span data-stu-id="09e79-167">A [char](char.md) literal.</span></span>
- <span data-ttu-id="09e79-168">A [řetězec](string.md) literálu.</span><span class="sxs-lookup"><span data-stu-id="09e79-168">A [string](string.md) literal.</span></span>

<span data-ttu-id="09e79-169">Konstantní výraz je vyhodnotit takto:</span><span class="sxs-lookup"><span data-stu-id="09e79-169">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="09e79-170">Pokud *expr* a *konstantní* jsou integrální typy operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="09e79-170">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="09e79-171">Jinak hodnota výrazu je určena voláním statických [Object.Equals (výraz, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metoda.</span><span class="sxs-lookup"><span data-stu-id="09e79-171">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="09e79-172">Následující příklad používá k určení, zda je konkrétní datum víkendu, první den v týdnu pracovní poslední den pracovní týden nebo středu pracovní dny vzoru konstantní.</span><span class="sxs-lookup"><span data-stu-id="09e79-172">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="09e79-173">Vyhodnocuje <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuálního dne na členech <xref:System.DayOfWeek> výčtu.</span><span class="sxs-lookup"><span data-stu-id="09e79-173">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span> 

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="09e79-174">Následující příklad používá konstantní vzor pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje se automatické kávy počítač.</span><span class="sxs-lookup"><span data-stu-id="09e79-174">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>
  
 [!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a><span data-ttu-id="09e79-175">Typ vzor</span><span class="sxs-lookup"><span data-stu-id="09e79-175">Type pattern</span></span>

<span data-ttu-id="09e79-176">Vzor typ umožňuje stručným typ vyhodnocení a převod.</span><span class="sxs-lookup"><span data-stu-id="09e79-176">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="09e79-177">Při použití s `switch` příkaz k provedení porovnávání vzorů testuje, zda výraz lze převést na zadaný typ a, pokud lze, obsahuje ji proměnné daného typu.</span><span class="sxs-lookup"><span data-stu-id="09e79-177">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="09e79-178">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="09e79-178">Its syntax is:</span></span>

```csharp
   case type varname 
```
<span data-ttu-id="09e79-179">kde *typ* je název typu, na který výsledek *expr* chcete převést, a *název_proměnné* je objekt, ke kterému výsledek *expr*je převést, pokud se podaří shody.</span><span class="sxs-lookup"><span data-stu-id="09e79-179">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> 

<span data-ttu-id="09e79-180">`case` Výraz `true` Pokud žádné z následujících:</span><span class="sxs-lookup"><span data-stu-id="09e79-180">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="09e79-181">*Expr* je instance stejného typu jako *typu*.</span><span class="sxs-lookup"><span data-stu-id="09e79-181">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="09e79-182">*Expr* představuje instanci typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="09e79-182">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="09e79-183">Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="09e79-183">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="09e79-184">*Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu* .</span><span class="sxs-lookup"><span data-stu-id="09e79-184">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="09e79-185">*Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="09e79-185">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="09e79-186">*Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="09e79-186">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="09e79-187">*Expr* představuje instanci typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="09e79-187">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="09e79-188">Pokud je nastavena hodnota true, případu výraz *název_proměnné* výborný přiřazen a má místní oboru v části přepínače.</span><span class="sxs-lookup"><span data-stu-id="09e79-188">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="09e79-189">Všimněte si, že `null` neodpovídá typu.</span><span class="sxs-lookup"><span data-stu-id="09e79-189">Note that `null` does not match a type.</span></span> <span data-ttu-id="09e79-190">Tak, aby odpovídala `null`, použijte následující `case` štítku:</span><span class="sxs-lookup"><span data-stu-id="09e79-190">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```
 
<span data-ttu-id="09e79-191">Následující příklad používá typ vzor k zadání informací o různé druhy typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="09e79-191">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="09e79-192">Bez porovnávání vzorů, může tento kód zapsat takto.</span><span class="sxs-lookup"><span data-stu-id="09e79-192">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="09e79-193">Použití porovnávání vzorů typu vytváří odstraněním potřeba otestovat, zda je výsledek převodu z kódu kompaktnější a čitelné `null` nebo provedení opakované přetypování.</span><span class="sxs-lookup"><span data-stu-id="09e79-193">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>  

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="09e79-194">`case` Příkaz a `when` – klauzule</span><span class="sxs-lookup"><span data-stu-id="09e79-194">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="09e79-195">Od verze jazyka C# 7, protože case – příkazy nemusí se vzájemně vylučují, můžete přidat `when` klauzule zadejte další podmínky, které musí být splněny pro příkaz case vyhodnotit na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="09e79-195">Starting with C# 7, because case statements need not be mutually exclusive, you can use add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="09e79-196">`when` Klauzule může být jakýkoli výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09e79-196">The `when` clause can be any expression that returns a Boolean value.</span></span> <span data-ttu-id="09e79-197">Jeden z běžných používá pro `when` klauzule slouží k části přepínač zabránit ve spouštění, pokud je hodnota výrazu shody `null`.</span><span class="sxs-lookup"><span data-stu-id="09e79-197">One of the more common uses for the `when` clause is used to prevent a switch section from executing when the value of a match expression is `null`.</span></span> 

 <span data-ttu-id="09e79-198">V následujícím příkladu definuje na základní `Shape` třída, `Rectangle` třídu odvozenou od `Shape`a `Square` třídu odvozenou od `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="09e79-198">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="09e79-199">Používá `when` klauzule zajistit, aby `ShowShapeInfo` zpracovává `Rectangle` objekt, který byl přiřazen stejné délky a šířky jako `Square` i když je nebyla vytvořena instance jako `Square` objektu.</span><span class="sxs-lookup"><span data-stu-id="09e79-199">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if is has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="09e79-200">Metoda nebude pokoušet o zobrazení informací o objekt, který je buď `null` nebo tvaru, jehož je nula.</span><span class="sxs-lookup"><span data-stu-id="09e79-200">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span> 

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
<span data-ttu-id="09e79-201">Všimněte si, že `when` klauzule v příkladu, který se pokusí o test zda `Shape` objekt `null` nepracuje.</span><span class="sxs-lookup"><span data-stu-id="09e79-201">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="09e79-202">Vzor správného typu chcete otestovat `null` je `case null:`.</span><span class="sxs-lookup"><span data-stu-id="09e79-202">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="09e79-203">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="09e79-203">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09e79-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="09e79-204">See Also</span></span>  

 [<span data-ttu-id="09e79-205">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="09e79-205">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="09e79-206">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="09e79-206">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="09e79-207">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="09e79-207">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="09e79-208">if-else</span><span class="sxs-lookup"><span data-stu-id="09e79-208">if-else</span></span>](if-else.md)  
 [<span data-ttu-id="09e79-209">Shoda vzoru</span><span class="sxs-lookup"><span data-stu-id="09e79-209">Pattern Matching</span></span>](../../pattern-matching.md)  
 

 
