---
title: 'Postupy: Přístup znakům v řetězcích v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 9833b562fc0b4115448ebefb8631f0d73eb15f6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618919"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Postupy: Přístup znakům v řetězcích v jazyce Visual Basic
Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost přístup ke znakům v zadaném umístění v řetězci.  
  
## <a name="example"></a>Příklad  
 Někdy je užitečné mít data o znaky v váš řetězec a umístění těchto znaků v rámci vašeho řetězce. Řetězec si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst pomocí odkazu na index tohoto znaku prostřednictvím <xref:System.String.Chars%2A> vlastnost.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 `index` Parametr <xref:System.String.Chars%2A> vlastnost je založený na nule.  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici. Některé znaky Unicode však může být reprezentována více než jeden znak. Další informace o tom, jak pracovat s znaků Unicode naleznete v tématu [jak: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Vlastnost vyvolá <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna délce řetězce, nebo pokud je menší než nula  
  
## <a name="see-also"></a>Viz také:
- <xref:System.String.Chars%2A>
- [Postupy: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
