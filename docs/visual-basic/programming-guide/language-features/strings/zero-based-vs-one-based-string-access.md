---
title: Přístup k řetězci založený na nule vs. One
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354290"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Přístup k řetězci v jazyce Visual Basic počítaný od nuly vs. počítaný od hodnoty jedna
Toto téma porovnává, jak Visual Basic a .NET Framework poskytují přístup ke znakům v řetězci. .NET Framework vždy poskytuje přístup založený na nule ke znakům v řetězci, zatímco Visual Basic poskytuje přístup založený na nule a jednom v závislosti na funkci.  
  
## <a name="one-based"></a>Založený na jednom  
 Příklad Visual Basic funkce založené na funkci `Mid` je považovat za funkce. Přebírá argument, který označuje pozici znaku, na které se dílčí řetězec spustí, počínaje pozicí 1. Metoda .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> přebírá index znaku v řetězci, na kterém je dílčí řetězec spuštěn, počínaje pozicí 0. Proto pokud máte řetězec "ABCDE", jednotlivé znaky jsou očíslovány 1, 2, 3, 4, 5 pro použití s funkcí `Mid`, ale 0, 1, 2, 3, 4 pro použití s metodou <xref:System.String.Substring%2A?displayProperty=nameWithType>.  
  
## <a name="zero-based"></a>Založený na nule  
 Příklad funkce Visual Basic založené na nule, je považovat za funkci `Split`. Rozdělí řetězec a vrátí pole obsahující podřetězce. Metoda .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> také rozdělí řetězec a vrátí pole obsahující podřetězce. Vzhledem k tomu, že funkce `Split` a metoda <xref:System.String.Split%2A> vrací .NET Framework pole, musí být založené na nule.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Seznámení s řetězci v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
