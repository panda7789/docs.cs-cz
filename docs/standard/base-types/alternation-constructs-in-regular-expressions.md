---
title: Konstrukce alternace v regulárních výrazech rozhraní .NET
description: Přečtěte si, jak používat konstrukce alternace pro podmíněné párování v regulárních výrazech.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159686"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="2251a-103">Konstrukce alternace v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="2251a-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="2251a-104">Konstrukce alternace upravují regulární výraz tak, aby umožňoval nebo nebo podmíněné porovnávání.</span><span class="sxs-lookup"><span data-stu-id="2251a-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="2251a-105">.NET podporuje tři konstrukce alternace:</span><span class="sxs-lookup"><span data-stu-id="2251a-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="2251a-106">Porovnávání vzorů s &#124;</span><span class="sxs-lookup"><span data-stu-id="2251a-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="2251a-107">Podmíněné shody s (?( výraz)ano&#124;ne)</span><span class="sxs-lookup"><span data-stu-id="2251a-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="2251a-108">Podmíněné párování založené na platné zachycené skupině</span><span class="sxs-lookup"><span data-stu-id="2251a-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="2251a-109">Porovnávání vzorů s &#124;</span><span class="sxs-lookup"><span data-stu-id="2251a-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="2251a-110">Můžete použít svislý pruh (`|`) znak, aby odpovídaly `|` některý z řady vzorků, kde znak odděluje každý vzorek.</span><span class="sxs-lookup"><span data-stu-id="2251a-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="2251a-111">Stejně jako třída `|` kladných znaků lze znak použít tak, aby odpovídal libovolnému z několika jednotlivých znaků.</span><span class="sxs-lookup"><span data-stu-id="2251a-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="2251a-112">Následující příklad používá kladné třídy znaků a buď/nebo vzor odpovídající `|` znak u hledání výskytů slov "šedá" nebo "šedá" v řetězci.</span><span class="sxs-lookup"><span data-stu-id="2251a-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="2251a-113">V tomto případě `|` znak vytvoří regulární výraz, který je podrobnější.</span><span class="sxs-lookup"><span data-stu-id="2251a-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="2251a-114">Regulární výraz, `|` který `\bgr(a|e)y\b`používá znak , je interpretován tak, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="2251a-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="2251a-115">Vzor</span><span class="sxs-lookup"><span data-stu-id="2251a-115">Pattern</span></span>|<span data-ttu-id="2251a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2251a-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="2251a-117">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="2251a-118">Zápas znaky "gr".</span><span class="sxs-lookup"><span data-stu-id="2251a-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="2251a-119">Porovná buď se znakem „a“, nebo s „e“.</span><span class="sxs-lookup"><span data-stu-id="2251a-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="2251a-120">Porovná "y" na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="2251a-121">Znak `|` lze také použít k provedení buď nebo zápas s více znaky nebo podvýrazy, které mohou zahrnovat libovolnou kombinaci literálů znaků a prvků jazyka regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="2251a-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="2251a-122">(Třída znaků tuto funkci neposkytuje.) Následující příklad používá `|` znak k extrahování čísla sociálního zabezpečení USA (SSN), což je 9místné číslo s formátem *ddd*-*dd*-*dddd*, nebo identifikační číslo zaměstnavatele USA (EIN), což je 9místné číslo s formátem *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="2251a-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="2251a-123">Regulární `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` výraz je interpretován tak, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="2251a-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="2251a-124">Vzor</span><span class="sxs-lookup"><span data-stu-id="2251a-124">Pattern</span></span>|<span data-ttu-id="2251a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2251a-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="2251a-126">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="2251a-127">Shoda jedné z následujících hodnot: dvě desetinná místa následovaná pomlčkou následovanou sedmi desetinnými místy; nebo tři desetinné číslice, pomlčku, dvě desetinné číslice, jiný spojovník a čtyři desetinné číslice.</span><span class="sxs-lookup"><span data-stu-id="2251a-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="2251a-128">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="2251a-129">Podmíněné shody s výrazem</span><span class="sxs-lookup"><span data-stu-id="2251a-129">Conditional matching with an expression</span></span>

<span data-ttu-id="2251a-130">Tento element jazyka se pokusí porovnat jeden ze dvou vzorů v závislosti na tom, zda může odpovídat počáteční vzorek.</span><span class="sxs-lookup"><span data-stu-id="2251a-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="2251a-131">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="2251a-131">Its syntax is:</span></span>  

<span data-ttu-id="2251a-132">`(?(`*výraz* `)` *ano* `|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="2251a-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="2251a-133">kde *výraz* je počáteční vzor, který se má shodovat, *ano* je vzorek, který odpovídá, pokud je *výraz* spárován, a *ne* je volitelný vzor, který odpovídá, pokud *výraz* není spárován.</span><span class="sxs-lookup"><span data-stu-id="2251a-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="2251a-134">Modul regulárních výrazů považuje *výraz* za výraz s nulovou šířkou; to znamená, že modul regulárních výrazů nepostoupí ve vstupním datovém proudu po vyhodnocení *výrazu*.</span><span class="sxs-lookup"><span data-stu-id="2251a-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="2251a-135">Proto tato konstrukce je ekvivalentní následující:</span><span class="sxs-lookup"><span data-stu-id="2251a-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="2251a-136">`(?(?=`*výraz* `)` *ano* `|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="2251a-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="2251a-137">kde `(?=` *výraz* `)` je konstrukce výrazu s nulovou šířkou.</span><span class="sxs-lookup"><span data-stu-id="2251a-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="2251a-138">(Další informace naleznete v [tématu Seskupování konstrukcí](grouping-constructs-in-regular-expressions.md).) Vzhledem k tomu, že modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz s nulovou šířkou), musí být *výraz* emitrovaný s nulovou šířkou (další informace viz [Kotvy)](anchors-in-regular-expressions.md)nebo dílčí výraz, který je také obsažen v *ano*.</span><span class="sxs-lookup"><span data-stu-id="2251a-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="2251a-139">V opačném případě nelze spárovat vzor *yes.*</span><span class="sxs-lookup"><span data-stu-id="2251a-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2251a-140">Pokud je *výraz* pojmenovaná nebo číslovaná zachytávající skupina, konstrukce alternace je interpretována jako test sběru; Další informace naleznete v další části [Podmíněné shody založené na platné skupině zachycení](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="2251a-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="2251a-141">Jinými slovy modul regulárních výrazů se nepokouší odpovídat zachycenépodřetězec, ale místo toho testuje přítomnost nebo nepřítomnost skupiny.</span><span class="sxs-lookup"><span data-stu-id="2251a-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="2251a-142">Následující příklad je varianta příkladu, který se zobrazí v [buď/nebo porovnávání vzorků s &#124;](#Either_Or) části.</span><span class="sxs-lookup"><span data-stu-id="2251a-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="2251a-143">Používá podmíněné porovnávání k určení, zda první tři znaky za hranice slova jsou dvě číslice následované pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="2251a-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="2251a-144">Pokud ano, pokusí se porovnat identifikační číslo amerického zaměstnavatele (EIN).</span><span class="sxs-lookup"><span data-stu-id="2251a-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="2251a-145">Pokud ne, pokusí se porovnat číslo sociálního zabezpečení USA (SSN).</span><span class="sxs-lookup"><span data-stu-id="2251a-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="2251a-146">Vzor regulárního výrazu `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="2251a-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="2251a-147">Vzor</span><span class="sxs-lookup"><span data-stu-id="2251a-147">Pattern</span></span>|<span data-ttu-id="2251a-148">Popis</span><span class="sxs-lookup"><span data-stu-id="2251a-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="2251a-149">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="2251a-150">Určete, zda se následující tři znaky skládají ze dvou číslic následovaných pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="2251a-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="2251a-151">Pokud se předchozí vzorek shoduje, shodovat se dvěma číslicemi následovanými pomlčkou následovanou sedmi číslicemi.</span><span class="sxs-lookup"><span data-stu-id="2251a-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="2251a-152">Pokud předchozí vzorek neodpovídá, shodovat se třemi desetinnými místy, pomlčkou, dvěma desetinnými místy, jinou pomlčkou a čtyřmi desetinnými místy.</span><span class="sxs-lookup"><span data-stu-id="2251a-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="2251a-153">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="2251a-154">Podmíněné párování založené na platné zachycené skupině</span><span class="sxs-lookup"><span data-stu-id="2251a-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="2251a-155">Tento element jazyka se pokusí porovnat jeden ze dvou vzorů v závislosti na tom, zda odpovídá zadané zachytávající skupině.</span><span class="sxs-lookup"><span data-stu-id="2251a-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="2251a-156">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="2251a-156">Its syntax is:</span></span>

<span data-ttu-id="2251a-157">`(?(`*jméno* `)` *ano* `|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="2251a-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="2251a-158">– nebo –</span><span class="sxs-lookup"><span data-stu-id="2251a-158">or</span></span>

<span data-ttu-id="2251a-159">`(?(`*číslo* `)` *ano* `|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="2251a-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="2251a-160">kde *název* je název a *číslo* je číslo zachytávající skupiny, *ano* je výraz, který se má shodovat, pokud *název* nebo *číslo* má shodu, a *ne* je volitelný výraz, který se má shodovat, pokud tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="2251a-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="2251a-161">Pokud *název* neodpovídá názvu zachytávající skupiny, která se používá ve vzoru regulárního výrazu, konstrukce alternace je interpretována jako test výrazů, jak je vysvětleno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="2251a-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="2251a-162">Obvykle to znamená, *expression* že výraz `false`vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="2251a-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="2251a-163">Pokud *number* neodpovídá číslované zachytávající skupině, která se používá ve vzoru <xref:System.ArgumentException>regulárních výrazů, modul regulárních výrazů vyvolá .</span><span class="sxs-lookup"><span data-stu-id="2251a-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="2251a-164">Následující příklad je varianta příkladu, který se zobrazí v [buď/nebo porovnávání vzorků s &#124;](#Either_Or) části.</span><span class="sxs-lookup"><span data-stu-id="2251a-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="2251a-165">Používá zachytávající `n2` skupinu s názvem, která se skládá ze dvou číslic následovaných pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="2251a-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="2251a-166">Konstrukce alternace testuje, zda tato zachytávající skupina byla spárována ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="2251a-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="2251a-167">Pokud ano, konstrukce alternace se pokusí porovnat posledních sedm číslic devítimístného identifikačního čísla zaměstnavatele USA (EIN).</span><span class="sxs-lookup"><span data-stu-id="2251a-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="2251a-168">Pokud tomu tak není, pokusí se porovnat devítimístné číslo sociálního zabezpečení USA (SSN).</span><span class="sxs-lookup"><span data-stu-id="2251a-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="2251a-169">Vzor regulárního výrazu `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="2251a-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="2251a-170">Vzor</span><span class="sxs-lookup"><span data-stu-id="2251a-170">Pattern</span></span>|<span data-ttu-id="2251a-171">Popis</span><span class="sxs-lookup"><span data-stu-id="2251a-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="2251a-172">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="2251a-173">Porovná nulový nebo jeden výskyt dvou číslic následovaný pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="2251a-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="2251a-174">Pojmenujte tuto `n2`zachytávající skupinu .</span><span class="sxs-lookup"><span data-stu-id="2251a-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="2251a-175">Otestujte, zda `n2` byl spárován ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="2251a-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="2251a-176">Pokud `n2` byla spárována, porovná sedm desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="2251a-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="2251a-177">Pokud `n2` nebyla spárována, porovná tři desetinná místa, pomlčku, dvě desetinné číslice, jiný spojovník a čtyři desetinné číslice.</span><span class="sxs-lookup"><span data-stu-id="2251a-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="2251a-178">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="2251a-178">Match a word boundary.</span></span>|  

<span data-ttu-id="2251a-179">Varianta tohoto příkladu, který používá číslovou skupinu namísto pojmenované skupiny, je uvedena v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2251a-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="2251a-180">Jeho vzor regulárního výrazu je `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="2251a-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="2251a-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="2251a-181">See also</span></span>

- [<span data-ttu-id="2251a-182">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="2251a-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
