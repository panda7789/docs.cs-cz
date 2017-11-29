---
title: "Použití odchylek v delegátech (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb8512945fa7aefa9afce4f4f1f8e0200dc3e2b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="34aff-102">Použití odchylek v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="34aff-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="34aff-103">Přiřadíte-li metodu s delegátem, *kovariance* a *kontravariance* poskytují flexibilitu pro odpovídající typu delegáta podpisem metoda.</span><span class="sxs-lookup"><span data-stu-id="34aff-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="34aff-104">Kovariance umožňuje metoda má návratový typ, který je odvozený více než která definována v delegát.</span><span class="sxs-lookup"><span data-stu-id="34aff-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="34aff-105">Kontravariance umožňuje metodu, která má parametr typy, které jsou odvozené méně než ty, které v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="34aff-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="34aff-106">Příklad 1: kovariance</span><span class="sxs-lookup"><span data-stu-id="34aff-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="34aff-107">Popis</span><span class="sxs-lookup"><span data-stu-id="34aff-107">Description</span></span>  
 <span data-ttu-id="34aff-108">Tento příklad ukazuje, jak lze pomocí metody, které mají návratové typy, které jsou odvozeny od návratový typ v hlavičce delegáta delegáti.</span><span class="sxs-lookup"><span data-stu-id="34aff-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="34aff-109">Datový typ vrácený `DogsHandler` je typu `Dogs`, která je odvozena z `Mammals` typ, který je definován v delegát.</span><span class="sxs-lookup"><span data-stu-id="34aff-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="34aff-110">Kód</span><span class="sxs-lookup"><span data-stu-id="34aff-110">Code</span></span>  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="34aff-111">Příklad 2: kontravariance</span><span class="sxs-lookup"><span data-stu-id="34aff-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="34aff-112">Popis</span><span class="sxs-lookup"><span data-stu-id="34aff-112">Description</span></span>  
 <span data-ttu-id="34aff-113">Tento příklad ukazuje, jak delegáti lze provádět pomocí metod, které mají parametry typu, které jsou základní typy delegáta podpis parametr typu.</span><span class="sxs-lookup"><span data-stu-id="34aff-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="34aff-114">S kontravariance můžete použít jeden obslužné rutiny události místo samostatné obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="34aff-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="34aff-115">Například můžete vytvořit obslužnou rutinu události, který přijímá `EventArgs` vstupní parametr a použít je s `Button.MouseClick` událost, která odešle `MouseEventArgs` typu jako parametr a také s `TextBox.KeyDown` událost, která odešle `KeyEventArgs` parametr.</span><span class="sxs-lookup"><span data-stu-id="34aff-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="34aff-116">Kód</span><span class="sxs-lookup"><span data-stu-id="34aff-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34aff-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="34aff-117">See Also</span></span>  
 [<span data-ttu-id="34aff-118">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="34aff-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="34aff-119">Použití odchylek pro Func a akce obecní delegáti (C#)</span><span class="sxs-lookup"><span data-stu-id="34aff-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
