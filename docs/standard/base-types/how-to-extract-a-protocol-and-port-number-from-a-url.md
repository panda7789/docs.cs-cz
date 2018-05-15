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
ms.openlocfilehash: ffb31030a2e29458165ae6615a51685ed163fbac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="d4ba8-102">Postupy: Extrahování protokolu a čísla portu z adresy URL</span><span class="sxs-lookup"><span data-stu-id="d4ba8-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="d4ba8-103">Následující příklad extrahuje protokol a číslo portu z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4ba8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4ba8-104">Example</span></span>  
 <span data-ttu-id="d4ba8-105">V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda vrátí protokol následovaným dvojtečkou a číslo portu.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="d4ba8-106">Regulární výraz `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` lze interpretovat, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="d4ba8-107">Vzor</span><span class="sxs-lookup"><span data-stu-id="d4ba8-107">Pattern</span></span>|<span data-ttu-id="d4ba8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d4ba8-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="d4ba8-109">Začne porovnávání na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="d4ba8-110">Porovná jeden nebo více znaků slova.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-110">Match one or more word characters.</span></span> <span data-ttu-id="d4ba8-111">Název této skupiny `proto`.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="d4ba8-112">Porovná dvojtečkou následované dvěma lomítka.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="d4ba8-113">Porovná jeden nebo více výskytů (ale co nejméně) libovolný znak než lomítko.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="d4ba8-114">Porovná nula nebo jeden výskyt dvojtečkou následuje jeden nebo více znaků, číslic.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="d4ba8-115">Název této skupiny `port`.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="d4ba8-116">Odpovídat lomítko.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="d4ba8-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda rozšíří `${proto}${port}` pořadí nahrazení, která zřetězí hodnoty dvou pojmenovaných skupin zaznamenané v regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="d4ba8-118">Je vhodnou alternativu explicitně zřetězení řetězců získaných z objektu kolekce vrácené <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="d4ba8-119">V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda s dvěma náhrady `${proto}` a `${port}`, zahrnout zaznamenané skupiny do výstupního řetězce.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="d4ba8-120">Zachycené skupiny můžete načíst z na shodu <xref:System.Text.RegularExpressions.GroupCollection> objektu místo toho, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="d4ba8-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d4ba8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4ba8-121">See Also</span></span>  
 [<span data-ttu-id="d4ba8-122">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d4ba8-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
