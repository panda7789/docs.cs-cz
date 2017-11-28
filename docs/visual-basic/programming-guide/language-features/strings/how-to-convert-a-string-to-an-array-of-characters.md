---
title: "Postupy: Převod řetězce na pole znaků v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59d0da52c8f78b93c76325e6242156c106deeaf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Postupy: Převod řetězce na pole znaků v jazyce Visual Basic
Někdy je užitečné používat data o znaky v řetězec vašeho a pozice z těchto znaků v řetězci, například když analyzujete řetězec. Tento příklad ukazuje, jak můžete získat pole znaky v řetězci voláním řetězec <xref:System.String.ToCharArray%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole jeho textových znaků Unicode. Důvody, proč tento rozdíl je, že znaky znakové sady Unicode text může skládat ze dvou nebo více `Char` znaků (například náhradní pár nebo kombinování sekvenci znaků). Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a "Ve standardu Unicode" na http://www.unicode.org.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Příklad  
 Je obtížné rozdělit řetězec na jeho text znaky znakové sady Unicode, ale to je nezbytné, pokud potřebujete informace o vizuální reprezentace řetězec. Tento příklad používá <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodu za účelem získání informací o textových znaků Unicode, které tvoří řetězec.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Postupy: přístup ke znakům v řetězcích](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Převod mezi řetězci a ostatními typy dat v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
