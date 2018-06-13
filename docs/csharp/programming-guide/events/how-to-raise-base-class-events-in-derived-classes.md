---
title: 'Postupy: Vyvolávání událostí třídy Base v odvozených třídách (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: e064c318f16c2fe87aa980b7dec7468b1e61ab25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320089"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="5855c-102">Postupy: Vyvolávání událostí třídy Base v odvozených třídách (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5855c-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="5855c-103">Následující jednoduchý příklad ukazuje standardní způsob deklarace události v základní třídě tak, aby se mohou být vyvolány z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="5855c-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="5855c-104">Tento vzor je často používány v třídách Windows Forms v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="5855c-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="5855c-105">Když vytváříte třídu, která lze použít jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou zvláštním typem delegáta, který jde volat jenom z v rámci třídy, který je deklarován.</span><span class="sxs-lookup"><span data-stu-id="5855c-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="5855c-106">Odvozené třídy nemohou vyvolat přímo události, které jsou deklarované v rámci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5855c-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="5855c-107">I když můžete někdy událost, která mohou být vyvolány pouze v základní třídě, ve většině případů, měli byste povolit odvozené třídy k vyvolání události základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5855c-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="5855c-108">K tomuto účelu můžete vytvořit chráněnou volajícím metodu v základní třídě, která zabalí události.</span><span class="sxs-lookup"><span data-stu-id="5855c-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="5855c-109">Volání metody nebo potlačení této metody volajícím, odvozené třídy vyvolat událost nepřímo.</span><span class="sxs-lookup"><span data-stu-id="5855c-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5855c-110">Nezadávejte deklarovat virtuálních událostí v základní třídě a jejich přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="5855c-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="5855c-111">Kompilátor jazyka C# nezpracovává tyto správně a zda odběratele odvozené události bude ve skutečnosti se přihlášení k odběru událostí – základní třída nepředvídatelným.</span><span class="sxs-lookup"><span data-stu-id="5855c-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5855c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5855c-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5855c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5855c-113">See Also</span></span>  
 [<span data-ttu-id="5855c-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5855c-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5855c-115">Události</span><span class="sxs-lookup"><span data-stu-id="5855c-115">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="5855c-116">Delegáti</span><span class="sxs-lookup"><span data-stu-id="5855c-116">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="5855c-117">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="5855c-117">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="5855c-118">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5855c-118">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
