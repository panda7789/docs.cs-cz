---
title: 'Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 6d0181a93831fa054d7ba1a740bafe1f228bfc15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331146"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="f7aa2-102">Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f7aa2-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="f7aa2-103">Událost je zvláštní druh vícesměrového vysílání delegáta, který jde volat jenom z v rámci třídy, která je definována v.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="f7aa2-104">Kód klienta jako odběratel u události tím, že poskytuje odkaz na metodu, která by měla být volána, když je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="f7aa2-105">Tyto metody jsou přidány do seznamu vyvolání tohoto delegáta prostřednictvím přístupových objektů událostí, které se podobají vlastnost přístupové objekty, s tím rozdílem, že jsou pojmenované přístupových objektů událostí `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="f7aa2-106">Ve většině případů není nutné k poskytování vlastních přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="f7aa2-107">Pokud ve vašem kódu jsou zadány žádné vlastních přístupových objektů událostí, kompilátor je přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="f7aa2-108">V některých případech ale může mít poskytnout vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="f7aa2-109">V tomto tématu se zobrazí jeden takový případ [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="f7aa2-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7aa2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7aa2-110">Example</span></span>  
 <span data-ttu-id="f7aa2-111">Následující příklad ukazuje, jak implementovat vlastní přidávat a odebírat přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="f7aa2-112">I když můžete nahradit žádný kód uvnitř přístupy, doporučujeme vám, že zamknete událostí, než přidáte nebo odeberete nové metody obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="f7aa2-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
```csharp
event EventHandler IDrawingObject.OnDraw  
{  
    add  
    {  
        lock (PreDrawEvent)  
        {  
            PreDrawEvent += value;  
        }  
    }  
    remove  
    {  
        lock (PreDrawEvent)  
        {  
            PreDrawEvent -= value;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7aa2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7aa2-113">See Also</span></span>  
 [<span data-ttu-id="f7aa2-114">Události</span><span class="sxs-lookup"><span data-stu-id="f7aa2-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="f7aa2-115">event</span><span class="sxs-lookup"><span data-stu-id="f7aa2-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)