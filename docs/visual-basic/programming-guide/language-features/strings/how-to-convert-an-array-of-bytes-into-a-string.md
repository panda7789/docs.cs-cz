---
title: 'Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: c22ae89322230d8a98ae3ae2c1485e73456e0a7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic
Toto téma ukazuje, jak převést bajtů z bajtového pole na řetězec.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Text.Encoding.GetString%2A> metodu <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kódování třída převést všech bajtů z bajtového pole do řetězce.  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 Můžete vybrat z několika kódování možnosti pro převedení pole bajtů na řetězec:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Kódování pro znaků ASCII (7 bitů) získá nastavit.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování pro ve formátu UTF-16 s využitím pořadí bajtů big endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování pro aktuální stránky kódu ANSI systému.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování pro ve formátu UTF-16 s využitím pořadí bajtů little endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování pro ve formátu UTF-32 s využitím pořadí bajtů little endian.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetString%2A>  
 [Postupy: převod řetězců na pole bajtů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
