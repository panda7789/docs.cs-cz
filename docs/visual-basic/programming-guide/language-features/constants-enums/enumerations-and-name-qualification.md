---
title: Výčty a kvalifikace názvu (Visual Basic)
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
ms.openlocfilehash: cd07c883c576e917cf1aa5072505854bc906eb3f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933963"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Výčty a kvalifikace názvu (Visual Basic)
Za normálních okolností při odkazování na člena výčtu, musí kvalifikovat název člena s názvem výčtu. Například k odkazování na `Sunday` členem vaší `Days` výčet, použijte následující syntaxi:  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Pomocí příkazu Imports  
 Můžete předejít použití plně kvalifikovaných názvů tak, že přidáte `Imports` příkazu deklarace oboru názvů část kódu, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports` Příkaz importuje názvy oborů názvů z odkazované projekty a sestavení a v rámci stejného projektu jako modul, ve kterém se zobrazí příkaz. Po přidání tohoto příkazu můžete odkazovat na vaše členy výčtu bez kvalifikace, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Uspořádání sady související s konstantami v výčty, můžete pomocí stejné konstantní názvy v různých kontextech. Například můžete použít stejné názvy pro den v týdnu konstanty v `Days` a `WorkDays` výčty. Pokud používáte `Imports` příkaz s vaší výčty, musí být opatrní a vyhnout se nejednoznačné odkazy. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Za předpokladu, že `Monday` členem obou `Days` výčet a `Workdays` výčet, tento kód vygeneruje chybu kompilátoru. Aby se zabránilo nejednoznačný odkazy k odkazování na jednotlivé – konstanta, kvalifikujte konstantní název s její výčet. Následující kód odkazuje `Saturday` konstanty v `Days` a `WorkDays` výčty.  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Postupy: iterace ve výčtu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
