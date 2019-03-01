---
title: 'Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 74dff310ccba0bebcf96576d769bf50420ca7397
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971686"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)
<xref:System.Enum.GetValues%2A> a <xref:System.Enum.GetNames%2A> metody umožňují určit řetězců a hodnot spojených s členy výčtu.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>K určení řetězce spojeného s výčet  
  
-   Použití <xref:System.Enum.GetNames%2A> metody mají být načteny řetězce spojené s členy výčtu. V tomto příkladu deklaruje výčet, `flavorEnum`, použije <xref:System.Enum.GetNames%2A> metodu pro zobrazení řetězce přidružené k jednotlivým členům.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Postupy: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: Iterace ve výčtu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
