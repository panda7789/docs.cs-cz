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
ms.openlocfilehash: 1849e3ae88b9805f74b2f792ad53b02aa87e6569
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209512"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView
Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek obsahuje uzly nejvyšší úrovně v jeho <xref:System.Windows.Forms.TreeView.Nodes%2A> kolekce. Každý <xref:System.Windows.Forms.TreeNode> má také svůj vlastní <xref:System.Windows.Forms.TreeNode.Nodes%2A> kolekce pro ukládání své podřízené uzly. Jsou obě vlastnosti kolekce typu <xref:System.Windows.Forms.TreeNodeCollection>, která poskytuje standardní kolekce členy, které vám umožňují přidat, odebrat a uspořádání uzlů na jedné úrovni uzlu hierarchie.  
  
### <a name="to-add-nodes-programmatically"></a>Přidání uzlů prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metoda stromového zobrazení <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Na odebrání uzlů prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metoda stromového zobrazení <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost k odebrání jednoho uzlu, nebo <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> metoda zrušte všechny uzly.  
  
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
  
## <a name="see-also"></a>Viz také:

- [TreeView – ovládací prvek](treeview-control-windows-forms.md)
- [Přehled ovládacího prvku TreeView](treeview-control-overview-windows-forms.md)
- [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Určení uzlu TreeView označeného kliknutím](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
