---
title: 'Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: cd091d743b04ef9d9709bde2b5a1205f3d7ae292
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979496"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic
Toto téma ukazuje, jak převést bajty z pole bajtů na řetězec.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Text.Encoding.GetString%2A> metodu <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kódování pro převod všech bajtů z bajtového pole do řetězce.  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 Můžete použít jednu z několika možností kódování převést řetězec na bajtové pole:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Získá kódování (7-bit) znakové sady ASCII.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu big endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování systému aktuální znakovou stránku ANSI.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu little endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-32 s využitím pořadí bajtů ve formátu little endian.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování UTF-7 formátu.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Postupy: Převod řetězce na pole bajtů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
