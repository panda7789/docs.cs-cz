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
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView
Ovládací prvek <xref:System.Windows.Forms.TreeView> model Windows Forms může zobrazit ikony vedle každého uzlu. Ikony jsou umístěny na nejbližší levé straně textu uzlu. Chcete-li zobrazit tyto ikony, je nutné přidružit stromové <xref:System.Windows.Forms.ImageList> zobrazení k ovládacímu prvku. Další informace o seznamech obrázků naleznete v tématu [Komponenta ImageList](imagelist-component-windows-forms.md) a [postupy: Přidejte nebo odeberte obrázky s komponentou](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)model Windows Forms ImageList.  
  
> [!NOTE]
> Chyba ve službě Microsoft .NET Framework verze 1,1 zabraňuje zobrazování obrázků v <xref:System.Windows.Forms.TreeView> uzlech při volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>aplikace. Chcete-li tuto chybu obejít <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> , zavolejte `Main` metodu hned po volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Tato chyba je opravena v .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Zobrazení obrázků ve stromovém zobrazení  
  
1. <xref:System.Windows.Forms.TreeView> Nastavte vlastnost<xref:System.Windows.Forms.TreeView.ImageList%2A> ovládacího prvku na existující <xref:System.Windows.Forms.ImageList> ovládací prvek, který chcete použít.  
  
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
  
2. Nastavte vlastnosti uzlu <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> . Vlastnost určuje obrázek zobrazený pro normální a rozbalené stavy uzlu <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> a vlastnost určuje obrázek zobrazený pro vybraný stav uzlu. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A>  
  
     Tyto vlastnosti lze nastavit v kódu nebo v editoru prvku TreeNode. Chcete-li otevřít Editor TreeNode, klikněte na tlačítko se ![třemi tečkami (tlačítko se třemi tečkami (...) v](./media/visual-studio-ellipsis-button.png)okno Vlastnosti sady Visual Studio <xref:System.Windows.Forms.TreeView.Nodes%2A> ) vedle vlastnosti v okno Vlastnosti.  
  
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
- [Postupy: Přidání a odebrání uzlů pomocí ovládacího prvku model Windows Forms TreeView](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Postupy: Iterovat všemi uzly model Windows Forms ovládacího prvku TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Zjistit, který uzel TreeView byl kliknuto](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
