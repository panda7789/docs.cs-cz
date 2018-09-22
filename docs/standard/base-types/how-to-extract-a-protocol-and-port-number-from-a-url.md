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
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583782"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Postupy: Extrahování protokolu a čísla portu z adresy URL
Následující příklad extrahuje protokol a číslo portu z adresy URL.  
  
## <a name="example"></a>Příklad  
 V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda vrátí protokolu za nímž následuje dvojtečka, za nímž následuje číslo portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` lze interpretovat, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku řetězce.|  
|`(?<proto>\w+)`|Porovná jeden nebo více znaků slova. Pojmenovat tuto skupinu `proto`.|  
|`://`|Porovná dvojtečku následovanou dvěma lomítky.|  
|`[^/]+?`|Porovná jeden nebo více výskytů (ale nejmenším) jakéhokoliv znaku jiného než lomítko.|  
|`(?<port>:\d+)?`|Porovná žádný nebo jeden výskyt dvojtečku následovanou jeden nebo více znaků číslice. Pojmenovat tuto skupinu `port`.|  
|`/`|Porovná znak lomítko.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda rozšiřuje `${proto}${port}` pořadí nahrazení, který zřetězí hodnoty ze dvou pojmenované skupiny zachycené ve vzoru regulárního výrazu. Je vhodné alternativou k explicitnímu zřetězení řetězců získaných z objektu kolekce vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost.  
  
 V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu se dvěma náhrady `${proto}` a `${port}`, aby zahrnoval zachycené skupiny ve výstupním řetězci. Zachycené skupiny můžete načíst z ke shodě <xref:System.Text.RegularExpressions.GroupCollection> objekt místo toho, jak ukazuje následující kód.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md)
