---
title: 'Postupy: Extrahování protokolu a čísla portu z adresy URL'
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
ms.openlocfilehash: c1d45dbcb2916af86d645d7813594f2b278bb7c2
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803869"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="df6b5-102">Postupy: Extrahování protokolu a čísla portu z adresy URL</span><span class="sxs-lookup"><span data-stu-id="df6b5-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="df6b5-103">Následující příklad extrahuje protokol a číslo portu z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="df6b5-103">The following example extracts a protocol and port number from a URL.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="df6b5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="df6b5-104">Example</span></span>  
 <span data-ttu-id="df6b5-105">V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda, která vrátí protokol následovaný dvojtečkou a číslem portu.</span><span class="sxs-lookup"><span data-stu-id="df6b5-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="df6b5-106">Vzor regulárního výrazu `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` může být interpretován tak, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="df6b5-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="df6b5-107">Vzor</span><span class="sxs-lookup"><span data-stu-id="df6b5-107">Pattern</span></span>|<span data-ttu-id="df6b5-108">Popis</span><span class="sxs-lookup"><span data-stu-id="df6b5-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="df6b5-109">Zahajte shodu na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="df6b5-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="df6b5-110">Porovná jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="df6b5-110">Match one or more word characters.</span></span> <span data-ttu-id="df6b5-111">Pojmenujte tuto skupinu `proto` .</span><span class="sxs-lookup"><span data-stu-id="df6b5-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="df6b5-112">Porovnává dvojtečku následovanou dvěma lomítky.</span><span class="sxs-lookup"><span data-stu-id="df6b5-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="df6b5-113">Porovnává jeden nebo více výskytů (ale s co nejmenším možným) libovolného znaku jiného než znak lomítka.</span><span class="sxs-lookup"><span data-stu-id="df6b5-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="df6b5-114">Porovná žádný nebo jeden výskyt dvojtečky následovaný jedním nebo více znaky číslice.</span><span class="sxs-lookup"><span data-stu-id="df6b5-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="df6b5-115">Pojmenujte tuto skupinu `port` .</span><span class="sxs-lookup"><span data-stu-id="df6b5-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="df6b5-116">Odpovídá znaku lomítka.</span><span class="sxs-lookup"><span data-stu-id="df6b5-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="df6b5-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Metoda rozbalí `${proto}${port}` sekvenci nahrazení, která zřetězí hodnotu dvou pojmenovaných skupin zachycených ve vzorku regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="df6b5-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="df6b5-118">Je vhodná alternativa k explicitnímu zřetězení řetězců načtených z objektu kolekce vráceného <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastností.</span><span class="sxs-lookup"><span data-stu-id="df6b5-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="df6b5-119">V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda se dvěma náhradami `${proto}` a `${port}` , pokud chcete zahrnout zachycené skupiny do výstupního řetězce.</span><span class="sxs-lookup"><span data-stu-id="df6b5-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="df6b5-120">Zachycené skupiny lze načíst z <xref:System.Text.RegularExpressions.GroupCollection> objektu shody, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="df6b5-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="df6b5-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df6b5-121">See also</span></span>

- [<span data-ttu-id="df6b5-122">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="df6b5-122">.NET Regular Expressions</span></span>](regular-expressions.md)
