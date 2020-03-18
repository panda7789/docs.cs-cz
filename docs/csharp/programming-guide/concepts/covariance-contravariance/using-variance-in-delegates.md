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
# <a name="using-variance-in-delegates-c"></a>Použití odchylky v delegátech (C#)
Při přiřazení metody delegátovi, *kovariance* a *contravariance* poskytují flexibilitu pro porovnávání typu delegáta s podpisem metody. Kovariance umožňuje metodu mít návratový typ, který je více odvozený než definovaný v delegátovi. Contravariance umožňuje metodu, která má typy parametrů, které jsou méně odvozené než ty v typu delegáta.  
  
## <a name="example-1-covariance"></a>Příklad 1: Kovariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak lze použít delegáty s metodami, které mají návratové typy, které jsou odvozeny z návratového typu v podpisu delegáta. Datový typ vrácený `DogsHandler` podle `Dogs`je typu , `Mammals` který je odvozen od typu, který je definován v delegáta.  
  
### <a name="code"></a>kód  
  
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

Tento příklad ukazuje, jak lze delegáty použít s metodami, které mají parametry, jejichž typy jsou základními typy typu parametru podpisu delegáta. S contravariance, můžete použít jednu obslužnou rutinu události namísto samostatných obslužných rutin. Následující příklad využívá dva delegáty:

- Delegát, <xref:System.Windows.Forms.KeyEventHandler> který definuje podpis [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) události. Jeho podpis je:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- Delegát, <xref:System.Windows.Forms.MouseEventHandler> který definuje podpis [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) události. Jeho podpis je:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

Příklad definuje obslužnou <xref:System.EventArgs> rutinu události s `Button.KeyDown` parametrem a používá ji ke zpracování události a události. `Button.MouseClick` Může to provést, protože <xref:System.EventArgs> je <xref:System.Windows.Forms.KeyEventArgs> základní <xref:System.Windows.Forms.MouseEventArgs>typ obou a .
  
### <a name="code"></a>kód  
  
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

- [Odchylka v delegátech (C#)](./variance-in-delegates.md)
- [Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)](./using-variance-for-func-and-action-generic-delegates.md)
