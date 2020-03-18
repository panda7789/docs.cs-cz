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
ms.openlocfilehash: f2704e3fb5ceb68609a475d52e11030177ad760b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138724"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="3bbf8-102">Postupy: Extrahování protokolu a čísla portu z adresy URL</span><span class="sxs-lookup"><span data-stu-id="3bbf8-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="3bbf8-103">Následující příklad extrahuje protokol a číslo portu z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bbf8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bbf8-104">Example</span></span>  
 <span data-ttu-id="3bbf8-105">Příklad používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu k vrácení protokolu následovaného dvojtečkou následovanou číslem portu.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="3bbf8-106">Vzor regulárního výrazu `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` lze interpretovat tak, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="3bbf8-107">Vzor</span><span class="sxs-lookup"><span data-stu-id="3bbf8-107">Pattern</span></span>|<span data-ttu-id="3bbf8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3bbf8-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="3bbf8-109">Začněte zápas na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="3bbf8-110">Porovná jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-110">Match one or more word characters.</span></span> <span data-ttu-id="3bbf8-111">Pojmenujte `proto`tuto skupinu .</span><span class="sxs-lookup"><span data-stu-id="3bbf8-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="3bbf8-112">Porovná dvojtečku následovanou dvěma značkami lomítka.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="3bbf8-113">Porovná jeden nebo více výskytů (ale co nejméně) libovolného znaku kromě znaku lomítka.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="3bbf8-114">Porovná nulový nebo jeden výskyt dvojtečky následovaný jedním nebo více číslicovými znaky.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="3bbf8-115">Pojmenujte `port`tuto skupinu .</span><span class="sxs-lookup"><span data-stu-id="3bbf8-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="3bbf8-116">Porovná lomítko.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="3bbf8-117">Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> rozšiřuje `${proto}${port}` náhradní sekvenci, která zřetězí hodnotu dvou pojmenovaných skupin zachycených ve vzoru regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="3bbf8-118">Je to vhodná alternativa k explicitnímu zřetězení řetězců načtených <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> z objektu kolekce vrácených vlastností.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="3bbf8-119">Příklad používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu se dvěma substitucemi `${proto}` a `${port}`, chcete-li zahrnout zachycené skupiny do výstupního řetězce.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="3bbf8-120">Můžete načíst zachycené skupiny z <xref:System.Text.RegularExpressions.GroupCollection> objektu shody místo, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="3bbf8-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3bbf8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bbf8-121">See also</span></span>

- [<span data-ttu-id="3bbf8-122">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3bbf8-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
