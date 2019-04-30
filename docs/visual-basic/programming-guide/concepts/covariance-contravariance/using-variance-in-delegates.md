---
title: Použití odchylek v delegátech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 19eb3070c1b8359a4eb050e7cf2f16622f66ebe9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787254"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="1dd3d-102">Použití odchylek v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dd3d-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="1dd3d-103">Když přiřadíte metody delegáta *kovariance* a *kontravariance* poskytují flexibilitu pro odpovídající typ delegáta se podpis metody.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="1dd3d-104">Kovariance povoluje metoda může mít návratový typ, který je odvozený víc než který definované v delegátu.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="1dd3d-105">Kontravariance umožní metodu, která má typy parametrů, které jsou méně odvozený než ty, které v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="1dd3d-106">Příklad 1: Kovariance</span><span class="sxs-lookup"><span data-stu-id="1dd3d-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="1dd3d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1dd3d-107">Description</span></span>

<span data-ttu-id="1dd3d-108">Tento příklad ukazuje, jak delegáty lze provádět pomocí metod, které mají návratové typy, které jsou odvozeny z návratového typu v signatuře delegátu.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="1dd3d-109">Datový typ vracený `DogsHandler` je typu `Dogs`, která je odvozena z `Mammals` typ, který je definován v delegátu.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="1dd3d-110">Kód</span><span class="sxs-lookup"><span data-stu-id="1dd3d-110">Code</span></span>

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a><span data-ttu-id="1dd3d-111">Příklad 2: Kontravariance</span><span class="sxs-lookup"><span data-stu-id="1dd3d-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="1dd3d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1dd3d-112">Description</span></span>

<span data-ttu-id="1dd3d-113">Tento příklad ukazuje, jak lze pomocí metody, které mají parametry typu, které jsou uvedeny základní typy typ parametru signatury delegáta delegátů.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="1dd3d-114">S kontravariance místo samostatných obslužné rutiny můžete použít jednu obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="1dd3d-115">Můžete například vytvořit obslužnou rutinu události, která přijímá `EventArgs` vstupní parametr a použít je s `Button.MouseClick` událost, která odesílá `MouseEventArgs` typ jako parametr a také s `TextBox.KeyDown` událost, která odesílá `KeyEventArgs` parametr.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>

### <a name="code"></a><span data-ttu-id="1dd3d-116">Kód</span><span class="sxs-lookup"><span data-stu-id="1dd3d-116">Code</span></span>

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a><span data-ttu-id="1dd3d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dd3d-117">See also</span></span>

- [<span data-ttu-id="1dd3d-118">Odchylky v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dd3d-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="1dd3d-119">Použití odchylek pro delegáty Func a Action obecný (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dd3d-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
