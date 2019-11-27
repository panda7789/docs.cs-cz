---
title: Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: 5c14a660481ed14c0d9f379c80f2d6934a3b6dcb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443168"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="e2c44-102">Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker</span><span class="sxs-lookup"><span data-stu-id="e2c44-102">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="e2c44-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e2c44-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e2c44-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e2c44-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e2c44-105">Toto téma obsahuje příklad kódu, který ukazuje, jak navigovat mezi [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prvky pomocí <xref:System.Windows.Automation.TreeWalker> třídy.</span><span class="sxs-lookup"><span data-stu-id="e2c44-105">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2c44-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2c44-106">Example</span></span>  
 <span data-ttu-id="e2c44-107">Následující příklad používá <xref:System.Windows.Automation.TreeWalker.GetParent%2A> k Projděte do stromu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], dokud nenajde kořenový prvek nebo plochu.</span><span class="sxs-lookup"><span data-stu-id="e2c44-107">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="e2c44-108">Prvek těsně pod, který je nadřazeným oknem zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="e2c44-108">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="e2c44-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2c44-109">Example</span></span>  
 <span data-ttu-id="e2c44-110">Následující příklad používá <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> a <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> k vytvoření <xref:System.Windows.Forms.TreeView>, který zobrazuje celý podstrom [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prvků, které jsou v zobrazení ovládacího prvku a jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="e2c44-110">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="e2c44-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2c44-111">See also</span></span>

- [<span data-ttu-id="e2c44-112">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2c44-112">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
