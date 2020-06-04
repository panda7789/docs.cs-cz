---
title: 'Postupy: Volání metody delegáta'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: f319727c007b93c7b334af0598f1b9f7c034144d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410718"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Postupy: Volání metody delegáta (Visual Basic)

Tento příklad ukazuje, jak přidružit metodu k delegátovi a následně tuto metodu vyvolat prostřednictvím delegáta.

### <a name="create-the-delegate-and-matching-procedures"></a>Vytvořit delegáta a postupy pro porovnání

1. Vytvořte delegáta s názvem `MySubDelegate` .

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

## <a name="see-also"></a>Viz také

- [Delegate – příkaz](../../../language-reference/statements/delegate-statement.md)
- [Delegáti](index.md)
- [Události](../events/index.md)
- [Vícevláknové aplikace](../../../../standard/threading/using-threads-and-threading.md)
