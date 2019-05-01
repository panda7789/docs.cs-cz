---
title: 'Postupy: Volání metody delegáta (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: ac3e32010e7c20ba76e39915d694b11ab3a65d40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973326"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Postupy: Volání metody delegáta (Visual Basic)
Tento příklad ukazuje, jak přidružit metodu delegáta a poté vyvolat tuto metodu prostřednictvím delegáta.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Vytvoření delegáta a odpovídající procedur  
  
1. Vytvoření delegáta s názvem `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2. Deklarujte třídu, která obsahuje metodu s stejný podpis jako delegát.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3. Definujte metodu, která vytvoří instanci delegáta a vyvolá metodu spojenou s delegátem voláním předdefinované `Invoke` metody.  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Vícevláknové aplikace](../../../../standard/threading/using-threads-and-threading.md)
