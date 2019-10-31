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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138724"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Postupy: Extrahování protokolu a čísla portu z adresy URL
Následující příklad extrahuje protokol a číslo portu z adresy URL.  
  
## <a name="example"></a>Příklad  
 V příkladu se pomocí metody <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> vrátí protokol následovaný dvojtečkou následovaným číslem portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` lze interpretovat, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahajte shodu na začátku řetězce.|  
|`(?<proto>\w+)`|Porovná jeden nebo více znaků slova. Pojmenujte tuto skupinu `proto`.|  
|`://`|Porovnává dvojtečku následovanou dvěma lomítky.|  
|`[^/]+?`|Porovnává jeden nebo více výskytů (ale s co nejmenším možným) libovolného znaku jiného než znak lomítka.|  
|`(?<port>:\d+)?`|Porovná žádný nebo jeden výskyt dvojtečky následovaný jedním nebo více znaky číslice. Pojmenujte tuto skupinu `port`.|  
|`/`|Odpovídá znaku lomítka.|  
  
 Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> rozšíří sekvenci nahrazení `${proto}${port}`, která zřetězí hodnotu dvou pojmenovaných skupin zachycených ve vzorku regulárního výrazu. Je vhodná alternativa k explicitnímu zřetězení řetězců načtených z objektu kolekce vráceného vlastností <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>.  
  
 V příkladu se používá metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> se dvěma náhradami, `${proto}` a `${port}`, aby se do výstupního řetězce zahrnuly zachycené skupiny. Zachycené skupiny lze načíst z objektu <xref:System.Text.RegularExpressions.GroupCollection> shody, jak ukazuje následující kód.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Regulární výrazy .NET](../../../docs/standard/base-types/regular-expressions.md)
