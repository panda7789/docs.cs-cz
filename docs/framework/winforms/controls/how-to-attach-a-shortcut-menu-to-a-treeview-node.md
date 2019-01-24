---
title: 'Postupy: Připojení místní nabídky k uzlu TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: 7c9e2a2fc51628116a7762e343f36f9f7e93fe67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685201"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a><span data-ttu-id="bcd14-102">Postupy: Připojení místní nabídky k uzlu TreeView</span><span class="sxs-lookup"><span data-stu-id="bcd14-102">How to: Attach a ShortCut Menu to a TreeView Node</span></span>
<span data-ttu-id="bcd14-103">Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek zobrazuje hierarchii uzlů, podobně jako u souborů a složek, na které se zobrazí v levém podokně Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="bcd14-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of Windows Explorer.</span></span> <span data-ttu-id="bcd14-104">Tím, že nastavíte <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastností, můžete zadat kontextové operace uživateli při jejich pravým tlačítkem myši <xref:System.Windows.Forms.TreeView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bcd14-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="bcd14-105">Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> komponenty u jednotlivých <xref:System.Windows.Forms.TreeNode> položky, můžete přidat vlastní úroveň funkce místní nabídku pro váš <xref:System.Windows.Forms.TreeView> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bcd14-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a><span data-ttu-id="bcd14-106">Přidružení místní nabídky k TreeNode prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="bcd14-106">To associate a shortcut menu with a TreeNode programmatically</span></span>  
  
1.  <span data-ttu-id="bcd14-107">Vytvořit instanci <xref:System.Windows.Forms.TreeView> ovládacím prvkem odpovídající nastavení vlastností, vytvoření kořenového <xref:System.Windows.Forms.TreeNode>a pak přidejte podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="bcd14-107">Instantiate a <xref:System.Windows.Forms.TreeView> control with the appropriate property settings, create a root <xref:System.Windows.Forms.TreeNode>, and then add subnodes.</span></span>  
  
2.  <span data-ttu-id="bcd14-108">Vytvořit instanci <xref:System.Windows.Forms.ContextMenuStrip> komponenty a pak přidejte <xref:System.Windows.Forms.ToolStripMenuItem> pro každou operaci, kterou chcete zpřístupnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bcd14-108">Instantiate a <xref:System.Windows.Forms.ContextMenuStrip> component, and then add a <xref:System.Windows.Forms.ToolStripMenuItem> for each operation you want to make available at run time.</span></span>  
  
3.  <span data-ttu-id="bcd14-109">Nastavte <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> vlastnost odpovídající <xref:System.Windows.Forms.TreeNode> do místní nabídky, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="bcd14-109">Set the <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> property of the appropriate <xref:System.Windows.Forms.TreeNode> to the shortcut menu you create.</span></span>  
  
4.  <span data-ttu-id="bcd14-110">Pokud je tato vlastnost nastavena, zobrazí se při klepnutí pravým tlačítkem myši na uzel v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="bcd14-110">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
 <span data-ttu-id="bcd14-111">Následující příklad kódu vytvoří základní <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ContextMenuStrip> přidruženou ke kořenovému adresáři <xref:System.Windows.Forms.TreeNode> z <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="bcd14-111">The following code example creates a basic <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ContextMenuStrip> associated with the root <xref:System.Windows.Forms.TreeNode> of the <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="bcd14-112">Budete muset přizpůsobit možnosti nabídek na ty, které odpovídají <xref:System.Windows.Forms.TreeView> vyvíjíte.</span><span class="sxs-lookup"><span data-stu-id="bcd14-112">You will need to customize the menu choices to those that fit the <xref:System.Windows.Forms.TreeView> you are developing.</span></span> <span data-ttu-id="bcd14-113">Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> události pro tyto položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="bcd14-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bcd14-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcd14-114">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="bcd14-115">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="bcd14-115">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
