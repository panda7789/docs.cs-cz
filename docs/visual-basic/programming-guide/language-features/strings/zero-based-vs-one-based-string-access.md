---
title: Přístup k řetězci založený na nule vs. One
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: ce2fcb2610c09a9591a5fd79da4baa74cc533c99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363653"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Přístup k řetězci v jazyce Visual Basic počítaný od nuly vs. počítaný od hodnoty jedna
Toto téma porovnává, jak Visual Basic a .NET Framework poskytují přístup ke znakům v řetězci. .NET Framework vždy poskytuje přístup založený na nule ke znakům v řetězci, zatímco Visual Basic poskytuje přístup založený na nule a jednom v závislosti na funkci.  
  
## <a name="one-based"></a>Založený na jednom  
 Pro příklad funkce Visual Basic založené na jedné, zvažte `Mid` funkci. Přebírá argument, který označuje pozici znaku, na které se dílčí řetězec spustí, počínaje pozicí 1. Metoda .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> přebírá index znaku v řetězci, na kterém je dílčí řetězec spuštěn, počínaje pozicí 0. Proto pokud máte řetězec "ABCDE", jednotlivé znaky jsou očíslovány 1, 2, 3, 4, 5 pro použití s `Mid` funkcí, ale 0, 1, 2, 3, 4 pro použití s <xref:System.String.Substring%2A?displayProperty=nameWithType> metodou.  
  
## <a name="zero-based"></a>Založený na nule  
 Příklad funkce Visual Basic založené na nule, je třeba vzít v úvahu `Split` funkci. Rozdělí řetězec a vrátí pole obsahující podřetězce. Metoda .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> také rozdělí řetězec a vrátí pole obsahující podřetězce. Vzhledem k tomu `Split` , že funkce a <xref:System.String.Split%2A> metoda vrací .NET Framework pole, musí být počítány od nuly.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Představení řetězců v jazyce Visual Basic](introduction-to-strings.md)
