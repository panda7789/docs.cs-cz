---
title: "Regulární výraz příklad: Vyhledávání atributů href"
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
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c6da140ea82fc3c6d3f5f3001f37711ffe861370
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="dab8a-102">Regulární výraz příklad: Vyhledávání atributů href</span><span class="sxs-lookup"><span data-stu-id="dab8a-102">Regular Expression Example: Scanning for HREFs</span></span>
<span data-ttu-id="dab8a-103">Následující příklad prohledá vstupní řetězec a zobrazí všechny href = "..." a jejich umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="dab8a-103">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  
  
## <a name="the-regex-object"></a><span data-ttu-id="dab8a-104">Objekt Regex</span><span class="sxs-lookup"><span data-stu-id="dab8a-104">The Regex Object</span></span>  
 <span data-ttu-id="dab8a-105">Protože `DumpHRefs` metodu lze volat vícekrát z uživatelského kódu, použije `static` (`Shared` v jazyce Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="dab8a-105">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dab8a-106">To umožňuje modul regulárních výrazů pro ukládání do mezipaměti regulárnímu výrazu a zabraňuje režijní náklady na vytvoření nové instance <xref:System.Text.RegularExpressions.Regex> objekt pokaždé, když je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="dab8a-106">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="dab8a-107">A <xref:System.Text.RegularExpressions.Match> objekt se pak použije k iteraci v rámci všechny shody v řetězci.</span><span class="sxs-lookup"><span data-stu-id="dab8a-107">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="dab8a-108">Následující příklad ukazuje volání `DumpHRefs` metoda.</span><span class="sxs-lookup"><span data-stu-id="dab8a-108">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="dab8a-109">Regulární výraz `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="dab8a-109">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="dab8a-110">Vzor</span><span class="sxs-lookup"><span data-stu-id="dab8a-110">Pattern</span></span>|<span data-ttu-id="dab8a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="dab8a-111">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="dab8a-112">Odpovídat řetězcového literálu "href".</span><span class="sxs-lookup"><span data-stu-id="dab8a-112">Match the literal string "href".</span></span> <span data-ttu-id="dab8a-113">Shoda nerozlišuje malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="dab8a-113">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="dab8a-114">Porovná žádný nebo více prázdných znaků.</span><span class="sxs-lookup"><span data-stu-id="dab8a-114">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="dab8a-115">Odpovídat symbolem rovná se.</span><span class="sxs-lookup"><span data-stu-id="dab8a-115">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="dab8a-116">Porovná žádný nebo více prázdných znaků.</span><span class="sxs-lookup"><span data-stu-id="dab8a-116">Match zero or more white-space characters.</span></span>|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|<span data-ttu-id="dab8a-117">Shodovat s jedním z následujících akcí bez výsledek přiřazení k zaznamenané skupiny:</span><span class="sxs-lookup"><span data-stu-id="dab8a-117">Match one of the following without assigning the result to a captured group:</span></span><br /><br /> <span data-ttu-id="dab8a-118">-A uvozovky nebo apostrof, za nímž následuje nula nebo více výskytů libovolného znaku než uvozovky nebo apostrof, za nímž následuje znak uvozovek nebo apostrof.</span><span class="sxs-lookup"><span data-stu-id="dab8a-118">-   A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="dab8a-119">Skupina s názvem `1` je součástí tohoto vzoru.</span><span class="sxs-lookup"><span data-stu-id="dab8a-119">The group named `1` is included in this pattern.</span></span><br /><span data-ttu-id="dab8a-120">-Jeden nebo více znaků prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="dab8a-120">-   One or more non-white-space characters.</span></span> <span data-ttu-id="dab8a-121">Skupina s názvem `1` je součástí tohoto vzoru.</span><span class="sxs-lookup"><span data-stu-id="dab8a-121">The group named `1` is included in this pattern.</span></span>|  
|`(?<1>[^"']*)`|<span data-ttu-id="dab8a-122">Přiřadit nula nebo více výskytů libovolného znaku než uvozovky nebo apostrofu zachycující skupiny s názvem `1`.</span><span class="sxs-lookup"><span data-stu-id="dab8a-122">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`"(?<1>\S+)`|<span data-ttu-id="dab8a-123">Přiřadit jeden nebo více znaků prázdné znaky zachycující skupiny s názvem `1`.</span><span class="sxs-lookup"><span data-stu-id="dab8a-123">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="dab8a-124">Porovnávání třídy výsledků</span><span class="sxs-lookup"><span data-stu-id="dab8a-124">Match Result Class</span></span>  
 <span data-ttu-id="dab8a-125">Výsledky hledání jsou uloženy v <xref:System.Text.RegularExpressions.Match> třídy, která poskytuje přístup ke všem dílčím řetězcům extrahovaným při hledání.</span><span class="sxs-lookup"><span data-stu-id="dab8a-125">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="dab8a-126">Pamatuje také řetězec a regulární výraz, který používají, aby bylo možno zavolat <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodu za účelem dalšího vyhledávání od kde skončilo poslední.</span><span class="sxs-lookup"><span data-stu-id="dab8a-126">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="dab8a-127">Explicitně pojmenované zachycování</span><span class="sxs-lookup"><span data-stu-id="dab8a-127">Explicitly Named Captures</span></span>  
 <span data-ttu-id="dab8a-128">V tradiční regulární výrazy zaznamenávání závorkách jsou automaticky číslované.</span><span class="sxs-lookup"><span data-stu-id="dab8a-128">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="dab8a-129">To vede k dva problémy.</span><span class="sxs-lookup"><span data-stu-id="dab8a-129">This leads to two problems.</span></span> <span data-ttu-id="dab8a-130">Nejprve regulární výraz je změnit jejich vložením či odstraněním sady závorek, je nutné všechen kód, který odkazuje na číslované zachycování přepsat tak, aby odrážely novou číslování.</span><span class="sxs-lookup"><span data-stu-id="dab8a-130">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="dab8a-131">Druhý protože různé sady závorek často používané k zajištění dva alternativní výrazy pro přijatelné shody, může být obtížné určit, které ze dvou výrazů skutečně vrátil výsledek.</span><span class="sxs-lookup"><span data-stu-id="dab8a-131">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="dab8a-132">K řešení těchto problémů <xref:System.Text.RegularExpressions.Regex> třída podporuje syntaxi `(?<name>…)` pro zachycení shody do zadaného slotu (slot můžete pojmenovat pomocí řetězce nebo celé číslo; rychleji můžete třeba připomenout celá čísla).</span><span class="sxs-lookup"><span data-stu-id="dab8a-132">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="dab8a-133">Proto alternativní shoda pro stejný řetězec, který všechny můžete přesměrováni na jednom místě.</span><span class="sxs-lookup"><span data-stu-id="dab8a-133">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="dab8a-134">V případě konfliktu je poslední shoda uložená do slotu úspěšná shoda.</span><span class="sxs-lookup"><span data-stu-id="dab8a-134">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="dab8a-135">(Úplný seznam více shod pro jeden slot je však k dispozici.</span><span class="sxs-lookup"><span data-stu-id="dab8a-135">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="dab8a-136">Najdete v článku <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce podrobnosti.)</span><span class="sxs-lookup"><span data-stu-id="dab8a-136">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab8a-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="dab8a-137">See Also</span></span>  
 [<span data-ttu-id="dab8a-138">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="dab8a-138">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
