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
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="463b2-102">Postupy: Volání metody delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="463b2-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="463b2-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span><span class="sxs-lookup"><span data-stu-id="463b2-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="463b2-104">Create the delegate and matching procedures</span><span class="sxs-lookup"><span data-stu-id="463b2-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="463b2-105">Create a delegate named `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="463b2-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="463b2-106">Declare a class that contains a method with the same signature as the delegate.</span><span class="sxs-lookup"><span data-stu-id="463b2-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="463b2-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span><span class="sxs-lookup"><span data-stu-id="463b2-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="463b2-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="463b2-108">See also</span></span>

- [<span data-ttu-id="463b2-109">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="463b2-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="463b2-110">Delegáty</span><span class="sxs-lookup"><span data-stu-id="463b2-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="463b2-111">Události</span><span class="sxs-lookup"><span data-stu-id="463b2-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="463b2-112">Vícevláknové aplikace</span><span class="sxs-lookup"><span data-stu-id="463b2-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
