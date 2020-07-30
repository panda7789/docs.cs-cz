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
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="87970-104">Postup implementace událostí rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="87970-104">How to implement interface events (C# Programming Guide)</span></span>
<span data-ttu-id="87970-105">[Rozhraní](../../language-reference/keywords/interface.md) může deklarovat [událost](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="87970-105">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="87970-106">Následující příklad ukazuje, jak implementovat události rozhraní ve třídě.</span><span class="sxs-lookup"><span data-stu-id="87970-106">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="87970-107">Pravidla jsou v podstatě stejná jako při implementaci libovolné metody rozhraní nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="87970-107">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="87970-108">Implementace událostí rozhraní ve třídě</span><span class="sxs-lookup"><span data-stu-id="87970-108">To implement interface events in a class</span></span>  
  
<span data-ttu-id="87970-109">Deklarujete událost ve třídě a pak ji vyvolejte v příslušných oblastech.</span><span class="sxs-lookup"><span data-stu-id="87970-109">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="87970-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="87970-110">Example</span></span>  
<span data-ttu-id="87970-111">Následující příklad ukazuje, jak zpracovat méně běžnou situaci, ve které vaše třída dědí ze dvou nebo více rozhraní a každé rozhraní obsahuje událost se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="87970-111">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="87970-112">V takovém případě je nutné zadat explicitní implementaci rozhraní alespoň pro jednu z událostí.</span><span class="sxs-lookup"><span data-stu-id="87970-112">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="87970-113">Když napíšete explicitní implementaci rozhraní pro událost, musíte také napsat `add` `remove` přístupové objekty události a.</span><span class="sxs-lookup"><span data-stu-id="87970-113">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="87970-114">Tyto jsou obvykle poskytovány kompilátorem, ale v tomto případě je kompilátor nemůže poskytnout.</span><span class="sxs-lookup"><span data-stu-id="87970-114">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="87970-115">Poskytnutím vlastních přístupových objektů můžete určit, jestli jsou tyto dvě události reprezentované stejnou událostí ve vaší třídě, nebo různými událostmi.</span><span class="sxs-lookup"><span data-stu-id="87970-115">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="87970-116">Například pokud by události měly být vyvolány v různých časech podle specifikací rozhraní, můžete každou událost přidružit k samostatné implementaci ve vaší třídě.</span><span class="sxs-lookup"><span data-stu-id="87970-116">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="87970-117">V následujícím příkladu předplatitelé určují, která `OnDraw` událost bude přijímat přetypováním odkazu na obrazec do `IShape` nebo `IDrawingObject` .</span><span class="sxs-lookup"><span data-stu-id="87970-117">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="87970-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87970-118">See also</span></span>

- [<span data-ttu-id="87970-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="87970-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="87970-120">Události</span><span class="sxs-lookup"><span data-stu-id="87970-120">Events</span></span>](./index.md)
- [<span data-ttu-id="87970-121">Delegáti</span><span class="sxs-lookup"><span data-stu-id="87970-121">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="87970-122">Implementace explicitního rozhraní</span><span class="sxs-lookup"><span data-stu-id="87970-122">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="87970-123">Jak vyvolávat události základní třídy v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="87970-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
