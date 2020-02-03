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
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.TreeView> může zobrazit ikony vedle každého uzlu. Ikony jsou umístěny na nejbližší levé straně textu uzlu. Chcete-li zobrazit tyto ikony, je nutné přidružit stromové zobrazení k ovládacímu prvku <xref:System.Windows.Forms.ImageList>. Další informace o seznamech obrázků naleznete v tématu [Komponenta ImageList](imagelist-component-windows-forms.md) a [Postupy: Přidání nebo odebrání obrázků s komponentou model Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
> Chyba ve službě Microsoft .NET Framework verze 1,1 zabraňuje zobrazování obrázků v <xref:System.Windows.Forms.TreeView> uzlech, pokud vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Chcete-li tuto chybu obejít, zavolejte <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> v metodě `Main` hned po volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Tato chyba je opravena v .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Zobrazení obrázků ve stromovém zobrazení  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.TreeView.ImageList%2A> ovládacího prvku <xref:System.Windows.Forms.TreeView> na existující ovládací prvek <xref:System.Windows.Forms.ImageList>, který chcete použít.  
  
     Tyto vlastnosti lze nastavit v Návrháři pomocí okno Vlastnosti nebo v kódu.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. Nastavte vlastnosti <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> uzlu. Vlastnost <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> určuje obrázek zobrazený pro normální a rozbalený stav uzlu a vlastnost <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> určuje obrázek zobrazený pro vybraný stav uzlu.  
  
     Tyto vlastnosti lze nastavit v kódu nebo v editoru prvku TreeNode. Chcete-li otevřít Editor TreeNode, klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.TreeView.Nodes%2A> na okno Vlastnosti.  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled ovládacího prvku TreeView](treeview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Určení uzlu TreeView označeného kliknutím](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
