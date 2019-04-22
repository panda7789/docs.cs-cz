---
title: 'Postupy: Iterace ve výčtu v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 63597145e96b04affc5f0e80e05a56b3fdf27278
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833357"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Postupy: Iterace ve výčtu v jazyce Visual Basic
Výčty poskytují pohodlný způsob pro práci se sadami související s konstantami a přidružení konstantních hodnot s názvy. Iterace ve výčtu, můžete přesunout ho do pole pomocí <xref:System.Enum.GetValues%2A> metody. Může také iteraci pomocí výčtu `For...Each` příkaz, pomocí <xref:System.Enum.GetNames%2A> nebo <xref:System.Enum.GetValues%2A> metoda extrahování řetězec nebo číselná hodnota.  
  
### <a name="to-iterate-through-an-enumeration"></a>K iteraci v rámci výčtu  
  
-   Deklarace pole a převést výčet přes <xref:System.Enum.GetValues%2A> by metoda před předáním pole jako jakoukoli jinou proměnnou. Následující příklad zobrazí každý člen výčtu <xref:Microsoft.VisualBasic.FirstDayOfWeek> jako prochází výčtu.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Postupy: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
