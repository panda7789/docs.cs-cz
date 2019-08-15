---
title: 'Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040450"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="7826e-102">Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7826e-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="7826e-103">Ovládací prvek <xref:System.Windows.Forms.TreeView> model Windows Forms zobrazí hierarchii uzlů podobný souborům a složkám zobrazeným v levém podokně funkce Průzkumník Windows v operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="7826e-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="7826e-104">Nastavením <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnosti můžete uživateli poskytnout operace závislé na <xref:System.Windows.Forms.TreeView> ovládacím prvku, když na něj klikne pravým tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="7826e-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="7826e-105">Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> komponentu k jednotlivým <xref:System.Windows.Forms.TreeNode> položkám, můžete přidat přizpůsobenou úroveň funkcí <xref:System.Windows.Forms.TreeView> místní nabídky ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="7826e-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="7826e-106">Přidružení místní nabídky ke prvku TreeNode v době návrhu</span><span class="sxs-lookup"><span data-stu-id="7826e-106">To associate a shortcut menu with a TreeNode at design time</span></span>

1. <span data-ttu-id="7826e-107">Přidejte do formuláře <xref:System.Windows.Forms.TreeView> ovládacíprvekapřidejte<xref:System.Windows.Forms.TreeView> uzly podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="7826e-107">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="7826e-108">Další informace najdete v tématu [jak: Přidávání a odebírání uzlů s ovládacím prvkem](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)model Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="7826e-108">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>

2. <span data-ttu-id="7826e-109"><xref:System.Windows.Forms.ContextMenuStrip> Přidejte komponentu do formuláře a pak přidejte položky nabídky do místní nabídky, která představuje operace na úrovni uzlu, které chcete zpřístupnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7826e-109">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="7826e-110">Další informace najdete v tématu [jak: Přidejte položky nabídky do ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span><span class="sxs-lookup"><span data-stu-id="7826e-110">For more information, see [How to: Add Menu Items to a ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>

3. <span data-ttu-id="7826e-111">Znovu otevřete dialogové okno **TreeNodeEditor** pro <xref:System.Windows.Forms.TreeView> ovládací prvek, vyberte uzel, který chcete upravit, a nastavte jeho <xref:System.Windows.Forms.ContextMenuStrip> vlastnost na místní nabídku, kterou jste přidali.</span><span class="sxs-lookup"><span data-stu-id="7826e-111">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>

4. <span data-ttu-id="7826e-112">Při nastavení této vlastnosti se místní nabídka zobrazí po kliknutí pravým tlačítkem myši na uzel.</span><span class="sxs-lookup"><span data-stu-id="7826e-112">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>

     <span data-ttu-id="7826e-113">Navíc budete chtít napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> událostí pro tyto položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="7826e-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>

## <a name="see-also"></a><span data-ttu-id="7826e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7826e-114">See also</span></span>

- [<span data-ttu-id="7826e-115">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="7826e-115">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="7826e-116">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="7826e-116">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="7826e-117">Ovládací prvek ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="7826e-117">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
