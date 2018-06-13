---
title: 'Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649149"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic
Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost, která má přístup ke znakům v zadaném umístění v řetězci.  
  
## <a name="example"></a>Příklad  
 Někdy je užitečné používat data o znaky v řetězec vašeho a pozice z těchto znaků v rámci vaší řetězec. Řetězce si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst odkazem index tento znak prostřednictvím <xref:System.String.Chars%2A> vlastnost.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 `index` Parametr <xref:System.String.Chars%2A> vlastnost je počítáno od nuly.  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici. Některé znaky kódování Unicode však může být reprezentovaný více než jeden znak. Další informace o tom, jak pracovat s znaky znakové sady Unicode, najdete v části [postupy: převedení řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Vlastnost vyvolává <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna hodnotě délky řetězce, nebo pokud ji je menší než nula  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String.Chars%2A>  
 [Postupy: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Převod mezi řetězci a ostatními typy dat v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Řetězce](../../../../visual-basic/programming-guide/language-features/strings/index.md)
