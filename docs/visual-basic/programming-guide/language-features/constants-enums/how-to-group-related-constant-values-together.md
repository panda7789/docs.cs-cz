---
title: 'Postupy: Seskupení souvisejících hodnot konstant (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 320373116ad4d61293690353fce6b7b152e79a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646400"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Postupy: Seskupení souvisejících hodnot konstant (Visual Basic)
Výčet je nejlepší způsob, jak seskupit související konstanty. Vytvoření výčtu s `Enum` prohlášení v části prohlášení o třídu nebo modul. Další informace najdete v tématu [postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Do skupiny souvisejících hodnot konstant  
  
1.  Zápis deklaraci, která zahrnuje úroveň přístupu kódu, `Enum` – klíčové slovo a platný název. Tento příklad vytvoří `Private` výčtu `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  Definujte konstanty ve výčtu. Tento příklad vytvoří `Public` výčtu `temperatureValues` a přiřadí jeho hodnoty.  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
