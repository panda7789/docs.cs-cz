---
title: 'Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 3620a3e11553bdd6878126388b612113b5722e89
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863658"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="01cb3-102">Postupy: Implementace událostí rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="01cb3-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="01cb3-103">[Rozhraní](../../../csharp/language-reference/keywords/interface.md) lze deklarovat [události](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="01cb3-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="01cb3-104">Následující příklad ukazuje, jak implementace událostí rozhraní ve třídě.</span><span class="sxs-lookup"><span data-stu-id="01cb3-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="01cb3-105">V podstatě pravidla jsou stejné jako při implementaci metody rozhraní ani vlastnost.</span><span class="sxs-lookup"><span data-stu-id="01cb3-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="01cb3-106">Implementace událostí rozhraní ve třídě</span><span class="sxs-lookup"><span data-stu-id="01cb3-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="01cb3-107">Deklarovat událost ve své třídě a následně ho vyvolat v příslušné oblasti.</span><span class="sxs-lookup"><span data-stu-id="01cb3-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="01cb3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="01cb3-108">Example</span></span>  
<span data-ttu-id="01cb3-109">Následující příklad ukazuje, jak zpracovat méně běžné situace, ve které vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní má událost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="01cb3-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="01cb3-110">V takovém případě je nutné zadat explicitní implementaci rozhraní pro nejméně jednu z událostí.</span><span class="sxs-lookup"><span data-stu-id="01cb3-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="01cb3-111">Při zápisu explicitní implementace rozhraní události, je nutné také napsat `add` a `remove` přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="01cb3-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="01cb3-112">Obvykle je poskytován kompilátorem, ale v tomto případě kompilátor nemůže poskytnout jim.</span><span class="sxs-lookup"><span data-stu-id="01cb3-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="01cb3-113">Poskytnutím vlastní přístupové objekty, můžete určit, zda dvě události představují stejnou událost ve své třídě, nebo jednotlivé události.</span><span class="sxs-lookup"><span data-stu-id="01cb3-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="01cb3-114">Například pokud události by měly být vyvolána v různých časech podle specifikace rozhraní, můžete přidružit každou událost samostatné implementaci ve své třídě.</span><span class="sxs-lookup"><span data-stu-id="01cb3-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="01cb3-115">V následujícím příkladu, předplatitelé určení, které `OnDraw` události se mu přetypováním tvar odkazu na buď `IShape` nebo `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="01cb3-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[WrapTwoInterfaceEvents](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs#everything)]
  
## <a name="see-also"></a><span data-ttu-id="01cb3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="01cb3-116">See Also</span></span>

- [<span data-ttu-id="01cb3-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="01cb3-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="01cb3-118">Události</span><span class="sxs-lookup"><span data-stu-id="01cb3-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="01cb3-119">Delegáti</span><span class="sxs-lookup"><span data-stu-id="01cb3-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="01cb3-120">Implementace explicitního rozhraní</span><span class="sxs-lookup"><span data-stu-id="01cb3-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
- [<span data-ttu-id="01cb3-121">Postupy: Vyvolávání událostí třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="01cb3-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
