---
title: 'Postup: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
ms.openlocfilehash: faed586a5814526b0169ea46c8bb452e3777d8ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182427"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)
Odvozený uzel můžete vytvořit v ovládacím prvku Windows Forms <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.ListView> nebo odvozené položky v ovládacím prvku. Derivation umožňuje přidat všechna pole, která požadujete, stejně jako vlastní metody a konstruktory pro jejich zpracování. Jedním z použití této funkce je připojit objekt Zákazník a každý uzel stromu nebo položku seznamu. Příklady zde jsou <xref:System.Windows.Forms.TreeView> pro ovládací prvek, ale stejný <xref:System.Windows.Forms.ListView> přístup lze použít pro ovládací prvek.  
  
### <a name="to-derive-a-tree-node"></a>Odvození uzlu stromu  
  
- Vytvořte novou třídu uzlu odvozenou od <xref:System.Windows.Forms.TreeNode> třídy, která má vlastní pole pro záznam cesty k souboru.  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### <a name="to-use-a-derived-tree-node"></a>Použití odvozeného uzlu stromu  
  
1. Nový odvozený uzel stromu můžete použít jako parametr pro volání.  
  
     V níže uvedeném příkladu je cesta nastavená pro umístění textového souboru složka Dokumenty. Důvodem je, že můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.  
  
    ```vb  
    ' You should replace the bold text file
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
    ```  
  
    ```csharp  
    // You should replace the bold text file
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\TextFile.txt") );  
    ```  
  
    ```cpp  
    // You should replace the bold text file
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2. Pokud jste předány uzel stromu <xref:System.Windows.Forms.TreeNode> a je zadán jako třída, pak budete muset přetypovat do odvozené třídy. Přetypování je explicitní převod z jednoho typu objektu na jiný. Další informace o přetypování naleznete [v tématu implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#) nebo [operátor přetypování: ()](/cpp/cpp/cast-operator-parens) (Visual C++).  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",
             myNode->FilePath));  
       }  
    ```  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [ListView – ovládací prvek](listview-control-windows-forms.md)
