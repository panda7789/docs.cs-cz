---
title: Postup implementace událostí rozhraní – Průvodce programováním v C#
description: Naučte se implementovat události rozhraní ve třídě. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: bd86aed4f8d8ac6e291c11fe441f87ac97593b03
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302123"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Postup implementace událostí rozhraní (Průvodce programováním v C#)
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
Následující příklad ukazuje, jak zpracovat méně běžnou situaci, ve které vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní obsahuje událost se stejným názvem. V takovém případě je nutné zadat explicitní implementaci rozhraní alespoň pro jednu z událostí. Když napíšete explicitní implementaci rozhraní pro událost, musíte také napsat `add` `remove` přístupové objekty události a. Tyto jsou obvykle poskytovány kompilátorem, ale v tomto případě je kompilátor nemůže poskytnout.  
  
Poskytnutím vlastních přístupových objektů můžete určit, jestli jsou tyto dvě události reprezentované stejnou událostí ve vaší třídě, nebo různými událostmi. Například pokud by události měly být vyvolány v různých časech podle specifikací rozhraní, můžete každou událost přidružit k samostatné implementaci ve vaší třídě. V následujícím příkladu předplatitelé určují, která `OnDraw` událost bude přijímat přetypováním odkazu na obrazec do `IShape` nebo `IDrawingObject` .  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Události](./index.md)
- [Delegáti](../delegates/index.md)
- [Implementace explicitního rozhraní](../interfaces/explicit-interface-implementation.md)
- [Jak vyvolávat události základní třídy v odvozených třídách](./how-to-raise-base-class-events-in-derived-classes.md)
