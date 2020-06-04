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
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414502"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Výčty a kvalifikace názvu (Visual Basic)
Obvykle při odkazování na člena výčtu musíte kvalifikovat název člena s názvem výčtu. Například pro odkazování na `Sunday` člena `Days` výčtu byste měli použít následující syntaxi:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Použití příkazu Imports  
 Můžete se vyhnout použití plně kvalifikovaného názvu přidáním `Imports` příkazu do oddílu deklarace oboru názvů v kódu, jak je uvedeno v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 `Imports`Příkaz naimportuje názvy oborů názvů z odkazovaných projektů a sestavení a ze stejného projektu jako modul, ve kterém se zobrazí příkaz. Po přidání tohoto příkazu můžete odkazovat na členy výčtu bez kvalifikace, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Uspořádáním sad souvisejících konstant v výčtech můžete použít stejné konstantní názvy v různých kontextech. Můžete například použít stejné názvy pro konstanty v týdnu ve `Days` `WorkDays` výčtech a. Použijete-li `Imports` příkaz s výčty, musíte být opatrní, aby nedocházelo k nejednoznačným odkazům. Uvažujte následující příklad:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Za předpokladu, že `Monday` je členem `Days` výčtu i `Workdays` výčtu, tento kód vygeneruje chybu kompilátoru. Chcete-li se vyhnout dvojznačným odkazům při odkazování na jednotlivé konstanty, kvalifikovat název konstanty pomocí jeho výčtu. Následující kód odkazuje na `Saturday` konstanty ve `Days` `WorkDays` výčtech a.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Viz také

- [Konstanty a výčty](../../../language-reference/constants-and-enumerations.md)
- [Postupy: deklarace výčtu](how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md)
- [Postupy: Iterace ve výčtu jazyka Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](when-to-use-an-enumeration.md)
- [Datové typy konstanty a literálu](constant-and-literal-data-types.md)
- [Enum – příkaz](../../../language-reference/statements/enum-statement.md)
- [Imports – příkaz (obor názvů a typ rozhraní .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Datové typy](../../../language-reference/data-types/index.md)
