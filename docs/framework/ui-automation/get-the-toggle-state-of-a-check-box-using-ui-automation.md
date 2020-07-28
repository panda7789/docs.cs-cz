---
title: Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní
description: Podívejte se na příklad kódu, který ukazuje, jak získat stav přepínání ovládacího prvku (například zaškrtávací políčko) pomocí automatizace uživatelského rozhraní Microsoft.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 36ec205a572fd6c9e52eec9d2c3e0618ddb0a07b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164146"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a><span data-ttu-id="f46e8-103">Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f46e8-103">Get the Toggle State of a Check Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="f46e8-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f46e8-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f46e8-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="f46e8-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f46e8-106">Toto téma ukazuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k získání stavu přepínání ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f46e8-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to get the toggle state of a control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f46e8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f46e8-107">Example</span></span>  
 <span data-ttu-id="f46e8-108">Tento příklad používá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> metodu <xref:System.Windows.Automation.AutomationElement> třídy pro získání <xref:System.Windows.Automation.TogglePattern> objektu z ovládacího prvku a vrácení jeho <xref:System.Windows.Automation.ToggleState> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f46e8-108">This example uses the <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to obtain a <xref:System.Windows.Automation.TogglePattern> object from a control and return its <xref:System.Windows.Automation.ToggleState> property.</span></span>  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
