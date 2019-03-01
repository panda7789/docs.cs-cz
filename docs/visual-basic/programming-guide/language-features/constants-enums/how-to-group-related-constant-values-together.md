---
title: 'Postupy: Seskupení souvisejících hodnot konstant společně (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 63475487c8a35f5b306b28d4e7097324bef00d85
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977822"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Postupy: Seskupení souvisejících hodnot konstant společně (Visual Basic)
Výčet je nejlepší způsob, jak seskupit související s konstantami. Vytvořit výčet s `Enum` příkazu v části deklarace třídy nebo modulu. Další informace najdete v tématu [jak: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Ke skupině souvisejících hodnot konstant  
  
1.  Zápis deklarace, která zahrnuje úroveň přístupu kódu, `Enum` – klíčové slovo a platný název. Tento příklad vytvoří `Private` výčet, `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  Definujte konstanty ve výčtu. Tento příklad vytvoří `Public` výčet `temperatureValues` a přiřazuje hodnoty.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
