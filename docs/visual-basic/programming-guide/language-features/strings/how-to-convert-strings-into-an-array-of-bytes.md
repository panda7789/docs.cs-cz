---
title: 'Postupy: převod řetězců na pole bajtů'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 76fde3120ce629ce32f29ca28d90eba24fff726c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351972"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Postupy: Převod řetězců na pole bajtů v jazyce Visual Basic
Toto téma ukazuje, jak převést řetězec na pole bajtů.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Text.Encoding.GetBytes%2A> třídy <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> Encoding pro převod řetězce na pole bajtů.  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 Můžete zvolit z několika možností kódování pro převod řetězce na pole bajtů:  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Získá kódování znakové sady ASCII (7 bitů).  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování formátu UTF-16 pomocí pořadí bajtů big-endian.  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování pro aktuální znakovou stránku ANSI systému.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-16 pomocí pořadí bajtů ve formátu Little endian.  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování formátu UTF-32 pomocí pořadí bajtů ve formátu Little endian.  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-7.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [Postupy: převedení pole bajtů na řetězec v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
