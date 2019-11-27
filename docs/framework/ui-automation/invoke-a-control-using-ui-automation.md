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
ms.openlocfilehash: e1b489e8daaaf9f5b8c0cb46374fa54bf165d49c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447012"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="5f2bc-102">Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f2bc-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="5f2bc-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="5f2bc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5f2bc-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5f2bc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5f2bc-105">Toto téma ukazuje, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="5f2bc-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="5f2bc-106">Vyhledání ovládacího prvku, který odpovídá podmínkám konkrétní vlastnosti, procházením zobrazení ovládacího prvku stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pro cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f2bc-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="5f2bc-107">Vytvořte <xref:System.Windows.Automation.AutomationElement> pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5f2bc-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="5f2bc-108">Získejte <xref:System.Windows.Automation.InvokePattern> objekt z jakéhokoli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu, který podporuje vzor ovládacího prvku <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="5f2bc-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="5f2bc-109">Použijte <xref:System.Windows.Automation.InvokePattern.Invoke%2A> k vyvolání ovládacího prvku z klientské obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="5f2bc-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f2bc-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f2bc-110">Example</span></span>  
 <span data-ttu-id="5f2bc-111">Tento příklad používá metodu <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> třídy <xref:System.Windows.Automation.AutomationElement> ke generování objektu <xref:System.Windows.Automation.InvokePattern> a k vyvolání ovládacího prvku pomocí metody <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f2bc-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="5f2bc-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f2bc-112">See also</span></span>

- [<span data-ttu-id="5f2bc-113">Ukázka InvokePattern, ExpandCollapsePattern a TogglePattern</span><span class="sxs-lookup"><span data-stu-id="5f2bc-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
