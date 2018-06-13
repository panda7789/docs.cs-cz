---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 240058a534456ae20c9c129a068bae575ac45eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596005"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Určuje, že jeden nebo více deklarované členské proměnné odkazovat na instanci třídy, který může vyvolat události.  
  
## <a name="remarks"></a>Poznámky  
 Když je proměnná definovaná pomocí `WithEvents`, deklarativně můžete určit, že metoda zpracovává události proměnné pomocí `Handles` – klíčové slovo.  
  
 Můžete použít `WithEvents` jenom na úrovni třídy nebo modulu. To znamená kontext deklarace `WithEvents` proměnná musí být třída nebo modul a nemůže být zdrojový soubor, obor názvů, struktura nebo postupu.  
  
 Nemůžete použít `WithEvents` na struktura člena.  
  
 Lze deklarovat pouze jednotlivé proměnné – není maticových – s `WithEvents`.  
  
## <a name="rules"></a>Pravidla  
  
-   **Typy elementů.** Je potřeba deklarovat `WithEvents` instancí třídy proměnné, které chcete být proměnné objektu tak, aby se může přijmout. Však nelze deklarovat je jako `Object`. Je třeba deklarovat jako určité třídy, který může vyvolat události.  
  
 `WithEvents` Modifikátor lze použít v tomto kontextu: [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
