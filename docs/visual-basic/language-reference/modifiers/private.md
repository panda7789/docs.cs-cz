---
title: Private (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)  
 [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Postupy](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
