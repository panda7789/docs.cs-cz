---
title: Proměnná '<variablename>' skrývá proměnnou z vnějšího bloku.
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592067"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Proměnná ' \<variablename > ' skrývá proměnnou v ohraničujícím bloku
Proměnná uzavřená v bloku má stejný název jako jiná místní proměnná.  
  
 **ID chyby:** BC30616  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přejmenujte proměnnou v uzavřeném bloku tak, že se neshoduje s jinými místními proměnnými. Příklad:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Běžnou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události. Pokud se jedná o tento případ, pojmenujte blokovou proměnnou `Catch` `ex` místo `e`.  
  
- Dalším běžným zdrojem této chyby je pokus o přístup k místní proměnné deklarované v bloku `Try` v samostatném bloku `Catch`. Chcete-li tento problém opravit, deklarujte proměnnou mimo strukturu `Try...Catch...Finally`.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
