---
title: 'Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 3620a3e11553bdd6878126388b612113b5722e89
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802755"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)
[Rozhraní](../../../csharp/language-reference/keywords/interface.md) lze deklarovat [události](../../../csharp/language-reference/keywords/event.md). Následující příklad ukazuje, jak implementace událostí rozhraní ve třídě. V podstatě pravidla jsou stejné jako při implementaci metody rozhraní ani vlastnost.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Implementace událostí rozhraní ve třídě  
  
Deklarovat událost ve své třídě a následně ho vyvolat v příslušné oblasti.  
  
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
Následující příklad ukazuje, jak zpracovat méně běžné situace, ve které vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní má událost se stejným názvem. V takovém případě je nutné zadat explicitní implementaci rozhraní pro nejméně jednu z událostí. Při zápisu explicitní implementace rozhraní události, je nutné také napsat `add` a `remove` přístupových objektů událostí. Obvykle je poskytován kompilátorem, ale v tomto případě kompilátor nemůže poskytnout jim.  
  
Poskytnutím vlastní přístupové objekty, můžete určit, zda dvě události představují stejnou událost ve své třídě, nebo jednotlivé události. Například pokud události by měly být vyvolána v různých časech podle specifikace rozhraní, můžete přidružit každou událost samostatné implementaci ve své třídě. V následujícím příkladu, předplatitelé určení, které `OnDraw` události se mu přetypováním tvar odkazu na buď `IShape` nebo `IDrawingObject`.  
  
 [!code-csharp[WrapTwoInterfaceEvents](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs#everything)]
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Události](../../../csharp/programming-guide/events/index.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
- [Implementace explicitního rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
- [Postupy: Vyvolávání událostí třídy Base v odvozených třídách](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
