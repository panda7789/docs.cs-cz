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
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="40d94-102">Jak implementovat události rozhraní (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="40d94-102">How to implement interface events (C# Programming Guide)</span></span>
<span data-ttu-id="40d94-103">[Rozhraní](../../language-reference/keywords/interface.md) může deklarovat [událost](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="40d94-103">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="40d94-104">Následující příklad ukazuje, jak implementovat události rozhraní ve třídě.</span><span class="sxs-lookup"><span data-stu-id="40d94-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="40d94-105">V podstatě pravidla jsou stejné jako při implementaci jakékoli metody rozhraní nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="40d94-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="40d94-106">Implementace událostí rozhraní ve třídě</span><span class="sxs-lookup"><span data-stu-id="40d94-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="40d94-107">Deklarujte událost ve své třídě a pak ji vyvolat v příslušných oblastech.</span><span class="sxs-lookup"><span data-stu-id="40d94-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="40d94-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="40d94-108">Example</span></span>  
<span data-ttu-id="40d94-109">Následující příklad ukazuje, jak zpracovat méně časté situace, ve kterém vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní má událost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="40d94-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="40d94-110">V takovém případě je nutné zadat explicitní implementaci rozhraní alespoň pro jednu z událostí.</span><span class="sxs-lookup"><span data-stu-id="40d94-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="40d94-111">Při zápisu explicitní implementace rozhraní pro událost, `add` musíte `remove` také zapsat přístupové objekty a události.</span><span class="sxs-lookup"><span data-stu-id="40d94-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="40d94-112">Obvykle jsou poskytovány kompilátorem, ale v tomto případě kompilátor nemůže poskytnout.</span><span class="sxs-lookup"><span data-stu-id="40d94-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="40d94-113">Poskytnutím vlastních přístupových skupin můžete určit, zda jsou dvě události reprezentovány stejnou událostí ve vaší třídě nebo různými událostmi.</span><span class="sxs-lookup"><span data-stu-id="40d94-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="40d94-114">Například pokud události by měly být vyvolány v různých časech podle specifikace rozhraní, můžete přidružit každou událost se samostatnou implementaci ve vaší třídě.</span><span class="sxs-lookup"><span data-stu-id="40d94-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="40d94-115">V následujícím příkladu odběratelé `OnDraw` určit, které události obdrží přetypování odkazu na tvar `IShape` nebo `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="40d94-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="40d94-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="40d94-116">See also</span></span>

- [<span data-ttu-id="40d94-117">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40d94-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="40d94-118">Akce</span><span class="sxs-lookup"><span data-stu-id="40d94-118">Events</span></span>](./index.md)
- [<span data-ttu-id="40d94-119">Delegáty</span><span class="sxs-lookup"><span data-stu-id="40d94-119">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="40d94-120">Implementace explicitního rozhraní</span><span class="sxs-lookup"><span data-stu-id="40d94-120">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="40d94-121">Jak vyvolávat události základní třídy v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="40d94-121">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
