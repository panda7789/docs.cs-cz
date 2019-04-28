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
ms.openlocfilehash: 3c44748798d5ed554fc9fbded9c3a4d981a66d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769028"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Postupy: Odkazování na aktuální instanci objektu (Visual Basic)
*Aktuální instance* objektu je instance, ve kterém právě spouští kód.  
  
 Můžete použít `Me` – klíčové slovo k odkazování na aktuální instanci.  
  
### <a name="to-refer-to-the-current-instance"></a>K odkazování na aktuální instanci  
  
- Použít `Me` – klíčové slovo, které běžně používáte název proměnné objektu.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     I když `Me` se chová stejně jako objekt proměnné, nelze ji deklarovat ani nic jí přiřadit. `Me` vždy odkazuje na aktuální instanci.  
  
## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
