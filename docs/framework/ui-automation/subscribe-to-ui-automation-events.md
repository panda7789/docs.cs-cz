---
title: Přihlášení k odběru událostí automatizace uživatelského rozhraní
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
ms.openlocfilehash: a5effd1d7a3cfaba5e068087b3008903e58b6739
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432988"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="e19fa-102">Přihlášení k odběru událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e19fa-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="e19fa-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e19fa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e19fa-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e19fa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e19fa-105">Toto téma ukazuje, jak se přihlásit k odběru událostí vyvolaných zprostředkovateli automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e19fa-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e19fa-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e19fa-106">Example</span></span>  
 <span data-ttu-id="e19fa-107">Následující příklad kódu zaregistruje obslužnou rutinu události pro událost, která je vyvolána při vyvolání ovládacího prvku, jako je například tlačítko, a odstraní jej při zavření formuláře aplikace.</span><span class="sxs-lookup"><span data-stu-id="e19fa-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="e19fa-108">Událost je identifikována <xref:System.Windows.Automation.AutomationEvent> předaná jako parametr pro <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="e19fa-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="e19fa-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e19fa-109">Example</span></span>  
 <span data-ttu-id="e19fa-110">Následující příklad ukazuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k přihlášení k odběru události, která je vyvolána v případě změny fokusu.</span><span class="sxs-lookup"><span data-stu-id="e19fa-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="e19fa-111">Obslužná rutina události je odregistrována v metodě, která by mohla být volána při vypnutí aplikace, nebo v případě, že již není vyžadováno oznámení událostí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e19fa-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="e19fa-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e19fa-112">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="e19fa-113">Přehled událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e19fa-113">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
