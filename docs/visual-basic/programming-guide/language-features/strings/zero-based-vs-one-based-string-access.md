---
title: "Počítaný od nuly vs. Přístup na základě jedné řetězce v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Počítaný od nuly vs. Přístup na základě jedné řetězce v jazyce Visual Basic
Toto téma porovnává jak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytnout přístup k znaky v řetězci. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Vždy poskytuje nule přístup k znaky v řetězci, zatímco [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] poskytuje nule a na základě jedné přístup, v závislosti na funkce.  
  
## <a name="one-based"></a>Na základě jedné  
 Příklad základem jedna [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fungovat, vezměte v úvahu `Mid` funkce. Trvá argument, který označuje znak na pozici, na které se spustí dílčí řetězec, počínaje na pozici 1. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda přebírá index znaku v řetězci, na které má začít, dílčí řetězec začínající na pozici 0. Pokud máte řetězec "ABCDE", proto jsou jednotlivé znaky číslované 1,2,3,4,5 pro použití s `Mid` funkce, ale 0,1,2,3,4 pro použití s <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda.  
  
## <a name="zero-based"></a>Počítaný od nuly  
 Příklad nulovým základem [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fungovat, vezměte v úvahu `Split` funkce. Rozdělí řetězec a vrátí pole obsahující dílčích řetězců. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda také rozdělí řetězec a vrátí pole obsahující dílčích řetězců. Protože `Split` funkce a <xref:System.String.Split%2A> metoda návratový [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pole, musí být od nuly.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Představení řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
