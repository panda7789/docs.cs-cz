---
title: 'Postupy: iterace prostřednictvím výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 6e8fd6760565a73d9d3b3d1d02fc872992eea354
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354025"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Postupy: Iterace ve výčtu jazyka Visual Basic
Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům. Chcete-li iterovat prostřednictvím výčtu, můžete jej přesunout do pole pomocí metody <xref:System.Enum.GetValues%2A>. Můžete také iterovat prostřednictvím výčtu pomocí příkazu `For...Each`, a to pomocí metody <xref:System.Enum.GetNames%2A> nebo <xref:System.Enum.GetValues%2A> k extrakci řetězcové nebo číselné hodnoty.  
  
### <a name="to-iterate-through-an-enumeration"></a>Iterace prostřednictvím výčtu  
  
- Deklarujte pole a převeďte na něj výčet pomocí metody <xref:System.Enum.GetValues%2A> před předáním pole stejným způsobem jako jakékoli jiné proměnné. Následující příklad zobrazuje jednotlivé členy výčtu <xref:Microsoft.VisualBasic.FirstDayOfWeek> při iterování výčtem.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Postupy: deklarace výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
