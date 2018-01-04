---
title: "Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3acc1a731fa584a17c8a96f8a02986a504cd302d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="ef31e-102">Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="ef31e-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="ef31e-103">Windows Forms <xref:System.Windows.Forms.TreeView> zobrazí hierarchie uzlů, podobně jako u souborů a složek, na které se zobrazí v levém podokně funkci Průzkumníka Windows v operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="ef31e-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="ef31e-104">Nastavením <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost, můžete zadat kontextové operace uživateli při jejich klikněte pravým tlačítkem myši <xref:System.Windows.Forms.TreeView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ef31e-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="ef31e-105">Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> součást s jednotlivé <xref:System.Windows.Forms.TreeNode> položek, můžete přidat vlastní úroveň funkce místní nabídky k vaší <xref:System.Windows.Forms.TreeView> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="ef31e-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef31e-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ef31e-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ef31e-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ef31e-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ef31e-108">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ef31e-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="ef31e-109">Přidružení místní nabídky k TreeNode v době návrhu</span><span class="sxs-lookup"><span data-stu-id="ef31e-109">To associate a shortcut menu with a TreeNode at design time</span></span>  
  
1.  <span data-ttu-id="ef31e-110">Přidat <xref:System.Windows.Forms.TreeView> řízení do svého formuláře a potom přidat uzly do <xref:System.Windows.Forms.TreeView> podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="ef31e-110">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="ef31e-111">Další informace najdete v tématu [postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ef31e-111">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>  
  
2.  <span data-ttu-id="ef31e-112">Přidat <xref:System.Windows.Forms.ContextMenuStrip> součásti do svého formuláře a pak přidejte položky nabídky do místní nabídky, která představují úrovni uzlu operace, které chcete zpřístupnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ef31e-112">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="ef31e-113">Další informace najdete v tématu [postupy: přidání položek nabídky do ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span><span class="sxs-lookup"><span data-stu-id="ef31e-113">For more information, see [How to: Add Menu Items to a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>  
  
3.  <span data-ttu-id="ef31e-114">Otevřete **TreeNodeEditor** dialogové okno pro <xref:System.Windows.Forms.TreeView> řídit, vyberte uzel pro úpravy a nastavit jeho <xref:System.Windows.Forms.ContextMenuStrip> vlastnost, která má místní nabídky, která jste přidali.</span><span class="sxs-lookup"><span data-stu-id="ef31e-114">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>  
  
4.  <span data-ttu-id="ef31e-115">Když je tato vlastnost nastavena, zobrazí se při kliknete pravým tlačítkem na uzel v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="ef31e-115">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
     <span data-ttu-id="ef31e-116">Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> události pro tyto položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="ef31e-116">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef31e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef31e-117">See Also</span></span>  
 [<span data-ttu-id="ef31e-118">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="ef31e-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="ef31e-119">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="ef31e-119">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="ef31e-120">Ovládací prvek ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="ef31e-120">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
