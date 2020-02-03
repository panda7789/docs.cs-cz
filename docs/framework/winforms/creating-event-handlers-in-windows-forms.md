---
title: Vytváření obslužných rutin událostí
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 90acb3c7691acbcb528ae66692af67c2fb28eeaf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742330"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="96c70-102">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96c70-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="96c70-103">Obslužná rutina události je procedura v kódu, který určuje, jaké akce se provádějí při výskytu události, například když uživatel klikne na tlačítko nebo když fronta zpráv obdrží zprávu.</span><span class="sxs-lookup"><span data-stu-id="96c70-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="96c70-104">Při vyvolání události se spustí obslužná rutina události nebo obslužné rutiny, které obdrží událost.</span><span class="sxs-lookup"><span data-stu-id="96c70-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="96c70-105">Události lze přiřadit více obslužným rutinám a metody, které zpracovávají konkrétní události, mohou být dynamicky změněny.</span><span class="sxs-lookup"><span data-stu-id="96c70-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="96c70-106">Můžete také použít Návrhář formulářů v aplikaci Visual Studio k vytváření obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="96c70-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="96c70-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="96c70-107">In This Section</span></span>

 <span data-ttu-id="96c70-108">[Přehled událostí](events-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="96c70-108">[Events Overview](events-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="96c70-109">Vysvětluje model událostí a roli delegátů.</span><span class="sxs-lookup"><span data-stu-id="96c70-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="96c70-110">[Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="96c70-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="96c70-111">Popisuje, jak zpracovávat události.</span><span class="sxs-lookup"><span data-stu-id="96c70-111">Describes how to handle events.</span></span>

 <span data-ttu-id="96c70-112">[Postupy: vytváření obslužných rutin událostí v době běhu pro model Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="96c70-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span></span>\
 <span data-ttu-id="96c70-113">Poskytuje pokyny k dynamické reakci na události systému nebo uživatele.</span><span class="sxs-lookup"><span data-stu-id="96c70-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="96c70-114">[Postupy: připojení více událostí k jedné obslužné rutině události v model Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="96c70-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span></span>\
 <span data-ttu-id="96c70-115">Poskytuje pokyny pro přiřazení stejné funkce více ovládacím prvkům prostřednictvím událostí.</span><span class="sxs-lookup"><span data-stu-id="96c70-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="96c70-116">[Pořadí událostí v model Windows Forms](order-of-events-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="96c70-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)</span></span>\
 <span data-ttu-id="96c70-117">Popisuje pořadí, ve kterém jsou události vyvolány v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="96c70-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="96c70-118">[Postupy: vytváření obslužných rutin událostí pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Popisuje, jak použít Návrhář formulářů k vytváření obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="96c70-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="96c70-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="96c70-119">Related Sections</span></span>

 <span data-ttu-id="96c70-120">[Události](../../standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="96c70-120">[Events](../../standard/events/index.md)</span></span>\
 <span data-ttu-id="96c70-121">Obsahuje odkazy na témata týkající se zpracování a vyvolávání událostí pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96c70-121">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="96c70-122">[Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="96c70-122">[Troubleshooting Inherited Event Handlers in Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span></span>\
 <span data-ttu-id="96c70-123">Obsahuje seznam běžných problémů, ke kterým dochází u obslužných rutin událostí ve zděděných součástech.</span><span class="sxs-lookup"><span data-stu-id="96c70-123">Lists common issues that occur with event handlers in inherited components.</span></span>
