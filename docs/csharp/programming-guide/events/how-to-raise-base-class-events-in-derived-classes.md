---
title: 'Postupy: Vyvolávání událostí třídy Base v odvozených třídách - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: bc968ea9c6f60ea6efda807bf254f595c61f8d4a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976080"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="49b54-102">Postupy: Vyvolávání událostí třídy Base v odvozených třídách (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="49b54-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="49b54-103">Následující jednoduchý příklad ukazuje standardní způsob pro deklaraci události v základní třídě tak, aby se také mohou být vyvolány z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="49b54-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="49b54-104">Tento model je často používána ve Windows Forms třídy v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="49b54-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="49b54-105">Když vytváříte třídu, která slouží jako základní třída pro jiné třídy, měli byste zvážit vzhledem k tomu, že události mají speciální typ delegáta, který lze vyvolat pouze z v rámci třídy, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="49b54-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="49b54-106">Odvozené třídy nelze přímo vyvolat události, které jsou deklarovány v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="49b54-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="49b54-107">I když v některých případech může být vhodné událost, která může být vyvolána pouze základní třídy, ve většině případů, měli byste povolit odvozené třídy, která se má vyvolat události základní třídy.</span><span class="sxs-lookup"><span data-stu-id="49b54-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="49b54-108">K tomuto účelu můžete vytvořit chráněné vyvolání metody základní třídy, která obaluje události.</span><span class="sxs-lookup"><span data-stu-id="49b54-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="49b54-109">Při volání nebo potlačení této vyvolání metody, mohou odvozené třídy vyvolat událost nepřímo.</span><span class="sxs-lookup"><span data-stu-id="49b54-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49b54-110">Nezadávejte deklarování virtuálních událostí v základní třídě a přepsat v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="49b54-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="49b54-111">Kompilátor jazyka C# nezpracovává tyto správně a zda předplatiteli odvozené událostí bude ve skutečnosti se přihlášení k odběru události základní třídy nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="49b54-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49b54-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="49b54-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="49b54-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49b54-113">See also</span></span>

- [<span data-ttu-id="49b54-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="49b54-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="49b54-115">Události</span><span class="sxs-lookup"><span data-stu-id="49b54-115">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="49b54-116">Delegáti</span><span class="sxs-lookup"><span data-stu-id="49b54-116">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="49b54-117">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="49b54-117">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="49b54-118">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49b54-118">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
