---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d7935cf691d961591ff5e3d2a290afb88de9165a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
Určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v kontextu jejich deklarace, včetně v rámci všechny obsažené typy.  
  
## <a name="remarks"></a>Poznámky  
 Pokud programovací element představuje speciálních funkcí, nebo obsahuje důvěrných dat, obvykle chcete omezit přístup k němu jako výhradně. Maximální omezení můžete dosáhnout tím, že pouze modulu, třídu nebo strukturu, která definuje, aby k němu přístup. Omezit přístup k elementu tímto způsobem, můžou deklarovat její `Private`.  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Private` jenom na úrovni modulu. To znamená kontext deklarace `Private` element musí být modul, třídu nebo strukturu a nemůže být zdrojový soubor, obor názvů, rozhraní nebo postupu.  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** Všechny kódu v rámci kontextu deklarace můžete přístup k jeho `Private` elementy. To zahrnuje kódu v rámci omezením typu, například vnořené třídy nebo výraz přiřazení ve výčtu. Žádný kód mimo kontext deklarace můžete přístup k jeho `Private` elementy.  
  
-   **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*. Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
