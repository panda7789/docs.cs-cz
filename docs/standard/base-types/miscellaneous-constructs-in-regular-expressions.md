---
title: "Různé konstrukce v regulárních výrazech"
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
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7a7c577c617ca8f40d64548f9f0f2d103c5887e1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a><span data-ttu-id="cc43f-102">Různé konstrukce v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="cc43f-102">Miscellaneous Constructs in Regular Expressions</span></span>
<span data-ttu-id="cc43f-103">Regulární výrazy v rozhraní .NET zahrnují tři různé jazykové konstrukty.</span><span class="sxs-lookup"><span data-stu-id="cc43f-103">Regular expressions in .NET include three miscellaneous language constructs.</span></span> <span data-ttu-id="cc43f-104">Jedno umožňuje povolit nebo zakázat určité možnosti porovnávání uprostřed vzor regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="cc43f-104">One lets you enable or disable particular matching options in the middle of a regular expression pattern.</span></span> <span data-ttu-id="cc43f-105">Zbývající dvě umožňují zahrnout komentáře v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="cc43f-105">The remaining two let you include comments in a regular expression.</span></span>  
  
## <a name="inline-options"></a><span data-ttu-id="cc43f-106">Vložené možnosti</span><span class="sxs-lookup"><span data-stu-id="cc43f-106">Inline Options</span></span>  
 <span data-ttu-id="cc43f-107">Můžete nastavit nebo zakázat konkrétní vzor odpovídající pomocí syntaxe možnosti pro součást regulární výraz</span><span class="sxs-lookup"><span data-stu-id="cc43f-107">You can set or disable specific pattern matching options for part of a regular expression by using the syntax</span></span>  
  
```  
(?imnsx-imnsx)  
```  
  
 <span data-ttu-id="cc43f-108">Můžete seznam možností, které chcete povolit po otazníku a možností, které chcete zakázat za znaménkem minus.</span><span class="sxs-lookup"><span data-stu-id="cc43f-108">You list the options you want to enable after the question mark, and the options you want to disable after the minus sign.</span></span> <span data-ttu-id="cc43f-109">Jednotlivé možnosti jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="cc43f-109">The following table describes each option.</span></span> <span data-ttu-id="cc43f-110">Další informace o jednotlivých možnostech najdete v tématu [možnosti regulárních výrazů](../../../docs/standard/base-types/regular-expression-options.md).</span><span class="sxs-lookup"><span data-stu-id="cc43f-110">For more information about each option, see [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
|<span data-ttu-id="cc43f-111">Možnost</span><span class="sxs-lookup"><span data-stu-id="cc43f-111">Option</span></span>|<span data-ttu-id="cc43f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cc43f-112">Description</span></span>|  
|------------|-----------------|  
|`i`|<span data-ttu-id="cc43f-113">Porovnávání.</span><span class="sxs-lookup"><span data-stu-id="cc43f-113">Case-insensitive matching.</span></span>|  
|`m`|<span data-ttu-id="cc43f-114">Víceřádkového režimu.</span><span class="sxs-lookup"><span data-stu-id="cc43f-114">Multiline mode.</span></span>|  
|`n`|<span data-ttu-id="cc43f-115">Pouze explicitní zachycení.</span><span class="sxs-lookup"><span data-stu-id="cc43f-115">Explicit captures only.</span></span> <span data-ttu-id="cc43f-116">(Závorky není fungovat jako zachytávající skupiny.)</span><span class="sxs-lookup"><span data-stu-id="cc43f-116">(Parentheses do not act as capturing groups.)</span></span>|  
|`s`|<span data-ttu-id="cc43f-117">Režim jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="cc43f-117">Single-line mode.</span></span>|  
|`x`|<span data-ttu-id="cc43f-118">Ignorovat prázdný znak a Povolit poznámky x-mode.</span><span class="sxs-lookup"><span data-stu-id="cc43f-118">Ignore unescaped white space, and allow x-mode comments.</span></span>|  
  
 <span data-ttu-id="cc43f-119">Všechny změny v možnosti regulárních výrazů, které jsou definované `(?imnsx-imnsx)` vytvořit zůstane v platnosti až do konce nadřazené skupiny.</span><span class="sxs-lookup"><span data-stu-id="cc43f-119">Any change in regular expression options defined by the `(?imnsx-imnsx)` construct remains in effect until the end of the enclosing group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc43f-120">`(?imnsx-imnsx:` *Dílčím výrazu* `)` seskupovací konstrukce poskytuje stejné funkce pro dílčím výrazu.</span><span class="sxs-lookup"><span data-stu-id="cc43f-120">The `(?imnsx-imnsx:`*subexpression*`)` grouping construct provides identical functionality for a subexpression.</span></span> <span data-ttu-id="cc43f-121">Další informace najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="cc43f-121">For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="cc43f-122">Následující příklad používá `i`, `n`, a `x` možnosti pro povolení nerozlišování a explicitní zachycování a Ignorovat prázdné znaky v vzor regulárního výrazu uprostřed regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="cc43f-122">The following example uses the `i`, `n`, and `x` options to enable case insensitivity and explicit captures, and to ignore white space in the regular expression pattern in the middle of a regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 <span data-ttu-id="cc43f-123">V příkladu definuje dva regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="cc43f-123">The example defines two regular expressions.</span></span> <span data-ttu-id="cc43f-124">První, `\b(D\w+)\s(d\w+)\b`, porovnává dva po sobě jdoucí slova, která začínají velká písmena "D" a "d" jedno malé písmeno.</span><span class="sxs-lookup"><span data-stu-id="cc43f-124">The first, `\b(D\w+)\s(d\w+)\b`, matches two consecutive words that begin with an uppercase "D" and a lowercase "d".</span></span> <span data-ttu-id="cc43f-125">Druhý regulární výraz, `\b(D\w+)(?ixn) \s (d\w+) \b`, používá vložené možnosti pro úpravu tohoto vzoru, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="cc43f-125">The second regular expression, `\b(D\w+)(?ixn) \s (d\w+) \b`, uses inline options to modify this pattern, as described in the following table.</span></span> <span data-ttu-id="cc43f-126">Porovnání výsledků potvrdí účinku `(?ixn)` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="cc43f-126">A comparison of the results confirms the effect of the `(?ixn)` construct.</span></span>  
  
|<span data-ttu-id="cc43f-127">Vzor</span><span class="sxs-lookup"><span data-stu-id="cc43f-127">Pattern</span></span>|<span data-ttu-id="cc43f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="cc43f-128">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="cc43f-129">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-129">Start at a word boundary.</span></span>|  
|`(D\w+)`|<span data-ttu-id="cc43f-130">Porovná velké "D", za nímž následuje jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-130">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="cc43f-131">Toto je první skupinu zachycení.</span><span class="sxs-lookup"><span data-stu-id="cc43f-131">This is the first capture group.</span></span>|  
|`(?ixn)`|<span data-ttu-id="cc43f-132">Z tohoto bodu nastaví porovnávání velká a malá písmena zkontrolujte pouze explicitní zaznamená a Ignorovat prázdné znaky v regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="cc43f-132">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`\s`|<span data-ttu-id="cc43f-133">Porovná prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="cc43f-133">Match a white-space character.</span></span>|  
|`(d\w+)`|<span data-ttu-id="cc43f-134">Odpovídat velké nebo malé "d" následuje jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-134">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="cc43f-135">Tato skupina není zachycena, protože `n` byla povolena možnost (explicitní zachytávání)...</span><span class="sxs-lookup"><span data-stu-id="cc43f-135">This group is not captured because the `n` (explicit capture) option was enabled..</span></span>|  
|`\b`|<span data-ttu-id="cc43f-136">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-136">Match a word boundary.</span></span>|  
  
## <a name="inline-comment"></a><span data-ttu-id="cc43f-137">Vložený komentář</span><span class="sxs-lookup"><span data-stu-id="cc43f-137">Inline Comment</span></span>  
 <span data-ttu-id="cc43f-138">`(?#` *Komentář* `)` konstrukce umožňuje zahrnout vložený komentář regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="cc43f-138">The `(?#` *comment*`)` construct lets you include an inline comment in a regular expression.</span></span> <span data-ttu-id="cc43f-139">Modul regulárních výrazů nepoužívá libovolná součást komentář v porovnávání vzorů, i když komentář je součástí řetězec, který je vrácený <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="cc43f-139">The regular expression engine does not use any part of the comment in pattern matching, although the comment is included in the string that is returned by the <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cc43f-140">Komentář končí první pravou závorkou.</span><span class="sxs-lookup"><span data-stu-id="cc43f-140">The comment ends at the first closing parenthesis.</span></span>  
  
 <span data-ttu-id="cc43f-141">V následujícím příkladu se opakuje první vzor regulárního výrazu z příkladu v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="cc43f-141">The following example repeats the first regular expression pattern from the example in the previous section.</span></span> <span data-ttu-id="cc43f-142">Přidá dva vložené komentáře regulární výraz, který se označuje, zda je výsledkem porovnávání malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="cc43f-142">It adds two inline comments to the regular expression to indicate whether the comparison is case-sensitive.</span></span> <span data-ttu-id="cc43f-143">Vzor regulárního výrazu `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="cc43f-143">The regular expression pattern, `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, is defined as follows.</span></span>  
  
|<span data-ttu-id="cc43f-144">Vzor</span><span class="sxs-lookup"><span data-stu-id="cc43f-144">Pattern</span></span>|<span data-ttu-id="cc43f-145">Popis</span><span class="sxs-lookup"><span data-stu-id="cc43f-145">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="cc43f-146">Začne na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-146">Start at a word boundary.</span></span>|  
|`(?# case-sensitive comparison)`|<span data-ttu-id="cc43f-147">Komentář.</span><span class="sxs-lookup"><span data-stu-id="cc43f-147">A comment.</span></span> <span data-ttu-id="cc43f-148">Porovnávání chování neovlivňuje.</span><span class="sxs-lookup"><span data-stu-id="cc43f-148">It does not affect pattern-matching behavior.</span></span>|  
|`(D\w+)`|<span data-ttu-id="cc43f-149">Porovná velké "D", za nímž následuje jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-149">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="cc43f-150">Toto je první zachytávající skupina.</span><span class="sxs-lookup"><span data-stu-id="cc43f-150">This is the first capturing group.</span></span>|  
|`\s`|<span data-ttu-id="cc43f-151">Porovná prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="cc43f-151">Match a white-space character.</span></span>|  
|`(?ixn)`|<span data-ttu-id="cc43f-152">Z tohoto bodu nastaví porovnávání velká a malá písmena zkontrolujte pouze explicitní zaznamená a Ignorovat prázdné znaky v regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="cc43f-152">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`(?#case-insensitive comparison)`|<span data-ttu-id="cc43f-153">Komentář.</span><span class="sxs-lookup"><span data-stu-id="cc43f-153">A comment.</span></span> <span data-ttu-id="cc43f-154">Porovnávání chování neovlivňuje.</span><span class="sxs-lookup"><span data-stu-id="cc43f-154">It does not affect pattern-matching behavior.</span></span>|  
|`(d\w+)`|<span data-ttu-id="cc43f-155">Odpovídat velké nebo malé "d" následuje jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-155">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="cc43f-156">Toto je druhý skupiny zachycení.</span><span class="sxs-lookup"><span data-stu-id="cc43f-156">This is the second capture group.</span></span>|  
|`\b`|<span data-ttu-id="cc43f-157">Porovná hranici slova.</span><span class="sxs-lookup"><span data-stu-id="cc43f-157">Match a word boundary.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a><span data-ttu-id="cc43f-158">Komentář konec řádku</span><span class="sxs-lookup"><span data-stu-id="cc43f-158">End-of-Line Comment</span></span>  
 <span data-ttu-id="cc43f-159">Znaménko čísla (`#`) označí x režimu komentář, který začíná znakem # neuvozené na konci regulární výraz a pokračuje v až do konce řádku.</span><span class="sxs-lookup"><span data-stu-id="cc43f-159">A number sign (`#`)marks an x-mode comment, which starts at the unescaped # character at the end of the regular expression pattern and continues until the end of the line.</span></span> <span data-ttu-id="cc43f-160">Pro použití této konstrukce, je třeba buď povolit `x` možnost (pomocí vložených možností) nebo zadejte <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> hodnotu `option` parametr při vytváření instance <xref:System.Text.RegularExpressions.Regex> objekt nebo volání statického <xref:System.Text.RegularExpressions.Regex> metoda.</span><span class="sxs-lookup"><span data-stu-id="cc43f-160">To use this construct, you must either enable the `x` option (through inline options) or supply the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> value to the `option` parameter when instantiating the <xref:System.Text.RegularExpressions.Regex> object or calling a static <xref:System.Text.RegularExpressions.Regex> method.</span></span>  
  
 <span data-ttu-id="cc43f-161">Následující příklad ilustruje konstrukce komentář konec řádku.</span><span class="sxs-lookup"><span data-stu-id="cc43f-161">The following example illustrates the end-of-line comment construct.</span></span> <span data-ttu-id="cc43f-162">Se určuje, zda je řetězec složený formátovací řetězec, který obsahuje alespoň jednu položku formátu.</span><span class="sxs-lookup"><span data-stu-id="cc43f-162">It determines whether a string is a composite format string that includes at least one format item.</span></span> <span data-ttu-id="cc43f-163">Následující tabulka popisuje konstrukce v regulární výraz:</span><span class="sxs-lookup"><span data-stu-id="cc43f-163">The following table describes the constructs in the regular expression pattern:</span></span>  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|<span data-ttu-id="cc43f-164">Vzor</span><span class="sxs-lookup"><span data-stu-id="cc43f-164">Pattern</span></span>|<span data-ttu-id="cc43f-165">Popis</span><span class="sxs-lookup"><span data-stu-id="cc43f-165">Description</span></span>|  
|-------------|-----------------|  
|`\{`|<span data-ttu-id="cc43f-166">Odpovídat žádná levá složená závorka.</span><span class="sxs-lookup"><span data-stu-id="cc43f-166">Match an opening brace.</span></span>|  
|`\d+`|<span data-ttu-id="cc43f-167">Porovná jednu nebo více desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="cc43f-167">Match one or more decimal digits.</span></span>|  
|`(,-*\d+)*`|<span data-ttu-id="cc43f-168">Porovná nula nebo jeden výskyt čárkou, za nímž následuje volitelné mínus, za nímž následuje jeden nebo více desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="cc43f-168">Match zero or one occurrence of a comma, followed by an optional minus sign, followed by one or more decimal digits.</span></span>|  
|`(\:\w{1,4}?)*`|<span data-ttu-id="cc43f-169">Porovná nula nebo jeden výskyt dvojtečkou, za nímž následuje jeden až čtyři, ale nejmenším možném, prázdných znaků.</span><span class="sxs-lookup"><span data-stu-id="cc43f-169">Match zero or one occurrence of a colon, followed by one to four, but as few as possible, white-space characters.</span></span>|  
|`(?#case insensitive comparison)`|<span data-ttu-id="cc43f-170">Vložený komentář.</span><span class="sxs-lookup"><span data-stu-id="cc43f-170">An inline comment.</span></span> <span data-ttu-id="cc43f-171">Nemá žádný vliv na porovnávání chování.</span><span class="sxs-lookup"><span data-stu-id="cc43f-171">It has no effect on pattern-matching behavior.</span></span>|  
|`\}`|<span data-ttu-id="cc43f-172">Pravé složené závorce odpovídat.</span><span class="sxs-lookup"><span data-stu-id="cc43f-172">Match a closing brace.</span></span>|  
|`(?x)`|<span data-ttu-id="cc43f-173">Povolte možnost Ignorovat vzor prázdný, tak, aby byl rozpoznán komentář konec řádku.</span><span class="sxs-lookup"><span data-stu-id="cc43f-173">Enable the ignore pattern white-space option so that the end-of-line comment will be recognized.</span></span>|  
|`# Looks for a composite format item.`|<span data-ttu-id="cc43f-174">Komentář konec řádku.</span><span class="sxs-lookup"><span data-stu-id="cc43f-174">An end-of-line comment.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 <span data-ttu-id="cc43f-175">Všimněte si, že, místo `(?x)` vytvořit v regulárním výrazu komentář může být také rozpoznán voláním <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda a předání <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="cc43f-175">Note that, instead of providing the `(?x)` construct in the regular expression, the comment could also have been recognized by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method and passing it the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> enumeration value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc43f-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc43f-176">See Also</span></span>  
 [<span data-ttu-id="cc43f-177">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="cc43f-177">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
