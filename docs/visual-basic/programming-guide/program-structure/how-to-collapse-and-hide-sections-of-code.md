---
title: 'Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: db396adf24c12542f720d3b235068aea2329288d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949733"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)
`#Region` Direktiva umožňuje sbalit a skrýt části kódu v souborech Visual Basic. `#Region` Direktiva umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití editoru kódu sady Visual Studio. Možnost selektivně skrývat kód usnadňuje správu a snazší čtení souborů. Další informace najdete v tématu [popisujícím sbalení](/visualstudio/ide/outlining).  
  
 `#Region`direktivy podporují sémantiku bloků kódu, `#If...#End If`jako je. To znamená, že nemohou začít v jednom bloku a končit jiným. počátek a konec musí být ve stejném bloku. `#Region`direktivy nejsou v rámci funkcí podporovány.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Sbalení a skrytí oddílu kódu  
  
- Umístěte oddíl kódu mezi `#Region` příkazy a `#End Region` , jak je uvedeno v následujícím příkladu:  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     `#Region` Blok lze použít několikrát v souboru kódu; proto mohou uživatelé definovat vlastní bloky procedur a tříd, které mohou být následně sbaleny. `#Region`bloky je také možné vnořit do jiných `#Region` bloků.  
  
    > [!NOTE]
    > Skrytí kódu nebrání jeho zkompilování a nemá vliv `#If...#End If` na příkazy.  
  
## <a name="see-also"></a>Viz také:

- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Sbalení](/visualstudio/ide/outlining)
