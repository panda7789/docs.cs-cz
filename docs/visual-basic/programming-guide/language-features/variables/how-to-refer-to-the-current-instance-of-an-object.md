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
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005664"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Postupy: Odkazování na aktuální instanci objektu (Visual Basic)
*Aktuální instance* objektu je instance, ve které je právě spuštěn kód.  
  
 Pomocí klíčového slova `Me` můžete odkazovat na aktuální instanci.  
  
### <a name="to-refer-to-the-current-instance"></a>Pro odkazování na aktuální instanci  
  
- Použijte klíčové slovo `Me`, kde byste normálně použili název proměnné objektu.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     I když `Me` se chová jako proměnná objektu, nemůžete ji deklarovat nebo k ní přiřadit cokoli. `Me` vždy odkazuje na aktuální instanci.  
  
## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
