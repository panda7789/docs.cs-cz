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
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView
Někdy je vhodné prostudovat každý uzel v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.TreeView> , aby bylo možné provést určitý výpočet hodnot uzlů. Tuto operaci lze provést pomocí rekurzivní procedury (rekurzivní metody v C# a C++), která projde každým uzlem v každé kolekci stromu.  
  
 Každý <xref:System.Windows.Forms.TreeNode> objekt ve stromovém zobrazení má vlastnosti, které lze použít k procházení stromového zobrazení: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>a <xref:System.Windows.Forms.TreeNode.Parent%2A>. Hodnota <xref:System.Windows.Forms.TreeNode.Parent%2A> vlastnosti je nadřazeným uzlem aktuálního uzlu. Podřízené uzly aktuálního uzlu, pokud existují, jsou uvedeny ve své <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastnosti. Samotný ovládací prvek <xref:System.Windows.Forms.TreeView.TopNode%2A> má vlastnost, která je kořenovým uzlem celého stromového zobrazení. <xref:System.Windows.Forms.TreeView>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>Iterace všemi uzly ovládacího prvku TreeView  
  
1. Vytvořte rekurzivní proceduru (rekurzivní metodu v C# a C++), která testuje každý uzel.  
  
2. Zavolejte proceduru.  
  
     Následující příklad ukazuje, jak vytisknout <xref:System.Windows.Forms.TreeNode> <xref:System.Windows.Forms.TreeNode.Text%2A> vlastnost jednotlivých objektů:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [Rekurzivní procedury](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
