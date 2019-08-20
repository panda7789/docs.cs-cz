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
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="71f1c-102">Postupy: Implementace událostí rozhraní (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="71f1c-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="71f1c-103">[Rozhraní](../../language-reference/keywords/interface.md) může deklarovat [událost](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="71f1c-103">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="71f1c-104">Následující příklad ukazuje, jak implementovat události rozhraní ve třídě.</span><span class="sxs-lookup"><span data-stu-id="71f1c-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="71f1c-105">Pravidla jsou v podstatě stejná jako při implementaci libovolné metody rozhraní nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="71f1c-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="71f1c-106">Implementace událostí rozhraní ve třídě</span><span class="sxs-lookup"><span data-stu-id="71f1c-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="71f1c-107">Deklarujete událost ve třídě a pak ji vyvolejte v příslušných oblastech.</span><span class="sxs-lookup"><span data-stu-id="71f1c-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="71f1c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="71f1c-108">Example</span></span>  
<span data-ttu-id="71f1c-109">Následující příklad ukazuje, jak zpracovat méně běžnou situaci, ve které vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní obsahuje událost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="71f1c-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="71f1c-110">V takovém případě je nutné zadat explicitní implementaci rozhraní alespoň pro jednu z událostí.</span><span class="sxs-lookup"><span data-stu-id="71f1c-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="71f1c-111">Když napíšete explicitní implementaci rozhraní pro událost, musíte také napsat `add` přístupové objekty události a. `remove`</span><span class="sxs-lookup"><span data-stu-id="71f1c-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="71f1c-112">Tyto jsou obvykle poskytovány kompilátorem, ale v tomto případě je kompilátor nemůže poskytnout.</span><span class="sxs-lookup"><span data-stu-id="71f1c-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="71f1c-113">Poskytnutím vlastních přístupových objektů můžete určit, jestli jsou tyto dvě události reprezentované stejnou událostí ve vaší třídě, nebo různými událostmi.</span><span class="sxs-lookup"><span data-stu-id="71f1c-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="71f1c-114">Například pokud by události měly být vyvolány v různých časech podle specifikací rozhraní, můžete každou událost přidružit k samostatné implementaci ve vaší třídě.</span><span class="sxs-lookup"><span data-stu-id="71f1c-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="71f1c-115">V následujícím příkladu předplatitelé určují, která `OnDraw` událost bude přijímat přetypováním odkazu na obrazec do `IShape` nebo `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="71f1c-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="71f1c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71f1c-116">See also</span></span>

- [<span data-ttu-id="71f1c-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="71f1c-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="71f1c-118">Události</span><span class="sxs-lookup"><span data-stu-id="71f1c-118">Events</span></span>](./index.md)
- [<span data-ttu-id="71f1c-119">Delegáti</span><span class="sxs-lookup"><span data-stu-id="71f1c-119">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="71f1c-120">Implementace explicitního rozhraní</span><span class="sxs-lookup"><span data-stu-id="71f1c-120">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="71f1c-121">Postupy: Vyvolat události třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="71f1c-121">How to: Raise Base Class Events in Derived Classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
