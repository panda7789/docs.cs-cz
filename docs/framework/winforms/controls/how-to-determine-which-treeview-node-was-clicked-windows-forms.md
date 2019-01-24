---
title: 'Postupy: Určení uzlu TreeView označeného kliknutím (Windows Forms)'
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
ms.openlocfilehash: 802367c26562d1b5aaf2398ed122cb97afbff255
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580107"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Postupy: Určení uzlu TreeView označeného kliknutím (Windows Forms)
Při práci s formuláři Windows <xref:System.Windows.Forms.TreeView> ovládacího prvku, běžné úlohy je určit došlo ke kliknutí na který uzel a reagují odpovídajícím způsobem.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>K určení uzlu TreeView označeného kliknutím  
  
1.  Použití <xref:System.EventArgs> objekt vrací odkaz na objekt kliknutí na uzel.  
  
2.  Určit, který uzel došlo ke kliknutí na kontrolou <xref:System.Windows.Forms.TreeViewEventArgs> třídu, která obsahuje data týkající se události.  
  
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
    >  Jako alternativu můžete použít <xref:System.Windows.Forms.MouseEventArgs> z <xref:System.Windows.Forms.Control.MouseDown> nebo <xref:System.Windows.Forms.Control.MouseUp> událostí zobrazíte <xref:System.Drawing.Point.X%2A> a <xref:System.Drawing.Point.Y%2A> koordinovat hodnoty <xref:System.Drawing.Point> kde došlo k kliknutím na. Potom použijte <xref:System.Windows.Forms.TreeView> ovládacího prvku <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metodou ke zjištění, který uzel došlo ke kliknutí na.  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
