---
title: 'Postupy: Volání metody delegáta'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 520bacfbe6103490e0459cd5af149c1d55a8fce4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345254"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Postupy: Volání metody delegáta (Visual Basic)

Tento příklad ukazuje, jak přidružit metodu k delegátovi a následně tuto metodu vyvolat prostřednictvím delegáta.

### <a name="create-the-delegate-and-matching-procedures"></a>Vytvořit delegáta a postupy pro porovnání

1. Vytvořte delegáta s názvem `MySubDelegate`.

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. Deklarujte třídu, která obsahuje metodu se stejnou signaturou jako delegát.

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. Definujte metodu, která vytvoří instanci delegáta a vyvolá metodu přidruženou k delegátovi voláním předdefinované `Invoke` metody.

    ```vb
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
