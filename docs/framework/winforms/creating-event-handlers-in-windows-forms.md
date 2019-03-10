---
title: Vytváření obslužných rutin událostí ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: f969769725ae099ddf477fd11efb03277a555fa6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716865"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="36bd5-102">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36bd5-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="36bd5-103">Obslužná rutina události je postup ve vašem kódu, který určuje, jaké akce se provádí při výskytu události, například když uživatel klikne na tlačítko nebo fronta zpráv přijme zprávu.</span><span class="sxs-lookup"><span data-stu-id="36bd5-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="36bd5-104">Při vyvolání události provádějí obslužné rutiny události nebo obslužných rutin, které obdrží událost.</span><span class="sxs-lookup"><span data-stu-id="36bd5-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="36bd5-105">Události je možné přiřadit k více obslužných rutin a metody, které zpracovávají konkrétní události je možné změnit dynamicky.</span><span class="sxs-lookup"><span data-stu-id="36bd5-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="36bd5-106">Návrhář formulářů Windows můžete také použít k vytvoření obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="36bd5-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36bd5-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="36bd5-107">In This Section</span></span>  
 [<span data-ttu-id="36bd5-108">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="36bd5-108">Events Overview</span></span>](events-overview-windows-forms.md)  
 <span data-ttu-id="36bd5-109">Popisuje model událostí a roli delegátů.</span><span class="sxs-lookup"><span data-stu-id="36bd5-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="36bd5-110">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="36bd5-110">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="36bd5-111">Popisuje, jak zpracovávat události.</span><span class="sxs-lookup"><span data-stu-id="36bd5-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="36bd5-112">Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36bd5-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="36bd5-113">Poskytuje pokyny pro dynamicky reagování na události systém nebo uživatel.</span><span class="sxs-lookup"><span data-stu-id="36bd5-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="36bd5-114">Postupy: Připojení více událostí jedné obslužné rutině událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36bd5-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="36bd5-115">Poskytuje pokyny pro přiřazování stejné funkce pro více ovládacích prvků prostřednictvím událostí.</span><span class="sxs-lookup"><span data-stu-id="36bd5-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="36bd5-116">Řazení událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36bd5-116">Order of Events in Windows Forms</span></span>](order-of-events-in-windows-forms.md)  
 <span data-ttu-id="36bd5-117">Popisuje pořadí, ve kterém jsou vyvolány události v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="36bd5-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 <span data-ttu-id="36bd5-118">[Postupy: Vytváření obslužných rutin událostí pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="36bd5-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))</span></span>  
 <span data-ttu-id="36bd5-119">Popisuje způsob použití návrháře Windows Forms k vytvoření obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="36bd5-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="36bd5-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="36bd5-120">Related Sections</span></span>  
 [<span data-ttu-id="36bd5-121">Události</span><span class="sxs-lookup"><span data-stu-id="36bd5-121">Events</span></span>](../../standard/events/index.md)  
 <span data-ttu-id="36bd5-122">Obsahuje odkazy na témata o zpracování a generování událostí pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="36bd5-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="36bd5-123">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36bd5-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="36bd5-124">Uvádí seznam běžných problémů, které mohou u obslužných rutin událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="36bd5-124">Lists common issues that occur with event handlers in inherited components.</span></span>
