---
title: Přihlášení k odběru událostí automatizace uživatelského rozhraní
description: Podívejte se, jak se přihlásit k odběru událostí vyvolaných zprostředkovateli automatizace uživatelského rozhraní. Vzorový kód Registruje obslužnou rutinu události pro událost vyvolanou při vyvolání ovládacího prvku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: 8f456702657c70837c6137e3e60335110361bcd9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163530"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="cfdaa-104">Přihlášení k odběru událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfdaa-104">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="cfdaa-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cfdaa-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cfdaa-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cfdaa-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cfdaa-107">Toto téma ukazuje, jak se přihlásit k odběru událostí vyvolaných zprostředkovateli automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cfdaa-107">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfdaa-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cfdaa-108">Example</span></span>  
 <span data-ttu-id="cfdaa-109">Následující příklad kódu zaregistruje obslužnou rutinu události pro událost, která je vyvolána při vyvolání ovládacího prvku, jako je například tlačítko, a odstraní jej při zavření formuláře aplikace.</span><span class="sxs-lookup"><span data-stu-id="cfdaa-109">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="cfdaa-110">Událost je identifikována <xref:System.Windows.Automation.AutomationEvent> předaným jako parametr do <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> .</span><span class="sxs-lookup"><span data-stu-id="cfdaa-110">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="cfdaa-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="cfdaa-111">Example</span></span>  
 <span data-ttu-id="cfdaa-112">Následující příklad ukazuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k přihlášení k odběru události, která je vyvolána při změně fokusu.</span><span class="sxs-lookup"><span data-stu-id="cfdaa-112">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="cfdaa-113">Obslužná rutina události je odregistrována v metodě, která by mohla být volána při vypnutí aplikace, nebo v případě, že již není vyžadováno oznámení událostí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cfdaa-113">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="cfdaa-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfdaa-114">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="cfdaa-115">Přehled událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfdaa-115">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
