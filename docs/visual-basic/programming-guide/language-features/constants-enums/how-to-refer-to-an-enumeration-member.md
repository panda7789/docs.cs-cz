---
title: 'Postupy: Odkazování na člena výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 01db5b84783eda45cd7867dc8fea8a69fc18b98a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353998"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Postupy: Odkazování na člena výčtu (Visual Basic)
Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům. Můžete například deklarovat výčet pro sadu celočíselných konstant přidružených ke dnům v týdnu a potom použít názvy dnů, nikoli jejich celočíselné hodnoty ve vašem kódu.  
  
 Pomocí příkazu `Imports` se můžete vyhnout použití plně kvalifikovaných názvů. Další informace naleznete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>Odkazování na člena výčtu  
  
- Kvalifikovat název člena s výčtem. Například následující příklad přiřadí `Saturday` člen výčtu `FirstDayOfWeek` do proměnné `DayValue`.  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: deklarace výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: iterace prostřednictvím výčtu v Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
