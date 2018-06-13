---
title: Proměnná &#39; &lt;NázevProměnné&gt; &#39; skryje proměnnou z vnějšího bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595089"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Proměnná &#39; &lt;NázevProměnné&gt; &#39; skryje proměnnou z vnějšího bloku
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
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
