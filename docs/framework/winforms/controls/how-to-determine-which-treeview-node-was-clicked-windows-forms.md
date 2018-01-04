---
title: "Postupy: Určení uzlu TreeView označeného kliknutím (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2671d2790b3c5e476513cd5932d4684838aeceb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="4087e-102">Postupy: Určení uzlu TreeView označeného kliknutím (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4087e-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="4087e-103">Při práci s Windows Forms <xref:System.Windows.Forms.TreeView> řízení, běžné úlohy je určit uzel označeného a reagují odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="4087e-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="4087e-104">K určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="4087e-104">To determine which TreeView node was clicked</span></span>  
  
1.  <span data-ttu-id="4087e-105">Použití <xref:System.EventArgs> objekt, který chcete vrátit odkaz na objekt kliknutelnou uzlu.</span><span class="sxs-lookup"><span data-stu-id="4087e-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2.  <span data-ttu-id="4087e-106">Určit, který uzel označeného kontrolou <xref:System.Windows.Forms.TreeViewEventArgs> třídy, která obsahuje data související s události.</span><span class="sxs-lookup"><span data-stu-id="4087e-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    >  <span data-ttu-id="4087e-107">Jako alternativu, můžete použít <xref:System.Windows.Forms.MouseEventArgs> z <xref:System.Windows.Forms.Control.MouseDown> nebo <xref:System.Windows.Forms.Control.MouseUp> událost, která má získat <xref:System.Drawing.Point.X%2A> a <xref:System.Drawing.Point.Y%2A> koordinaci hodnoty <xref:System.Drawing.Point> kde došlo k chybě a klikněte na.</span><span class="sxs-lookup"><span data-stu-id="4087e-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="4087e-108">Potom použít <xref:System.Windows.Forms.TreeView> ovládacího prvku <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metoda k určení, který uzel označeného.</span><span class="sxs-lookup"><span data-stu-id="4087e-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4087e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4087e-109">See Also</span></span>  
 [<span data-ttu-id="4087e-110">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="4087e-110">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
