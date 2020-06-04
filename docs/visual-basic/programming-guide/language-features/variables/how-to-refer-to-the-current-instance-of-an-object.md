---
title: 'Postupy: Odkazování na aktuální instanci objektu'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 43bfd54592fb1d26cbf7f268b7e098e01e3745d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410422"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Postupy: Odkazování na aktuální instanci objektu (Visual Basic)
*Aktuální instance* objektu je instance, ve které je právě spuštěn kód.  
  
 `Me`Klíčové slovo se používá pro odkazování na aktuální instanci.  
  
### <a name="to-refer-to-the-current-instance"></a>Pro odkazování na aktuální instanci  
  
- Použijte `Me` klíčové slovo, kde byste normálně použili název proměnné objektu.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     I když se `Me` chová jako proměnná objektu, nelze ji deklarovat nebo k ní nelze přiřazovat žádné položky. `Me`vždy odkazuje na aktuální instanci.  
  
## <a name="see-also"></a>Viz také

- [Proměnné objektu](object-variables.md)
- [Přiřazení proměnné objektu](object-variable-assignment.md)
- [Me, My, MyBase a MyClass](../../program-structure/me-my-mybase-and-myclass.md)
