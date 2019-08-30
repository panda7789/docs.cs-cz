---
title: Použití variance v delegátechC#()
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 980caf8d5e4699115d203a89fab7994d18cc1707
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168372"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="0fc1d-102">Použití variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="0fc1d-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="0fc1d-103">Když přiřadíte metodu delegátovi, *kovariance* a *kontravariance* poskytují flexibilitu pro porovnání typu delegáta s podpisem metody.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="0fc1d-104">Kovariance povoluje, aby metoda měla návratový typ, který je více odvozen od definice v delegátu.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="0fc1d-105">Kontravariance povoluje metodu, která má typy parametrů, které jsou méně odvozené než hodnoty v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="0fc1d-106">Příklad 1: Kovariance</span><span class="sxs-lookup"><span data-stu-id="0fc1d-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="0fc1d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0fc1d-107">Description</span></span>  
 <span data-ttu-id="0fc1d-108">Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají návratové typy odvozené od návratového typu v signatuře delegáta.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="0fc1d-109">Datový typ vrácený funkcí `DogsHandler` je typu `Dogs`, `Mammals` který je odvozen z typu, který je definován v delegátu.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0fc1d-110">Kód</span><span class="sxs-lookup"><span data-stu-id="0fc1d-110">Code</span></span>  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="0fc1d-111">Příklad 2: Kontravariance</span><span class="sxs-lookup"><span data-stu-id="0fc1d-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="0fc1d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0fc1d-112">Description</span></span>

<span data-ttu-id="0fc1d-113">Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají parametry, jejichž typy jsou základní typy parametrů signatury delegátů.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="0fc1d-114">S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="0fc1d-115">Následující příklad využívá dva delegáty:</span><span class="sxs-lookup"><span data-stu-id="0fc1d-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="0fc1d-116">Delegát, který definuje signaturu události [Button. KeyDown.](xref:System.Windows.Forms.Control.KeyDown) <xref:System.Windows.Forms.KeyEventHandler></span><span class="sxs-lookup"><span data-stu-id="0fc1d-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="0fc1d-117">Jeho signatura je:</span><span class="sxs-lookup"><span data-stu-id="0fc1d-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="0fc1d-118">Delegát, který definuje podpis události [Button. MouseClick.](xref:System.Windows.Forms.Control.MouseDown) <xref:System.Windows.Forms.MouseEventHandler></span><span class="sxs-lookup"><span data-stu-id="0fc1d-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="0fc1d-119">Jeho signatura je:</span><span class="sxs-lookup"><span data-stu-id="0fc1d-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="0fc1d-120">V příkladu je definována obslužná rutina události <xref:System.EventArgs> s parametrem a používá ji pro zpracování `Button.KeyDown` událostí `Button.MouseClick` a.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="0fc1d-121">To může být způsobeno <xref:System.EventArgs> tím, že je základní typ <xref:System.Windows.Forms.KeyEventArgs> a <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0fc1d-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span> 
  
### <a name="code"></a><span data-ttu-id="0fc1d-122">Kód</span><span class="sxs-lookup"><span data-stu-id="0fc1d-122">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fc1d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fc1d-123">See also</span></span>

- [<span data-ttu-id="0fc1d-124">Variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="0fc1d-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="0fc1d-125">Použití odchylky pro obecné delegáty Func a ActionC#()</span><span class="sxs-lookup"><span data-stu-id="0fc1d-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
