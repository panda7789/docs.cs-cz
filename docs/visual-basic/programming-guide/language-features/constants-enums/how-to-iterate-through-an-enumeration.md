---
title: 'Postupy: Iterace ve výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414424"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>Postupy: Iterace ve výčtu jazyka Visual Basic
Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům. Chcete-li iterovat prostřednictvím výčtu, můžete jej přesunout do pole pomocí <xref:System.Enum.GetValues%2A> metody. Můžete také iterovat prostřednictvím výčtu pomocí `For...Each` příkazu <xref:System.Enum.GetNames%2A> nebo <xref:System.Enum.GetValues%2A> k extrakci řetězcové nebo číselné hodnoty.  
  
### <a name="to-iterate-through-an-enumeration"></a>Iterace prostřednictvím výčtu  
  
- Deklarujte pole a převeďte na něj výčet pomocí <xref:System.Enum.GetValues%2A> metody před předáním pole stejným způsobem jako jakákoli jiná proměnná. Následující příklad zobrazuje jednotlivé členy výčtu <xref:Microsoft.VisualBasic.FirstDayOfWeek> při iterování prostřednictvím výčtu.  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>Viz také

- [Přehled výčtů](enumerations-overview.md)
- [Postupy: deklarace výčtu](how-to-declare-enumerations.md)
- [Kdy použít výčet](when-to-use-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Postupy: Odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Pole](../arrays/index.md)
