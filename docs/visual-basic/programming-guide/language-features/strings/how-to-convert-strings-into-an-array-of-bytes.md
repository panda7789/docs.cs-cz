---
title: 'Postupy: Převod řetězce na pole bajtů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 786065fde9814d31ac36b56e1455d5b1685122ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665348"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Postupy: Převod řetězce na pole bajtů v jazyce Visual Basic
Toto téma ukazuje, jak převést pole bajtů na řetězec.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Text.Encoding.GetBytes%2A> metodu <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kódování třídy pro převod řetězce na pole bajtů.  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 Můžete použít jednu z několika možností kódování převést řetězec na bajtové pole:  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Získá kódování (7-bit) znakové sady ASCII.  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu big endian.  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Získá kódování systému aktuální znakovou stránku ANSI.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-16 s využitím pořadí bajtů ve formátu little endian.  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Získá kódování ve formátu UTF-32 s využitím pořadí bajtů ve formátu little endian.  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Získá kódování UTF-7 formátu.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Získá kódování pro formát UTF-8.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [Postupy: Převod pole bajtů na řetězec v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
