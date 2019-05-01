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
ms.openlocfilehash: 1a857aade86d2366bb68ce14d716b3ce532ecb05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013254"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView
Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek mohl zobrazit ikony vedle každého uzlu. Ikony jsou umístěny na bezprostředně vlevo od textu uzlu. Chcete-li zobrazit tyto ikony, je třeba přidružit zobrazení stromu s <xref:System.Windows.Forms.ImageList> ovládacího prvku. Další informace o seznamech image, najdete v části [komponenty ImageList](imagelist-component-windows-forms.md) a [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Chyby v rozhraní Microsoft .NET Framework verze 1.1 bránil imagí v <xref:System.Windows.Forms.TreeView> uzly, když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Chcete-li vyřešit tuto chybu, zavolejte <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> ve vašich `Main` ihned po volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. V této opravy chyby [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
### <a name="to-display-images-in-a-tree-view"></a>Chcete-li zobrazit obrázky ve stromovém zobrazení  
  
1. Nastavte <xref:System.Windows.Forms.TreeView> ovládacího prvku <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost ke stávající <xref:System.Windows.Forms.ImageList> ovládacího prvku, které chcete použít.  
  
     Tyto vlastnosti můžete nastavit v návrháři se v okně Vlastnosti, nebo v kódu.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. Nastavte uzel <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> vlastnosti. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Vlastnost určuje obrázek zobrazený pro běžné a rozšířené státy uzlu a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> vlastnost určuje obrázek zobrazený pro vybraný stav uzlu.  
  
     Tyto vlastnosti můžete nastavit v kódu nebo v rámci Editor objektu TreeNode. Editor objektu TreeNode, klikněte na tlačítko se třemi tečkami ( ![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastností v okně Vlastnosti.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku TreeView](treeview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání uzlů s ovládacím prvku Windows Forms TreeView](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Určení uzlu TreeView označeného kliknutím](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
