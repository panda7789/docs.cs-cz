---
title: Použití odchylek v delegátech (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 44a6153a9a1c0aa0aebb18710ea9e770fd4e57fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667269"
---
# <a name="using-variance-in-delegates-c"></a>Použití odchylek v delegátech (C#)
Když přiřadíte metody delegáta *kovariance* a *kontravariance* poskytují flexibilitu pro odpovídající typ delegáta se podpis metody. Kovariance povoluje metoda může mít návratový typ, který je odvozený víc než který definované v delegátu. Kontravariance umožní metodu, která má typy parametrů, které jsou méně odvozený než ty, které v typu delegáta.  
  
## <a name="example-1-covariance"></a>Příklad 1: Kovariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak delegáty lze provádět pomocí metod, které mají návratové typy, které jsou odvozeny z návratového typu v signatuře delegátu. Datový typ vracený `DogsHandler` je typu `Dogs`, která je odvozena z `Mammals` typ, který je definován v delegátu.  
  
### <a name="code"></a>Kód  
  
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
  
## <a name="example-2-contravariance"></a>Příklad 2: Kontravariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak lze pomocí metody, které mají parametry typu, které jsou uvedeny základní typy typ parametru signatury delegáta delegátů. S kontravariance místo samostatných obslužné rutiny můžete použít jednu obslužnou rutinu události. Můžete například vytvořit obslužnou rutinu události, která přijímá `EventArgs` vstupní parametr a použít je s `Button.MouseClick` událost, která odesílá `MouseEventArgs` typ jako parametr a také s `TextBox.KeyDown` událost, která odesílá `KeyEventArgs` parametr.  
  
### <a name="code"></a>Kód  
  
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
  
## <a name="see-also"></a>Viz také:

- [Odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Použití odchylek pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
