---
title: "Postupy: Extrahování protokolu a čísla portu z adresy URL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 62931273acd41768d131c08510e14ff187d64296
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Postupy: Extrahování protokolu a čísla portu z adresy URL
Následující příklad extrahuje protokol a číslo portu z adresy URL.  
  
## <a name="example"></a>Příklad  
 V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda vrátí protokol následovaným dvojtečkou a číslo portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Regulární výraz `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` lze interpretovat, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začne porovnávání na začátku řetězce.|  
|`(?<proto>\w+)`|Porovná jeden nebo více znaků slova. Název této skupiny `proto`.|  
|`://`|Porovná dvojtečkou následované dvěma lomítka.|  
|`[^/]+?`|Porovná jeden nebo více výskytů (ale co nejméně) libovolný znak než lomítko.|  
|`(?<port>:\d+)?`|Porovná nula nebo jeden výskyt dvojtečkou následuje jeden nebo více znaků, číslic. Název této skupiny `port`.|  
|`/`|Odpovídat lomítko.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda rozšíří `${proto}${port}` pořadí nahrazení, která zřetězí hodnoty dvou pojmenovaných skupin zaznamenané v regulární výraz. Je vhodnou alternativu explicitně zřetězení řetězců získaných z objektu kolekce vrácené <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost.  
  
 V příkladu se používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda s dvěma náhrady `${proto}` a `${port}`, zahrnout zaznamenané skupiny do výstupního řetězce. Zachycené skupiny můžete načíst z na shodu <xref:System.Text.RegularExpressions.GroupCollection> objektu místo toho, jak ukazuje následující kód.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
