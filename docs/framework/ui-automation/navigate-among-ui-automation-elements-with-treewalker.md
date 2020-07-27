---
title: Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker
description: Podívejte se na příklad kódu, který ukazuje, jak navigovat mezi prvky automatizace uživatelského rozhraní pomocí třídy třídy TreeWalker.
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
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168020"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="e4294-103">Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker</span><span class="sxs-lookup"><span data-stu-id="e4294-103">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="e4294-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e4294-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e4294-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e4294-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e4294-106">Toto téma obsahuje příklad kódu, který ukazuje, jak navigovat mezi [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prvky pomocí <xref:System.Windows.Automation.TreeWalker> třídy.</span><span class="sxs-lookup"><span data-stu-id="e4294-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4294-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4294-107">Example</span></span>  
 <span data-ttu-id="e4294-108">Následující příklad používá <xref:System.Windows.Automation.TreeWalker.GetParent%2A> ke [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] stromové struktuře, dokud nenajde kořenový prvek nebo plochu.</span><span class="sxs-lookup"><span data-stu-id="e4294-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="e4294-109">Prvek těsně pod, který je nadřazeným oknem zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="e4294-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="e4294-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4294-110">Example</span></span>  
 <span data-ttu-id="e4294-111">Následující příklad používá <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> a <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> k vytvoření <xref:System.Windows.Forms.TreeView> , který zobrazuje celý podstrom [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prvků, které jsou v zobrazení ovládacího prvku a jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="e4294-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="e4294-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4294-112">See also</span></span>

- [<span data-ttu-id="e4294-113">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4294-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
