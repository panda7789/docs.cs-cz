---
title: Proměnná '<variablename>' skrývá proměnnou z vnějšího bloku.
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 474a920c9cfdfba7a8157320d9c88b8677958425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406518"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Proměnná '\<variablename>' skrývá proměnnou z vnějšího bloku.
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
  
- Běžnou příčinou této chyby je použití `Catch e As Exception` uvnitř obslužné rutiny události. Pokud se jedná o tento případ, pojmenujte `Catch` blokovou proměnnou `ex` místo `e` .  
  
- Dalším běžným zdrojem této chyby je pokus o přístup k místní proměnné deklarované `Try` v bloku v samostatném `Catch` bloku. Chcete-li tento problém opravit, deklarujte proměnnou mimo `Try...Catch...Finally` strukturu.  
  
## <a name="see-also"></a>Viz také

- [Try...Catch....Finally – příkaz](../statements/try-catch-finally-statement.md)
- [Deklarace proměnné](../../programming-guide/language-features/variables/variable-declaration.md)
