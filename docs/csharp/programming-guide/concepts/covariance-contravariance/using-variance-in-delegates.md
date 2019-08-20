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
# <a name="using-variance-in-delegates-c"></a>Použití variance v delegátechC#()
Když přiřadíte metodu delegátovi, *kovariance* a *kontravariance* poskytují flexibilitu pro porovnání typu delegáta s podpisem metody. Kovariance povoluje, aby metoda měla návratový typ, který je více odvozen od definice v delegátu. Kontravariance povoluje metodu, která má typy parametrů, které jsou méně odvozené než hodnoty v typu delegáta.  
  
## <a name="example-1-covariance"></a>Příklad 1: Kovariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají návratové typy odvozené od návratového typu v signatuře delegáta. Datový typ vrácený funkcí `DogsHandler` je typu `Dogs`, `Mammals` který je odvozen z typu, který je definován v delegátu.  
  
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
 Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají parametry typu, které jsou základními typy typu parametru signatury delegáta. S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin. Můžete například vytvořit `EventArgs` obslužnou rutinu události, která přijímá vstupní parametr a použije ji `Button.MouseClick` s událostí, která odešle `MouseEventArgs` typ `TextBox.KeyDown` jako parametr, `KeyEventArgs` a také událost, která odešle parametr.  
  
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

- [Variance v delegátechC#()](./variance-in-delegates.md)
- [Použití odchylky pro obecné delegáty Func a ActionC#()](./using-variance-for-func-and-action-generic-delegates.md)
