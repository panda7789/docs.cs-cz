---
title: "Potíže s vlákny při automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
caps.latest.revision: "9"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: a1eaed2a7876c6e6981e7cc4172442b19800586b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-threading-issues"></a><span data-ttu-id="2e68e-102">Potíže s vlákny při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e68e-102">UI Automation Threading Issues</span></span>
> [!NOTE]
>  <span data-ttu-id="2e68e-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2e68e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2e68e-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="2e68e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="2e68e-105">Z důvodu způsob [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] používá zpráv systému Windows, je v konfliktu může dojít, když klientské aplikace pokusí o interakci s vlastním [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2e68e-105">Because of the way [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uses Windows messages, conflicts can occur when a client application attempts to interact with its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] on the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="2e68e-106">Tyto konflikty může vést k velmi nízký výkon nebo i způsobit, že aplikace přestane reagovat.</span><span class="sxs-lookup"><span data-stu-id="2e68e-106">These conflicts can lead to very slow performance or even cause the application to stop responding.</span></span>  
  
 <span data-ttu-id="2e68e-107">Pokud klientské aplikace slouží k interakci se všechny elementy na ploše, včetně vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], měli byste si všechny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volání na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="2e68e-107">If your client application is intended to interact with all elements on the desktop, including its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you should make all [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls on a separate thread.</span></span> <span data-ttu-id="2e68e-108">To zahrnuje vyhledání elementy (například pomocí <xref:System.Windows.Automation.TreeWalker> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metoda) a pomocí vzorů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2e68e-108">This includes locating elements (for example, by using <xref:System.Windows.Automation.TreeWalker> or the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method) and using control patterns.</span></span>  
  
 <span data-ttu-id="2e68e-109">Je bezpečné, aby [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volá v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obslužné rutiny události, protože obslužná rutina události je volána vždy na jinou hodnotu než[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2e68e-109">It is safe to make [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event handler, because the event handler is always called on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="2e68e-110">Ale při přihlášení k odběru událostí, které mohou pocházet z klientské aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], je třeba volání <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, nebo související metody, na jinou hodnotu než[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2e68e-110">However, when subscribing to events that may originate from your client application's [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you must make the call to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, or a related method, on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="2e68e-111">Obslužné rutiny událostí ve stejném vlákně, odeberte.</span><span class="sxs-lookup"><span data-stu-id="2e68e-111">Remove event handlers on the same thread.</span></span>
