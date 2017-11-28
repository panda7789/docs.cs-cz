---
title: "Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; skryje proměnnou z vnějšího bloku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords: BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Proměnná & č. 39; &lt;NázevProměnné&gt;& č. 39; skryje proměnnou z vnějšího bloku
Proměnné v bloku má stejný název jako jiný místní proměnné.  
  
 **ID chyby:** BC30616  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přejmenujte proměnné v závorkách bloku tak, aby není stejná jako ostatní místní proměnné. Příklad:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Obvyklou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události. Pokud je to tento případ, název `Catch` proměnná bloku `ex` místo `e`.  
  
-   Další běžné zdroj této chyby je pokus o přístup k místní proměnné deklarované v rámci `Try` blokovat v samostatném `Catch` bloku. Chcete-li vyřešit tento problém, deklarovat proměnnou mimo `Try...Catch...Finally` struktura.  
  
## <a name="see-also"></a>Viz také  
 [Try... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
