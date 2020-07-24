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
# <a name="using-variance-in-delegates-c"></a>Použití variance v delegátech (C#)
Když přiřadíte metodu delegátovi, *kovariance* a *kontravariance* poskytují flexibilitu pro porovnání typu delegáta s podpisem metody. Kovariance povoluje, aby metoda měla návratový typ, který je více odvozen od definice v delegátu. Kontravariance povoluje metodu, která má typy parametrů, které jsou méně odvozené než hodnoty v typu delegáta.  
  
## <a name="example-1-covariance"></a>Příklad 1: kovariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají návratové typy odvozené od návratového typu v signatuře delegáta. Datový typ vrácený funkcí `DogsHandler` je typu `Dogs` , který je odvozen z `Mammals` typu, který je definován v delegátu.  
  
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
  
## <a name="example-2-contravariance"></a>Příklad 2: kontravariance  
  
### <a name="description"></a>Popis

Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají parametry, jejichž typy jsou základní typy parametrů signatury delegátů. S kontravariance můžete použít jednu obslužnou rutinu události místo samostatných obslužných rutin. Následující příklad využívá dva delegáty:

- <xref:System.Windows.Forms.KeyEventHandler>Delegát, který definuje signaturu události [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) . Jeho signatura je:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <xref:System.Windows.Forms.MouseEventHandler>Delegát, který definuje podpis události [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) . Jeho signatura je:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

V příkladu je definována obslužná rutina události s <xref:System.EventArgs> parametrem a používá ji pro zpracování `Button.KeyDown` `Button.MouseClick` událostí a. To může být způsobeno tím, že <xref:System.EventArgs> je základní typ <xref:System.Windows.Forms.KeyEventArgs> a <xref:System.Windows.Forms.MouseEventArgs> .
  
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
  
## <a name="see-also"></a>Viz také

- [Variance v delegátech (C#)](./variance-in-delegates.md)
- [Použití odchylky pro obecné delegáty Func a Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)
