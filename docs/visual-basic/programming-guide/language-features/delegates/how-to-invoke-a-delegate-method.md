---
title: 'Postupy: Volání metody delegáta (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: aca87dd9fa1990d44c99aab7753f2fd7d508adc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Postupy: Volání metody delegáta (Visual Basic)
Tento příklad ukazuje, jak přidružit metody delegáta a pak volání této metody prostřednictvím delegáta.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Vytvořit odpovídající postupů a delegování  
  
1.  Vytvoření delegáta s názvem `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  Třída, která obsahuje metodu se stejným podpisem jako delegáta deklarujte.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  Zadejte metodu, která vytvoří instanci delegáta a vyvolá metodu spojenou s delegátem voláním integrované `Invoke` metoda.  
  
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
 [Vícevláknové aplikace](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
