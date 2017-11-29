---
title: "Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView"
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
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 057612bfb28333df0aebaa5ca19555f4c4951687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="60531-102">Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="60531-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="60531-103">Někdy je užitečné k prozkoumání každý uzel ve Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek, aby bylo možné provést některé výpočet hodnot uzlu.</span><span class="sxs-lookup"><span data-stu-id="60531-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="60531-104">Tuto operaci lze provést pomocí postupu rekurzivní (rekurzivní metody v jazyce C# a C++), který iteruje každý uzel v každé z kolekcí stromu.</span><span class="sxs-lookup"><span data-stu-id="60531-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="60531-105">Každý <xref:System.Windows.Forms.TreeNode> objekt ve stromovém zobrazení má vlastnosti, které můžete použít k zobrazení stromu přejděte: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, a <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span><span class="sxs-lookup"><span data-stu-id="60531-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="60531-106">Hodnota <xref:System.Windows.Forms.TreeNode.Parent%2A> vlastnost je nadřazený uzel aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="60531-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="60531-107">Podřízené uzly z aktuálního uzlu, pokud jsou k dispozici jsou uvedeny v jeho <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="60531-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="60531-108"><xref:System.Windows.Forms.TreeView> Má vlastní ovládací prvek <xref:System.Windows.Forms.TreeView.TopNode%2A> vlastnost, která je kořenový uzel stromu celého zobrazení.</span><span class="sxs-lookup"><span data-stu-id="60531-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="60531-109">Chcete-li iterace všemi uzly ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="60531-109">To iterate through all nodes of the TreeView control</span></span>  
  
1.  <span data-ttu-id="60531-110">Vytvoření rekurzivní procedury (rekurzivní metody v jazyce C# a C++), který testuje každý uzel.</span><span class="sxs-lookup"><span data-stu-id="60531-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2.  <span data-ttu-id="60531-111">Voláním procedury.</span><span class="sxs-lookup"><span data-stu-id="60531-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="60531-112">Následující příklad ukazuje, jak každý tisknout <xref:System.Windows.Forms.TreeNode> objektu <xref:System.Windows.Forms.TreeNode.Text%2A> vlastnost:</span><span class="sxs-lookup"><span data-stu-id="60531-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60531-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="60531-113">See Also</span></span>  
 [<span data-ttu-id="60531-114">TreeView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="60531-114">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="60531-115">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="60531-115">Recursive Procedures</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
