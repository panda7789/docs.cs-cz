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
ms.openlocfilehash: 9edb809624727aba5c40b410d0356804257bf516
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964653"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Výčty a kvalifikace názvu (Visual Basic)
Za normálních okolností při odkazování na člena výčtu, musí kvalifikovat název člena s názvem výčtu. Například k odkazování na `Sunday` členem vaší `Days` výčet, použijte následující syntaxi:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Pomocí příkazu Imports  
 Můžete předejít použití plně kvalifikovaných názvů tak, že přidáte `Imports` příkazu deklarace oboru názvů část kódu, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 `Imports` Příkaz importuje názvy oborů názvů z odkazované projekty a sestavení a v rámci stejného projektu jako modul, ve kterém se zobrazí příkaz. Po přidání tohoto příkazu můžete odkazovat na vaše členy výčtu bez kvalifikace, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Uspořádání sady související s konstantami v výčty, můžete pomocí stejné konstantní názvy v různých kontextech. Například můžete použít stejné názvy pro den v týdnu konstanty v `Days` a `WorkDays` výčty. Pokud používáte `Imports` příkaz s vaší výčty, musí být opatrní a vyhnout se nejednoznačné odkazy. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Za předpokladu, že `Monday` členem obou `Days` výčet a `Workdays` výčet, tento kód vygeneruje chybu kompilátoru. Aby se zabránilo nejednoznačný odkazy k odkazování na jednotlivé – konstanta, kvalifikujte konstantní název s její výčet. Následující kód odkazuje `Saturday` konstanty v `Days` a `WorkDays` výčty.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Viz také:
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Postupy: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Postupy: Iterace ve výčtu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
