---
title: Výčty a kvalifikace názvu
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 4121266447b771ba954ad52a46e0d8b88de3f9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347498"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Výčty a kvalifikace názvu (Visual Basic)
Obvykle při odkazování na člena výčtu musíte kvalifikovat název člena s názvem výčtu. Například chcete-li odkazovat na `Sunday` člena `Days` výčtu, použijte následující syntaxi:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Použití příkazu Imports  
 Používání plně kvalifikovaných názvů se můžete vyhnout přidáním příkazu `Imports` do oddílu deklarace oboru názvů v kódu, jak je uvedeno v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 Příkaz `Imports` importuje názvy oborů názvů z odkazovaných projektů a sestavení a v rámci stejného projektu jako modul, ve kterém se příkaz zobrazí. Po přidání tohoto příkazu můžete odkazovat na členy výčtu bez kvalifikace, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Uspořádáním sad souvisejících konstant v výčtech můžete použít stejné konstantní názvy v různých kontextech. Můžete například použít stejné názvy pro konstanty v týdnu v `Days` a výčtech `WorkDays`. Použijete-li příkaz `Imports` s výčty, musíte být opatrní, aby nedocházelo k nejednoznačným odkazům. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Za předpokladu, že `Monday` je členem výčtu `Days` i výčtu `Workdays`, tento kód vygeneruje chybu kompilátoru. Chcete-li se vyhnout dvojznačným odkazům při odkazování na jednotlivé konstanty, kvalifikovat název konstanty pomocí jeho výčtu. Následující kód odkazuje na `Saturday` konstanty v `Days` a výčtech `WorkDays`.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Viz také:

- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Postupy: deklarace výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Postupy: iterace prostřednictvím výčtu v Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
