---
title: "Vytváření obslužných rutin událostí ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0625d5272b4c3ae4f21793d0b0fc8645158e6a2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="d3290-102">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3290-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="d3290-103">Obslužné rutiny události je procedura ve vašem kódu, který určuje, jaké akce provede, když dojde k události, například když uživatel klikne na tlačítko nebo fronta zpráv přijme nějakou zprávu.</span><span class="sxs-lookup"><span data-stu-id="d3290-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="d3290-104">Pokud se vyvolá událost, jsou spustit obslužnou rutinu události nebo obslužné rutiny, které přijímají události.</span><span class="sxs-lookup"><span data-stu-id="d3290-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="d3290-105">Události lze přiřadit k více obslužných rutin a metody, které zpracovávají konkrétní události lze změnit dynamicky.</span><span class="sxs-lookup"><span data-stu-id="d3290-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="d3290-106">Návrhář formulářů Windows můžete také použít k vytvoření obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="d3290-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3290-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d3290-107">In This Section</span></span>  
 [<span data-ttu-id="d3290-108">Přehled událostí</span><span class="sxs-lookup"><span data-stu-id="d3290-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="d3290-109">Popisuje model událostí a roli delegáti.</span><span class="sxs-lookup"><span data-stu-id="d3290-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="d3290-110">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="d3290-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="d3290-111">Popisuje postup zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="d3290-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="d3290-112">Postupy: vytváření obslužných rutin událostí v době běhu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3290-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="d3290-113">Poskytuje pokyny pro dynamicky reagování na události systému nebo uživatele.</span><span class="sxs-lookup"><span data-stu-id="d3290-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="d3290-114">Postupy: připojení více událostí k jedné obslužné rutině událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3290-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="d3290-115">Poskytuje pokyny pro přiřazení k více ovládacích prvků prostřednictvím událostí stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="d3290-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="d3290-116">Pořadí událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3290-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="d3290-117">Popisuje pořadí, ve kterém jsou vyvolány události v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3290-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="d3290-118">Postupy: vytváření obslužných rutin událostí pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d3290-118">How to: Create Event Handlers Using the Designer</span></span>](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="d3290-119">Popisuje, jak používat návrhář formulářů Windows k vytváření obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="d3290-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d3290-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d3290-120">Related Sections</span></span>  
 [<span data-ttu-id="d3290-121">Události</span><span class="sxs-lookup"><span data-stu-id="d3290-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="d3290-122">Obsahuje odkazy na témata o zpracování a generování událostí pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3290-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="d3290-123">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3290-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="d3290-124">Jsou uvedeny běžné problémy, ke kterým dochází u obslužné rutiny událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="d3290-124">Lists common issues that occur with event handlers in inherited components.</span></span>
