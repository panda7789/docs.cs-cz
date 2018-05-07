---
title: Počítaný od nuly vs. Přístup na základě jedné řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a0a42f72d94adf1c10865374017fa61e833df40f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Počítaný od nuly vs. Přístup na základě jedné řetězce v jazyce Visual Basic
Toto téma porovnává jak Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytnout přístup k znaky v řetězci. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Vždy poskytuje nule přístup k znaky v řetězci, zatímco Visual Basic poskytuje nule a na základě jedné přístup, v závislosti na funkce.  
  
## <a name="one-based"></a>Na základě jedné  
 Příklad funkce na základě jedné jazyka Visual Basic, vezměte v úvahu `Mid` funkce. Trvá argument, který označuje znak na pozici, na které se spustí dílčí řetězec, počínaje na pozici 1. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda přebírá index znaku v řetězci, na které má začít, dílčí řetězec začínající na pozici 0. Pokud máte řetězec "ABCDE", proto jsou jednotlivé znaky číslované 1,2,3,4,5 pro použití s `Mid` funkce, ale 0,1,2,3,4 pro použití s <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda.  
  
## <a name="zero-based"></a>Počítaný od nuly  
 Příklad nule funkce jazyka Visual Basic, vezměte v úvahu `Split` funkce. Rozdělí řetězec a vrátí pole obsahující dílčích řetězců. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda také rozdělí řetězec a vrátí pole obsahující dílčích řetězců. Protože `Split` funkce a <xref:System.String.Split%2A> metoda návratový [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pole, musí být od nuly.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Představení řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
