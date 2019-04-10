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
ms.openlocfilehash: 4cbb5fbdb24790a7ddbce5c38060703c7ba7024a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326889"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="768c0-102">Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="768c0-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="768c0-103">Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek obsahuje uzly nejvyšší úrovně v jeho <xref:System.Windows.Forms.TreeView.Nodes%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="768c0-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="768c0-104">Každý <xref:System.Windows.Forms.TreeNode> má také svůj vlastní <xref:System.Windows.Forms.TreeNode.Nodes%2A> kolekce pro ukládání své podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="768c0-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="768c0-105">Jsou obě vlastnosti kolekce typu <xref:System.Windows.Forms.TreeNodeCollection>, která poskytuje standardní kolekce členy, které vám umožňují přidat, odebrat a uspořádání uzlů na jedné úrovni uzlu hierarchie.</span><span class="sxs-lookup"><span data-stu-id="768c0-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="768c0-106">Přidání uzlů prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="768c0-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="768c0-107">Použití <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metoda stromového zobrazení <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="768c0-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="768c0-108">Na odebrání uzlů prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="768c0-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="768c0-109">Použití <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metoda stromového zobrazení <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost k odebrání jednoho uzlu, nebo <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> metoda zrušte všechny uzly.</span><span class="sxs-lookup"><span data-stu-id="768c0-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="768c0-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="768c0-110">See also</span></span>

- [<span data-ttu-id="768c0-111">TreeView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="768c0-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="768c0-112">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="768c0-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="768c0-113">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="768c0-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="768c0-114">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="768c0-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="768c0-115">Postupy: Určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="768c0-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="768c0-116">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="768c0-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
