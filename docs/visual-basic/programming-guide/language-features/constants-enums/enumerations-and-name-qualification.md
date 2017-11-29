---
title: "Výčty a kvalifikace názvu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb97d6a8f4b7e81f2b759010214e200ec63ff21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Výčty a kvalifikace názvu (Visual Basic)
Za normálních okolností k odkazování na člena výčtu, musíte před název člena s názvem výčtu. Pro příklad, který bude odkazovat na `Sunday` členem vaší `Days` výčet, použijte následující syntaxi:  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Pomocí příkazu importy  
 Používání plně kvalifikované názvy přidáním se můžete vyhnout `Imports` příkaz, který má v oboru názvů deklarace části kódu, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports` Příkaz importuje názvy oborů názvů prostřednictvím odkazovaného projekty a sestavení a v rámci stejného projektu jako modul, ve kterém se zobrazí příkaz. Po přidání tohoto prohlášení, můžete odkazovat na vaše členy výčtu bez kvalifikace, jako v následujícím příkladu:  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Uspořádání sady souvisejících konstanty v výčty, můžete pomocí stejné konstantní názvy v různých kontextech. Například můžete použít stejné názvy konstanty den v týdnu v `Days` a `WorkDays` výčty. Pokud použijete `Imports` příkaz s vaší výčty, musí být snažte se vyhnout nejednoznačný odkazy. Podívejte se na následující příklad:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Za předpokladu, že `Monday` je členem obou `Days` výčet a `Workdays` výčtu, tento kód se generuje chyba kompilátoru. Aby se zabránilo nejednoznačný odkazy k odkazování na jednotlivé konstanta, kvalifikovat konstantní název s její výčet. Následující kód odkazuje `Saturday` konstanty v `Days` a `WorkDays` výčty.  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Postupy: odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Postupy: iterace výčet v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Postupy: určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Kdy použít výčet](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Enum – příkaz](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Imports – příkaz (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
