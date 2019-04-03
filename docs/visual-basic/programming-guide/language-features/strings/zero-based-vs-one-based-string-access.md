---
title: Přístup k řetězci se základem 0 vs. Přístup k řetězci základem 1 v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a6ceb10d4a3cb9463551d8c85375ddbbb607ffdc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830328"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Přístup k řetězci se základem 0 vs. Přístup k řetězci základem 1 v jazyce Visual Basic
Toto téma srovnává způsobu, jakým Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytují přístup ke znakům v řetězci. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Vždy poskytuje založený na nule přístup ke znakům v řetězci, zatímco Visual Basic poskytuje přístup založený na nule a založen na jedničce, v závislosti na funkci.  
  
## <a name="one-based"></a>Základem 1  
 Příklad funkce jazyka Visual Basic založen na jedničce, vezměte v úvahu `Mid` funkce. To přebírá argument, který označuje znak na pozici, na které se spustí dílčí řetězec, počínaje pozice 1. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda má index znaku v řetězci, na které má spustit, podřetězec počínaje pozice 0. Pokud máte řetězec "ABCDE", proto jsou jednotlivé znaky číslované 1,2,3,4,5 pro použití s `Mid` funkce, ale 0,1,2,3,4 pro použití se službou <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda.  
  
## <a name="zero-based"></a>Od nuly  
 Příklad založený na nule funkce jazyka Visual Basic, vezměte v úvahu `Split` funkce. Rozdělí řetězec a vrátí pole obsahující podřetězce. [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda také rozdělí řetězec a vrátí pole obsahující podřetězce. Protože `Split` funkce a <xref:System.String.Split%2A> metoda návratový [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pole, musí být založený na nule.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Úvod do řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
