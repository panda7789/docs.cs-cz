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

Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají parametry, jejichž typy jsou základní typy parametrů signatury delegátů. S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin. Následující příklad využívá dva delegáty:

- Delegát, který definuje signaturu události [Button. KeyDown.](xref:System.Windows.Forms.Control.KeyDown) <xref:System.Windows.Forms.KeyEventHandler> Jeho signatura je:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- Delegát, který definuje podpis události [Button. MouseClick.](xref:System.Windows.Forms.Control.MouseDown) <xref:System.Windows.Forms.MouseEventHandler> Jeho signatura je:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

V příkladu je definována obslužná rutina události <xref:System.EventArgs> s parametrem a používá ji pro zpracování `Button.KeyDown` událostí `Button.MouseClick` a. To může být způsobeno <xref:System.EventArgs> tím, že je základní typ <xref:System.Windows.Forms.KeyEventArgs> a <xref:System.Windows.Forms.MouseEventArgs>. 
  
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
