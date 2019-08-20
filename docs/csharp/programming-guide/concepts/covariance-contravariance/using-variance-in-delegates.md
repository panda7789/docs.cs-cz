---
title: Použití variance v delegátechC#()
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 00e11d4ce755c8c75b73023fec14d95ebc96b4fe
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595260"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="dc855-102">Použití variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="dc855-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="dc855-103">Když přiřadíte metodu delegátovi, *kovariance* a *kontravariance* poskytují flexibilitu pro porovnání typu delegáta s podpisem metody.</span><span class="sxs-lookup"><span data-stu-id="dc855-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="dc855-104">Kovariance povoluje, aby metoda měla návratový typ, který je více odvozen od definice v delegátu.</span><span class="sxs-lookup"><span data-stu-id="dc855-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="dc855-105">Kontravariance povoluje metodu, která má typy parametrů, které jsou méně odvozené než hodnoty v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="dc855-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="dc855-106">Příklad 1: Kovariance</span><span class="sxs-lookup"><span data-stu-id="dc855-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="dc855-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dc855-107">Description</span></span>  
 <span data-ttu-id="dc855-108">Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají návratové typy odvozené od návratového typu v signatuře delegáta.</span><span class="sxs-lookup"><span data-stu-id="dc855-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="dc855-109">Datový typ vrácený funkcí `DogsHandler` je typu `Dogs`, `Mammals` který je odvozen z typu, který je definován v delegátu.</span><span class="sxs-lookup"><span data-stu-id="dc855-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dc855-110">Kód</span><span class="sxs-lookup"><span data-stu-id="dc855-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="dc855-111">Příklad 2: Kontravariance</span><span class="sxs-lookup"><span data-stu-id="dc855-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="dc855-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dc855-112">Description</span></span>  
 <span data-ttu-id="dc855-113">Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají parametry typu, které jsou základními typy typu parametru signatury delegáta.</span><span class="sxs-lookup"><span data-stu-id="dc855-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="dc855-114">S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="dc855-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="dc855-115">Můžete například vytvořit `EventArgs` obslužnou rutinu události, která přijímá vstupní parametr a použije ji `Button.MouseClick` s událostí, která odešle `MouseEventArgs` typ `TextBox.KeyDown` jako parametr, `KeyEventArgs` a také událost, která odešle parametr.</span><span class="sxs-lookup"><span data-stu-id="dc855-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dc855-116">Kód</span><span class="sxs-lookup"><span data-stu-id="dc855-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc855-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc855-117">See also</span></span>

- [<span data-ttu-id="dc855-118">Variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="dc855-118">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="dc855-119">Použití odchylky pro obecné delegáty Func a ActionC#()</span><span class="sxs-lookup"><span data-stu-id="dc855-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
