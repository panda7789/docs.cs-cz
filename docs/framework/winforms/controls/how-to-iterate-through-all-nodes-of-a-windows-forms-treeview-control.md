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
ms.openlocfilehash: c6345ab5e5d4f4e480bb2724e7a1d795de2bef5d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651848"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView
Někdy je užitečné si prohlédnout každý uzel ve Windows Forms <xref:System.Windows.Forms.TreeView> ovládacího prvku, aby bylo možné provést některé výpočtu pro hodnoty uzlu. Tuto operaci lze provést pomocí rekurzivní procedury (rekurzivní metodu v C# a C++), který prochází každý uzel v každé z kolekcí stromu.  
  
 Každý <xref:System.Windows.Forms.TreeNode> objektu ve stromovém zobrazení má vlastnosti, které můžete použít k navigaci ve stromovém zobrazení: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, a <xref:System.Windows.Forms.TreeNode.Parent%2A>. Hodnota <xref:System.Windows.Forms.TreeNode.Parent%2A> vlastnost je nadřazený uzel pro aktuální uzel. Podřízené uzly pro aktuální uzel, pokud existují, jsou uvedeny v jeho <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastnost. <xref:System.Windows.Forms.TreeView> Samotný ovládací prvek má <xref:System.Windows.Forms.TreeView.TopNode%2A> vlastnost, která je kořenový uzel celý strom.  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>K iteraci v rámci všech uzlů v ovládacím prvku TreeView  
  
1.  Vytvoření rekurzivní procedury (rekurzivní metodu v C# a C++), který testuje každý uzel.  
  
2.  Zavolejte proceduru.  
  
     Následující příklad ukazuje, jak vytisknout každý <xref:System.Windows.Forms.TreeNode> objektu <xref:System.Windows.Forms.TreeNode.Text%2A> vlastnost:  
  
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
- [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [Rekurzivní procedury](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
