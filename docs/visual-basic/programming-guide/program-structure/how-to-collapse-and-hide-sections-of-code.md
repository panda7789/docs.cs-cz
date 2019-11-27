---
title: 'Postupy: Sbalení a skrytí sekcí kódu'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: e7aacdc3f41199127b00d276b382ec4a5f258da0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347399"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Postupy: Sbalení a skrytí sekcí kódu (Visual Basic)

Direktiva `#Region` umožňuje sbalit a skrýt části kódu v souborech Visual Basic. Direktiva `#Region` umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití editoru kódu sady Visual Studio. Možnost selektivně skrývat kód usnadňuje správu a snazší čtení souborů. Další informace najdete v tématu [popisujícím sbalení](/visualstudio/ide/outlining).

direktivy `#Region` podporují sémantiku bloků kódu, jako je například `#If...#End If`. To znamená, že nemohou začít v jednom bloku a končit jiným. počátek a konec musí být ve stejném bloku. direktivy `#Region` nejsou v rámci funkcí podporovány.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Sbalení a skrytí oddílu kódu

Umístěte část kódu mezi příkazy `#Region` a `#End Region`, jako v následujícím příkladu:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

Blok `#Region` lze použít několikrát v souboru kódu; Uživatelé tak mohou definovat vlastní bloky procedur a tříd, které mohou být následně sbaleny. bloky `#Region` lze také vnořit do jiných `#Region` bloků.

> [!NOTE]
> Skrývání kódu nebrání jeho kompilování a nemá vliv na `#If...#End If` příkazy.

## <a name="see-also"></a>Viz také:

- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Direktiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Sbalení](/visualstudio/ide/outlining)
