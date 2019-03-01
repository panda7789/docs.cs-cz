---
title: 'Postupy: Odkazování na člena výčtu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: e4f7ede26329ed97c65be8218be78aa40b1294e9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976262"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Postupy: Odkazování na člena výčtu (Visual Basic)
Výčty poskytují pohodlný způsob pro práci se sadami související s konstantami a přidružení konstantních hodnot s názvy. Můžete třeba deklarovat výčet sady konstanty typu integer, které jsou spojené s dny v týdnu a potom použít názvy dní, namísto jejich celočíselných hodnot ve vašem kódu.  
  
 Nepoužívejte plně kvalifikované názvy s `Imports` příkazu. Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>K odkazování na člena výčtu  
  
-   Kvalifikujte název člena výčtu. Například následující příklad přiřadí `Saturday` člena `FirstDayOfWeek` výčet proměnné `DayValue`.  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: Iterace ve výčtu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
