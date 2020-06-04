---
title: 'Postupy: Seskupení souvisejících hodnot konstant'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: d2393af8b0c2b0c2e528f9908a78fbc7f182c8cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414437"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>Postupy: Seskupení souvisejících hodnot konstant (Visual Basic)
Výčet je nejlepším způsobem, jak seskupovat související konstanty. Vytvoříte výčet s `Enum` příkazem v oddílu deklarace třídy nebo modulu. Další informace naleznete v tématu [How to: Declare a Enumeration](how-to-declare-enumerations.md).  
  
### <a name="to-group-related-constant-values"></a>Seskupení souvisejících konstantních hodnot  
  
1. Napište deklaraci, která obsahuje úroveň přístupu ke kódu, `Enum` klíčové slovo a platný název. Tento příklad vytvoří `Private` výčet `temperatureValues` .  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. Definujte konstanty ve výčtu. Tento příklad vytvoří `Public` výčet `temperatureValues` a přiřadí jeho hodnoty.  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Postupy: Odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md)
- [Kdy použít výčet](when-to-use-an-enumeration.md)
- [Přehled konstant](constants-overview.md)
- [Datové typy konstanty a literálu](constant-and-literal-data-types.md)
- [Konstanty a výčty](../../../language-reference/constants-and-enumerations.md)
