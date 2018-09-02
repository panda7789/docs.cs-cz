---
title: 'Postupy: Volání metody delegáta (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 9fea3ddbc9fb553041671713a64e4b866ee38b50
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392435"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Postupy: Volání metody delegáta (Visual Basic)
Tento příklad ukazuje, jak přidružit metodu delegáta a poté vyvolat tuto metodu prostřednictvím delegáta.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Vytvoření delegáta a odpovídající procedur  
  
1.  Vytvoření delegáta s názvem `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  Deklarujte třídu, která obsahuje metodu s stejný podpis jako delegát.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  Definujte metodu, která vytvoří instanci delegáta a vyvolá metodu spojenou s delegátem voláním předdefinované `Invoke` metody.  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Vícevláknové aplikace](https://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
