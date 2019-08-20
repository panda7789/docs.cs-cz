---
title: 'Postupy: Implementovat události rozhraní – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 574ea9927a22c24c356d84652fd29692c519247b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590514"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Postupy: Implementace událostí rozhraní (C# Průvodce programováním)
[Rozhraní](../../language-reference/keywords/interface.md) může deklarovat [událost](../../language-reference/keywords/event.md). Následující příklad ukazuje, jak implementovat události rozhraní ve třídě. Pravidla jsou v podstatě stejná jako při implementaci libovolné metody rozhraní nebo vlastnosti.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Implementace událostí rozhraní ve třídě  
  
Deklarujete událost ve třídě a pak ji vyvolejte v příslušných oblastech.  
  
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
Následující příklad ukazuje, jak zpracovat méně běžnou situaci, ve které vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní obsahuje událost se stejným názvem. V takovém případě je nutné zadat explicitní implementaci rozhraní alespoň pro jednu z událostí. Když napíšete explicitní implementaci rozhraní pro událost, musíte také napsat `add` přístupové objekty události a. `remove` Tyto jsou obvykle poskytovány kompilátorem, ale v tomto případě je kompilátor nemůže poskytnout.  
  
Poskytnutím vlastních přístupových objektů můžete určit, jestli jsou tyto dvě události reprezentované stejnou událostí ve vaší třídě, nebo různými událostmi. Například pokud by události měly být vyvolány v různých časech podle specifikací rozhraní, můžete každou událost přidružit k samostatné implementaci ve vaší třídě. V následujícím příkladu předplatitelé určují, která `OnDraw` událost bude přijímat přetypováním odkazu na obrazec do `IShape` nebo `IDrawingObject`.  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Události](./index.md)
- [Delegáti](../delegates/index.md)
- [Implementace explicitního rozhraní](../interfaces/explicit-interface-implementation.md)
- [Postupy: Vyvolat události třídy Base v odvozených třídách](./how-to-raise-base-class-events-in-derived-classes.md)
