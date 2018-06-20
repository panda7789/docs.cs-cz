---
title: 'Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 9bd030efb2e3e7bdbf3bb727948a2aae04a2fe50
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208374"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)
[Rozhraní](../../../csharp/language-reference/keywords/interface.md) můžou deklarovat [událostí](../../../csharp/language-reference/keywords/event.md). Následující příklad ukazuje postup implementace událostí rozhraní v třídě. V podstatě pravidla jsou stejné jako při implementaci žádné rozhraní metody nebo vlastnosti.  
  
### <a name="to-implement-interface-events-in-a-class"></a>Implementace událostí rozhraní v třídě  
  
-   Deklarace událostí v třídě a pak ji použít v příslušné oblasti.  
  
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
Následující příklad ukazuje, jak ke zpracování méně běžné situace, ve kterém třídě dědí ze dvou nebo více rozhraní a každé rozhraní má událost se stejným názvem. V takovém případě je nutné zadat explicitní implementace rozhraní pro minimálně jeden z událostí. Když píšete explicitní implementace rozhraní pro událost, musíte také napsat `add` a `remove` přístupových objektů událostí. Za normálních okolností jsou poskytovány kompilátorem, ale v takovém případě by je kompilátor nemůže poskytnout.  
  
Zadáním vlastních přístupových objektů můžete určit, zda jsou dvě události reprezentované stejnou událost ve třídě, nebo jednotlivé události. Například pokud má se vrhnout události v různou dobu podle specifikace rozhraní, můžete přidružit každé události samostatné implementace v třídě. V následujícím příkladu odběratele určit, které `OnDraw` událostí, zobrazí se jim podle přetypování tvar odkaz na buď `IShape` nebo `IDrawingObject`.  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Implementace explicitního rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [Postupy: Vyvolávání událostí třídy Base v odvozených třídách](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
