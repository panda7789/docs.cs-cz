---
title: 'Příklad regulárního výrazu: Změna formátů kalendářních dat'
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
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 358e26957747073fec9dfe9eb0d404cb438afaf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084182"
---
# <a name="regular-expression-example-changing-date-formats"></a>Příklad regulárního výrazu: Změna formátů kalendářních dat
Následující příklad kódu <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> používá metodu k nahrazení kalendářních dat, která mají formulář *mm*/*dd*/*yy, daty,* která mají formulář *dd*-*mm*-*yy*.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Následující kód ukazuje, `MDYToDMY` jak lze metodu volat v aplikaci.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentáře  
 Vzor regulárního výrazu `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?<month>\d{1,2})`|Porovná jednu nebo dvě desetinná místa. Tohle je `month` zachycená skupina.|  
|`/`|Porovná značku lomítka.|  
|`(?<day>\d{1,2})`|Porovná jednu nebo dvě desetinná místa. Tohle je `day` zachycená skupina.|  
|`/`|Porovná značku lomítka.|  
|`(?<year>\d{2,4})`|Shoda od dvou do čtyř desetinných míst. Tohle je `year` zachycená skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzorek `${day}-${month}-${year}` definuje náhradní řetězec, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`$(day)`|Přidejte řetězec zachycený `day` zachytávající skupinou.|  
|`-`|Přidejte pomlčku.|  
|`$(month)`|Přidejte řetězec zachycený `month` zachytávající skupinou.|  
|`-`|Přidejte pomlčku.|  
|`$(year)`|Přidejte řetězec zachycený `year` zachytávající skupinou.|  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
