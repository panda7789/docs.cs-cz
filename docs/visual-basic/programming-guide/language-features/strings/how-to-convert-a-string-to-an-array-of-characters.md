---
title: 'Postupy: Převod řetězce na pole znaků v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: 9d68e3d90c52d6a4312ccb7c0c9610968e7a4b55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603752"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Postupy: Převod řetězce na pole znaků v jazyce Visual Basic
Někdy je užitečné mít data o znaky v váš řetězec a umístění těchto znaků v řetězci, například když je analýza řetězce. Tento příklad ukazuje, jak získat pole znaků v řetězci pomocí volání řetězce <xref:System.String.ToCharArray%2A> metody.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole jeho textové znaky kódování Unicode. Důvod pro tento rozdíl je, že znaky kódování Unicode se může skládat ze dvou nebo více `Char` znaky (například náhradní pár nebo kombinování posloupnosti znaků). Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a [standardu Unicode](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Příklad  
 Je obtížnější rozdělit řetězec na jeho textové znaky Unicode, ale to je nezbytné, pokud potřebujete informace o bude obsahovat vizuální reprezentaci řetězce. V tomto příkladu <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodu k získání informací o textové znaky Unicode, které společně tvoří řetězec.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Postupy: Přístup znakům v řetězcích](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
