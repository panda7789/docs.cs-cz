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
ms.openlocfilehash: d960eaae2aa479e0be74e9a5e4fdbfec8ff411c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182175"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="d8807-102">Postupy: Určení uzlu TreeView označeného kliknutím (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d8807-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="d8807-103">Při práci s <xref:System.Windows.Forms.TreeView> ovládacím prvkem Windows Forms je běžným úkolem určit, na který uzel bylo klepnuto, a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="d8807-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="d8807-104">Chcete-li zjistit, na který uzel TreeView bylo kliknuto</span><span class="sxs-lookup"><span data-stu-id="d8807-104">To determine which TreeView node was clicked</span></span>  
  
1. <span data-ttu-id="d8807-105">Pomocí <xref:System.EventArgs> objektu vraťte odkaz na objekt klepnutého uzlu.</span><span class="sxs-lookup"><span data-stu-id="d8807-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2. <span data-ttu-id="d8807-106">Zjistěte, na který uzel bylo <xref:System.Windows.Forms.TreeViewEventArgs> kliknuto kontrolou třídy, která obsahuje data související s událostí.</span><span class="sxs-lookup"><span data-stu-id="d8807-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    > <span data-ttu-id="d8807-107">Jako alternativu můžete použít <xref:System.Windows.Forms.MouseEventArgs> událost <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> nebo k <xref:System.Drawing.Point.X%2A> získání <xref:System.Drawing.Point.Y%2A> a souřadnicových hodnot místa, <xref:System.Drawing.Point> kde došlo ke kliknutí.</span><span class="sxs-lookup"><span data-stu-id="d8807-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="d8807-108">Potom použijte <xref:System.Windows.Forms.TreeView> metodu <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> ovládacího prvku k určení, na který uzel bylo kliknuto.</span><span class="sxs-lookup"><span data-stu-id="d8807-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8807-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8807-109">See also</span></span>

- [<span data-ttu-id="d8807-110">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="d8807-110">TreeView Control</span></span>](treeview-control-windows-forms.md)
