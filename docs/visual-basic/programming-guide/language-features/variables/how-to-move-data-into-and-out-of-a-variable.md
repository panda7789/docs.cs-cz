---
title: 'Postupy: Přesun dat do a z proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 033d1cb0116b78ca9e3677c920ee5745117573d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663521"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Postupy: Přesun dat do a z proměnné (Visual Basic)
Uložení hodnoty do proměnné tak, že vložíte název proměnné na levé straně příkazu přiřazení.  
  
## <a name="putting-data-in-a-variable"></a>Ukládání dat do proměnné  
  
#### <a name="to-store-a-value-in-a-variable"></a>K uložení hodnoty v proměnné  
  
- Použijte název proměnné na levé straně příkazu přiřazení.  
  
     Následující příklad nastaví hodnotu proměnné `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     Hodnota generovaná na pravé straně příkazu přiřazení je uložen v proměnné.  
  
## <a name="getting-data-from-a-variable"></a>Získání dat z proměnné  
 Hodnota proměnné načtete zahrnutím název proměnné ve výrazu.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>Načíst hodnotu z proměnné  
  
- Použijte název proměnné ve výrazu. Proměnnou můžete použít kdekoli můžete použít konstanta nebo literál, s výjimkou ve výrazu, který definuje hodnotu konstanty.  
  
     -nebo-  
  
- Použijte název proměnné po rovnosti (`=`) Přihlaste se příkazu přiřazení.  
  
     Následující příklad přečte hodnotu proměnné `startValue` a použije se hodnota proměnné `counter` ve výrazu.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     Hodnota proměnné podílí na výraz, stejně jako by konstantu, a pak je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="see-also"></a>Viz také:

- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
