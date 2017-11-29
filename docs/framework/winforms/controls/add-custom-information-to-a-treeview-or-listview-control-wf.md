---
title: "Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)"
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
f1_keywords: ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e7086e52992f575781449e5dc2a83c3443f558d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="753b4-102">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="753b4-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="753b4-103">Můžete vytvořit odvozené uzel ve Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek nebo odvozené položky v <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="753b4-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="753b4-104">Odvození umožňuje přidat všechna pole, které budete potřebovat, a také vlastních metod a konstruktory pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="753b4-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="753b4-105">Jedno použití této funkce je objekt zákazníka připojit na jednotlivé položky seznamu nebo uzel stromu.</span><span class="sxs-lookup"><span data-stu-id="753b4-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="753b4-106">Zde uvedené příklady jsou pro <xref:System.Windows.Forms.TreeView> řízení, ale stejný postup lze použít pro <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="753b4-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="753b4-107">Odvození uzel stromu</span><span class="sxs-lookup"><span data-stu-id="753b4-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="753b4-108">Vytvořte novou třídu uzlu, odvozené od <xref:System.Windows.Forms.TreeNode> třídy, která obsahuje vlastní pole, k zaznamenání cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="753b4-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="753b4-109">Použít uzel odvozené stromu</span><span class="sxs-lookup"><span data-stu-id="753b4-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="753b4-110">Můžete vytvořit nový uzel stromu odvozené jako parametr pro volání funkcí.</span><span class="sxs-lookup"><span data-stu-id="753b4-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="753b4-111">V následujícím příkladu je cesta k umístění textového souboru nastavení složky Dokumenty.</span><span class="sxs-lookup"><span data-stu-id="753b4-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="753b4-112">Důvodem je, že můžete předpokládat, že většina počítačů s operačním systémem Windows budou obsahovat tento adresář.</span><span class="sxs-lookup"><span data-stu-id="753b4-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="753b4-113">To také umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit.</span><span class="sxs-lookup"><span data-stu-id="753b4-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2.  <span data-ttu-id="753b4-114">Pokud se předávají uzlu stromu a je zadán jako <xref:System.Windows.Forms.TreeNode> třídy, pak bude potřeba převést na odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="753b4-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="753b4-115">Přetypování je explicitní převod z jednoho typu objektu na jiný.</span><span class="sxs-lookup"><span data-stu-id="753b4-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="753b4-116">Další informace o přetypování najdete v tématu [implicitní a explicitní převody](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), [() operátor](~/docs/csharp/language-reference/operators/invocation-operator.md) ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]), nebo [operátor přetypování: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) .</span><span class="sxs-lookup"><span data-stu-id="753b4-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="753b4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="753b4-117">See Also</span></span>  
 [<span data-ttu-id="753b4-118">TreeView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="753b4-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="753b4-119">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="753b4-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
