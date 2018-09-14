---
title: 'Příklad regulárního výrazu: Změna formátů data'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c26608115a22a5402d671c5f5e51c75442a0a5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519283"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="d8627-102">Příklad regulárního výrazu: Změna formátů data</span><span class="sxs-lookup"><span data-stu-id="d8627-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="d8627-103">Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody lze nahradit data, která bude mít formát _služba ._protokol *mm*/*dd*/*rr* s daty, která mít formát _služba ._protokol *dd*-*mm*-*rr*.</span><span class="sxs-lookup"><span data-stu-id="d8627-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8627-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8627-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="d8627-105">Následující kód ukazuje jak `MDYToDMY` metodu lze volat v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d8627-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="d8627-106">Komentáře</span><span class="sxs-lookup"><span data-stu-id="d8627-106">Comments</span></span>  
 <span data-ttu-id="d8627-107">Vzor regulárního výrazu `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` interpretována, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d8627-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d8627-108">Vzor</span><span class="sxs-lookup"><span data-stu-id="d8627-108">Pattern</span></span>|<span data-ttu-id="d8627-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d8627-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="d8627-110">Začne porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8627-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="d8627-111">Porovná jednu nebo dvě desetinné číslice.</span><span class="sxs-lookup"><span data-stu-id="d8627-111">Match one or two decimal digits.</span></span> <span data-ttu-id="d8627-112">Toto je `month` zachycenou skupinou.</span><span class="sxs-lookup"><span data-stu-id="d8627-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="d8627-113">Porovná lomítko.</span><span class="sxs-lookup"><span data-stu-id="d8627-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="d8627-114">Porovná jednu nebo dvě desetinné číslice.</span><span class="sxs-lookup"><span data-stu-id="d8627-114">Match one or two decimal digits.</span></span> <span data-ttu-id="d8627-115">Toto je `day` zachycenou skupinou.</span><span class="sxs-lookup"><span data-stu-id="d8627-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="d8627-116">Porovná lomítko.</span><span class="sxs-lookup"><span data-stu-id="d8627-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="d8627-117">Porovná dvě pro čtyři desítková čísla.</span><span class="sxs-lookup"><span data-stu-id="d8627-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="d8627-118">Toto je `year` zachycenou skupinou.</span><span class="sxs-lookup"><span data-stu-id="d8627-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="d8627-119">Ukončí porovnání na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="d8627-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="d8627-120">Vzor `${day}-${month}-${year}` řetězci pro nahrazení definuje, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d8627-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="d8627-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="d8627-121">Pattern</span></span>|<span data-ttu-id="d8627-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d8627-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="d8627-123">Přidejte řetězec zachycena `day` zachytávající skupinu.</span><span class="sxs-lookup"><span data-stu-id="d8627-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="d8627-124">Přidáte spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d8627-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="d8627-125">Přidejte řetězec zachycena `month` zachytávající skupinu.</span><span class="sxs-lookup"><span data-stu-id="d8627-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="d8627-126">Přidáte spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="d8627-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="d8627-127">Přidejte řetězec zachycena `year` zachytávající skupinu.</span><span class="sxs-lookup"><span data-stu-id="d8627-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8627-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8627-128">See also</span></span>

- [<span data-ttu-id="d8627-129">Regulárních výrazů .NET</span><span class="sxs-lookup"><span data-stu-id="d8627-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
