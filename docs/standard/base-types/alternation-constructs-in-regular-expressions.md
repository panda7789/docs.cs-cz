---
title: "Konstrukce alternace v regulárních výrazech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8e565d029096b88d304b9cfc241807084873e735
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="837df-102">Konstrukce alternace v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="837df-102">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a><span data-ttu-id="837df-103">Konstrukce alternace upravit regulární výraz k povolení buď / nebo nebo podmíněného odpovídající.</span><span class="sxs-lookup"><span data-stu-id="837df-103">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="837df-104">Rozhraní .NET podporuje tři konstrukce alternace:</span><span class="sxs-lookup"><span data-stu-id="837df-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="837df-105">Porovnávání vzorů s &#124;</span><span class="sxs-lookup"><span data-stu-id="837df-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="837df-106">Podmíněné porovnávání pomocí (? () výraz) Ano &#124; ne)</span><span class="sxs-lookup"><span data-stu-id="837df-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="837df-107">Podmíněné porovnávání založené na platnou zaznamenané skupinu</span><span class="sxs-lookup"><span data-stu-id="837df-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="837df-108">Pro porovnávání s &#124;</span><span class="sxs-lookup"><span data-stu-id="837df-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="837df-109">Můžete použít svislá čára (`|`) znak tak, aby odpovídaly některého z řady vzory, kde `|` odděluje každý vzorek.</span><span class="sxs-lookup"><span data-stu-id="837df-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="837df-110">Třída pozitivních znaků, jako `|` znak slouží k porovnání kteréhokoli z jedné znaků.</span><span class="sxs-lookup"><span data-stu-id="837df-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="837df-111">Následující příklad používá jak třídu kladné znaků a buď / nebo vzor odpovídající pomocí `|` pro nalezení výskytů slova "gray" nebo "Los" v řetězci.</span><span class="sxs-lookup"><span data-stu-id="837df-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="837df-112">V takovém případě `|` znak vytváří regulární výraz, který je podrobnější.</span><span class="sxs-lookup"><span data-stu-id="837df-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="837df-113">Regulární výraz, který používá `|` znak, `\bgr(a|e)y\b`, se interpretují jako uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="837df-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="837df-114">Vzor</span><span class="sxs-lookup"><span data-stu-id="837df-114">Pattern</span></span>|<span data-ttu-id="837df-115">Popis</span><span class="sxs-lookup"><span data-stu-id="837df-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="837df-116">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="837df-117">Porovná znaky "gr".</span><span class="sxs-lookup"><span data-stu-id="837df-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="837df-118">Porovná buď se znakem „a“, nebo s „e“.</span><span class="sxs-lookup"><span data-stu-id="837df-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="837df-119">Porovná "y" na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="837df-120">`|` Znak lze použít také pro porovnávání buď / nebo k vyhledání s více znaky nebo podvýrazy, které může obsahovat libovolnou kombinaci znakové literály a prvků jazyka regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="837df-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="837df-121">(Třída znaků neposkytuje tuto funkci.) Následující příklad používá `|` znaků k extrakci buď USA Číslo sociálního pojištění (SSN), což je číslo 9 číslic ve formátu *ddd*-*dd*-*dddd*, nebo US Zaměstnavatel identifikační číslo (EIN), což je číslo 9 číslic ve formátu *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="837df-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="837df-122">Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="837df-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="837df-123">Vzor</span><span class="sxs-lookup"><span data-stu-id="837df-123">Pattern</span></span>|<span data-ttu-id="837df-124">Popis</span><span class="sxs-lookup"><span data-stu-id="837df-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="837df-125">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="837df-126">Porovná jednu z následujících: dva desetinných míst, za nímž následuje pomlčka následované sedm desítkových číslic; nebo tři desetinných míst, pomlčku, dvě desetinných míst, další pomlčku a čtyři desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="837df-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="837df-127">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="837df-128">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="837df-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="837df-129">Podmíněné porovnávání s výrazem</span><span class="sxs-lookup"><span data-stu-id="837df-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="837df-130">Tento prvek jazyka se pokusí o porovnání jedním ze dvou vzorů v závislosti na tom, zda lze porovnat počáteční vzorek.</span><span class="sxs-lookup"><span data-stu-id="837df-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="837df-131">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="837df-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="837df-132">`(?(`*výraz* `)` *Ano* `|` *žádné*`)`</span><span class="sxs-lookup"><span data-stu-id="837df-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="837df-133">kde *výraz* je počáteční vzor pro shodu, *Ano* je vzor pro porovnání, pokud *výraz* je nalezena shoda, a *žádné* je nepovinný Pokud odpovídající vzor *výraz* neodpovídá.</span><span class="sxs-lookup"><span data-stu-id="837df-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="837df-134">Modul regulárních výrazů zpracovává *výraz* jako assertion nulovou šířkou; to znamená, modul regulárních výrazů není zálohy v vstupního datového proudu po vyhodnocuje *výraz*.</span><span class="sxs-lookup"><span data-stu-id="837df-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="837df-135">Proto tento konstruktor je ekvivalentní následující:</span><span class="sxs-lookup"><span data-stu-id="837df-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="837df-136">`(?(?=`*výraz* `)` *Ano* `|` *žádné*`)`</span><span class="sxs-lookup"><span data-stu-id="837df-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="837df-137">kde `(?=` *výraz* `)` je konstrukce nulové šířky.</span><span class="sxs-lookup"><span data-stu-id="837df-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="837df-138">(Další informace najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Protože modul regulárních výrazů interpretuje *výraz* jako element anchor (assertion nulovou šířkou), *výraz* musí být buď nulovou šířkou assertion (Další informace najdete v tématu [ Kotvy](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) nebo dílčím výrazu, která je také součástí *Ano*.</span><span class="sxs-lookup"><span data-stu-id="837df-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="837df-139">Jinak *Ano* vzor nelze porovnat.</span><span class="sxs-lookup"><span data-stu-id="837df-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="837df-140">Pokud *výraz*je zachycené skupiny s názvem nebo číslem, alternace interpretována jako testovací zachycení; Další informace najdete v části Další [podmíněné porovnávání založené na platné zachycené skupině](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="837df-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="837df-141">Jinými slovy modul regulárních výrazů nepokusí tak, aby odpovídaly zaznamenané dílčí řetězec, ale místo toho testů pro existenci nebo neexistenci skupiny.</span><span class="sxs-lookup"><span data-stu-id="837df-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="837df-142">V následujícím příkladu se odlišuje od příkladu, který se zobrazí v [buď / nebo vzor odpovídající pomocí &#124;](#Either_Or) části.</span><span class="sxs-lookup"><span data-stu-id="837df-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="837df-143">Chcete-li určit, jestli prvních tří znaků na hranici slova jsou dvě číslice následované pomlčka pomocí podmíněného porovnávání.</span><span class="sxs-lookup"><span data-stu-id="837df-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="837df-144">Pokud ano, pokusí se porovnat americké Identifikační číslo zaměstnavatele (EIN).</span><span class="sxs-lookup"><span data-stu-id="837df-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="837df-145">Pokud ne, pokusí se porovnat americké Číslo sociálního pojištění (SSN).</span><span class="sxs-lookup"><span data-stu-id="837df-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="837df-146">Regulární výraz `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="837df-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="837df-147">Vzor</span><span class="sxs-lookup"><span data-stu-id="837df-147">Pattern</span></span>|<span data-ttu-id="837df-148">Popis</span><span class="sxs-lookup"><span data-stu-id="837df-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="837df-149">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="837df-150">Určí, zda následující tři znaky se skládají ze dvou číslic, za nímž následuje pomlčka.</span><span class="sxs-lookup"><span data-stu-id="837df-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="837df-151">Pokud předchozí vzor odpovídá, porovná dvě číslice následované pomlčkou, za nímž následuje sedm číslic.</span><span class="sxs-lookup"><span data-stu-id="837df-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="837df-152">Pokud předchozí vzorek neodpovídá, odpovídat tři desetinných míst, pomlčku, dvě desetinných míst, další pomlčku a čtyři desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="837df-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="837df-153">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="837df-154">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="837df-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="837df-155">Podmíněné porovnávání založené na platnou zaznamenané skupinu</span><span class="sxs-lookup"><span data-stu-id="837df-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="837df-156">Tento prvek jazyka se pokusí o porovnání jedním ze dvou vzorů v závislosti na tom, jestli ho odpovídá zadané zaznamenávání skupiny.</span><span class="sxs-lookup"><span data-stu-id="837df-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="837df-157">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="837df-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="837df-158">`(?(`*název* `)` *Ano* `|` *žádné*`)`</span><span class="sxs-lookup"><span data-stu-id="837df-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="837df-159">or</span><span class="sxs-lookup"><span data-stu-id="837df-159">or</span></span>  
  
 <span data-ttu-id="837df-160">`(?(`*číslo* `)` *Ano* `|` *žádné*`)`</span><span class="sxs-lookup"><span data-stu-id="837df-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="837df-161">kde *název* je název a *číslo* je číslo zachycené skupiny, *Ano* je výraz pro porovnání, pokud *název* nebo *číslo* má odpovídající, a *žádné* je volitelný výraz pro porovnání, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="837df-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="837df-162">Pokud *název* neodpovídá název zaznamenávání skupinu, která se používá v regulární výraz, alternace interpretována jako test výrazu, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="837df-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="837df-163">Obvykle to znamená, že *výraz* vyhodnocuje `false`.</span><span class="sxs-lookup"><span data-stu-id="837df-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="837df-164">Pokud *číslo* neodpovídá číslované zaznamenávání skupině, která se používá v vzor regulárního výrazu, vyvolá modul regulární výraz <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="837df-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="837df-165">V následujícím příkladu se odlišuje od příkladu, který se zobrazí v [buď / nebo vzor odpovídající pomocí &#124;](#Either_Or) části.</span><span class="sxs-lookup"><span data-stu-id="837df-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="837df-166">Používá zaznamenávání skupinu s názvem `n2` který se skládá ze dvou číslic, za nímž následuje pomlčka.</span><span class="sxs-lookup"><span data-stu-id="837df-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="837df-167">Konstrukce alternace testy, zda byla odpovídá této zaznamenávání skupiny ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="837df-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="837df-168">Pokud ano, pokusí se porovnat posledních pět číslic amerického zahraniční konstrukce alternace Identifikační číslo zaměstnavatele (EIN).</span><span class="sxs-lookup"><span data-stu-id="837df-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="837df-169">Pokud ne, pokusí se porovnat zahraniční USA Číslo sociálního pojištění (SSN).</span><span class="sxs-lookup"><span data-stu-id="837df-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="837df-170">Regulární výraz `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="837df-170">The regular expression pattern `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="837df-171">Vzor</span><span class="sxs-lookup"><span data-stu-id="837df-171">Pattern</span></span>|<span data-ttu-id="837df-172">Popis</span><span class="sxs-lookup"><span data-stu-id="837df-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="837df-173">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)*`|<span data-ttu-id="837df-174">Porovná nula nebo jeden výskyt dvě číslice následované pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="837df-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="837df-175">Název této skupiny zaznamenávání `n2`.</span><span class="sxs-lookup"><span data-stu-id="837df-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="837df-176">Test zda `n2` , odpovídal ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="837df-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="837df-177">Pokud `n2` byla obsažena, porovná sedm desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="837df-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="837df-178">Pokud `n2` nebyla shodná, odpovídají tři desetinných míst, pomlčku, dvě desetinných míst, další pomlčku a čtyři desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="837df-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="837df-179">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="837df-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="837df-180">Varianta tohoto příkladu, který používá skupinu číslovaných místo s názvem skupiny je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="837df-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="837df-181">Jeho vzor regulárního výrazu je `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="837df-181">Its regular expression pattern is `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="837df-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="837df-182">See Also</span></span>  
 [<span data-ttu-id="837df-183">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="837df-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
