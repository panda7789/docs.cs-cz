---
title: Jak implementovat události rozhraní - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 8c0d221ef1272a43e2682ef2af3fa37d2d12d35e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167477"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Jak implementovat události rozhraní (Průvodce programováním jazyka C#)
[Rozhraní](../../language-reference/keywords/interface.md) může deklarovat [událost](../../language-reference/keywords/event.md). Následující příklad ukazuje, jak implementovat události rozhraní ve třídě. V podstatě pravidla jsou stejné jako při implementaci jakékoli metody rozhraní nebo vlastnosti.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Implementace událostí rozhraní ve třídě  
  
Deklarujte událost ve své třídě a pak ji vyvolat v příslušných oblastech.  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje, jak zpracovat méně časté situace, ve kterém vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní má událost se stejným názvem. V takovém případě je nutné zadat explicitní implementaci rozhraní alespoň pro jednu z událostí. Při zápisu explicitní implementace rozhraní pro událost, `add` musíte `remove` také zapsat přístupové objekty a události. Obvykle jsou poskytovány kompilátorem, ale v tomto případě kompilátor nemůže poskytnout.  
  
Poskytnutím vlastních přístupových skupin můžete určit, zda jsou dvě události reprezentovány stejnou událostí ve vaší třídě nebo různými událostmi. Například pokud události by měly být vyvolány v různých časech podle specifikace rozhraní, můžete přidružit každou událost se samostatnou implementaci ve vaší třídě. V následujícím příkladu odběratelé `OnDraw` určit, které události obdrží přetypování odkazu na tvar `IShape` nebo `IDrawingObject`.  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Akce](./index.md)
- [Delegáty](../delegates/index.md)
- [Implementace explicitního rozhraní](../interfaces/explicit-interface-implementation.md)
- [Jak vyvolávat události základní třídy v odvozených třídách](./how-to-raise-base-class-events-in-derived-classes.md)
