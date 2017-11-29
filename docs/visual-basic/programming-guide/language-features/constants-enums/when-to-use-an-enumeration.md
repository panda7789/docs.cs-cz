---
title: "Kdy použít výčet (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3b2937cc71c0c31bd8dce3d77fb33f48e1b5750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kdy použít výčet (Visual Basic)
Výčty nabízí snadný způsob, jak pracovat s sady souvisejících konstanty. Na výčtu nebo `Enum`, je symbolický název pro sadu hodnot. Výčty jsou považovány za datové typy a můžete je použít k vytvoření sad konstanty pro použití s proměnnými a vlastnosti.  
  
## <a name="when-to-use-an-enumeration"></a>Kdy použít výčet  
 Vždy, když procedury přijímá omezenou sadu proměnných, zvažte použití výčet. Výčty zajistěte pro jasnější a srozumitelnější kód, zvláště pokud smysluplný názvy jsou použity.  
  
 Mezi výhody používání výčty patří:  
  
-   Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.  
  
-   Lze snadno ke změně hodnot v budoucnu.  
  
-   Díky kód snadněji číst, což znamená, že je méně pravděpodobné, že se do ní ovládat chyby.  
  
-   Zajišťuje kompatibilitu. Váš kód s výčty, je méně pravděpodobné, že nezdaří, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.  
  
## <a name="naming-enumerations"></a>Pojmenování výčty  
 Použijte zásady vytváření názvů pro členy výčtu. Když [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dojde název člena výčtu, může být vyvolána výjimka, pokud obsahovat další odkazovaného typu knihovny se stejným názvem. Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo součásti.  
  
 K odkazování na člena výčtu, je nutné kvalifikaci název člena s názvem výčtu jinak použít `Imports` příkaz. Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Předdefinované výčty  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]poskytuje řadu předdefinovaných výčty, jako například `FirstDayOfWeek` a `MsgBoxResult`, aby se usnadnilo kódu. Seznam naleznete v části [konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Postupy: odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Postupy: iterace výčet v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Postupy: určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Enum – příkaz](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
