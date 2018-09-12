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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c6845a85f9d3e07a4ecc9aad1ec11df8cdbc1f7a
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493350"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="30aa6-102">Přihlášení k odběru událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="30aa6-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
>  <span data-ttu-id="30aa6-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="30aa6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="30aa6-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="30aa6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="30aa6-105">Toto téma ukazuje vytvoření odběru událostí vyvolaných zprostředkovatelů automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="30aa6-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30aa6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="30aa6-106">Example</span></span>  
 <span data-ttu-id="30aa6-107">Následující ukázkový kód Registruje obslužnou rutinu události pro událost, která se vyvolá, když ovládací prvek, jako je například tlačítko se vyvolá a odstraní ji zavře formulář přihlášky.</span><span class="sxs-lookup"><span data-stu-id="30aa6-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="30aa6-108">Událost je identifikována <xref:System.Windows.Automation.AutomationEvent> předán jako parametr <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="30aa6-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="30aa6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="30aa6-109">Example</span></span>  
 <span data-ttu-id="30aa6-110">Následující příklad ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k přihlásit k odběru události, která je vyvolána při změně fokusu.</span><span class="sxs-lookup"><span data-stu-id="30aa6-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="30aa6-111">Obslužná rutina události je Neregistrovaný kód v metodě, která může být volána při ukončení aplikace nebo oznámení o události uživatelského rozhraní se už nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="30aa6-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="30aa6-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="30aa6-112">See Also</span></span>  
 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>  
 [<span data-ttu-id="30aa6-113">Přehled událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="30aa6-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
