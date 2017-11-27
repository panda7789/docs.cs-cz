---
title: "Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ff5fedeeaa427bb62991f9b406c167647dc376d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="c3f0d-102">Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c3f0d-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="c3f0d-103">Událost je zvláštní druh vícesměrového vysílání delegáta, který jde volat jenom z v rámci třídy, která je definována v.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="c3f0d-104">Kód klienta jako odběratel u události tím, že poskytuje odkaz na metodu, která by měla být volána, když je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="c3f0d-105">Tyto metody jsou přidány do seznamu vyvolání tohoto delegáta prostřednictvím přístupových objektů událostí, které se podobají vlastnost přístupové objekty, s tím rozdílem, že jsou pojmenované přístupových objektů událostí `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="c3f0d-106">Ve většině případů není nutné k poskytování vlastních přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="c3f0d-107">Pokud ve vašem kódu jsou zadány žádné vlastních přístupových objektů událostí, kompilátor je přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="c3f0d-108">V některých případech ale může mít poskytnout vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="c3f0d-109">V tomto tématu se zobrazí jeden takový případ [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="c3f0d-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3f0d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3f0d-110">Example</span></span>  
 <span data-ttu-id="c3f0d-111">Následující příklad ukazuje, jak implementovat vlastní přidávat a odebírat přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="c3f0d-112">I když můžete nahradit žádný kód uvnitř přístupy, doporučujeme vám, že zamknete událostí, než přidáte nebo odeberete nové metody obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="c3f0d-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="c3f0d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3f0d-113">See Also</span></span>  
 [<span data-ttu-id="c3f0d-114">Události</span><span class="sxs-lookup"><span data-stu-id="c3f0d-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="c3f0d-115">události</span><span class="sxs-lookup"><span data-stu-id="c3f0d-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)
