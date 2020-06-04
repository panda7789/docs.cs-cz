---
title: 'Postupy: Určení řetězce spojeného s hodnotou výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 525da9206472afefa9f85b49ceee0775cbd168c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414463"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)
<xref:System.Enum.GetValues%2A>Metody a <xref:System.Enum.GetNames%2A> umožňují určit řetězce a hodnoty přidružené ke členům výčtu.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Určení řetězce přidruženého k výčtu  
  
- Použijte <xref:System.Enum.GetNames%2A> metodu pro načtení řetězců přidružených k členům výčtu. Tento příklad deklaruje výčet, `flavorEnum` a poté používá <xref:System.Enum.GetNames%2A> metodu k zobrazení řetězců přidružených k jednotlivým členům.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Postupy: deklarace výčtu](how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Postupy: Iterace ve výčtu jazyka Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Kdy použít výčet](when-to-use-an-enumeration.md)
- [Enum – příkaz](../../../language-reference/statements/enum-statement.md)
