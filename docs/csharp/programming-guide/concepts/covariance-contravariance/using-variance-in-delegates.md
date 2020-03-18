---
title: Použití odchylky v delegátech (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 83e86e760edb17f6d9ae61864c154062d41416e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169763"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="1516a-102">Použití odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="1516a-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="1516a-103">Při přiřazení metody delegátovi, *kovariance* a *contravariance* poskytují flexibilitu pro porovnávání typu delegáta s podpisem metody.</span><span class="sxs-lookup"><span data-stu-id="1516a-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="1516a-104">Kovariance umožňuje metodu mít návratový typ, který je více odvozený než definovaný v delegátovi.</span><span class="sxs-lookup"><span data-stu-id="1516a-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="1516a-105">Contravariance umožňuje metodu, která má typy parametrů, které jsou méně odvozené než ty v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="1516a-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="1516a-106">Příklad 1: Kovariance</span><span class="sxs-lookup"><span data-stu-id="1516a-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="1516a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1516a-107">Description</span></span>  
 <span data-ttu-id="1516a-108">Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají návratové typy, které jsou odvozeny z návratového typu v podpisu delegáta.</span><span class="sxs-lookup"><span data-stu-id="1516a-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="1516a-109">Datový typ vrácený `DogsHandler` podle `Dogs`je typu , `Mammals` který je odvozen od typu, který je definován v delegáta.</span><span class="sxs-lookup"><span data-stu-id="1516a-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1516a-110">kód</span><span class="sxs-lookup"><span data-stu-id="1516a-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="1516a-111">Příklad 2: Kontravariance</span><span class="sxs-lookup"><span data-stu-id="1516a-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="1516a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1516a-112">Description</span></span>

<span data-ttu-id="1516a-113">Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají parametry, jejichž typy jsou základními typy typu parametru podpisu delegáta.</span><span class="sxs-lookup"><span data-stu-id="1516a-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="1516a-114">S contravariance, můžete použít jednu obslužnou rutinu události namísto samostatných obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="1516a-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="1516a-115">Následující příklad využívá dva delegáty:</span><span class="sxs-lookup"><span data-stu-id="1516a-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="1516a-116">Delegát, <xref:System.Windows.Forms.KeyEventHandler> který definuje podpis [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) události.</span><span class="sxs-lookup"><span data-stu-id="1516a-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="1516a-117">Jeho podpis je:</span><span class="sxs-lookup"><span data-stu-id="1516a-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="1516a-118">Delegát, <xref:System.Windows.Forms.MouseEventHandler> který definuje podpis [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) události.</span><span class="sxs-lookup"><span data-stu-id="1516a-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="1516a-119">Jeho podpis je:</span><span class="sxs-lookup"><span data-stu-id="1516a-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="1516a-120">Příklad definuje obslužnou <xref:System.EventArgs> rutinu události s `Button.KeyDown` parametrem a používá ji ke zpracování události a události. `Button.MouseClick`</span><span class="sxs-lookup"><span data-stu-id="1516a-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="1516a-121">Může to provést, protože <xref:System.EventArgs> je <xref:System.Windows.Forms.KeyEventArgs> základní <xref:System.Windows.Forms.MouseEventArgs>typ obou a .</span><span class="sxs-lookup"><span data-stu-id="1516a-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="1516a-122">kód</span><span class="sxs-lookup"><span data-stu-id="1516a-122">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1516a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1516a-123">See also</span></span>

- [<span data-ttu-id="1516a-124">Odchylka v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="1516a-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="1516a-125">Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)</span><span class="sxs-lookup"><span data-stu-id="1516a-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
