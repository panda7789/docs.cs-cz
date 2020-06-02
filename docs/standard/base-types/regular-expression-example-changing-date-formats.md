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
ms.openlocfilehash: 4290bf0d6ee9deec8129c5f4f6092eedb08345f0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276176"
---
# <a name="regular-expression-example-changing-date-formats"></a>Příklad regulárního výrazu: Změna formátů data
Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu k nahrazení kalendářních dat, která mají formát *mm* / *DD* / *RR* s kalendářními daty, která mají tvar *DD* - *mm* - *RR*.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Následující kód ukazuje, jak `MDYToDMY` lze metodu volat v aplikaci.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentáře  
 Vzor regulárního výrazu `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(?<month>\d{1,2})`|Porovnává jednu nebo dvě desítkové číslice. Toto je `month` zachycená skupina.|  
|`/`|Odpovídá znaku lomítka.|  
|`(?<day>\d{1,2})`|Porovnává jednu nebo dvě desítkové číslice. Toto je `day` zachycená skupina.|  
|`/`|Odpovídá znaku lomítka.|  
|`(?<year>\d{2,4})`|Porovnává dvě až čtyři desítkové číslice. Toto je `year` zachycená skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor `${day}-${month}-${year}` definuje náhradní řetězec, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`$(day)`|Přidejte řetězec zachycený `day` zachycující skupinou.|  
|`-`|Přidejte spojovník.|  
|`$(month)`|Přidejte řetězec zachycený `month` zachycující skupinou.|  
|`-`|Přidejte spojovník.|  
|`$(year)`|Přidejte řetězec zachycený `year` zachycující skupinou.|  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy .NET](regular-expressions.md)
