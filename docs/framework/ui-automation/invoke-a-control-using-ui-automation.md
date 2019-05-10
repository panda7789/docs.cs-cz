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
ms.openlocfilehash: 19087cfaa22d166017bcf4e3ce5e6caf73ae5fe5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624556"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="52af1-102">Vyvolání ovládacího prvku s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="52af1-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="52af1-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="52af1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="52af1-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="52af1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="52af1-105">Toto téma ukazuje, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="52af1-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="52af1-106">Najít ovládací prvek, který odpovídá konkrétní vlastnost podmínky procházením zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu pro cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="52af1-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="52af1-107">Vytvoření <xref:System.Windows.Automation.AutomationElement> pro každý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="52af1-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="52af1-108">Získat <xref:System.Windows.Automation.InvokePattern> objekt z libovolného [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nalezen element, který podporuje <xref:System.Windows.Automation.InvokePattern> – vzor ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="52af1-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="52af1-109">Použití <xref:System.Windows.Automation.InvokePattern.Invoke%2A> k vyvolání ovládacího prvku z obslužné rutiny události klienta.</span><span class="sxs-lookup"><span data-stu-id="52af1-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52af1-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="52af1-110">Example</span></span>  
 <span data-ttu-id="52af1-111">Tento příklad používá <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metodu <xref:System.Windows.Automation.AutomationElement> k vygenerování <xref:System.Windows.Automation.InvokePattern> objektu a vyvolání ovládacího prvku pomocí <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="52af1-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="52af1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52af1-112">See also</span></span>

- [<span data-ttu-id="52af1-113">Vlastnost InvokePattern ExpandCollapsePattern a vlastnost TogglePattern vzorku</span><span class="sxs-lookup"><span data-stu-id="52af1-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
