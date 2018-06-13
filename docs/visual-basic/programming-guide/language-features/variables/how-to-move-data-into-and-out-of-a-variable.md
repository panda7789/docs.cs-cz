---
title: 'Postupy: Přesun dat do proměnné a z proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bfda451cefff699561253910715d8450414b00ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650865"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Postupy: Přesun dat do proměnné a z proměnné (Visual Basic)
Hodnotu můžete uložit jako proměnnou umístěním název proměnné na levé straně příkazu přiřazení.  
  
## <a name="putting-data-in-a-variable"></a>Ukládání dat do proměnné  
  
#### <a name="to-store-a-value-in-a-variable"></a>K uložení hodnotu do proměnné  
  
-   Použijte název proměnné na levé straně příkazu přiřazení.  
  
     Následující příklad nastaví hodnotu proměnné `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     Hodnota generovaná na pravé straně přiřazení příkazu je uložené v proměnné.  
  
## <a name="getting-data-from-a-variable"></a>Získání dat z proměnné  
 Hodnota proměnné můžete načíst tak, že včetně názvu proměnné ve výrazu.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>K načtení hodnoty z proměnné  
  
-   Použijte název proměnné ve výrazu. Proměnnou můžete použít kdekoli můžete použít konstantu nebo literál, s výjimkou v výraz, který definuje hodnotu konstanty.  
  
     -nebo-  
  
-   Použijte název proměnné následující rovno (`=`) přihlásit příkazu přiřazení.  
  
     Následující příklad načte hodnotu proměnné `startValue` a pak používá hodnotu proměnné `counter` ve výrazu.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     Hodnota proměnné se účastní výraz stejně, jako by konstanta, a pak je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="see-also"></a>Viz také  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
