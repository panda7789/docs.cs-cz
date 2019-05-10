---
title: 'Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)'
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
ms.openlocfilehash: 9e2942e11ed10dffcfad8f0329295827b7f0d4d8
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452739"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)
Můžete vytvořit odvozené uzel ve Windows Forms <xref:System.Windows.Forms.TreeView> ovládacího prvku nebo odvozené položky v <xref:System.Windows.Forms.ListView> ovládacího prvku. Odvození umožňuje přidejte všechna pole, které potřebujete, a také vlastní metody a konstruktory pro jejich zpracování. Jedno použití této funkce je připojit objekt zákazníků na jednotlivé položky seznamu nebo uzlu stromu. Příklady v tomto článku jsou určené pro <xref:System.Windows.Forms.TreeView> ovládacího prvku, ale stejný postup lze použít pro <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
### <a name="to-derive-a-tree-node"></a>K odvození uzlu stromu  
  
- Vytvořte novou třídu uzlu, odvozený z <xref:System.Windows.Forms.TreeNode> třídu, která má vlastní pole do záznamu cesty souboru.  
  
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
  
### <a name="to-use-a-derived-tree-node"></a>Určený uzel odvozené stromu  
  
1. Nový uzel stromu odvozené můžete použít jako parametr pro volání funkce.  
  
     V následujícím příkladu je cesta k umístění textového souboru nastavení složky Dokumenty. Důvodem je, že budete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace.  
  
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
  
2. Pokud jsou předány uzlu stromu a je typovaný jako <xref:System.Windows.Forms.TreeNode> třídy, je třeba přetypovat na odvozenou třídu. Přetypování je explicitní převod z jednoho typu objektu na jiný. Další informace o přetypování, naleznete v tématu [implicitní a explicitní převody](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [přetypování a převody typu](~/docs/csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#), nebo [operátor přetypování: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) .  
  
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
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [Ovládací prvek ListView](listview-control-windows-forms.md)
