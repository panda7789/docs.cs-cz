---
title: 'Postupy: převod pole bajtů na řetězec'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 8c1d9d1d2e89390873bc1c3dbb9623f047433a9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351978"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic
Toto téma ukazuje, jak převést bajty z bajtového pole na řetězec.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Text.Encoding.GetString%2A> třídy <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> Encoding pro převod všech bajtů z pole bajtů do řetězce.  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 Můžete vybrat z několika možností kódování pro převod pole bajtů na řetězec:  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Získá kódování znakové sady ASCII (7 bitů).  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování formátu UTF-16 pomocí pořadí bajtů big-endian.  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování pro aktuální znakovou stránku ANSI systému.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-16 pomocí pořadí bajtů ve formátu Little endian.  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování formátu UTF-32 pomocí pořadí bajtů ve formátu Little endian.  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-7.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Postupy: převod řetězců na pole bajtů v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
