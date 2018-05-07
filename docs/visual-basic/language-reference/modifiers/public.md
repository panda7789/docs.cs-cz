---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: f6c18ecb748f62dd47a9689edb23089ca306dbe2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
