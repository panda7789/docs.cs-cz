---
title: Zero-based vs. One-based String Access
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
This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string. The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.  
  
## <a name="one-based"></a>One-Based  
 For an example of a one-based Visual Basic function, consider the `Mid` function. It takes an argument that indicates the character position at which the substring will start, starting with position 1. The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0. Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.  
  
## <a name="zero-based"></a>Zero-Based  
 For an example of a zero-based Visual Basic function, consider the `Split` function. It splits a string and returns an array containing the substrings. The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings. Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
