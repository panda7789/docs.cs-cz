---
title: Public (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6cd70adf6ec31c56f39d0443d320dd1b00b00d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Určuje, že jeden nebo více deklarované programovací elementy žádná omezení přístupu.  
  
## <a name="remarks"></a>Poznámky  
 Při publikování komponenty nebo sadu součástí, například knihovny tříd, chcete obvykle programovací prvky, které mají být přístupné kód, který bude spolupracovat s vaší sestavení. Přenést takové neomezený přístup na element, můžou deklarovat její `Public`.  
  
 Veřejný přístup je úroveň programovací element v normální, pokud nepotřebujete omezit přístup k němu. Všimněte si, že úroveň přístupu tohoto elementu deklarované v rámci rozhraní, modulu, třídu nebo strukturu výchozí `Public` Pokud neprovedete deklaraci ho jinak.  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo obor názvů. To znamená kontext deklarace `Public` element musí být zdrojový soubor, obor názvů, rozhraní, modulu, třídu nebo strukturu a nemůže být procedury.  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** Všechny kód, který můžete získat přístup k modulu, třídu nebo strukturu můžete přístup k jeho `Public` elementy.  
  
-   **Výchozí úroveň přístupu.** Lokální proměnné uvnitř procedury výchozí veřejný přístup, a nelze použít žádné modifikátory přístupu na ně.  
  
-   **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*. Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public` Modifikátor lze použít v těchto kontexty:  
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Privátní](../../../visual-basic/language-reference/modifiers/private.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Postupy](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
