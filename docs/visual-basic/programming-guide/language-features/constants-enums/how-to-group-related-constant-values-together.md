---
title: 'Postupy: Seskupení souvisejících hodnot konstant'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354032"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Postupy: Seskupení souvisejících hodnot konstant (Visual Basic)
Výčet je nejlepším způsobem, jak seskupovat související konstanty. Vytvoříte výčet pomocí příkazu `Enum` v oddílu deklarace třídy nebo modulu. Další informace naleznete v tématu [How to: Declare a Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Seskupení souvisejících konstantních hodnot  
  
1. Napište deklaraci, která zahrnuje úroveň přístupu kódu, klíčové slovo `Enum` a platný název. Tento příklad vytvoří výčet `Private` `temperatureValues`.  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Definujte konstanty ve výčtu. Tento příklad vytvoří `temperatureValues` výčtu `Public` a přiřadí jeho hodnoty.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
