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
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Postupy: Extrahování protokolu a čísla portu z adresy URL
Následující příklad extrahuje protokol a číslo portu z adresy URL.  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Příklad  
 V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda, která vrátí protokol následovaný dvojtečkou a číslem portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` může být interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahajte shodu na začátku řetězce.|  
|`(?<proto>\w+)`|Porovná jeden nebo více znaků slova. Pojmenujte tuto skupinu `proto` .|  
|`://`|Porovnává dvojtečku následovanou dvěma lomítky.|  
|`[^/]+?`|Porovnává jeden nebo více výskytů (ale s co nejmenším možným) libovolného znaku jiného než znak lomítka.|  
|`(?<port>:\d+)?`|Porovná žádný nebo jeden výskyt dvojtečky následovaný jedním nebo více znaky číslice. Pojmenujte tuto skupinu `port` .|  
|`/`|Odpovídá znaku lomítka.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Metoda rozbalí `${proto}${port}` sekvenci nahrazení, která zřetězí hodnotu dvou pojmenovaných skupin zachycených ve vzorku regulárního výrazu. Je vhodná alternativa k explicitnímu zřetězení řetězců načtených z objektu kolekce vráceného <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastností.  
  
 V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda se dvěma náhradami `${proto}` a `${port}` , pokud chcete zahrnout zachycené skupiny do výstupního řetězce. Zachycené skupiny lze načíst z <xref:System.Text.RegularExpressions.GroupCollection> objektu shody, jak ukazuje následující kód.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Regulární výrazy .NET](regular-expressions.md)
