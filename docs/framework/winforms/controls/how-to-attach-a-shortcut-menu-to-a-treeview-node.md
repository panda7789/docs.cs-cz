---
title: "Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca251c9dec87db0ecb4b565b522839ace7f44479
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a><span data-ttu-id="863bc-102">Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView</span><span class="sxs-lookup"><span data-stu-id="863bc-102">How to: Attach a ShortCut Menu to a TreeView Node</span></span>
<span data-ttu-id="863bc-103">Windows Forms <xref:System.Windows.Forms.TreeView> zobrazí hierarchie uzlů, podobně jako u souborů a složek, na které se zobrazí v levém podokně Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="863bc-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of Windows Explorer.</span></span> <span data-ttu-id="863bc-104">Nastavením <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost, můžete zadat kontextové operace uživateli při jejich klikněte pravým tlačítkem myši <xref:System.Windows.Forms.TreeView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="863bc-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="863bc-105">Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> součást s jednotlivé <xref:System.Windows.Forms.TreeNode> položek, můžete přidat vlastní úroveň funkce místní nabídky k vaší <xref:System.Windows.Forms.TreeView> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="863bc-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a><span data-ttu-id="863bc-106">Přidružení místní nabídky k TreeNode prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="863bc-106">To associate a shortcut menu with a TreeNode programmatically</span></span>  
  
1.  <span data-ttu-id="863bc-107">Vytváření instancí <xref:System.Windows.Forms.TreeView> řízení s odpovídající nastavení vlastností, vytvořte kořenové <xref:System.Windows.Forms.TreeNode>a poté přidejte podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="863bc-107">Instantiate a <xref:System.Windows.Forms.TreeView> control with the appropriate property settings, create a root <xref:System.Windows.Forms.TreeNode>, and then add subnodes.</span></span>  
  
2.  <span data-ttu-id="863bc-108">Vytváření instancí <xref:System.Windows.Forms.ContextMenuStrip> součást a poté přidejte <xref:System.Windows.Forms.ToolStripMenuItem> pro každou operaci, kterou chcete zpřístupnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="863bc-108">Instantiate a <xref:System.Windows.Forms.ContextMenuStrip> component, and then add a <xref:System.Windows.Forms.ToolStripMenuItem> for each operation you want to make available at run time.</span></span>  
  
3.  <span data-ttu-id="863bc-109">Nastavte <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> vlastnost odpovídající <xref:System.Windows.Forms.TreeNode> do místní nabídky, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="863bc-109">Set the <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> property of the appropriate <xref:System.Windows.Forms.TreeNode> to the shortcut menu you create.</span></span>  
  
4.  <span data-ttu-id="863bc-110">Když je tato vlastnost nastavena, zobrazí se při kliknete pravým tlačítkem na uzel v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="863bc-110">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
 <span data-ttu-id="863bc-111">Následující příklad kódu vytvoří základní <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ContextMenuStrip> přidruženou ke kořenovému adresáři <xref:System.Windows.Forms.TreeNode> z <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="863bc-111">The following code example creates a basic <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ContextMenuStrip> associated with the root <xref:System.Windows.Forms.TreeNode> of the <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="863bc-112">Budete muset přizpůsobit možnosti nabídky na ty, které nevejde <xref:System.Windows.Forms.TreeView> vyvíjíte.</span><span class="sxs-lookup"><span data-stu-id="863bc-112">You will need to customize the menu choices to those that fit the <xref:System.Windows.Forms.TreeView> you are developing.</span></span> <span data-ttu-id="863bc-113">Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> události pro tyto položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="863bc-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="863bc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="863bc-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [<span data-ttu-id="863bc-115">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="863bc-115">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
