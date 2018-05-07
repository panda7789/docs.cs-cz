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
ms.openlocfilehash: 89a2c1411ab64b4a20ad291165cfa6d83511c4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView
Někdy je užitečné k prozkoumání každý uzel ve Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek, aby bylo možné provést některé výpočet hodnot uzlu. Tuto operaci lze provést pomocí postupu rekurzivní (rekurzivní metody v jazyce C# a C++), který iteruje každý uzel v každé z kolekcí stromu.  
  
 Každý <xref:System.Windows.Forms.TreeNode> objekt ve stromovém zobrazení má vlastnosti, které můžete použít k zobrazení stromu přejděte: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, a <xref:System.Windows.Forms.TreeNode.Parent%2A>. Hodnota <xref:System.Windows.Forms.TreeNode.Parent%2A> vlastnost je nadřazený uzel aktuální uzel. Podřízené uzly z aktuálního uzlu, pokud jsou k dispozici jsou uvedeny v jeho <xref:System.Windows.Forms.TreeNode.Nodes%2A> vlastnost. <xref:System.Windows.Forms.TreeView> Má vlastní ovládací prvek <xref:System.Windows.Forms.TreeView.TopNode%2A> vlastnost, která je kořenový uzel stromu celého zobrazení.  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>Chcete-li iterace všemi uzly ovládacího prvku TreeView  
  
1.  Vytvoření rekurzivní procedury (rekurzivní metody v jazyce C# a C++), který testuje každý uzel.  
  
2.  Voláním procedury.  
  
     Následující příklad ukazuje, jak každý tisknout <xref:System.Windows.Forms.TreeNode> objektu <xref:System.Windows.Forms.TreeNode.Text%2A> vlastnost:  
  
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
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Rekurzivní procedury](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
