---
title: 'Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: c7c801242c7d5958cce9826a5f60d13a0b257add
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348058"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="a3f61-102">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="a3f61-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="a3f61-103">Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek mohl zobrazit ikony vedle každého uzlu.</span><span class="sxs-lookup"><span data-stu-id="a3f61-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="a3f61-104">Ikony jsou umístěny na bezprostředně vlevo od textu uzlu.</span><span class="sxs-lookup"><span data-stu-id="a3f61-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="a3f61-105">Chcete-li zobrazit tyto ikony, je třeba přidružit zobrazení stromu s <xref:System.Windows.Forms.ImageList> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a3f61-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="a3f61-106">Další informace o seznamech image, najdete v části [komponenty ImageList](imagelist-component-windows-forms.md) a [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="a3f61-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3f61-107">Chyby v rozhraní Microsoft .NET Framework verze 1.1 bránil imagí v <xref:System.Windows.Forms.TreeView> uzly, když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a3f61-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a3f61-108">Chcete-li vyřešit tuto chybu, zavolejte <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> ve vašich `Main` ihned po volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3f61-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="a3f61-109">Tato chyba je opravena v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a3f61-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="a3f61-110">Chcete-li zobrazit obrázky ve stromovém zobrazení</span><span class="sxs-lookup"><span data-stu-id="a3f61-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="a3f61-111">Nastavte <xref:System.Windows.Forms.TreeView> ovládacího prvku <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost ke stávající <xref:System.Windows.Forms.ImageList> ovládacího prvku, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a3f61-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="a3f61-112">Tyto vlastnosti můžete nastavit v návrháři se v okně Vlastnosti, nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="a3f61-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="a3f61-113">Nastavte uzel <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a3f61-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="a3f61-114"><xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Vlastnost určuje obrázek zobrazený pro běžné a rozšířené státy uzlu a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> vlastnost určuje obrázek zobrazený pro vybraný stav uzlu.</span><span class="sxs-lookup"><span data-stu-id="a3f61-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="a3f61-115">Tyto vlastnosti můžete nastavit v kódu nebo v rámci Editor objektu TreeNode.</span><span class="sxs-lookup"><span data-stu-id="a3f61-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="a3f61-116">Editor objektu TreeNode, klikněte na tlačítko se třemi tečkami ( ![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle položky <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastností v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a3f61-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a3f61-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3f61-117">See also</span></span>

- [<span data-ttu-id="a3f61-118">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="a3f61-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="a3f61-119">Postupy: Přidání a odebrání uzlů s ovládacím prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="a3f61-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="a3f61-120">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="a3f61-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="a3f61-121">Postupy: Určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="a3f61-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="a3f61-122">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a3f61-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
