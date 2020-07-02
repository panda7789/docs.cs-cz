---
title: 'Příklad regulárního výrazu: Změna formátů data'
ms.date: 06/30/2020
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
ms.openlocfilehash: 3b657ac6c88a1ee846f7f1d2156a18fd34621808
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803947"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="246ac-102">Příklad regulárního výrazu: Změna formátů data</span><span class="sxs-lookup"><span data-stu-id="246ac-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="246ac-103">Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu k nahrazení kalendářních dat, která mají formát *mm* / *DD* / *RR* s kalendářními daty, která mají tvar *DD* - *mm* - *RR*.</span><span class="sxs-lookup"><span data-stu-id="246ac-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="246ac-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="246ac-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="246ac-105">Následující kód ukazuje, jak `MDYToDMY` lze metodu volat v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="246ac-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="246ac-106">Komentáře</span><span class="sxs-lookup"><span data-stu-id="246ac-106">Comments</span></span>  
 <span data-ttu-id="246ac-107">Vzor regulárního výrazu `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` je interpretován tak, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="246ac-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="246ac-108">Vzor</span><span class="sxs-lookup"><span data-stu-id="246ac-108">Pattern</span></span>|<span data-ttu-id="246ac-109">Popis</span><span class="sxs-lookup"><span data-stu-id="246ac-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="246ac-110">Začne porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="246ac-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="246ac-111">Porovnává jednu nebo dvě desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="246ac-111">Match one or two decimal digits.</span></span> <span data-ttu-id="246ac-112">Toto je `month` zachycená skupina.</span><span class="sxs-lookup"><span data-stu-id="246ac-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="246ac-113">Odpovídá znaku lomítka.</span><span class="sxs-lookup"><span data-stu-id="246ac-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="246ac-114">Porovnává jednu nebo dvě desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="246ac-114">Match one or two decimal digits.</span></span> <span data-ttu-id="246ac-115">Toto je `day` zachycená skupina.</span><span class="sxs-lookup"><span data-stu-id="246ac-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="246ac-116">Odpovídá znaku lomítka.</span><span class="sxs-lookup"><span data-stu-id="246ac-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="246ac-117">Porovnává dvě až čtyři desítkové číslice.</span><span class="sxs-lookup"><span data-stu-id="246ac-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="246ac-118">Toto je `year` zachycená skupina.</span><span class="sxs-lookup"><span data-stu-id="246ac-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="246ac-119">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="246ac-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="246ac-120">Vzor `${day}-${month}-${year}` definuje náhradní řetězec, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="246ac-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="246ac-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="246ac-121">Pattern</span></span>|<span data-ttu-id="246ac-122">Popis</span><span class="sxs-lookup"><span data-stu-id="246ac-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="246ac-123">Přidejte řetězec zachycený `day` zachycující skupinou.</span><span class="sxs-lookup"><span data-stu-id="246ac-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="246ac-124">Přidejte spojovník.</span><span class="sxs-lookup"><span data-stu-id="246ac-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="246ac-125">Přidejte řetězec zachycený `month` zachycující skupinou.</span><span class="sxs-lookup"><span data-stu-id="246ac-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="246ac-126">Přidejte spojovník.</span><span class="sxs-lookup"><span data-stu-id="246ac-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="246ac-127">Přidejte řetězec zachycený `year` zachycující skupinou.</span><span class="sxs-lookup"><span data-stu-id="246ac-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="246ac-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="246ac-128">See also</span></span>

- [<span data-ttu-id="246ac-129">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="246ac-129">.NET Regular Expressions</span></span>](regular-expressions.md)
