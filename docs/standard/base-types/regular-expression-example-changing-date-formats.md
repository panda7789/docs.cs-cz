---
title: 'Příklad regulárního výrazu: Změna formátů kalendářních dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 358e26957747073fec9dfe9eb0d404cb438afaf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084182"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="d5f63-102">Příklad regulárního výrazu: Změna formátů kalendářních dat</span><span class="sxs-lookup"><span data-stu-id="d5f63-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="d5f63-103">Následující příklad kódu <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> používá metodu k nahrazení kalendářních dat, která mají formulář *mm*/*dd*/*yy, daty,* která mají formulář *dd*-*mm*-*yy*.</span><span class="sxs-lookup"><span data-stu-id="d5f63-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5f63-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5f63-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="d5f63-105">Následující kód ukazuje, `MDYToDMY` jak lze metodu volat v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d5f63-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="d5f63-106">Komentáře</span><span class="sxs-lookup"><span data-stu-id="d5f63-106">Comments</span></span>  
 <span data-ttu-id="d5f63-107">Vzor regulárního výrazu `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` je interpretován tak, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d5f63-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d5f63-108">Vzor</span><span class="sxs-lookup"><span data-stu-id="d5f63-108">Pattern</span></span>|<span data-ttu-id="d5f63-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d5f63-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d5f63-110">Začne porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d5f63-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="d5f63-111">Porovná jednu nebo dvě desetinná místa.</span><span class="sxs-lookup"><span data-stu-id="d5f63-111">Match one or two decimal digits.</span></span> <span data-ttu-id="d5f63-112">Tohle je `month` zachycená skupina.</span><span class="sxs-lookup"><span data-stu-id="d5f63-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="d5f63-113">Porovná značku lomítka.</span><span class="sxs-lookup"><span data-stu-id="d5f63-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="d5f63-114">Porovná jednu nebo dvě desetinná místa.</span><span class="sxs-lookup"><span data-stu-id="d5f63-114">Match one or two decimal digits.</span></span> <span data-ttu-id="d5f63-115">Tohle je `day` zachycená skupina.</span><span class="sxs-lookup"><span data-stu-id="d5f63-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="d5f63-116">Porovná značku lomítka.</span><span class="sxs-lookup"><span data-stu-id="d5f63-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="d5f63-117">Shoda od dvou do čtyř desetinných míst.</span><span class="sxs-lookup"><span data-stu-id="d5f63-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="d5f63-118">Tohle je `year` zachycená skupina.</span><span class="sxs-lookup"><span data-stu-id="d5f63-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="d5f63-119">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d5f63-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="d5f63-120">Vzorek `${day}-${month}-${year}` definuje náhradní řetězec, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d5f63-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="d5f63-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="d5f63-121">Pattern</span></span>|<span data-ttu-id="d5f63-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d5f63-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="d5f63-123">Přidejte řetězec zachycený `day` zachytávající skupinou.</span><span class="sxs-lookup"><span data-stu-id="d5f63-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="d5f63-124">Přidejte pomlčku.</span><span class="sxs-lookup"><span data-stu-id="d5f63-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="d5f63-125">Přidejte řetězec zachycený `month` zachytávající skupinou.</span><span class="sxs-lookup"><span data-stu-id="d5f63-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="d5f63-126">Přidejte pomlčku.</span><span class="sxs-lookup"><span data-stu-id="d5f63-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="d5f63-127">Přidejte řetězec zachycený `year` zachytávající skupinou.</span><span class="sxs-lookup"><span data-stu-id="d5f63-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5f63-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5f63-128">See also</span></span>

- [<span data-ttu-id="d5f63-129">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d5f63-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
