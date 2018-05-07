---
title: 'Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c14ea61feba7d7d85f9a4fc377aefdd8fa240c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)
<xref:System.Enum.GetValues%2A> a <xref:System.Enum.GetNames%2A> metody vám umožňují určit řetězce a hodnoty přidružené členy výčtu.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>K určení řetězce spojeného s výčet  
  
-   Použití <xref:System.Enum.GetNames%2A> metoda pro načtení řetězců přidružené členy výčtu. Tento příklad deklaruje výčet, `flavorEnum`, použije <xref:System.Enum.GetNames%2A> metodu pro zobrazení řetězce přidružené k každého člena.  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Enum.GetValues%2A>  
 <xref:System.Enum.GetNames%2A>  
 <xref:System.Enum>  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Postupy: iterace výčet v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
