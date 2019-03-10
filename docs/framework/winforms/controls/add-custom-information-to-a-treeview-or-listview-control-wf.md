---
title: 'Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)'
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
ms.openlocfilehash: 40ac3fb3a148c351cf5acca235569e2a1a439a3e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709659"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="4d446-102">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4d446-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="4d446-103">Můžete vytvořit odvozené uzel ve Windows Forms <xref:System.Windows.Forms.TreeView> ovládacího prvku nebo odvozené položky v <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4d446-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="4d446-104">Odvození umožňuje přidejte všechna pole, které potřebujete, a také vlastní metody a konstruktory pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="4d446-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="4d446-105">Jedno použití této funkce je připojit objekt zákazníků na jednotlivé položky seznamu nebo uzlu stromu.</span><span class="sxs-lookup"><span data-stu-id="4d446-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="4d446-106">Příklady v tomto článku jsou určené pro <xref:System.Windows.Forms.TreeView> ovládacího prvku, ale stejný postup lze použít pro <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4d446-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="4d446-107">K odvození uzlu stromu</span><span class="sxs-lookup"><span data-stu-id="4d446-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="4d446-108">Vytvořte novou třídu uzlu, odvozený z <xref:System.Windows.Forms.TreeNode> třídu, která má vlastní pole do záznamu cesty souboru.</span><span class="sxs-lookup"><span data-stu-id="4d446-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="4d446-109">Určený uzel odvozené stromu</span><span class="sxs-lookup"><span data-stu-id="4d446-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="4d446-110">Nový uzel stromu odvozené můžete použít jako parametr pro volání funkce.</span><span class="sxs-lookup"><span data-stu-id="4d446-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="4d446-111">V následujícím příkladu je cesta k umístění textového souboru nastavení složky Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="4d446-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="4d446-112">Důvodem je, že budete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="4d446-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="4d446-113">Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d446-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
    treeView1.Nodes.Add(new myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
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
  
2.  <span data-ttu-id="4d446-114">Pokud jsou předány uzlu stromu a je typovaný jako <xref:System.Windows.Forms.TreeNode> třídy, je třeba přetypovat na odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="4d446-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="4d446-115">Přetypování je explicitní převod z jednoho typu objektu na jiný.</span><span class="sxs-lookup"><span data-stu-id="4d446-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="4d446-116">Další informace o přetypování, naleznete v tématu [implicitní a explicitní převody](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [() operátor](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), nebo [operátor přetypování: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) .</span><span class="sxs-lookup"><span data-stu-id="4d446-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d446-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d446-117">See also</span></span>
- [<span data-ttu-id="4d446-118">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="4d446-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="4d446-119">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="4d446-119">ListView Control</span></span>](listview-control-windows-forms.md)
