---
title: 'Postupy: Určit, na který uzel TreeView se kliknul (model Windows Forms)'
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
ms.openlocfilehash: ab93158daf987e2f19516b8fb3abf80bfe79a12c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967333"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Postupy: Určit, na který uzel TreeView se kliknul (model Windows Forms)
Při práci s ovládacím prvkem <xref:System.Windows.Forms.TreeView> model Windows Forms je běžnou úlohou určit, na který uzel byl kliknuto, a odpovídajícím způsobem reagovat.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Určení, který uzel TreeView byl kliknuto  
  
1. <xref:System.EventArgs> Pomocí objektu vraťte odkaz na kliknuto na objekt uzlu.  
  
2. Určete, na který uzel byl kliknuto, <xref:System.Windows.Forms.TreeViewEventArgs> kontrolou třídy, která obsahuje data související s událostí.  
  
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
    > Jako alternativu můžete <xref:System.Windows.Forms.MouseEventArgs> použít <xref:System.Windows.Forms.Control.MouseDown> událost <xref:System.Windows.Forms.Control.MouseUp> <xref:System.Drawing.Point.Y%2A> <xref:System.Drawing.Point> nebo a získat tak hodnoty asouřadnici,kdesekliknutíobjevilo.<xref:System.Drawing.Point.X%2A> Poté pomocí <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metody ovládacího prvku určete, který uzel byl kliknuto.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
