---
title: "Postupy: Přesun dat do proměnné a z proměnné (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
