---
title: Jak zvýšit události základní třídy v odvozených třídách - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712322"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="6f580-102">Jak zvýšit události základní třídy v odvozených třídách (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6f580-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="6f580-103">Následující jednoduchý příklad ukazuje standardní způsob deklarování událostí v základní třídě tak, aby mohly být také vyvolány z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="6f580-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="6f580-104">Tento vzor se používá ve velké míře ve třídách Windows Forms v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f580-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="6f580-105">Při vytváření třídy, která může být použita jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou zvláštní typ delegáta, který lze vyvolat pouze z třídy, která je deklarovala.</span><span class="sxs-lookup"><span data-stu-id="6f580-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="6f580-106">Odvozené třídy nelze přímo vyvolat události, které jsou deklarovány v rámci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6f580-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="6f580-107">I když někdy můžete chtít událost, která může být vyvolána pouze základní třídy, většinu času, měli byste povolit odvozené třídy vyvolat události základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6f580-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="6f580-108">Chcete-li to provést, můžete vytvořit chráněnou metodu vyvolání v základní třídě, která zabalí událost.</span><span class="sxs-lookup"><span data-stu-id="6f580-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="6f580-109">Voláním nebo přepsáním této metody vyvolání mohou odvozené třídy vyvolat událost nepřímo.</span><span class="sxs-lookup"><span data-stu-id="6f580-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f580-110">Nedeklarujte virtuální události v základní třídě a přepsat je v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="6f580-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="6f580-111">Kompilátor Jazyka C# nezpracovává tyto správně a je nepředvídatelné, zda odběratel odvozené události bude skutečně přihlášení k odběru události základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6f580-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f580-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f580-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6f580-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f580-113">See also</span></span>

- [<span data-ttu-id="6f580-114">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6f580-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6f580-115">Akce</span><span class="sxs-lookup"><span data-stu-id="6f580-115">Events</span></span>](./index.md)
- [<span data-ttu-id="6f580-116">Delegáty</span><span class="sxs-lookup"><span data-stu-id="6f580-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="6f580-117">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="6f580-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="6f580-118">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6f580-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
