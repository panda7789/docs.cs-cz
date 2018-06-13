---
title: 'Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: 2491f4d4c40ea412ee42f8cd99c4c8682baa94a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525935"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView
Windows Forms <xref:System.Windows.Forms.TreeView> řízení ukládá uzly nejvyšší úrovně v jeho <xref:System.Windows.Forms.TreeView.Nodes%2A> kolekce. Každý <xref:System.Windows.Forms.TreeNode> má také vlastní <xref:System.Windows.Forms.TreeNode.Nodes%2A> kolekce k uložení jeho podřízené uzly. Obě vlastnosti kolekce jsou typu <xref:System.Windows.Forms.TreeNodeCollection>, který poskytuje standardní kolekci členů, které vám umožní přidat, odebrat a uspořádání uzlů na jedné úrovni hierarchie uzlu.  
  
### <a name="to-add-nodes-programmatically"></a>Chcete-li přidat uzly prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metoda zobrazení stromu <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost.  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a>Odebrat uzly prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metoda zobrazení stromu <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost k odebrání jednoho uzlu, nebo <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> metoda zrušte všechny uzly.  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Přehled ovládacího prvku TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Postupy: Určení uzlu TreeView označeného kliknutím](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
