---
title: 'Postupy: Extrahování protokolu a čísla portu z adresy URL'
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a08e97b02e2f60422132e97e2f3f7d4d2d5b8ec4
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700203"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="17f76-102">Postupy: Extrahování protokolu a čísla portu z adresy URL</span><span class="sxs-lookup"><span data-stu-id="17f76-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="17f76-103">Následující příklad extrahuje protokol a číslo portu z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="17f76-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17f76-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="17f76-104">Example</span></span>  
 <span data-ttu-id="17f76-105">V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda vrátí protokolu za nímž následuje dvojtečka, za nímž následuje číslo portu.</span><span class="sxs-lookup"><span data-stu-id="17f76-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="17f76-106">Vzor regulárního výrazu `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` lze interpretovat, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="17f76-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="17f76-107">Vzor</span><span class="sxs-lookup"><span data-stu-id="17f76-107">Pattern</span></span>|<span data-ttu-id="17f76-108">Popis</span><span class="sxs-lookup"><span data-stu-id="17f76-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="17f76-109">Zahájí porovnávání na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="17f76-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="17f76-110">Porovná jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="17f76-110">Match one or more word characters.</span></span> <span data-ttu-id="17f76-111">Pojmenovat tuto skupinu `proto`.</span><span class="sxs-lookup"><span data-stu-id="17f76-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="17f76-112">Porovná dvojtečku následovanou dvěma lomítky.</span><span class="sxs-lookup"><span data-stu-id="17f76-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="17f76-113">Porovná jeden nebo více výskytů (ale nejmenším) jakéhokoliv znaku jiného než lomítko.</span><span class="sxs-lookup"><span data-stu-id="17f76-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="17f76-114">Porovná žádný nebo jeden výskyt dvojtečku následovanou jeden nebo více znaků číslice.</span><span class="sxs-lookup"><span data-stu-id="17f76-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="17f76-115">Pojmenovat tuto skupinu `port`.</span><span class="sxs-lookup"><span data-stu-id="17f76-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="17f76-116">Porovná znak lomítko.</span><span class="sxs-lookup"><span data-stu-id="17f76-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="17f76-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda rozšiřuje `${proto}${port}` pořadí nahrazení, který zřetězí hodnoty ze dvou pojmenované skupiny zachycené ve vzoru regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="17f76-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="17f76-118">Je vhodné alternativou k explicitnímu zřetězení řetězců získaných z objektu kolekce vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="17f76-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="17f76-119">V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu se dvěma náhrady `${proto}` a `${port}`, aby zahrnoval zachycené skupiny ve výstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="17f76-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="17f76-120">Zachycené skupiny můžete načíst z ke shodě <xref:System.Text.RegularExpressions.GroupCollection> objekt místo toho, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="17f76-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="17f76-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17f76-121">See also</span></span>

- [<span data-ttu-id="17f76-122">Regulárních výrazů .NET</span><span class="sxs-lookup"><span data-stu-id="17f76-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
