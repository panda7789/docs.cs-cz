---
title: 'Postupy: Vyvolat události třídy Base v odvozených třídách – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: dd44460f04d628ea382a5bd95960c97ebd9c3ee5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590414"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="01710-102">Postupy: Vyvolat události třídy Base v odvozených třídách (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="01710-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="01710-103">Následující jednoduchý příklad ukazuje standardní způsob, jak deklarovat události v základní třídě tak, aby mohly být také vyvolány z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="01710-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="01710-104">Tento model se používá rozsáhle v model Windows Forms třídy v knihovně tříd .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="01710-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="01710-105">Když vytvoříte třídu, která může být použita jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou speciálním typem delegáta, který lze volat pouze z třídy, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="01710-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="01710-106">Odvozené třídy nemohou přímo vyvolat události, které jsou deklarovány v rámci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="01710-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="01710-107">I když v některých případech můžete chtít událost, která může být vyvolána pouze základní třídou, měla by tato odvozená třída umožňovat vyvolání událostí základní třídy.</span><span class="sxs-lookup"><span data-stu-id="01710-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="01710-108">K tomu můžete vytvořit chráněnou metodu vyvolání v základní třídě, která zabalí událost.</span><span class="sxs-lookup"><span data-stu-id="01710-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="01710-109">Voláním nebo přepsáním této metody vyvolání mohou odvozené třídy událost vyvolat nepřímo.</span><span class="sxs-lookup"><span data-stu-id="01710-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01710-110">Nedeklarujte virtuální události v základní třídě a přepište je v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="01710-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="01710-111">C# Kompilátor tyto správně nezpracovává a je nepředvídatelné, zda bude předplatitelem odvozené události ve skutečnosti přihlášena k odběru události základní třídy.</span><span class="sxs-lookup"><span data-stu-id="01710-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01710-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="01710-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01710-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01710-113">See also</span></span>

- [<span data-ttu-id="01710-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="01710-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="01710-115">Události</span><span class="sxs-lookup"><span data-stu-id="01710-115">Events</span></span>](./index.md)
- [<span data-ttu-id="01710-116">Delegáti</span><span class="sxs-lookup"><span data-stu-id="01710-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="01710-117">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="01710-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="01710-118">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01710-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
