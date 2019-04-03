---
title: Proměnná '<variablename>' skrývá proměnnou z vnějšího bloku.
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 15c35cbb829bec782771b584ea25b111b81b5e1f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827130"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Proměnná '\<NázevProměnné >' skrývá proměnnou v nadřízeném bloku
Proměnné v bloku má stejný název jako jiná místní proměnná.  
  
 **ID chyby:** BC30616  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přejmenujte proměnnou v uzavřeném bloku tak, že není stejný jako další místní proměnné. Příklad:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Běžnou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události. Pokud tomu tak, `Catch` proměnná bloku `ex` spíše než `e`.  
  
-   Další běžné zdroje této chyby je pokus o přístup k místní proměnné deklarované v rámci `Try` blokovat v samostatném `Catch` bloku. Když to pokud chcete opravit, deklarujte proměnnou mimo `Try...Catch...Finally` struktury.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
