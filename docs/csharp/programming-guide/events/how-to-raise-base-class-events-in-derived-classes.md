---
title: Postup vyvolání událostí třídy Base v odvozených třídách – Průvodce programováním v C#
description: Přečtěte si, jak vyvolávat události třídy Base v odvozených třídách. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: b0b0a16a1fd165e437fc79ccacb20d406f5cff63
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302097"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="2536d-104">Postup vyvolání událostí třídy Base v odvozených třídách (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2536d-104">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="2536d-105">Následující jednoduchý příklad ukazuje standardní způsob, jak deklarovat události v základní třídě tak, aby mohly být také vyvolány z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="2536d-105">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="2536d-106">Tento model se používá rozsáhle v model Windows Forms třídy v knihovnách tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="2536d-106">This pattern is used extensively in Windows Forms classes in the .NET class libraries.</span></span>  
  
 <span data-ttu-id="2536d-107">Když vytvoříte třídu, která může být použita jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou speciálním typem delegáta, který lze volat pouze z třídy, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="2536d-107">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="2536d-108">Odvozené třídy nemohou přímo vyvolat události, které jsou deklarovány v rámci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2536d-108">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="2536d-109">I když v některých případech můžete chtít událost, která může být vyvolána pouze základní třídou, měla by tato odvozená třída umožňovat vyvolání událostí základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2536d-109">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="2536d-110">K tomu můžete vytvořit chráněnou metodu vyvolání v základní třídě, která zabalí událost.</span><span class="sxs-lookup"><span data-stu-id="2536d-110">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="2536d-111">Voláním nebo přepsáním této metody vyvolání mohou odvozené třídy událost vyvolat nepřímo.</span><span class="sxs-lookup"><span data-stu-id="2536d-111">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2536d-112">Nedeklarujte virtuální události v základní třídě a přepište je v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="2536d-112">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="2536d-113">Kompilátor jazyka C# tyto správně nezpracovává a je nepředvídatelné, zda bude předplatitelem odvozené události ve skutečnosti přihlášena k odběru události základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2536d-113">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2536d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2536d-114">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2536d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2536d-115">See also</span></span>

- [<span data-ttu-id="2536d-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2536d-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2536d-117">Události</span><span class="sxs-lookup"><span data-stu-id="2536d-117">Events</span></span>](./index.md)
- [<span data-ttu-id="2536d-118">Delegáti</span><span class="sxs-lookup"><span data-stu-id="2536d-118">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="2536d-119">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="2536d-119">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="2536d-120">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2536d-120">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
