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
ms.openlocfilehash: 329060e0c53178a9320be9a7cdff492d69917782
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211251"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="ea12d-102">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea12d-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="ea12d-103">Obslužná rutina události je postup ve vašem kódu, který určuje, jaké akce se provádí při výskytu události, například když uživatel klikne na tlačítko nebo fronta zpráv přijme zprávu.</span><span class="sxs-lookup"><span data-stu-id="ea12d-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="ea12d-104">Při vyvolání události provádějí obslužné rutiny události nebo obslužných rutin, které obdrží událost.</span><span class="sxs-lookup"><span data-stu-id="ea12d-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="ea12d-105">Události je možné přiřadit k více obslužných rutin a metody, které zpracovávají konkrétní události je možné změnit dynamicky.</span><span class="sxs-lookup"><span data-stu-id="ea12d-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="ea12d-106">Můžete také použít Návrhář formulářů Windows v sadě Visual Studio pro vytváření obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="ea12d-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ea12d-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ea12d-107">In This Section</span></span>

 <span data-ttu-id="ea12d-108">[Přehled událostí](events-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="ea12d-108">[Events Overview](events-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="ea12d-109">Popisuje model událostí a roli delegátů.</span><span class="sxs-lookup"><span data-stu-id="ea12d-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="ea12d-110">[Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="ea12d-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="ea12d-111">Popisuje, jak zpracovávat události.</span><span class="sxs-lookup"><span data-stu-id="ea12d-111">Describes how to handle events.</span></span>

 <span data-ttu-id="ea12d-112">[Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="ea12d-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span></span>
 <span data-ttu-id="ea12d-113">Poskytuje pokyny pro dynamicky reagování na události systém nebo uživatel.</span><span class="sxs-lookup"><span data-stu-id="ea12d-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="ea12d-114">[Postupy: Připojení více událostí jedné obslužné rutině událostí ve Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="ea12d-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="ea12d-115">Poskytuje pokyny pro přiřazování stejné funkce pro více ovládacích prvků prostřednictvím událostí.</span><span class="sxs-lookup"><span data-stu-id="ea12d-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="ea12d-116">[Řazení událostí ve Windows Forms](order-of-events-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="ea12d-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="ea12d-117">Popisuje pořadí, ve kterém jsou vyvolány události v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ea12d-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="ea12d-118">[Postupy: Vytvoření s použitím obslužné rutiny události návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) popisuje způsob použití návrháře Windows Forms k vytvoření obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ea12d-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ea12d-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ea12d-119">Related Sections</span></span>

 <span data-ttu-id="ea12d-120">[Události](../../standard/events/index.md)\\</span><span class="sxs-lookup"><span data-stu-id="ea12d-120">[Events](../../standard/events/index.md)\\</span></span>
 <span data-ttu-id="ea12d-121">Obsahuje odkazy na témata o zpracování a generování událostí pomocí [!INCLUDE [dnprdnshort](../../../includes/dnprdnshort-md.md)\].</span><span class="sxs-lookup"><span data-stu-id="ea12d-121">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)\].</span></span>

 <span data-ttu-id="ea12d-122">[Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span><span class="sxs-lookup"><span data-stu-id="ea12d-122">[Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span></span>
 <span data-ttu-id="ea12d-123">Uvádí seznam běžných problémů, které mohou u obslužných rutin událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="ea12d-123">Lists common issues that occur with event handlers in inherited components.</span></span>
