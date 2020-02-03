---
title: 'Postupy: Určení uzlu TreeView označeného kliknutím'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 7a0e2b69bbec0eb03d40bee2c8e2d4bc9c3558f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742009"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Postupy: Určení uzlu TreeView označeného kliknutím (Windows Forms)
Při práci s ovládacím prvkem model Windows Forms <xref:System.Windows.Forms.TreeView> je běžnou úlohou určit, na který uzel byl kliknuto, a odpovídajícím způsobem reagovat.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Určení, který uzel TreeView byl kliknuto  
  
1. Použijte objekt <xref:System.EventArgs> k vrácení odkazu na kliknuto na objekt uzlu.  
  
2. Určete, na který uzel byl kliknuto, kontrolou třídy <xref:System.Windows.Forms.TreeViewEventArgs>, která obsahuje data související s událostí.  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    > Jako alternativu můžete použít <xref:System.Windows.Forms.MouseEventArgs> události <xref:System.Windows.Forms.Control.MouseDown> nebo <xref:System.Windows.Forms.Control.MouseUp> a získat tak <xref:System.Drawing.Point.X%2A> a <xref:System.Drawing.Point.Y%2A> hodnoty souřadnic <xref:System.Drawing.Point>, na kterých došlo k kliknutí. Poté pomocí <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metody <xref:System.Windows.Forms.TreeView> ovládacího prvku určete, který uzel byl kliknuto.  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
