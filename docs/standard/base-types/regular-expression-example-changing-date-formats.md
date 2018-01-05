---
title: "Příklad regulární výraz: Změna formátů data"
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
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 93c526e87f7aba650cce397962c7262b6fd2f085
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-example-changing-date-formats"></a>Příklad regulární výraz: Změna formátů data
Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody lze nahradit kalendářních dat, které mají tvar *mm*/*dd*/*rr* s data, která mít formát *dd*-*mm*-*rr*.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Následující kód ukazuje jak `MDYToDMY` metodu lze volat v aplikaci.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentáře  
 Regulární výraz `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?<month>\d{1,2})`|Odpovídat jedna nebo dvě desetinných míst. Toto je `month` zaznamenané skupiny.|  
|`/`|Porovná lomítko.|  
|`(?<day>\d{1,2})`|Odpovídat jedna nebo dvě desetinných míst. Toto je `day` zaznamenané skupiny.|  
|`/`|Porovná lomítko.|  
|`(?<year>\d{2,4})`|Odpovídat ze dvou na čtyři desítková číslice. Toto je `year` zaznamenané skupiny.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor `${day}-${month}-${year}` definuje náhradní řetězec, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`$(day)`|Přidejte řetězec zachyceny `day` zaznamenávání skupiny.|  
|`-`|Přidejte pomlčka.|  
|`$(month)`|Přidejte řetězec zachyceny `month` zaznamenávání skupiny.|  
|`-`|Přidejte pomlčka.|  
|`$(year)`|Přidejte řetězec zachyceny `year` zaznamenávání skupiny.|  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
