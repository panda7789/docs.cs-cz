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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="b17d3-102">Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="b17d3-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="b17d3-103">Ovládací prvek <xref:System.Windows.Forms.TreeView> Windows Forms ukládá uzly <xref:System.Windows.Forms.TreeView.Nodes%2A> nejvyšší úrovně ve své kolekci.</span><span class="sxs-lookup"><span data-stu-id="b17d3-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="b17d3-104">Každý <xref:System.Windows.Forms.TreeNode> má také <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastní kolekci pro uložení podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="b17d3-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="b17d3-105">Obě vlastnosti kolekce <xref:System.Windows.Forms.TreeNodeCollection>jsou typu , který poskytuje standardní členy kolekce, které umožňují přidat, odebrat a změnit uspořádání uzlů na jedné úrovni hierarchie uzlů.</span><span class="sxs-lookup"><span data-stu-id="b17d3-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="b17d3-106">Chcete-li přidat uzly programově</span><span class="sxs-lookup"><span data-stu-id="b17d3-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="b17d3-107">Použijte <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metodu vlastnosti stromového <xref:System.Windows.Forms.TreeView.Nodes%2A> zobrazení.</span><span class="sxs-lookup"><span data-stu-id="b17d3-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="b17d3-108">Chcete-li odstranit uzly programově</span><span class="sxs-lookup"><span data-stu-id="b17d3-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="b17d3-109">Pomocí <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metody <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnosti stromového zobrazení odeberte jeden uzel <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> nebo metodu k vymazání všech uzlů.</span><span class="sxs-lookup"><span data-stu-id="b17d3-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b17d3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b17d3-110">See also</span></span>

- [<span data-ttu-id="b17d3-111">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="b17d3-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="b17d3-112">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="b17d3-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="b17d3-113">Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="b17d3-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="b17d3-114">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="b17d3-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="b17d3-115">Postupy: Určení uzlu TreeView označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="b17d3-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="b17d3-116">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b17d3-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
