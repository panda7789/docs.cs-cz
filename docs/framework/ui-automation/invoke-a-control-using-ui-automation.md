---
title: Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní
description: Pomocí automatizace uživatelského rozhraní můžete najít ovládací prvek, který odpovídá určitým podmínkám vlastnosti, vytvořit třída AutomationElement neobsahuje, získat InvokePattern a použít vyvolání na ovládacím prvku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 2347a620aab848bf6bcc649a9780aa5a3a520822
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168179"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="1ba9d-103">Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ba9d-103">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="1ba9d-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1ba9d-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1ba9d-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="1ba9d-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="1ba9d-106">Toto téma ukazuje, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="1ba9d-106">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="1ba9d-107">Vyhledání ovládacího prvku, který odpovídá podmínkám konkrétní vlastnosti, procházením zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ba9d-107">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="1ba9d-108">Vytvořte <xref:System.Windows.Automation.AutomationElement> pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1ba9d-108">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="1ba9d-109">Získejte <xref:System.Windows.Automation.InvokePattern> objekt z libovolného [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu, který podporuje <xref:System.Windows.Automation.InvokePattern> vzor ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1ba9d-109">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="1ba9d-110">Slouží <xref:System.Windows.Automation.InvokePattern.Invoke%2A> k vyvolání ovládacího prvku z klientské obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1ba9d-110">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ba9d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ba9d-111">Example</span></span>  
 <span data-ttu-id="1ba9d-112">Tento příklad používá <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metodu <xref:System.Windows.Automation.AutomationElement> třídy pro generování <xref:System.Windows.Automation.InvokePattern> objektu a vyvolání ovládacího prvku pomocí <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1ba9d-112">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="1ba9d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ba9d-113">See also</span></span>

- [<span data-ttu-id="1ba9d-114">Ukázka InvokePattern, ExpandCollapsePattern a TogglePattern</span><span class="sxs-lookup"><span data-stu-id="1ba9d-114">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
