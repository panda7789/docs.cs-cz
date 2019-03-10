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
ms.openlocfilehash: 306c1f684f1f4c2deb057f7d81c93856ee6189e7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715392"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="7f72f-102">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="7f72f-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="7f72f-103">Někdy je užitečné si prohlédnout každý uzel ve Windows Forms <xref:System.Windows.Forms.TreeView> ovládacího prvku, aby bylo možné provést některé výpočtu pro hodnoty uzlu.</span><span class="sxs-lookup"><span data-stu-id="7f72f-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="7f72f-104">Tuto operaci lze provést pomocí rekurzivní procedury (rekurzivní metodu v C# a C++), který prochází každý uzel v každé z kolekcí stromu.</span><span class="sxs-lookup"><span data-stu-id="7f72f-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="7f72f-105">Každý <xref:System.Windows.Forms.TreeNode> objektu ve stromovém zobrazení má vlastnosti, které můžete použít k navigaci ve stromovém zobrazení: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, a <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span><span class="sxs-lookup"><span data-stu-id="7f72f-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="7f72f-106">Hodnota <xref:System.Windows.Forms.TreeNode.Parent%2A> vlastnost je nadřazený uzel pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="7f72f-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="7f72f-107">Podřízené uzly pro aktuální uzel, pokud existují, jsou uvedeny v jeho <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7f72f-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="7f72f-108"><xref:System.Windows.Forms.TreeView> Samotný ovládací prvek má <xref:System.Windows.Forms.TreeView.TopNode%2A> vlastnost, která je kořenový uzel celý strom.</span><span class="sxs-lookup"><span data-stu-id="7f72f-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="7f72f-109">K iteraci v rámci všech uzlů v ovládacím prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="7f72f-109">To iterate through all nodes of the TreeView control</span></span>  
  
1.  <span data-ttu-id="7f72f-110">Vytvoření rekurzivní procedury (rekurzivní metodu v C# a C++), který testuje každý uzel.</span><span class="sxs-lookup"><span data-stu-id="7f72f-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2.  <span data-ttu-id="7f72f-111">Zavolejte proceduru.</span><span class="sxs-lookup"><span data-stu-id="7f72f-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="7f72f-112">Následující příklad ukazuje, jak vytisknout každý <xref:System.Windows.Forms.TreeNode> objektu <xref:System.Windows.Forms.TreeNode.Text%2A> vlastnost:</span><span class="sxs-lookup"><span data-stu-id="7f72f-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f72f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f72f-113">See also</span></span>
- [<span data-ttu-id="7f72f-114">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="7f72f-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="7f72f-115">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="7f72f-115">Recursive Procedures</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
