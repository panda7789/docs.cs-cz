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
ms.openlocfilehash: 61f1b93d2f54923f0dfc4832a79fe35dc319d0f6
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331754"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="d08bf-103">Konstrukce alternace v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="d08bf-103">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a><span data-ttu-id="d08bf-104">Konstrukce alternace upravují regulární výraz pro povolení nebo podmíněné porovnání.</span><span class="sxs-lookup"><span data-stu-id="d08bf-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="d08bf-105">Rozhraní .NET podporuje tři konstrukce alternace:</span><span class="sxs-lookup"><span data-stu-id="d08bf-105">.NET supports three alternation constructs:</span></span>  
  
- [<span data-ttu-id="d08bf-106">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="d08bf-106">Pattern matching with &#124;</span></span>](#Either_Or)  
  
- [<span data-ttu-id="d08bf-107">Podmíněné porovnání s (? ( výraz) Ano&#124;ne)</span><span class="sxs-lookup"><span data-stu-id="d08bf-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
- [<span data-ttu-id="d08bf-108">Podmíněné porovnání na základě platné zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="d08bf-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="d08bf-109">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="d08bf-109">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="d08bf-110">Znak svislé čáry (`|`) můžete použít k vyhledání jedné z řady vzorů, `|` kde znak odděluje každý vzorek.</span><span class="sxs-lookup"><span data-stu-id="d08bf-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="d08bf-111">Podobně jako třída pozitivního znaku, `|` lze znak použít k vyhledání jednoho z několika jednoduchých znaků.</span><span class="sxs-lookup"><span data-stu-id="d08bf-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="d08bf-112">V následujícím příkladu je použita třída pozitivního znaku a buď porovnávání vzorů, nebo porovnávání `|` se znakem pro hledání výskytů slov "Gray" nebo "šedá" v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d08bf-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="d08bf-113">V tomto případě `|` znak vytvoří regulární výraz, který je podrobněji podrobnější.</span><span class="sxs-lookup"><span data-stu-id="d08bf-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="d08bf-114">Regulární výraz, který používá `|` znak, `\bgr(a|e)y\b`, je interpretován tak, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d08bf-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d08bf-115">Vzor</span><span class="sxs-lookup"><span data-stu-id="d08bf-115">Pattern</span></span>|<span data-ttu-id="d08bf-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d08bf-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d08bf-117">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="d08bf-118">Porovnává se se znaky "GR".</span><span class="sxs-lookup"><span data-stu-id="d08bf-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="d08bf-119">Porovná buď se znakem „a“, nebo s „e“.</span><span class="sxs-lookup"><span data-stu-id="d08bf-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="d08bf-120">Porovnává s "y" na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-120">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="d08bf-121">`|` Znak lze také použít k provedení shody s více znaky nebo podvýrazy, které mohou obsahovat libovolnou kombinaci znakových literálů a prvků jazyka regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="d08bf-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="d08bf-122">(Třída znaků tuto funkci neposkytuje.) Následující příklad používá `|` znak k extrakci typu USA. Číslo sociálního pojištění (SSN), což je číslo 9 číslic ve formátu *DDD*-*DD*-*dddd*nebo USA Identifikační číslo zaměstnavatele (EIN), což je číslo 9 číslic ve formátu *DD*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="d08bf-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="d08bf-123">Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` je interpretován tak, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d08bf-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d08bf-124">Vzor</span><span class="sxs-lookup"><span data-stu-id="d08bf-124">Pattern</span></span>|<span data-ttu-id="d08bf-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d08bf-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d08bf-126">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="d08bf-127">Porovnává jednu z následujících hodnot: dvě desítkové číslice následované spojovníkem a sedmi desítkových číslic; nebo tři desítkové číslice, pomlčky, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="d08bf-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="d08bf-128">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-128">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="d08bf-129">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d08bf-129">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="d08bf-130">Podmíněné porovnání s výrazem</span><span class="sxs-lookup"><span data-stu-id="d08bf-130">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="d08bf-131">Tento prvek jazyka se pokusí vyhledat jeden ze dvou vzorů v závislosti na tom, zda se může shodovat s počátečním vzorem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-131">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="d08bf-132">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="d08bf-132">Its syntax is:</span></span>  
  
 <span data-ttu-id="d08bf-133">`(?(`*výraz* `)`  Ano –`|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="d08bf-133">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d08bf-134">*výraz* WHERE je počáteční vzorek, který se má shodovat, *Ano* je vzor, který se má shodovat, pokud se *výraz* shoduje, a *ne* je volitelný vzor, který by odpovídal, pokud se *výraz* neshoduje.</span><span class="sxs-lookup"><span data-stu-id="d08bf-134">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="d08bf-135">Modul regulárních výrazů považuje *výraz* za kontrolní výraz s nulovou šířkou; To znamená, že modul regulárních výrazů není ve vstupním datovém proudu před vyhodnocením *výrazu*.</span><span class="sxs-lookup"><span data-stu-id="d08bf-135">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="d08bf-136">Proto je tato konstrukce ekvivalentní následujícímu:</span><span class="sxs-lookup"><span data-stu-id="d08bf-136">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="d08bf-137">`(?(?=`*výraz* `)`  Ano –`|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="d08bf-137">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d08bf-138">výraz `(?=`Where`)` je konstrukce kontrolního výrazu s nulovou šířkou.</span><span class="sxs-lookup"><span data-stu-id="d08bf-138">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="d08bf-139">(Další informace naleznete v tématu [seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Vzhledem k tomu, že modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz s nulovou šířkou), musí být *výraz* buď kontrolní výraz s nulovou šířkou (Další informace naleznete v tématu [kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) nebo dílčí výraz, který je také obsažen v *Ano*.</span><span class="sxs-lookup"><span data-stu-id="d08bf-139">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="d08bf-140">V opačném případě nelze porovnat vzor *Ano* .</span><span class="sxs-lookup"><span data-stu-id="d08bf-140">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d08bf-141">Pokud je *výraz*pojmenovanou nebo číslovanou zachytávající skupinou, konstrukce alternace je interpretována jako test Capture; Další informace najdete v další části s podmíněným [porovnáním na základě platné skupiny zachycení](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="d08bf-141">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="d08bf-142">Jinými slovy, modul regulárních výrazů se nepokusí porovnat zachycený dílčí řetězec, ale místo toho testuje přítomnost nebo nepřítomnost skupiny.</span><span class="sxs-lookup"><span data-stu-id="d08bf-142">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="d08bf-143">V následujícím příkladu je variace příkladu, který se zobrazí v sekci [se &#124; porovnáváním](#Either_Or) nebo vzorem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-143">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="d08bf-144">Pomocí podmíněného porovnání Určuje, zda první tři znaky po hranici slova jsou dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-144">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="d08bf-145">Pokud jsou, pokusí se porovnat USA Identifikační číslo zaměstnavatele (EIN).</span><span class="sxs-lookup"><span data-stu-id="d08bf-145">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="d08bf-146">Pokud tomu tak není, pokusí se porovnat americký Rodné číslo (sociální zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="d08bf-146">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="d08bf-147">Vzor `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d08bf-147">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d08bf-148">Vzor</span><span class="sxs-lookup"><span data-stu-id="d08bf-148">Pattern</span></span>|<span data-ttu-id="d08bf-149">Popis</span><span class="sxs-lookup"><span data-stu-id="d08bf-149">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d08bf-150">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-150">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="d08bf-151">Určí, zda následující tři znaky sestávají ze dvou číslic následovaných spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-151">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="d08bf-152">Pokud předchozí vzor souhlasí, porovná dvě číslice následované spojovníkem následovaným sedmi číslicemi.</span><span class="sxs-lookup"><span data-stu-id="d08bf-152">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="d08bf-153">Pokud předchozí vzor neodpovídá, porovnává tři desítkové číslice, pomlčku, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="d08bf-153">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="d08bf-154">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-154">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="d08bf-155">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d08bf-155">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="d08bf-156">Podmíněné porovnání na základě platné zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="d08bf-156">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="d08bf-157">Tento prvek jazyka se pokusí vyhledat jeden ze dvou vzorů v závislosti na tom, zda se shodoval se zadanou zachytávající skupinou.</span><span class="sxs-lookup"><span data-stu-id="d08bf-157">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="d08bf-158">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="d08bf-158">Its syntax is:</span></span>  
  
 <span data-ttu-id="d08bf-159">`(?(`*název* `)`  Ano –`|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="d08bf-159">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d08bf-160">or</span><span class="sxs-lookup"><span data-stu-id="d08bf-160">or</span></span>  
  
 <span data-ttu-id="d08bf-161">`(?(`*číslo* `)`  Ano –`|` *ne*`)`</span><span class="sxs-lookup"><span data-stu-id="d08bf-161">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="d08bf-162">kde *Name* je název a *číslo* je číslo zachytávající skupiny, *Ano* je výraz, který se má shodovat, pokud má *název* nebo *číslo* shodu a *ne* není volitelný výraz, který by odpovídal, pokud není.</span><span class="sxs-lookup"><span data-stu-id="d08bf-162">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="d08bf-163">Pokud *název* neodpovídá názvu zachytávající skupiny, která je použita ve vzoru regulárního výrazu, konstrukce alternace je interpretována jako test výrazu, jak je vysvětleno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="d08bf-163">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="d08bf-164">Obvykle to znamená, že je *výraz* vyhodnocen `false`jako.</span><span class="sxs-lookup"><span data-stu-id="d08bf-164">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="d08bf-165">Pokud *číslo* neodpovídá očíslované zachytávající skupině, která je použita ve vzoru regulárního výrazu, modul regulárních výrazů vyvolá <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="d08bf-165">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="d08bf-166">V následujícím příkladu je variace příkladu, který se zobrazí v sekci [se &#124; porovnáváním](#Either_Or) nebo vzorem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-166">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="d08bf-167">Používá zachytávající skupinu s názvem `n2` , která se skládá ze dvou číslic následovaných spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-167">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="d08bf-168">Konstrukce alternace testuje, zda byla tato zachytávající skupina spárována ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="d08bf-168">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="d08bf-169">Pokud má, konstrukce alternace se pokusí porovnat posledních sedm číslic v devíti číslicích. Identifikační číslo zaměstnavatele (EIN).</span><span class="sxs-lookup"><span data-stu-id="d08bf-169">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="d08bf-170">Pokud tomu tak není, pokusí se porovnat s devíti číslicemi USA. Rodné číslo (sociální zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="d08bf-170">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="d08bf-171">Vzor `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` regulárního výrazu je interpretován tak, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d08bf-171">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d08bf-172">Vzor</span><span class="sxs-lookup"><span data-stu-id="d08bf-172">Pattern</span></span>|<span data-ttu-id="d08bf-173">Popis</span><span class="sxs-lookup"><span data-stu-id="d08bf-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d08bf-174">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-174">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="d08bf-175">Porovná žádný nebo jeden výskyt dvou číslic následovaný spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-175">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="d08bf-176">Pojmenujte tuto `n2`zachytávající skupinu.</span><span class="sxs-lookup"><span data-stu-id="d08bf-176">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="d08bf-177">Otestuje `n2` , zda byla shodná se vstupním řetězcem.</span><span class="sxs-lookup"><span data-stu-id="d08bf-177">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="d08bf-178">Pokud `n2` se shodoval, porovná sedm desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="d08bf-178">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="d08bf-179">Pokud `n2` se neshodoval, porovná tři desítkové číslice, pomlčku, dvě desítkové číslice, další spojovník a čtyři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="d08bf-179">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="d08bf-180">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d08bf-180">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="d08bf-181">V následujícím příkladu je uvedena variace tohoto příkladu, který používá očíslovanou skupinu namísto pojmenované skupiny.</span><span class="sxs-lookup"><span data-stu-id="d08bf-181">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="d08bf-182">Jeho vzor regulárního výrazu `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`je.</span><span class="sxs-lookup"><span data-stu-id="d08bf-182">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d08bf-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d08bf-183">See also</span></span>

- [<span data-ttu-id="d08bf-184">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="d08bf-184">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
