---
title: 'Postupy: Odkazování na aktuální instanci objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: c1b79f1b6a9768941d6fe966c5b5886ea742f808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648356"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Postupy: Odkazování na aktuální instanci objektu (Visual Basic)
*Aktuální instance* objektu je instance, ve kterém je aktuálně provádění kódu.  
  
 Můžete použít `Me` – klíčové slovo k odkazování na aktuální instanci.  
  
### <a name="to-refer-to-the-current-instance"></a>K odkazování na aktuální instanci  
  
-   Použít `Me` – klíčové slovo, které běžně používáte název proměnné objektu.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     I když `Me` chová jako objekt proměnné, nelze ho deklarovat nebo nic přiřadit ho. `Me` vždy odkazuje na aktuální instanci.  
  
## <a name="see-also"></a>Viz také  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
