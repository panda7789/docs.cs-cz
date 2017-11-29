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
# <a name="using-variance-in-delegates-c"></a>Použití odchylek v delegátech (C#)
Přiřadíte-li metodu s delegátem, *kovariance* a *kontravariance* poskytují flexibilitu pro odpovídající typu delegáta podpisem metoda. Kovariance umožňuje metoda má návratový typ, který je odvozený více než která definována v delegát. Kontravariance umožňuje metodu, která má parametr typy, které jsou odvozené méně než ty, které v typu delegáta.  
  
## <a name="example-1-covariance"></a>Příklad 1: kovariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak lze pomocí metody, které mají návratové typy, které jsou odvozeny od návratový typ v hlavičce delegáta delegáti. Datový typ vrácený `DogsHandler` je typu `Dogs`, která je odvozena z `Mammals` typ, který je definován v delegát.  
  
### <a name="code"></a>Kód  
  
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
  
## <a name="example-2-contravariance"></a>Příklad 2: kontravariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak delegáti lze provádět pomocí metod, které mají parametry typu, které jsou základní typy delegáta podpis parametr typu. S kontravariance můžete použít jeden obslužné rutiny události místo samostatné obslužné rutiny. Například můžete vytvořit obslužnou rutinu události, který přijímá `EventArgs` vstupní parametr a použít je s `Button.MouseClick` událost, která odešle `MouseEventArgs` typu jako parametr a také s `TextBox.KeyDown` událost, která odešle `KeyEventArgs` parametr.  
  
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
 [Odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [Použití odchylek pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
