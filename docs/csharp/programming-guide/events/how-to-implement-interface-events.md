---
title: Postup implementace událostí rozhraní – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: cd2192d6146a431559f5cd9dd1a80da577695d66
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346342"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="25a2e-102">Postup implementace událostí rozhraní (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="25a2e-102">How to implement interface events (C# Programming Guide)</span></span>
<span data-ttu-id="25a2e-103">[Rozhraní](../../language-reference/keywords/interface.md) může deklarovat [událost](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="25a2e-103">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="25a2e-104">Následující příklad ukazuje, jak implementovat události rozhraní ve třídě.</span><span class="sxs-lookup"><span data-stu-id="25a2e-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="25a2e-105">Pravidla jsou v podstatě stejná jako při implementaci libovolné metody rozhraní nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="25a2e-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="25a2e-106">Implementace událostí rozhraní ve třídě</span><span class="sxs-lookup"><span data-stu-id="25a2e-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="25a2e-107">Deklarujete událost ve třídě a pak ji vyvolejte v příslušných oblastech.</span><span class="sxs-lookup"><span data-stu-id="25a2e-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="25a2e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="25a2e-108">Example</span></span>  
<span data-ttu-id="25a2e-109">Následující příklad ukazuje, jak zpracovat méně běžnou situaci, ve které vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní obsahuje událost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="25a2e-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="25a2e-110">V takovém případě je nutné zadat explicitní implementaci rozhraní alespoň pro jednu z událostí.</span><span class="sxs-lookup"><span data-stu-id="25a2e-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="25a2e-111">Když napíšete explicitní implementaci rozhraní pro událost, musíte také zapsat `add` a `remove` přistupující objekty události.</span><span class="sxs-lookup"><span data-stu-id="25a2e-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="25a2e-112">Tyto jsou obvykle poskytovány kompilátorem, ale v tomto případě je kompilátor nemůže poskytnout.</span><span class="sxs-lookup"><span data-stu-id="25a2e-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="25a2e-113">Poskytnutím vlastních přístupových objektů můžete určit, jestli jsou tyto dvě události reprezentované stejnou událostí ve vaší třídě, nebo různými událostmi.</span><span class="sxs-lookup"><span data-stu-id="25a2e-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="25a2e-114">Například pokud by události měly být vyvolány v různých časech podle specifikací rozhraní, můžete každou událost přidružit k samostatné implementaci ve vaší třídě.</span><span class="sxs-lookup"><span data-stu-id="25a2e-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="25a2e-115">V následujícím příkladu předplatitelé určují, které `OnDraw` události budou obdržet přetypováním odkazu na obrazec do `IShape` nebo `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="25a2e-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="25a2e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25a2e-116">See also</span></span>

- [<span data-ttu-id="25a2e-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="25a2e-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="25a2e-118">Události</span><span class="sxs-lookup"><span data-stu-id="25a2e-118">Events</span></span>](./index.md)
- [<span data-ttu-id="25a2e-119">Delegáti</span><span class="sxs-lookup"><span data-stu-id="25a2e-119">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="25a2e-120">Implementace explicitního rozhraní</span><span class="sxs-lookup"><span data-stu-id="25a2e-120">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="25a2e-121">Postup vyvolání událostí třídy Base v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="25a2e-121">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
