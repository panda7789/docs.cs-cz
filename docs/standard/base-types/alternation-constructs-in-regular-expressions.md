---
title: Konstrukce alternace v regulárních výrazech .NET
description: Naučte se používat konstrukce alternace pro podmíněné porovnání v regulárních výrazech.
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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: c6f33023d747ce20964c7cb83a66d6764b6030cd
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736618"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="a7428-103">Konstrukce alternace v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="a7428-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="a7428-104">Konstrukce alternace upravují regulární výraz pro povolení nebo podmíněné porovnání.</span><span class="sxs-lookup"><span data-stu-id="a7428-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="a7428-105">Rozhraní .NET podporuje tři konstrukce alternace:</span><span class="sxs-lookup"><span data-stu-id="a7428-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="a7428-106">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="a7428-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="a7428-107">Podmíněné porovnání s (? ( výraz) Ano&#124;ne)</span><span class="sxs-lookup"><span data-stu-id="a7428-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="a7428-108">Podmíněné porovnání na základě platné zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="a7428-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="a7428-109">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="a7428-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="a7428-110">Znak svislé čáry (`|`) můžete použít k vyhledání jedné z řady vzorů, kde znak `|` odděluje každý vzorek.</span><span class="sxs-lookup"><span data-stu-id="a7428-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="a7428-111">Podobně jako třída pozitivního znaku, znak `|` lze použít k porovnávání kteréhokoli z několika jednoduchých znaků.</span><span class="sxs-lookup"><span data-stu-id="a7428-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="a7428-112">V následujícím příkladu je použita třída pozitivního znaku a buď porovnávání se vzorem, nebo pomocí znaku `|` pro vyhledání výskytů slov "Gray" nebo "šedá" v řetězci.</span><span class="sxs-lookup"><span data-stu-id="a7428-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="a7428-113">V tomto případě znak `|` vytvoří regulární výraz, který je podrobnější.</span><span class="sxs-lookup"><span data-stu-id="a7428-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="a7428-114">Regulární výraz, který používá znak `|`, `\bgr(a|e)y\b`, je interpretován tak, jak je uvedeno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a7428-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="a7428-115">Vzor</span><span class="sxs-lookup"><span data-stu-id="a7428-115">Pattern</span></span>|<span data-ttu-id="a7428-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a7428-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a7428-117">Začněte na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="a7428-118">Porovnává se se znaky "GR".</span><span class="sxs-lookup"><span data-stu-id="a7428-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="a7428-119">Porovnává buď se znakem "a", nebo "e".</span><span class="sxs-lookup"><span data-stu-id="a7428-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="a7428-120">Porovnává s "y" na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="a7428-121">Znak `|` lze také použít k provedení shody s více znaky nebo podvýrazy, které mohou obsahovat libovolnou kombinaci znakových literálů a prvků jazyka regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="a7428-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="a7428-122">(Třída znaků tuto funkci neposkytuje.) V následujícím příkladu se pomocí znaku `|` extrahuje buď číslo sociálního pojištění (rodné číslo), což je 9 číslic, ve formátu *ddd*-*DD*-*dddd*, nebo v USA (EIN) identifikační číslo (), což je 9 číslic čísla ve formátu *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="a7428-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="a7428-123">Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a7428-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="a7428-124">Vzor</span><span class="sxs-lookup"><span data-stu-id="a7428-124">Pattern</span></span>|<span data-ttu-id="a7428-125">Popis</span><span class="sxs-lookup"><span data-stu-id="a7428-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a7428-126">Začněte na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="a7428-127">Porovnává jednu z následujících hodnot: dvě desítkové číslice následované spojovníkem a sedmi desítkových číslic; nebo tři desítkové číslice, pomlčky, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="a7428-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="a7428-128">Ukončí porovnávání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="a7428-129">Podmíněné porovnání s výrazem</span><span class="sxs-lookup"><span data-stu-id="a7428-129">Conditional matching with an expression</span></span>

<span data-ttu-id="a7428-130">Tento prvek jazyka se pokusí vyhledat jeden ze dvou vzorů v závislosti na tom, zda se může shodovat s počátečním vzorem.</span><span class="sxs-lookup"><span data-stu-id="a7428-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="a7428-131">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="a7428-131">Its syntax is:</span></span>  

<span data-ttu-id="a7428-132">*výraz* `(?(` `)` *Ano* `|` *žádná* `)`</span><span class="sxs-lookup"><span data-stu-id="a7428-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a7428-133">*výraz* WHERE je počáteční vzorek, který se má shodovat, *Ano* je vzor, který se má shodovat, pokud se *výraz* shoduje, a *ne* je volitelný vzor, který by odpovídal, pokud se *výraz* neshoduje.</span><span class="sxs-lookup"><span data-stu-id="a7428-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="a7428-134">Modul regulárních výrazů považuje *výraz* za kontrolní výraz s nulovou šířkou; To znamená, že modul regulárních výrazů není ve vstupním datovém proudu před vyhodnocením *výrazu*.</span><span class="sxs-lookup"><span data-stu-id="a7428-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="a7428-135">Proto je tato konstrukce ekvivalentní následujícímu:</span><span class="sxs-lookup"><span data-stu-id="a7428-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="a7428-136">*výraz* `(?(?=` `)` *Ano* `|` *žádná* `)`</span><span class="sxs-lookup"><span data-stu-id="a7428-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a7428-137">kde*výraz*`(?=` `)` je konstrukce kontrolního výrazu s nulovou šířkou.</span><span class="sxs-lookup"><span data-stu-id="a7428-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="a7428-138">(Další informace naleznete v tématu [seskupovací konstrukce](grouping-constructs-in-regular-expressions.md).) Vzhledem k tomu, že modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz s nulovou šířkou), musí být *výraz* buď kontrolní výraz s nulovou šířkou (Další informace naleznete v tématu [kotvy](anchors-in-regular-expressions.md)) nebo dílčí výraz, který je také obsažen v *Ano*.</span><span class="sxs-lookup"><span data-stu-id="a7428-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="a7428-139">V opačném případě nelze porovnat vzor *Ano* .</span><span class="sxs-lookup"><span data-stu-id="a7428-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7428-140">Pokud je *výraz* pojmenovanou nebo číslovanou zachytávající skupinou, konstrukce alternace je interpretována jako test Capture; Další informace najdete v další části s [podmíněným porovnáním na základě platné skupiny zachycení](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="a7428-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="a7428-141">Jinými slovy, modul regulárních výrazů se nepokusí porovnat zachycený dílčí řetězec, ale místo toho testuje přítomnost nebo nepřítomnost skupiny.</span><span class="sxs-lookup"><span data-stu-id="a7428-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="a7428-142">V následujícím příkladu je variace příkladu, který se zobrazí v sekci [se &#124; porovnáváním nebo vzorem](#Either_Or) .</span><span class="sxs-lookup"><span data-stu-id="a7428-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="a7428-143">Pomocí podmíněného porovnání Určuje, zda první tři znaky po hranici slova jsou dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a7428-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="a7428-144">Pokud jsou, pokusí se porovnat identifikační číslo zaměstnavatele v USA (EIN).</span><span class="sxs-lookup"><span data-stu-id="a7428-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="a7428-145">V takovém případě se pokusí porovnat číslo sociálního pojištění (SSN) USA.</span><span class="sxs-lookup"><span data-stu-id="a7428-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="a7428-146">Vzor regulárního výrazu `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a7428-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="a7428-147">Vzor</span><span class="sxs-lookup"><span data-stu-id="a7428-147">Pattern</span></span>|<span data-ttu-id="a7428-148">Popis</span><span class="sxs-lookup"><span data-stu-id="a7428-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a7428-149">Začněte na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="a7428-150">Určí, zda následující tři znaky sestávají ze dvou číslic následovaných spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a7428-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="a7428-151">Pokud předchozí vzor souhlasí, porovná dvě číslice následované spojovníkem následovaným sedmi číslicemi.</span><span class="sxs-lookup"><span data-stu-id="a7428-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="a7428-152">Pokud předchozí vzor neodpovídá, porovnává tři desítkové číslice, pomlčku, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="a7428-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="a7428-153">Odpovídá hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="a7428-154">Podmíněné porovnání na základě platné zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="a7428-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="a7428-155">Tento prvek jazyka se pokusí vyhledat jeden ze dvou vzorů v závislosti na tom, zda se shodoval se zadanou zachytávající skupinou.</span><span class="sxs-lookup"><span data-stu-id="a7428-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="a7428-156">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="a7428-156">Its syntax is:</span></span>

<span data-ttu-id="a7428-157">`(?(` *název* `)` *Ano* `|` *žádná* `)`</span><span class="sxs-lookup"><span data-stu-id="a7428-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a7428-158">nebo</span><span class="sxs-lookup"><span data-stu-id="a7428-158">or</span></span>

<span data-ttu-id="a7428-159">`(?(` *číslo* `)` *Ano* `|` *žádná* `)`</span><span class="sxs-lookup"><span data-stu-id="a7428-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="a7428-160">kde *Name* je název a *číslo* je číslo zachytávající skupiny, *Ano* je výraz, který se má shodovat, pokud má *název* nebo *číslo* shodu a *ne* není volitelný výraz, který by odpovídal, pokud není.</span><span class="sxs-lookup"><span data-stu-id="a7428-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="a7428-161">Pokud *název* neodpovídá názvu zachytávající skupiny, která je použita ve vzoru regulárního výrazu, konstrukce alternace je interpretována jako test výrazu, jak je vysvětleno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="a7428-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="a7428-162">Obvykle to znamená, že *výraz* je vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="a7428-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="a7428-163">Pokud *číslo* neodpovídá očíslované zachytávající skupině, která je použita ve vzoru regulárního výrazu, modul regulárních výrazů vyvolá <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="a7428-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="a7428-164">V následujícím příkladu je variace příkladu, který se zobrazí v sekci [se &#124; porovnáváním nebo vzorem](#Either_Or) .</span><span class="sxs-lookup"><span data-stu-id="a7428-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="a7428-165">Používá zachytávající skupinu s názvem `n2`, která se skládá ze dvou číslic následovaných spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a7428-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="a7428-166">Konstrukce alternace testuje, zda byla tato zachytávající skupina spárována ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="a7428-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="a7428-167">Pokud má, konstrukce alternace se pokusí porovnat posledních sedm číslic, které mají identifikační číslo zaměstnavatele USA (EIN).</span><span class="sxs-lookup"><span data-stu-id="a7428-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="a7428-168">Pokud tomu tak není, pokusí se vyhledat devět číslic rodné číslo (USA).</span><span class="sxs-lookup"><span data-stu-id="a7428-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="a7428-169">Vzor regulárního výrazu `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a7428-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="a7428-170">Vzor</span><span class="sxs-lookup"><span data-stu-id="a7428-170">Pattern</span></span>|<span data-ttu-id="a7428-171">Popis</span><span class="sxs-lookup"><span data-stu-id="a7428-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a7428-172">Začněte na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="a7428-173">Porovná žádný nebo jeden výskyt dvou číslic následovaný spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a7428-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="a7428-174">Pojmenujte tuto zachytávající skupinu `n2`.</span><span class="sxs-lookup"><span data-stu-id="a7428-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="a7428-175">Otestuje, zda byl ve vstupním řetězci spárován `n2`.</span><span class="sxs-lookup"><span data-stu-id="a7428-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="a7428-176">Pokud se shodovala hodnota `n2`, porovná sedm desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="a7428-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="a7428-177">Pokud se neshoduje `n2`, porovná tři desítkové číslice, pomlčku, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="a7428-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="a7428-178">Odpovídá hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a7428-178">Match a word boundary.</span></span>|  

<span data-ttu-id="a7428-179">V následujícím příkladu je uvedena variace tohoto příkladu, který používá očíslovanou skupinu namísto pojmenované skupiny.</span><span class="sxs-lookup"><span data-stu-id="a7428-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="a7428-180">Jeho vzor regulárního výrazu je `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="a7428-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a7428-181">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="a7428-181">See also</span></span>

- [<span data-ttu-id="a7428-182">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="a7428-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
