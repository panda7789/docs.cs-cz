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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909813"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="0349a-102">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="0349a-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="0349a-103">Ovládací prvek <xref:System.Windows.Forms.TreeView> model Windows Forms může zobrazit ikony vedle každého uzlu.</span><span class="sxs-lookup"><span data-stu-id="0349a-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="0349a-104">Ikony jsou umístěny na nejbližší levé straně textu uzlu.</span><span class="sxs-lookup"><span data-stu-id="0349a-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="0349a-105">Chcete-li zobrazit tyto ikony, je nutné přidružit stromové <xref:System.Windows.Forms.ImageList> zobrazení k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="0349a-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="0349a-106">Další informace o seznamech obrázků naleznete v tématu [Komponenta ImageList](imagelist-component-windows-forms.md) a [postupy: Přidejte nebo odeberte obrázky s komponentou](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)model Windows Forms ImageList.</span><span class="sxs-lookup"><span data-stu-id="0349a-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0349a-107">Chyba ve službě Microsoft .NET Framework verze 1,1 zabraňuje zobrazování obrázků v <xref:System.Windows.Forms.TreeView> uzlech při volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>aplikace.</span><span class="sxs-lookup"><span data-stu-id="0349a-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0349a-108">Chcete-li tuto chybu obejít <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> , zavolejte `Main` metodu hned po volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="0349a-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="0349a-109">Tato chyba je opravena v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="0349a-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="0349a-110">Zobrazení obrázků ve stromovém zobrazení</span><span class="sxs-lookup"><span data-stu-id="0349a-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="0349a-111"><xref:System.Windows.Forms.TreeView> Nastavte vlastnost<xref:System.Windows.Forms.TreeView.ImageList%2A> ovládacího prvku na existující <xref:System.Windows.Forms.ImageList> ovládací prvek, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="0349a-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="0349a-112">Tyto vlastnosti lze nastavit v Návrháři pomocí okno Vlastnosti nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="0349a-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="0349a-113">Nastavte vlastnosti uzlu <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> .</span><span class="sxs-lookup"><span data-stu-id="0349a-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="0349a-114">Vlastnost určuje obrázek zobrazený pro normální a rozbalené stavy uzlu <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> a vlastnost určuje obrázek zobrazený pro vybraný stav uzlu. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="0349a-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="0349a-115">Tyto vlastnosti lze nastavit v kódu nebo v editoru prvku TreeNode.</span><span class="sxs-lookup"><span data-stu-id="0349a-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="0349a-116">Chcete-li otevřít Editor TreeNode, klikněte na tlačítko se ![třemi tečkami (tlačítko se třemi tečkami (...) v](./media/visual-studio-ellipsis-button.png)okno Vlastnosti sady Visual Studio <xref:System.Windows.Forms.TreeView.Nodes%2A> ) vedle vlastnosti v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0349a-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0349a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0349a-117">See also</span></span>

- [<span data-ttu-id="0349a-118">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="0349a-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="0349a-119">Postupy: Přidání a odebrání uzlů pomocí ovládacího prvku model Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="0349a-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="0349a-120">Postupy: Iterovat všemi uzly model Windows Forms ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="0349a-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="0349a-121">Postupy: Zjistit, který uzel TreeView byl kliknuto</span><span class="sxs-lookup"><span data-stu-id="0349a-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="0349a-122">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0349a-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
