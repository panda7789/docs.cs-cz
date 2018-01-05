---
title: "Přihlášení k odběru událostí automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 688ec0ba33b018eaba2f7293127c3869fcf5df48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="bd413-102">Přihlášení k odběru událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd413-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
>  <span data-ttu-id="bd413-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bd413-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bd413-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bd413-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bd413-105">Toto téma ukazuje, jak k odběru události vyvolané službou zprostředkovatelů automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd413-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd413-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd413-106">Example</span></span>  
 <span data-ttu-id="bd413-107">Následující příklad kódu zaregistruje obslužné rutiny události pro událost, která se vyvolá, když ovládací prvek tlačítko je vyvolána a odstraní ji zavře formulář žádosti.</span><span class="sxs-lookup"><span data-stu-id="bd413-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="bd413-108">Událost je identifikována <xref:System.Windows.Automation.AutomationEvent> předány jako parametr, který se <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd413-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="bd413-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd413-109">Example</span></span>  
 <span data-ttu-id="bd413-110">Následující příklad ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k odběru na událost, která se vyvolá, když se změní fokus.</span><span class="sxs-lookup"><span data-stu-id="bd413-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="bd413-111">Obslužné rutiny události je odhlásil v metodu, která může být volána při ukončení aplikace, nebo když oznámení událostí uživatelského rozhraní, které se už nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="bd413-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="bd413-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd413-112">See Also</span></span>  
 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>  
 [<span data-ttu-id="bd413-113">Přehled událostí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd413-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
