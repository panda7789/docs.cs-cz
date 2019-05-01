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
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="75105-102">Postupy: Volání metody delegáta (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75105-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="75105-103">Tento příklad ukazuje, jak přidružit metodu delegáta a poté vyvolat tuto metodu prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="75105-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="75105-104">Vytvoření delegáta a odpovídající procedur</span><span class="sxs-lookup"><span data-stu-id="75105-104">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="75105-105">Vytvoření delegáta s názvem `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="75105-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2. <span data-ttu-id="75105-106">Deklarujte třídu, která obsahuje metodu s stejný podpis jako delegát.</span><span class="sxs-lookup"><span data-stu-id="75105-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3. <span data-ttu-id="75105-107">Definujte metodu, která vytvoří instanci delegáta a vyvolá metodu spojenou s delegátem voláním předdefinované `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="75105-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="75105-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75105-108">See also</span></span>

- [<span data-ttu-id="75105-109">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="75105-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="75105-110">Delegáti</span><span class="sxs-lookup"><span data-stu-id="75105-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="75105-111">Události</span><span class="sxs-lookup"><span data-stu-id="75105-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="75105-112">Vícevláknové aplikace</span><span class="sxs-lookup"><span data-stu-id="75105-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
