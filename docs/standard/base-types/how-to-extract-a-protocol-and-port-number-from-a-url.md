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
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Postupy: Extrahování protokolu a čísla portu z adresy URL
Následující příklad extrahuje protokol a číslo portu z adresy URL.  
  
## <a name="example"></a>Příklad  
 Příklad používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu k vrácení protokolu následovaného dvojtečkou následovanou číslem portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` lze interpretovat tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začněte zápas na začátku řetězce.|  
|`(?<proto>\w+)`|Porovná jeden nebo více znaků slova. Pojmenujte `proto`tuto skupinu .|  
|`://`|Porovná dvojtečku následovanou dvěma značkami lomítka.|  
|`[^/]+?`|Porovná jeden nebo více výskytů (ale co nejméně) libovolného znaku kromě znaku lomítka.|  
|`(?<port>:\d+)?`|Porovná nulový nebo jeden výskyt dvojtečky následovaný jedním nebo více číslicovými znaky. Pojmenujte `port`tuto skupinu .|  
|`/`|Porovná lomítko.|  
  
 Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> rozšiřuje `${proto}${port}` náhradní sekvenci, která zřetězí hodnotu dvou pojmenovaných skupin zachycených ve vzoru regulárního výrazu. Je to vhodná alternativa k explicitnímu zřetězení řetězců načtených <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> z objektu kolekce vrácených vlastností.  
  
 Příklad používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu se dvěma substitucemi `${proto}` a `${port}`, chcete-li zahrnout zachycené skupiny do výstupního řetězce. Můžete načíst zachycené skupiny z <xref:System.Text.RegularExpressions.GroupCollection> objektu shody místo, jak ukazuje následující kód.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
