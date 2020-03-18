---
title: Jak implementovat vlastní přístupové objekty událostí – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705350"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="0ee8d-102">Jak implementovat vlastní přístupové objekty událostí (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0ee8d-102">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="0ee8d-103">Událost je zvláštní druh delegáta vícesměrového vysílání, který lze vyvolat pouze z třídy, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="0ee8d-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="0ee8d-104">Klientský kód se přihlásí k události tím, že poskytuje odkaz na metodu, která by měla být vyvolána při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="0ee8d-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="0ee8d-105">Tyto metody jsou přidány do seznamu vyvolání delegáta prostřednictvím přístupových objektů událostí, které se `add` `remove`podobají přistupující objekty vlastností, s tím rozdílem, že přístupové objekty události jsou pojmenovány a .</span><span class="sxs-lookup"><span data-stu-id="0ee8d-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="0ee8d-106">Ve většině případů není třeba zadat vlastní přístupové objekty událostí.</span><span class="sxs-lookup"><span data-stu-id="0ee8d-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="0ee8d-107">Pokud jsou ve vašem kódu zadány žádné vlastní přístupové objekty událostí, kompilátor je přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="0ee8d-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="0ee8d-108">V některých případech však bude pravděpodobně muset poskytnout vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="0ee8d-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="0ee8d-109">Jeden takový případ je uveden v tématu [Jak implementovat události rozhraní](./how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="0ee8d-109">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0ee8d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ee8d-110">Example</span></span>  
 <span data-ttu-id="0ee8d-111">Následující příklad ukazuje, jak implementovat vlastní přistupující a odebrané přistupovače událostí.</span><span class="sxs-lookup"><span data-stu-id="0ee8d-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="0ee8d-112">Přestože můžete nahradit libovolný kód uvnitř přistupujících operátorů, doporučujeme zamknout událost před přidáním nebo odebráním nové metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0ee8d-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="0ee8d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ee8d-113">See also</span></span>

- [<span data-ttu-id="0ee8d-114">Akce</span><span class="sxs-lookup"><span data-stu-id="0ee8d-114">Events</span></span>](./index.md)
- [<span data-ttu-id="0ee8d-115">Událost</span><span class="sxs-lookup"><span data-stu-id="0ee8d-115">event</span></span>](../../language-reference/keywords/event.md)
