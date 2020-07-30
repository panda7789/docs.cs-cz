---
title: Implementace vlastních přístupových objektů událostí – Průvodce programováním v C#
description: Naučte se implementovat vlastní přistupující objekty událostí. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4094aa1fedbceb68790b484608b3ea0ebc1e5cf6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302136"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="52248-104">Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="52248-104">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="52248-105">Událost je zvláštní druh delegáta vícesměrového vysílání, který lze volat pouze z třídy, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="52248-105">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="52248-106">Kód klienta se přihlašuje k odběru události tím, že poskytuje odkaz na metodu, která by měla být vyvolána při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="52248-106">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="52248-107">Tyto metody jsou přidány do seznamu volání delegáta prostřednictvím přístupových objektů, které se podobají přístupovým vlastnostem události, s tím rozdílem, že přistupující objekty události jsou pojmenované `add` a `remove` .</span><span class="sxs-lookup"><span data-stu-id="52248-107">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="52248-108">Ve většině případů nemusíte zadávat vlastní přistupující objekty události.</span><span class="sxs-lookup"><span data-stu-id="52248-108">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="52248-109">Nejsou-li v kódu zadány žádné vlastní přístupové objekty události, kompilátor je přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="52248-109">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="52248-110">V některých případech ale možná budete muset zadat vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="52248-110">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="52248-111">Takový případ je uveden v tématu [jak implementovat události rozhraní](./how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="52248-111">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="52248-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="52248-112">Example</span></span>  
 <span data-ttu-id="52248-113">Následující příklad ukazuje, jak implementovat vlastní přidávání a odebírání přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="52248-113">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="52248-114">I když v přístupových objektech můžete nahradit libovolný kód, doporučujeme před přidáním nebo odebráním nové metody obslužné rutiny události uzamknout událost.</span><span class="sxs-lookup"><span data-stu-id="52248-114">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="52248-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52248-115">See also</span></span>

- [<span data-ttu-id="52248-116">Události</span><span class="sxs-lookup"><span data-stu-id="52248-116">Events</span></span>](./index.md)
- [<span data-ttu-id="52248-117">událostí</span><span class="sxs-lookup"><span data-stu-id="52248-117">event</span></span>](../../language-reference/keywords/event.md)
