---
title: Použití odchylek v delegátech
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 9c2aad0e4b9408939600938412fe5c3e73b5bf15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349033"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="45fed-102">Použití variance v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fed-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="45fed-103">Když přiřadíte metodu delegátovi, *kovariance* a *kontravariance* poskytují flexibilitu pro porovnání typu delegáta s podpisem metody.</span><span class="sxs-lookup"><span data-stu-id="45fed-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="45fed-104">Kovariance povoluje, aby metoda měla návratový typ, který je více odvozen od definice v delegátu.</span><span class="sxs-lookup"><span data-stu-id="45fed-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="45fed-105">Kontravariance povoluje metodu, která má typy parametrů, které jsou méně odvozené než hodnoty v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="45fed-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="45fed-106">Příklad 1: kovariance</span><span class="sxs-lookup"><span data-stu-id="45fed-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="45fed-107">Popis</span><span class="sxs-lookup"><span data-stu-id="45fed-107">Description</span></span>

<span data-ttu-id="45fed-108">Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají návratové typy odvozené od návratového typu v signatuře delegáta.</span><span class="sxs-lookup"><span data-stu-id="45fed-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="45fed-109">Datový typ vrácený `DogsHandler` je typu `Dogs`, který je odvozen z typu `Mammals`, který je definován v delegátu.</span><span class="sxs-lookup"><span data-stu-id="45fed-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="45fed-110">Kód</span><span class="sxs-lookup"><span data-stu-id="45fed-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="45fed-111">Příklad 2: kontravariance</span><span class="sxs-lookup"><span data-stu-id="45fed-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="45fed-112">Popis</span><span class="sxs-lookup"><span data-stu-id="45fed-112">Description</span></span>

<span data-ttu-id="45fed-113">Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají parametry, jejichž typy jsou základní typy parametrů signatury delegátů.</span><span class="sxs-lookup"><span data-stu-id="45fed-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="45fed-114">S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="45fed-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="45fed-115">Následující příklad využívá dva delegáty:</span><span class="sxs-lookup"><span data-stu-id="45fed-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="45fed-116">Delegát <xref:System.Windows.Forms.KeyEventHandler>, který definuje signaturu události [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) .</span><span class="sxs-lookup"><span data-stu-id="45fed-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="45fed-117">Jeho signatura je:</span><span class="sxs-lookup"><span data-stu-id="45fed-117">Its signature is:</span></span>

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <span data-ttu-id="45fed-118">Delegát <xref:System.Windows.Forms.MouseEventHandler>, který definuje podpis události [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) .</span><span class="sxs-lookup"><span data-stu-id="45fed-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="45fed-119">Jeho signatura je:</span><span class="sxs-lookup"><span data-stu-id="45fed-119">Its signature is:</span></span>

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

<span data-ttu-id="45fed-120">V příkladu je definována obslužná rutina události s parametrem <xref:System.EventArgs> a používá ji pro zpracování událostí `Button.KeyDown` a `Button.MouseClick`.</span><span class="sxs-lookup"><span data-stu-id="45fed-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="45fed-121">To může být způsobeno tím, že <xref:System.EventArgs> je základní typ <xref:System.Windows.Forms.KeyEventArgs> a <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="45fed-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>

### <a name="code"></a><span data-ttu-id="45fed-122">Kód</span><span class="sxs-lookup"><span data-stu-id="45fed-122">Code</span></span>

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

## <a name="see-also"></a><span data-ttu-id="45fed-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45fed-123">See also</span></span>

- [<span data-ttu-id="45fed-124">Variance v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fed-124">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="45fed-125">Použití odchylky pro obecné delegáty Func a Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fed-125">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
