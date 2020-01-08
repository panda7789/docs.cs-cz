---
title: Postup vyvolání událostí třídy Base v odvozených třídách C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 6176b94b15edccb139ddd7de3101930b505d98a8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346296"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="8b9c4-102">Postup vyvolání událostí třídy Base v odvozených třídáchC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8b9c4-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="8b9c4-103">Následující jednoduchý příklad ukazuje standardní způsob, jak deklarovat události v základní třídě tak, aby mohly být také vyvolány z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="8b9c4-104">Tento model se používá rozsáhle v model Windows Forms třídy v knihovně tříd .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="8b9c4-105">Když vytvoříte třídu, která může být použita jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou speciálním typem delegáta, který lze volat pouze z třídy, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="8b9c4-106">Odvozené třídy nemohou přímo vyvolat události, které jsou deklarovány v rámci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="8b9c4-107">I když v některých případech můžete chtít událost, která může být vyvolána pouze základní třídou, měla by tato odvozená třída umožňovat vyvolání událostí základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="8b9c4-108">K tomu můžete vytvořit chráněnou metodu vyvolání v základní třídě, která zabalí událost.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="8b9c4-109">Voláním nebo přepsáním této metody vyvolání mohou odvozené třídy událost vyvolat nepřímo.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b9c4-110">Nedeklarujte virtuální události v základní třídě a přepište je v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="8b9c4-111">C# Kompilátor tyto správně nezpracovává a je nepředvídatelné, zda bude předplatitelem odvozené události ve skutečnosti přihlášena k odběru události základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8b9c4-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b9c4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b9c4-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8b9c4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b9c4-113">See also</span></span>

- [<span data-ttu-id="8b9c4-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8b9c4-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8b9c4-115">Události</span><span class="sxs-lookup"><span data-stu-id="8b9c4-115">Events</span></span>](./index.md)
- [<span data-ttu-id="8b9c4-116">Delegáti</span><span class="sxs-lookup"><span data-stu-id="8b9c4-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="8b9c4-117">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="8b9c4-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="8b9c4-118">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b9c4-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
