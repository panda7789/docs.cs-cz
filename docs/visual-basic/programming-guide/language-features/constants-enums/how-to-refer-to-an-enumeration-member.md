---
title: "Postupy: Odkazování na člena výčtu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4e6eb9c011095c6cf0abe1ee3ac7a68f156f01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>Postupy: Odkazování na člena výčtu (Visual Basic)
Výčty poskytují pohodlný způsob pro práci se sadami související konstanty a přidružení konstantních hodnot k názvy. Můžete například deklarovat výčet sady konstanty typu integer, které jsou přidružené k dny v týdnu a pak použít názvy dnů, nikoli jejich celočíselné hodnoty v kódu.  
  
 Nepoužívejte plně kvalifikované názvy se `Imports` příkaz. Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-refer-to-an-enumeration-member"></a>K odkazování na člena výčtu  
  
-   Název člena s výčtu kvalifikaci. Například následující příklad přiřadí `Saturday` členem `FirstDayOfWeek` výčtu proměnnou `DayValue`.  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Postupy: iterace výčet v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Postupy: určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
