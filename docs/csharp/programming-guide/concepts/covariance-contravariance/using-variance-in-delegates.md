---
title: Použití odchylek v delegátech (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 5be4f786d2e1b8a0ead3fd58fe056e188faa916a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501721"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="a82b3-102">Použití odchylek v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="a82b3-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="a82b3-103">Když přiřadíte metody delegáta *kovariance* a *kontravariance* poskytují flexibilitu pro odpovídající typ delegáta se podpis metody.</span><span class="sxs-lookup"><span data-stu-id="a82b3-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="a82b3-104">Kovariance povoluje metoda může mít návratový typ, který je odvozený víc než který definované v delegátu.</span><span class="sxs-lookup"><span data-stu-id="a82b3-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="a82b3-105">Kontravariance umožní metodu, která má typy parametrů, které jsou méně odvozený než ty, které v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="a82b3-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="a82b3-106">Příklad 1: kovariance</span><span class="sxs-lookup"><span data-stu-id="a82b3-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="a82b3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a82b3-107">Description</span></span>  
 <span data-ttu-id="a82b3-108">Tento příklad ukazuje, jak delegáty lze provádět pomocí metod, které mají návratové typy, které jsou odvozeny z návratového typu v signatuře delegátu.</span><span class="sxs-lookup"><span data-stu-id="a82b3-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="a82b3-109">Datový typ vracený `DogsHandler` je typu `Dogs`, která je odvozena z `Mammals` typ, který je definován v delegátu.</span><span class="sxs-lookup"><span data-stu-id="a82b3-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a82b3-110">Kód</span><span class="sxs-lookup"><span data-stu-id="a82b3-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="a82b3-111">Příklad 2: kontravariance</span><span class="sxs-lookup"><span data-stu-id="a82b3-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="a82b3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a82b3-112">Description</span></span>  
 <span data-ttu-id="a82b3-113">Tento příklad ukazuje, jak lze pomocí metody, které mají parametry typu, které jsou uvedeny základní typy typ parametru signatury delegáta delegátů.</span><span class="sxs-lookup"><span data-stu-id="a82b3-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="a82b3-114">S kontravariance místo samostatných obslužné rutiny můžete použít jednu obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="a82b3-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="a82b3-115">Můžete například vytvořit obslužnou rutinu události, která přijímá `EventArgs` vstupní parametr a použít je s `Button.MouseClick` událost, která odesílá `MouseEventArgs` typ jako parametr a také s `TextBox.KeyDown` událost, která odesílá `KeyEventArgs` parametr.</span><span class="sxs-lookup"><span data-stu-id="a82b3-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a82b3-116">Kód</span><span class="sxs-lookup"><span data-stu-id="a82b3-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a82b3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a82b3-117">See Also</span></span>

- [<span data-ttu-id="a82b3-118">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="a82b3-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
- [<span data-ttu-id="a82b3-119">Použití odchylek pro delegáty Func a Action obecný (C#)</span><span class="sxs-lookup"><span data-stu-id="a82b3-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
