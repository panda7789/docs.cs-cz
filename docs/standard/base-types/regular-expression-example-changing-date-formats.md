---
title: 'Příklad regulárního výrazu: Změna formátů data'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c26608115a22a5402d671c5f5e51c75442a0a5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48264385"
---
# <a name="regular-expression-example-changing-date-formats"></a>Příklad regulárního výrazu: Změna formátů data
Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody lze nahradit data, která bude mít formát _služba ._protokol *mm*/*dd*/*rr* s daty, která mít formát _služba ._protokol *dd*-*mm*-*rr*.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Následující kód ukazuje jak `MDYToDMY` metodu lze volat v aplikaci.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentáře  
 Vzor regulárního výrazu `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?<month>\d{1,2})`|Porovná jednu nebo dvě desetinné číslice. Toto je `month` zachycenou skupinou.|  
|`/`|Porovná lomítko.|  
|`(?<day>\d{1,2})`|Porovná jednu nebo dvě desetinné číslice. Toto je `day` zachycenou skupinou.|  
|`/`|Porovná lomítko.|  
|`(?<year>\d{2,4})`|Porovná dvě pro čtyři desítková čísla. Toto je `year` zachycenou skupinou.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor `${day}-${month}-${year}` řetězci pro nahrazení definuje, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`$(day)`|Přidejte řetězec zachycena `day` zachytávající skupinu.|  
|`-`|Přidáte spojovníkem.|  
|`$(month)`|Přidejte řetězec zachycena `month` zachytávající skupinu.|  
|`-`|Přidáte spojovníkem.|  
|`$(year)`|Přidejte řetězec zachycena `year` zachytávající skupinu.|  
  
## <a name="see-also"></a>Viz také:

- [Regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md)
