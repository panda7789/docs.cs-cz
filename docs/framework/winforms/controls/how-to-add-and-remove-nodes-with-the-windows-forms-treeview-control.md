---
title: Přidání a odebrání uzlů pomocí ovládacího prvku TreeView
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
ms.openlocfilehash: f1e74e6d2f827167c32a6955b3010b59cb2f85b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142209"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView
Ovládací prvek <xref:System.Windows.Forms.TreeView> Windows Forms ukládá uzly <xref:System.Windows.Forms.TreeView.Nodes%2A> nejvyšší úrovně ve své kolekci. Každý <xref:System.Windows.Forms.TreeNode> má také <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastní kolekci pro uložení podřízených uzlů. Obě vlastnosti kolekce <xref:System.Windows.Forms.TreeNodeCollection>jsou typu , který poskytuje standardní členy kolekce, které umožňují přidat, odebrat a změnit uspořádání uzlů na jedné úrovni hierarchie uzlů.  
  
### <a name="to-add-nodes-programmatically"></a>Chcete-li přidat uzly programově  
  
1. Použijte <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metodu vlastnosti stromového <xref:System.Windows.Forms.TreeView.Nodes%2A> zobrazení.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Chcete-li odstranit uzly programově  
  
1. Pomocí <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metody <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnosti stromového zobrazení odeberte jeden uzel <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> nebo metodu k vymazání všech uzlů.  
  
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

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [Přehled ovládacího prvku TreeView](treeview-control-overview-windows-forms.md)
- [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Určení uzlu TreeView označeného kliknutím](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
