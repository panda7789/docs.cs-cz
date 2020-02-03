---
title: Nastavení ikon pro ovládací prvek TreeView
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
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737264"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="22eb2-102">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="22eb2-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="22eb2-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.TreeView> může zobrazit ikony vedle každého uzlu.</span><span class="sxs-lookup"><span data-stu-id="22eb2-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="22eb2-104">Ikony jsou umístěny na nejbližší levé straně textu uzlu.</span><span class="sxs-lookup"><span data-stu-id="22eb2-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="22eb2-105">Chcete-li zobrazit tyto ikony, je nutné přidružit stromové zobrazení k ovládacímu prvku <xref:System.Windows.Forms.ImageList>.</span><span class="sxs-lookup"><span data-stu-id="22eb2-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="22eb2-106">Další informace o seznamech obrázků naleznete v tématu [Komponenta ImageList](imagelist-component-windows-forms.md) a [Postupy: Přidání nebo odebrání obrázků s komponentou model Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="22eb2-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22eb2-107">Chyba ve službě Microsoft .NET Framework verze 1,1 zabraňuje zobrazování obrázků v <xref:System.Windows.Forms.TreeView> uzlech, pokud vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22eb2-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="22eb2-108">Chcete-li tuto chybu obejít, zavolejte <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> v metodě `Main` hned po volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="22eb2-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="22eb2-109">Tato chyba je opravena v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="22eb2-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="22eb2-110">Zobrazení obrázků ve stromovém zobrazení</span><span class="sxs-lookup"><span data-stu-id="22eb2-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="22eb2-111">Nastavte vlastnost <xref:System.Windows.Forms.TreeView.ImageList%2A> ovládacího prvku <xref:System.Windows.Forms.TreeView> na existující ovládací prvek <xref:System.Windows.Forms.ImageList>, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="22eb2-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="22eb2-112">Tyto vlastnosti lze nastavit v Návrháři pomocí okno Vlastnosti nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="22eb2-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="22eb2-113">Nastavte vlastnosti <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> uzlu.</span><span class="sxs-lookup"><span data-stu-id="22eb2-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="22eb2-114">Vlastnost <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> určuje obrázek zobrazený pro normální a rozbalený stav uzlu a vlastnost <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> určuje obrázek zobrazený pro vybraný stav uzlu.</span><span class="sxs-lookup"><span data-stu-id="22eb2-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="22eb2-115">Tyto vlastnosti lze nastavit v kódu nebo v editoru prvku TreeNode.</span><span class="sxs-lookup"><span data-stu-id="22eb2-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="22eb2-116">Chcete-li otevřít Editor TreeNode, klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.TreeView.Nodes%2A> na okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="22eb2-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22eb2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="22eb2-117">See also</span></span>

- [<span data-ttu-id="22eb2-118">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="22eb2-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="22eb2-119">Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="22eb2-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="22eb2-120">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="22eb2-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="22eb2-121">Postupy: Určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="22eb2-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="22eb2-122">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="22eb2-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
