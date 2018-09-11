---
title: Konstrukce alternace v regulárních výrazech
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
ms.openlocfilehash: 6b653972fad71ce3a89c35598513b94f71fb4bf0
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361291"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="a3a3e-102">Konstrukce alternace v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="a3a3e-102">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="a3a3e-103">Konstrukce alternace upravují regulární výraz, aby buď / nebo podmíněného přiřazování nebo.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-103">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="a3a3e-104">.NET podporuje tři konstrukcí alternace:</span><span class="sxs-lookup"><span data-stu-id="a3a3e-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="a3a3e-105">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="a3a3e-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="a3a3e-106">Podmíněné porovnávání s (? () výraz) Ano&#124;žádné)</span><span class="sxs-lookup"><span data-stu-id="a3a3e-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="a3a3e-107">Podmíněného přiřazování na základě platný zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="a3a3e-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="a3a3e-108">Porovnávání vzorů s&#124;</span><span class="sxs-lookup"><span data-stu-id="a3a3e-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="a3a3e-109">Můžete použít svislá čára (`|`) znaků tak, aby odpovídaly některou z řady vzory, kde `|` odděluje každý vzorek.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="a3a3e-110">Třída kladné znaků, jako jsou `|` znak můžete použít tak, aby odpovídaly některou z jednoho znaků.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="a3a3e-111">Následující příklad používá třídu kladné znaků a buď / nebo porovnávání vzorů s `|` znak vyhledáte výskyty slova "gray" nebo "šedou" v řetězci.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="a3a3e-112">V takovém případě `|` znak vytváří regulární výraz, který je podrobnější.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="a3a3e-113">Regulární výraz, který používá `|` znak, `\bgr(a|e)y\b`, je interpretován tak, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="a3a3e-114">Vzor</span><span class="sxs-lookup"><span data-stu-id="a3a3e-114">Pattern</span></span>|<span data-ttu-id="a3a3e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a3a3e-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a3a3e-116">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="a3a3e-117">Porovná znaky "gr".</span><span class="sxs-lookup"><span data-stu-id="a3a3e-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="a3a3e-118">Porovná buď se znakem „a“, nebo s „e“.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="a3a3e-119">Odpovídá "y", na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="a3a3e-120">`|` Znak je také možné provést buď / nebo shodu s více znaky nebo dílčích výrazů, které může obsahovat libovolnou kombinaci znakové literály a prvky jazyka regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="a3a3e-121">(Znak třídy tuto funkci neposkytuje.) V následujícím příkladu `|` znaků k extrakci buď USA Sociálního pojištění USA (SSN), což je číslo 9 číslic s formátem *ddd*-*dd*-*dddd*, nebo číslu Zaměstnavatel identifikační číslo (EIN), což je číslo 9 číslic s formátem *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="a3a3e-122">Regulární výraz `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="a3a3e-123">Vzor</span><span class="sxs-lookup"><span data-stu-id="a3a3e-123">Pattern</span></span>|<span data-ttu-id="a3a3e-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a3a3e-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a3a3e-125">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="a3a3e-126">Porovná jednu z následujících akcí: dvě desetinné číslice, za nímž následuje spojovník následovaný písmenem sedm desítkových číslic; nebo tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="a3a3e-127">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="a3a3e-128">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="a3a3e-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="a3a3e-129">Podmíněné porovnávání s výrazem</span><span class="sxs-lookup"><span data-stu-id="a3a3e-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="a3a3e-130">Tento prvek jazyka se pokusí porovnat jednu ze dvou vzorků v závislosti na tom, zda lze porovnat počáteční vzorek.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="a3a3e-131">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="a3a3e-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="a3a3e-132">`(?(` *výraz* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="a3a3e-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="a3a3e-133">kde *výraz* je počáteční vzor pro shodu, *Ano* je vzor splněno, pokud *výraz* je nalezena shoda, a *žádné* je volitelný Pokud odpovídající vzor *výraz* se neshoduje.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="a3a3e-134">Modul regulárních výrazů zachází *výraz* jako kontrolní výraz nulové šířky; to znamená, že modul regulárních výrazů nepřesouvejte vpřed v vstupního datového proudu po je vyhodnocen jako *výraz*.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="a3a3e-135">Proto tento konstruktor je ekvivalentní následujícímu zápisu:</span><span class="sxs-lookup"><span data-stu-id="a3a3e-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="a3a3e-136">`(?(?=` *výraz* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="a3a3e-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="a3a3e-137">kde `(?=` *výraz* `)` je konstrukce kontrolní výraz nulové šířky.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="a3a3e-138">(Další informace najdete v tématu [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Protože modul regulárních výrazů interpretuje *výraz* jako kotvu (kontrolní výraz nulové šířky), *výraz* musí být buď kontrolní výraz nulové šířky (Další informace najdete v tématu [ Kotvy vztahů](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) nebo jako dílčí výraz, který je také součástí *Ano*.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="a3a3e-139">V opačném případě *Ano* vzor neshoduje.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3a3e-140">Pokud *výraz*pojmenovanou nebo číslovanou zachytávající skupinu, je konstrukce alternace, je interpretován jako zachycení testu; Další informace naleznete v další části [podmíněné odpovídající založené na platné zachycené skupině](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="a3a3e-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="a3a3e-141">Jinými slovy modul regulárních výrazů nepokusí tak, aby odpovídaly zachycené podřetězce, ale místo toho testy pro přítomnosti nebo nepřítomnosti skupiny.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="a3a3e-142">Následující příklad je podobný příkladu, který se zobrazí [buď / nebo porovnávání vzorů s &#124; ](#Either_Or) oddílu.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="a3a3e-143">Používá podmíněného přiřazování k určení, zda první tři znaky po hranici slova jsou dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="a3a3e-144">Pokud ano, pokusí se porovnat USA Zaměstnavatel identifikační číslo (EIN).</span><span class="sxs-lookup"><span data-stu-id="a3a3e-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="a3a3e-145">Pokud ne, pokusí se porovnat americké Číslo sociálního pojištění (SSN).</span><span class="sxs-lookup"><span data-stu-id="a3a3e-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="a3a3e-146">Vzor regulárního výrazu `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="a3a3e-147">Vzor</span><span class="sxs-lookup"><span data-stu-id="a3a3e-147">Pattern</span></span>|<span data-ttu-id="a3a3e-148">Popis</span><span class="sxs-lookup"><span data-stu-id="a3a3e-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a3a3e-149">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="a3a3e-150">Určení, zda následující tři znaky jsou dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="a3a3e-151">Pokud předchozí vzor odpovídá, porovná dvě číslice následované spojovníkem a 7 číslicemi.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="a3a3e-152">Pokud předchozí vzorek neodpovídá, porovná tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="a3a3e-153">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="a3a3e-154">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="a3a3e-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="a3a3e-155">Podmíněného přiřazování na základě platný zachycené skupiny</span><span class="sxs-lookup"><span data-stu-id="a3a3e-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="a3a3e-156">Tento prvek jazyka se pokusí porovnat jednu ze dvou vzorků v závislosti na tom, jestli má odpovídá zadané zachytávající skupiny.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="a3a3e-157">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="a3a3e-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="a3a3e-158">`(?(` *název* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="a3a3e-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="a3a3e-159">or</span><span class="sxs-lookup"><span data-stu-id="a3a3e-159">or</span></span>  
  
 <span data-ttu-id="a3a3e-160">`(?(` *číslo* `)` *Ano* `|` *žádné* `)`</span><span class="sxs-lookup"><span data-stu-id="a3a3e-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="a3a3e-161">kde *název* je název a *číslo* je počet zachytávající skupinu, *Ano* je výraz, který se shodují, pokud *název* nebo *číslo* shoduje, a *žádné* je volitelný výraz, který splněno, pokud tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="a3a3e-162">Pokud *název* neodpovídá názvu zachytávající skupinu, která se používá ve vzoru regulárního výrazu, alternace je interpretován jako test výrazu, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="a3a3e-163">Obvykle to znamená, že *výraz* vyhodnotí jako `false`.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="a3a3e-164">Pokud *číslo* neodpovídá očíslovanou zachytávající skupinu, která se používá ve vzoru regulárního výrazu, vyvolá modul regulárních výrazů <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="a3a3e-165">Následující příklad je podobný příkladu, který se zobrazí [buď / nebo porovnávání vzorů s &#124; ](#Either_Or) oddílu.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="a3a3e-166">Používá zachytávající skupina s názvem `n2` , která obsahuje dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="a3a3e-167">Konstrukce alternace testuje, jestli tato zachytávající skupina pravá složená závorka ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="a3a3e-168">Pokud ano, bude se Alternující konstrukce pokusí se porovnat posledních 7 číslic devět číslic USA Zaměstnavatel identifikační číslo (EIN).</span><span class="sxs-lookup"><span data-stu-id="a3a3e-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="a3a3e-169">Pokud ne, pokusí se porovnat devět číslic USA Číslo sociálního pojištění (SSN).</span><span class="sxs-lookup"><span data-stu-id="a3a3e-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="a3a3e-170">Vzor regulárního výrazu `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-170">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="a3a3e-171">Vzor</span><span class="sxs-lookup"><span data-stu-id="a3a3e-171">Pattern</span></span>|<span data-ttu-id="a3a3e-172">Popis</span><span class="sxs-lookup"><span data-stu-id="a3a3e-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="a3a3e-173">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="a3a3e-174">Porovná žádný nebo jeden výskyt dvě číslice následované spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="a3a3e-175">Název této zachytávající skupiny `n2`.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="a3a3e-176">Test, zda `n2` odpovídal ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="a3a3e-177">Pokud `n2` byla shoda, porovná sedm desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="a3a3e-178">Pokud `n2` neodpovídá, odpovídá tři desítkové číslice, spojovník, dvě desetinné číslice, jiné spojovník a čtyři desítková čísla.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="a3a3e-179">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="a3a3e-180">Variace tohoto příkladu, který používá číslované skupiny místo pojmenovanou skupinu se zobrazí v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="a3a3e-181">Jeho vzor regulárního výrazu je `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="a3a3e-181">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a3a3e-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3a3e-182">See also</span></span>

- [<span data-ttu-id="a3a3e-183">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="a3a3e-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
