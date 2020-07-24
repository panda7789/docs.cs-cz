---
title: Použití variance v delegátech (C#)
description: Naučte se používat variance v delegátech pomocí zahrnutých příkladů kódu kovariance a kontravariance.
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 62b0555ee29c5e7d2ba0954a8949d61596122cc7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105683"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="a06b7-103">Použití variance v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="a06b7-103">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="a06b7-104">Když přiřadíte metodu delegátovi, *kovariance* a *kontravariance* poskytují flexibilitu pro porovnání typu delegáta s podpisem metody.</span><span class="sxs-lookup"><span data-stu-id="a06b7-104">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="a06b7-105">Kovariance povoluje, aby metoda měla návratový typ, který je více odvozen od definice v delegátu.</span><span class="sxs-lookup"><span data-stu-id="a06b7-105">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="a06b7-106">Kontravariance povoluje metodu, která má typy parametrů, které jsou méně odvozené než hodnoty v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="a06b7-106">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="a06b7-107">Příklad 1: kovariance</span><span class="sxs-lookup"><span data-stu-id="a06b7-107">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="a06b7-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a06b7-108">Description</span></span>  
 <span data-ttu-id="a06b7-109">Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají návratové typy odvozené od návratového typu v signatuře delegáta.</span><span class="sxs-lookup"><span data-stu-id="a06b7-109">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="a06b7-110">Datový typ vrácený funkcí `DogsHandler` je typu `Dogs` , který je odvozen z `Mammals` typu, který je definován v delegátu.</span><span class="sxs-lookup"><span data-stu-id="a06b7-110">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a06b7-111">Kód</span><span class="sxs-lookup"><span data-stu-id="a06b7-111">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="a06b7-112">Příklad 2: kontravariance</span><span class="sxs-lookup"><span data-stu-id="a06b7-112">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="a06b7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a06b7-113">Description</span></span>

<span data-ttu-id="a06b7-114">Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají parametry, jejichž typy jsou základní typy parametrů signatury delegátů.</span><span class="sxs-lookup"><span data-stu-id="a06b7-114">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="a06b7-115">S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="a06b7-115">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="a06b7-116">Následující příklad využívá dva delegáty:</span><span class="sxs-lookup"><span data-stu-id="a06b7-116">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="a06b7-117"><xref:System.Windows.Forms.KeyEventHandler>Delegát, který definuje signaturu události [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) .</span><span class="sxs-lookup"><span data-stu-id="a06b7-117">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="a06b7-118">Jeho signatura je:</span><span class="sxs-lookup"><span data-stu-id="a06b7-118">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="a06b7-119"><xref:System.Windows.Forms.MouseEventHandler>Delegát, který definuje podpis události [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) .</span><span class="sxs-lookup"><span data-stu-id="a06b7-119">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="a06b7-120">Jeho signatura je:</span><span class="sxs-lookup"><span data-stu-id="a06b7-120">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="a06b7-121">V příkladu je definována obslužná rutina události s <xref:System.EventArgs> parametrem a používá ji pro zpracování `Button.KeyDown` `Button.MouseClick` událostí a.</span><span class="sxs-lookup"><span data-stu-id="a06b7-121">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="a06b7-122">To může být způsobeno tím, že <xref:System.EventArgs> je základní typ <xref:System.Windows.Forms.KeyEventArgs> a <xref:System.Windows.Forms.MouseEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="a06b7-122">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="a06b7-123">Kód</span><span class="sxs-lookup"><span data-stu-id="a06b7-123">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a06b7-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a06b7-124">See also</span></span>

- [<span data-ttu-id="a06b7-125">Variance v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="a06b7-125">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="a06b7-126">Použití odchylky pro obecné delegáty Func a Action (C#)</span><span class="sxs-lookup"><span data-stu-id="a06b7-126">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
