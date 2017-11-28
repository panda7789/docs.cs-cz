---
title: "Postupy: Odkazování na aktuální instanci objektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
     I když `Me` chová jako objekt proměnné, nelze ho deklarovat nebo nic přiřadit ho. `Me`vždy odkazuje na aktuální instanci.  
  
## <a name="see-also"></a>Viz také  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [ME, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
