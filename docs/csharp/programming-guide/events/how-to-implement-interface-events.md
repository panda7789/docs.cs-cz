---
title: "Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 944b894e7e5f305d35d4db96d7426bf05322ca54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="5efec-102">Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5efec-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="5efec-103">[Rozhraní](../../../csharp/language-reference/keywords/interface.md) můžou deklarovat [událostí](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="5efec-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="5efec-104">Následující příklad ukazuje postup implementace událostí rozhraní v třídě.</span><span class="sxs-lookup"><span data-stu-id="5efec-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="5efec-105">V podstatě pravidla jsou stejné jako při implementaci žádné rozhraní metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5efec-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
### <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="5efec-106">Implementace událostí rozhraní v třídě</span><span class="sxs-lookup"><span data-stu-id="5efec-106">To implement interface events in a class</span></span>  
  
-   <span data-ttu-id="5efec-107">Deklarace událostí v třídě a pak ji použít v příslušné oblasti.</span><span class="sxs-lookup"><span data-stu-id="5efec-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
    ```  
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
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="5efec-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5efec-108">Example</span></span>  
 <span data-ttu-id="5efec-109">Následující příklad ukazuje, jak ke zpracování méně běžné situace, ve kterém třídě dědí ze dvou nebo více rozhraní a každé rozhraní má událost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="5efec-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="5efec-110">V takovém případě je nutné zadat explicitní implementace rozhraní pro minimálně jeden z událostí.</span><span class="sxs-lookup"><span data-stu-id="5efec-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="5efec-111">Když píšete explicitní implementace rozhraní pro událost, musíte také napsat `add` a `remove` přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="5efec-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="5efec-112">Za normálních okolností jsou poskytovány kompilátorem, ale v takovém případě by je kompilátor nemůže poskytnout.</span><span class="sxs-lookup"><span data-stu-id="5efec-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
 <span data-ttu-id="5efec-113">Zadáním vlastních přístupových objektů můžete určit, zda jsou dvě události reprezentované stejnou událost ve třídě, nebo jednotlivé události.</span><span class="sxs-lookup"><span data-stu-id="5efec-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="5efec-114">Například pokud má se vrhnout události v různou dobu podle specifikace rozhraní, můžete přidružit každé události samostatné implementace v třídě.</span><span class="sxs-lookup"><span data-stu-id="5efec-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="5efec-115">V následujícím příkladu odběratele určit, které `OnDraw` událostí, zobrazí se jim podle přetypování tvar odkaz na buď `IShape` nebo `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="5efec-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5efec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5efec-116">See Also</span></span>  
 [<span data-ttu-id="5efec-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5efec-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5efec-118">Události</span><span class="sxs-lookup"><span data-stu-id="5efec-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="5efec-119">Delegáti</span><span class="sxs-lookup"><span data-stu-id="5efec-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="5efec-120">Implementace explicitního rozhraní</span><span class="sxs-lookup"><span data-stu-id="5efec-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [<span data-ttu-id="5efec-121">Postupy: vyvolávání událostí třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="5efec-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
