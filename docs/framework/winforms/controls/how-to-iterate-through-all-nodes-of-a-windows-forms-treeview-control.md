---
title: 'Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
ms.openlocfilehash: 00a0f19803967f02795e3eade767786eecc1f4dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966549"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="69c70-102">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="69c70-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="69c70-103">Někdy je vhodné prostudovat každý uzel v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.TreeView> , aby bylo možné provést určitý výpočet hodnot uzlů.</span><span class="sxs-lookup"><span data-stu-id="69c70-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="69c70-104">Tuto operaci lze provést pomocí rekurzivní procedury (rekurzivní metody v C# a C++), která projde každým uzlem v každé kolekci stromu.</span><span class="sxs-lookup"><span data-stu-id="69c70-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="69c70-105">Každý <xref:System.Windows.Forms.TreeNode> objekt ve stromovém zobrazení má vlastnosti, které lze použít k procházení stromového zobrazení: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>a <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span><span class="sxs-lookup"><span data-stu-id="69c70-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="69c70-106">Hodnota <xref:System.Windows.Forms.TreeNode.Parent%2A> vlastnosti je nadřazeným uzlem aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="69c70-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="69c70-107">Podřízené uzly aktuálního uzlu, pokud existují, jsou uvedeny ve své <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69c70-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="69c70-108">Samotný ovládací prvek <xref:System.Windows.Forms.TreeView.TopNode%2A> má vlastnost, která je kořenovým uzlem celého stromového zobrazení. <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="69c70-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="69c70-109">Iterace všemi uzly ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="69c70-109">To iterate through all nodes of the TreeView control</span></span>  
  
1. <span data-ttu-id="69c70-110">Vytvořte rekurzivní proceduru (rekurzivní metodu v C# a C++), která testuje každý uzel.</span><span class="sxs-lookup"><span data-stu-id="69c70-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2. <span data-ttu-id="69c70-111">Zavolejte proceduru.</span><span class="sxs-lookup"><span data-stu-id="69c70-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="69c70-112">Následující příklad ukazuje, jak vytisknout <xref:System.Windows.Forms.TreeNode> <xref:System.Windows.Forms.TreeNode.Text%2A> vlastnost jednotlivých objektů:</span><span class="sxs-lookup"><span data-stu-id="69c70-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="69c70-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69c70-113">See also</span></span>

- [<span data-ttu-id="69c70-114">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="69c70-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="69c70-115">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="69c70-115">Recursive Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
