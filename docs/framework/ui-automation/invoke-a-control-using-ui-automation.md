---
title: Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923726"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="77c5d-102">Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="77c5d-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="77c5d-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="77c5d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="77c5d-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="77c5d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="77c5d-105">Toto téma ukazuje, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="77c5d-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="77c5d-106">Vyhledání ovládacího prvku, který odpovídá podmínkám konkrétní vlastnosti, procházením zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího prvku stromové struktury cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="77c5d-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="77c5d-107"><xref:System.Windows.Automation.AutomationElement> Vytvořte pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="77c5d-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="77c5d-108">Získejte objekt z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] libovolného<xref:System.Windows.Automation.InvokePattern> elementu, který podporuje vzor ovládacího prvku. <xref:System.Windows.Automation.InvokePattern></span><span class="sxs-lookup"><span data-stu-id="77c5d-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="77c5d-109">Slouží <xref:System.Windows.Automation.InvokePattern.Invoke%2A> k vyvolání ovládacího prvku z klientské obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="77c5d-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77c5d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="77c5d-110">Example</span></span>  
 <span data-ttu-id="77c5d-111">Tento příklad používá <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metodu <xref:System.Windows.Automation.AutomationElement> třídy pro generování <xref:System.Windows.Automation.InvokePattern> <xref:System.Windows.Automation.InvokePattern.Invoke%2A> objektu a vyvolání ovládacího prvku pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="77c5d-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="77c5d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77c5d-112">See also</span></span>

- [<span data-ttu-id="77c5d-113">Ukázka InvokePattern, ExpandCollapsePattern a TogglePattern</span><span class="sxs-lookup"><span data-stu-id="77c5d-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
