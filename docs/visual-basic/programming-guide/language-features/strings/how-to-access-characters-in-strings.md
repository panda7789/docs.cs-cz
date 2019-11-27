---
title: 'Postupy: Přístup ke znakům v řetězcích'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352460"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic
Tento příklad ukazuje, jak použít vlastnost <xref:System.String.Chars%2A> pro přístup k znaku v zadaném umístění v řetězci.  
  
## <a name="example"></a>Příklad  
 Někdy je užitečné mít data o znacích v řetězci a umístění těchto znaků v rámci řetězce. Řetězec lze představit jako pole znaků (`Char` instance); můžete načíst konkrétní znak odkazem na index daného znaku prostřednictvím vlastnosti <xref:System.String.Chars%2A>.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 Parametr `index` vlastnosti <xref:System.String.Chars%2A> je založený na nule.  
  
## <a name="robust-programming"></a>Robustní programování  
 Vlastnost <xref:System.String.Chars%2A> vrací znak na zadané pozici. Některé znaky Unicode však mohou být reprezentovány více než jedním znakem. Další informace o tom, jak pracovat se znaky kódování Unicode, naleznete v tématu [How to: Convert String to Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 Vlastnost <xref:System.String.Chars%2A> vyvolá výjimku <xref:System.IndexOutOfRangeException>, pokud je parametr `index` větší nebo roven délce řetězce, nebo pokud je menší než nula.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String.Chars%2A>
- [Postupy: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Převod mezi řetězci a ostatními datovými typy v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
