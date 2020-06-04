---
title: 'Postupy: Převod řetězce na pole znaků'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: eca8cd7be8da1f6149dadf1e9edeab5e5225ab9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360667"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Postupy: Převod řetězce na pole znaků v jazyce Visual Basic
Někdy je užitečné mít data o znacích v řetězci a umístění těchto znaků v rámci řetězce, například při analýze řetězce. Tento příklad ukazuje, jak lze získat pole znaků v řetězci voláním <xref:System.String.ToCharArray%2A> metody řetězce.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole textových znaků Unicode. Důvodem pro tento rozdíl je, že textové znaky Unicode mohou být složeny ze dvou nebo více `Char` znaků (například náhradní dvojice nebo kombinování znakových sekvencí). Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a [standardu Unicode](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Příklad  
 Je obtížnější rozdělit řetězec na své textové znaky Unicode, ale to je nezbytné, pokud potřebujete informace o vizuálním znázornění řetězce. Tento příklad používá <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodu k získání informací o textových znacích Unicode, které tvoří řetězec.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Postupy: Přístup ke znakům v řetězcích](how-to-access-characters-in-strings.md)
- [Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic](converting-between-strings-and-other-data-types.md)
- [Řetězce](index.md)
