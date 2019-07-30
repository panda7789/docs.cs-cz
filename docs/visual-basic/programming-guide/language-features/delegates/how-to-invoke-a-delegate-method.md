---
title: 'Postupy: Vyvolání metody delegáta (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c2bdb65c9d060e854db3319e4aa5b2e93b9681af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629586"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="785b1-102">Postupy: Vyvolání metody delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="785b1-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="785b1-103">Tento příklad ukazuje, jak přidružit metodu k delegátovi a následně tuto metodu vyvolat prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="785b1-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="785b1-104">Vytvořit delegáta a postupy pro porovnání</span><span class="sxs-lookup"><span data-stu-id="785b1-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="785b1-105">Vytvořte delegáta s `MySubDelegate`názvem.</span><span class="sxs-lookup"><span data-stu-id="785b1-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="785b1-106">Deklarujte třídu, která obsahuje metodu se stejnou signaturou jako delegát.</span><span class="sxs-lookup"><span data-stu-id="785b1-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="785b1-107">Definujte metodu, která vytvoří instanci delegáta a vyvolá metodu přidruženou k delegátovi voláním předdefinované `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="785b1-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="785b1-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="785b1-108">See also</span></span>

- [<span data-ttu-id="785b1-109">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="785b1-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="785b1-110">Delegáti</span><span class="sxs-lookup"><span data-stu-id="785b1-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="785b1-111">Události</span><span class="sxs-lookup"><span data-stu-id="785b1-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="785b1-112">Vícevláknové aplikace</span><span class="sxs-lookup"><span data-stu-id="785b1-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
