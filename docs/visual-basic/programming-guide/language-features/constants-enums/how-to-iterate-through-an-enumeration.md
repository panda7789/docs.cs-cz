---
title: 'Postupy: Iterace ve výčtu jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646575"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Postupy: Iterace ve výčtu jazyka Visual Basic
Výčty poskytují pohodlný způsob pro práci se sadami související konstanty a přidružení konstantních hodnot k názvy. K iteraci v rámci výčet, můžete jej přesunout do pole pomocí <xref:System.Enum.GetValues%2A> metoda. Můžete také iterovat k výčtu pomocí `For...Each` příkaz, pomocí <xref:System.Enum.GetNames%2A> nebo <xref:System.Enum.GetValues%2A> Metoda získání řetězec nebo číselné hodnoty.  
  
### <a name="to-iterate-through-an-enumeration"></a>K iteraci v rámci výčet  
  
-   Deklarace pole a převést jej s výčtu <xref:System.Enum.GetValues%2A> metody před předáním pole jako jste by jakoukoli jinou proměnnou. Následující příklad zobrazí každý člen výčtu <xref:Microsoft.VisualBasic.FirstDayOfWeek> jako iteruje v rámci výčtu.  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
