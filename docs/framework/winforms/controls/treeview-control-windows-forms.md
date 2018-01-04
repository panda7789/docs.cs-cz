---
title: "TreeView – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- checked list items [Windows Forms], Windows Forms controls
- list controls [Windows Forms], Windows Forms
- list items [Windows Forms], Windows Forms controls that display
- TreeView control [Windows Forms]
ms.assetid: 879438b4-4eac-45c6-b345-0229c9b21ab0
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2183954363c03064d9d41480bb63e32cca58b857
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="treeview-control-windows-forms"></a><span data-ttu-id="fc0af-102">TreeView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fc0af-102">TreeView Control (Windows Forms)</span></span>
<span data-ttu-id="fc0af-103">Windows Forms `TreeView` zobrazí hierarchie uzly, stejně, jako způsob souborů a složek, jsou zobrazeny v levém podokně funkci Průzkumníka Windows v operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="fc0af-103">The Windows Forms `TreeView` control displays a hierarchy of nodes, like the way files and folders are displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc0af-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fc0af-104">In This Section</span></span>  
 [<span data-ttu-id="fc0af-105">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="fc0af-105">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 <span data-ttu-id="fc0af-106">Vysvětluje, co je ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fc0af-106">Explains what the control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="fc0af-107">Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="fc0af-107">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 <span data-ttu-id="fc0af-108">Poskytuje pokyny pro přidání a odebrání uzlů v zobrazení stromu.</span><span class="sxs-lookup"><span data-stu-id="fc0af-108">Gives instructions for adding and remove nodes from a tree view.</span></span>  
  
 [<span data-ttu-id="fc0af-109">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fc0af-109">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="fc0af-110">Obsahují pokyny pro odvozování položku v zobrazení seznamu nebo uzel v zobrazení stromu k přidání všech polí, metody nebo konstruktory, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="fc0af-110">Gives instructions for deriving an item in a list view or a node in a tree view to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="fc0af-111">Postupy: Určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="fc0af-111">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 <span data-ttu-id="fc0af-112">Poskytuje pokyny pro určení kliknuli jste na uzel v zobrazení stromu, takže aplikace může reagovat správně.</span><span class="sxs-lookup"><span data-stu-id="fc0af-112">Gives instructions for determining which node in a tree view was clicked, so the application can respond appropriately.</span></span>  
  
 [<span data-ttu-id="fc0af-113">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="fc0af-113">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 <span data-ttu-id="fc0af-114">Poskytuje pokyny pro zkoumání každý uzel ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="fc0af-114">Gives instructions for examining every node in a tree view.</span></span>  
  
 [<span data-ttu-id="fc0af-115">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="fc0af-115">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 <span data-ttu-id="fc0af-116">Poskytuje pokyny pro zobrazení ikon pro uzly v zobrazení stromu.</span><span class="sxs-lookup"><span data-stu-id="fc0af-116">Gives instructions for displaying icons for the nodes of a tree view.</span></span>  
  
 [<span data-ttu-id="fc0af-117">Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView</span><span class="sxs-lookup"><span data-stu-id="fc0af-117">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
 <span data-ttu-id="fc0af-118">Ukazuje, jak přidat místní nabídky do zobrazení uzlu stromu.</span><span class="sxs-lookup"><span data-stu-id="fc0af-118">Demonstrates how to add a shortcut menu to a tree view node.</span></span>  
  
 <span data-ttu-id="fc0af-119">Viz také [postupy: Přidání a odebrání uzlů s Windows Forms TreeView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/ms233651\(v=vs.110\)), [postupy: připojení místní nabídky k TreeNode pomocí návrháře](http://msdn.microsoft.com/library/ms171708\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fc0af-119">Also see [How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer](http://msdn.microsoft.com/library/ms233651\(v=vs.110\)), [How to: Attach a Shortcut Menu to a TreeNode Using the Designer](http://msdn.microsoft.com/library/ms171708\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fc0af-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="fc0af-120">Reference</span></span>  
 <span data-ttu-id="fc0af-121"><xref:System.Windows.Forms.TreeView>– Třída</span><span class="sxs-lookup"><span data-stu-id="fc0af-121"><xref:System.Windows.Forms.TreeView> class</span></span>  
 <span data-ttu-id="fc0af-122">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="fc0af-122">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fc0af-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fc0af-123">Related Sections</span></span>  
 [<span data-ttu-id="fc0af-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc0af-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="fc0af-125">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="fc0af-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
