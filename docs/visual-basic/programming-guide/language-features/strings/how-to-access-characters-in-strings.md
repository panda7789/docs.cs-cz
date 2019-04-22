---
title: 'Postupy: Přístup znakům v řetězcích v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 840a769b0bb322ef7b878a312437c5ec200ab074
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834488"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Postupy: Přístup znakům v řetězcích v jazyce Visual Basic
Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost přístup ke znakům v zadaném umístění v řetězci.  
  
## <a name="example"></a>Příklad  
 Někdy je užitečné mít data o znaky v váš řetězec a umístění těchto znaků v rámci vašeho řetězce. Řetězec si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst pomocí odkazu na index tohoto znaku prostřednictvím <xref:System.String.Chars%2A> vlastnost.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index` Parametr <xref:System.String.Chars%2A> vlastnost je založený na nule.  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici. Některé znaky Unicode však může být reprezentována více než jeden znak. Další informace o tom, jak pracovat s znaků Unicode naleznete v tématu [jak: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Vlastnost vyvolá <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna délce řetězce, nebo pokud je menší než nula  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String.Chars%2A>
- [Postupy: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
