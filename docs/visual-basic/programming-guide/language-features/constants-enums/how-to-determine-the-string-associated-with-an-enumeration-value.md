---
title: 'Postupy: Určení řetězce spojeného s hodnotou výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c396a4e2ebe973f5be65c3fab5f22cdedb29be1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351137"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)
Metody <xref:System.Enum.GetValues%2A> a <xref:System.Enum.GetNames%2A> umožňují určit řetězce a hodnoty přidružené ke členům výčtu.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Určení řetězce přidruženého k výčtu  
  
- Použijte metodu <xref:System.Enum.GetNames%2A> k načtení řetězců přidružených ke členům výčtu. Tento příklad deklaruje výčet `flavorEnum`a poté používá metodu <xref:System.Enum.GetNames%2A> k zobrazení řetězců přidružených k jednotlivým členům.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Postupy: deklarace výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: iterace prostřednictvím výčtu v Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
