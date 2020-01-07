---
title: Implementace vlastních přístupových objektů událostí – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: af44b88ddd0e34f9dfd0b56718b5bc7241ef5d03
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635454"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="7c7bc-102">Implementace vlastních přístupových objektů událostí (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="7c7bc-102">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="7c7bc-103">Událost je zvláštní druh delegáta vícesměrového vysílání, který lze volat pouze z třídy, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="7c7bc-104">Kód klienta se přihlašuje k odběru události tím, že poskytuje odkaz na metodu, která by měla být vyvolána při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="7c7bc-105">Tyto metody se přidají do seznamu volání delegáta prostřednictvím přístupových objektů události, které se podobají přístupovým vlastnostem události s tím rozdílem, že přístupové objekty událostí jsou pojmenované `add` a `remove`.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="7c7bc-106">Ve většině případů nemusíte zadávat vlastní přistupující objekty události.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="7c7bc-107">Nejsou-li v kódu zadány žádné vlastní přístupové objekty události, kompilátor je přidá automaticky.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="7c7bc-108">V některých případech ale možná budete muset zadat vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="7c7bc-109">Takový případ je uveden v tématu [jak implementovat události rozhraní](./how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="7c7bc-109">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="7c7bc-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c7bc-110">Example</span></span>  
 <span data-ttu-id="7c7bc-111">Následující příklad ukazuje, jak implementovat vlastní přidávání a odebírání přístupových objektů událostí.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="7c7bc-112">I když v přístupových objektech můžete nahradit libovolný kód, doporučujeme před přidáním nebo odebráním nové metody obslužné rutiny události uzamknout událost.</span><span class="sxs-lookup"><span data-stu-id="7c7bc-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="7c7bc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c7bc-113">See also</span></span>

- [<span data-ttu-id="7c7bc-114">Události</span><span class="sxs-lookup"><span data-stu-id="7c7bc-114">Events</span></span>](./index.md)
- [<span data-ttu-id="7c7bc-115">event</span><span class="sxs-lookup"><span data-stu-id="7c7bc-115">event</span></span>](../../language-reference/keywords/event.md)
