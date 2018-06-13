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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="99d13-102">Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="99d13-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="99d13-103">Windows Forms <xref:System.Windows.Forms.TreeView> řízení ukládá uzly nejvyšší úrovně v jeho <xref:System.Windows.Forms.TreeView.Nodes%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="99d13-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="99d13-104">Každý <xref:System.Windows.Forms.TreeNode> má také vlastní <xref:System.Windows.Forms.TreeNode.Nodes%2A> kolekce k uložení jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="99d13-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="99d13-105">Obě vlastnosti kolekce jsou typu <xref:System.Windows.Forms.TreeNodeCollection>, který poskytuje standardní kolekci členů, které vám umožní přidat, odebrat a uspořádání uzlů na jedné úrovni hierarchie uzlu.</span><span class="sxs-lookup"><span data-stu-id="99d13-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="99d13-106">Chcete-li přidat uzly prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="99d13-106">To add nodes programmatically</span></span>  
  
1.  <span data-ttu-id="99d13-107">Použití <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metoda zobrazení stromu <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="99d13-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="99d13-108">Odebrat uzly prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="99d13-108">To remove nodes programmatically</span></span>  
  
1.  <span data-ttu-id="99d13-109">Použití <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metoda zobrazení stromu <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost k odebrání jednoho uzlu, nebo <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> metoda zrušte všechny uzly.</span><span class="sxs-lookup"><span data-stu-id="99d13-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99d13-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="99d13-110">See Also</span></span>  
 [<span data-ttu-id="99d13-111">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="99d13-111">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="99d13-112">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="99d13-112">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="99d13-113">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="99d13-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="99d13-114">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="99d13-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="99d13-115">Postupy: Určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="99d13-115">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="99d13-116">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="99d13-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
