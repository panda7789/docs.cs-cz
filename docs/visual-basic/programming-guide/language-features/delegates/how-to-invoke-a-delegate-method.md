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
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="e00be-102">Postupy: Volání metody delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e00be-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="e00be-103">Tento příklad ukazuje, jak přidružit metodu k delegátovi a následně tuto metodu vyvolat prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="e00be-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="e00be-104">Vytvořit delegáta a postupy pro porovnání</span><span class="sxs-lookup"><span data-stu-id="e00be-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="e00be-105">Vytvořte delegáta s názvem `MySubDelegate` .</span><span class="sxs-lookup"><span data-stu-id="e00be-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="e00be-106">Deklarujte třídu, která obsahuje metodu se stejnou signaturou jako delegát.</span><span class="sxs-lookup"><span data-stu-id="e00be-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="e00be-107">Definujte metodu, která vytvoří instanci delegáta a vyvolá metodu přidruženou k delegátovi voláním předdefinované `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="e00be-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="e00be-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e00be-108">See also</span></span>

- [<span data-ttu-id="e00be-109">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="e00be-109">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="e00be-110">Delegáti</span><span class="sxs-lookup"><span data-stu-id="e00be-110">Delegates</span></span>](index.md)
- [<span data-ttu-id="e00be-111">Události</span><span class="sxs-lookup"><span data-stu-id="e00be-111">Events</span></span>](../events/index.md)
- [<span data-ttu-id="e00be-112">Vícevláknové aplikace</span><span class="sxs-lookup"><span data-stu-id="e00be-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
