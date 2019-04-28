---
title: 'Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], examples
- ListView control [Windows Forms], examples
- RichTextBox control [Windows Forms], examples
- Panel control [Windows Forms], examples
- TreeView control [Windows Forms], examples
- Splitter control [Windows Forms], examples
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
ms.openlocfilehash: 8650ba3b8011e50779080e31d94727609f2d08f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747092"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a><span data-ttu-id="5d3a9-102">Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d3a9-102">How to: Create a Multipane User Interface with Windows Forms</span></span>
<span data-ttu-id="5d3a9-103">V následujícím postupu vytvoříte, který je podobný tomu použitému v aplikaci Microsoft Outlook s více podokny uživatelské rozhraní **složky** seznamu, **zprávy** podokně a **veverziPreview** podokně.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-103">In the following procedure, you will create a multipane user interface that is similar to the one used in Microsoft Outlook, with a **Folder** list, a **Messages** pane, and a **Preview** pane.</span></span> <span data-ttu-id="5d3a9-104">Toto uspořádání se dosahuje hlavně prostřednictvím Ukotvování ovládacích prvků ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-104">This arrangement is achieved chiefly through docking controls with the form.</span></span>  
  
 <span data-ttu-id="5d3a9-105">Můžete ukotvit ovládacího prvku, zjistíte, které okrajem nadřazeného kontejneru ovládacího prvku je připojen k.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-105">When you dock a control, you determine which edge of the parent container a control is fastened to.</span></span> <span data-ttu-id="5d3a9-106">Proto pokud nastavíte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Right>, pravým okrajem ovládacího prvku se ukotven k pravým okrajem jeho nadřazeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-106">Thus, if you set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Right>, the right edge of the control will be docked to the right edge of its parent control.</span></span> <span data-ttu-id="5d3a9-107">Kromě toho ukotvených okrajem ovládacího prvku svou velikost tak, aby odpovídaly u ovládacího prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-107">Additionally, the docked edge of the control is resized to match that of its container control.</span></span> <span data-ttu-id="5d3a9-108">Další informace o tom, jak <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost funguje, najdete v článku [jak: Ukotvování ovládacích prvků ve Windows Forms](how-to-dock-controls-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5d3a9-108">For more information about how the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property works, see [How to: Dock Controls on Windows Forms](how-to-dock-controls-on-windows-forms.md).</span></span>  
  
 <span data-ttu-id="5d3a9-109">Tento postup se zaměřuje na uspořádání <xref:System.Windows.Forms.SplitContainer> a další ovládací prvky ve formuláři, nikoli na přidání funkce do aplikace, které napodobují aplikace Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-109">This procedure focuses on arranging the <xref:System.Windows.Forms.SplitContainer> and the other controls on the form, not on adding functionality to make the application mimic Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="5d3a9-110">K vytvoření tohoto uživatelského rozhraní, umístěte všechny ovládací prvky v rámci <xref:System.Windows.Forms.SplitContainer> ovládací prvek, který obsahuje <xref:System.Windows.Forms.TreeView> ovládacího prvku na panelu vlevo.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-110">To create this user interface, you place all the controls within a <xref:System.Windows.Forms.SplitContainer> control, which contains a <xref:System.Windows.Forms.TreeView> control in the left-hand panel.</span></span> <span data-ttu-id="5d3a9-111">Na pravém panelu <xref:System.Windows.Forms.SplitContainer> ovládací prvek obsahuje druhý <xref:System.Windows.Forms.SplitContainer> ovládacím prvkem <xref:System.Windows.Forms.ListView> ovládací prvek výše <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-111">The right-hand panel of the <xref:System.Windows.Forms.SplitContainer> control contains a second <xref:System.Windows.Forms.SplitContainer> control with a <xref:System.Windows.Forms.ListView> control above a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="5d3a9-112">Tyto <xref:System.Windows.Forms.SplitContainer> ovládací prvky umožňují nezávislé Změna velikosti jiných ovládacích prvků ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-112">These <xref:System.Windows.Forms.SplitContainer> controls enable independent resizing of the other controls on the form.</span></span> <span data-ttu-id="5d3a9-113">Můžete upravit postupy v tomto postupu vytváření vlastního uživatelského rozhraní vlastní.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-113">You can adapt the techniques in this procedure to craft custom user interfaces of your own.</span></span>  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a><span data-ttu-id="5d3a9-114">Chcete-li vytvořit uživatelským rozhraním stylu aplikace Outlook prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5d3a9-114">To create an Outlook-style user interface programmatically</span></span>  
  
1. <span data-ttu-id="5d3a9-115">Ve formuláři deklarujte každý ovládací prvek, který se skládá z uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-115">Within a form, declare each control that comprises your user interface.</span></span> <span data-ttu-id="5d3a9-116">V tomto příkladu použijte <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, a <xref:System.Windows.Forms.RichTextBox> ovládacích prvků tak, aby napodoboval uživatelského rozhraní aplikace Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-116">For this example, use the <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, and <xref:System.Windows.Forms.RichTextBox> controls to mimic the Microsoft Outlook user interface.</span></span>  
  
    ```vb  
    Private WithEvents treeView1 As System.Windows.Forms.TreeView  
    Private WithEvents listView1 As System.Windows.Forms.ListView  
    Private WithEvents richTextBox1 As System.Windows.Forms.RichTextBox  
    Private WithEvents splitContainer1 As _  
        System.Windows.Forms.SplitContainer  
    Private WithEvents splitContainer2 As _  
        System.Windows.Forms.SplitContainer  
    ```  
  
    ```csharp  
    private System.Windows.Forms.TreeView treeView1;  
    private System.Windows.Forms.ListView listView1;  
    private System.Windows.Forms.RichTextBox richTextBox1;  
    private System.Windows.Forms. SplitContainer splitContainer2;  
    private System.Windows.Forms. SplitContainer splitContainer1;  
    ```  
  
2. <span data-ttu-id="5d3a9-117">Vytvořte proceduru, která definuje uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-117">Create a procedure that defines your user interface.</span></span> <span data-ttu-id="5d3a9-118">Následující kód nastaví vlastnosti tak, aby formuláře budou vypadat podobně jako na uživatelské rozhraní v aplikaci Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-118">The following code sets the properties so that the form will resemble the user interface in Microsoft Outlook.</span></span> <span data-ttu-id="5d3a9-119">Pomocí další ovládací prvky nebo je jinak ukotvení, je stejně snadné vytvořit další uživatelské rozhraní, které jsou stejně flexibilní.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-119">However, by using other controls or docking them differently, it is just as easy to create other user interfaces that are equally flexible.</span></span>  
  
    ```vb  
    Public Sub CreateOutlookUI()  
        ' Create an instance of each control being used.  
        Me.components = New System.ComponentModel.Container()  
        Me.treeView1 = New System.Windows.Forms.TreeView()  
        Me.listView1 = New System.Windows.Forms.ListView()  
        Me.richTextBox1 = New System.Windows.Forms.RichTextBox()  
        Me.splitContainer1 = New System.Windows.Forms.SplitContainer()  
        Me.splitContainer2= New System.Windows.Forms. SplitContainer()  
  
        ' Should you develop this into a working application,  
        ' use the AddHandler method to hook up event procedures here.  
  
        ' Set properties of TreeView control.  
        ' Use the With statement to avoid repetitive code.  
        With Me.treeView1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 0  
            .Nodes.Add("treeView")  
        End With  
  
    ' Set properties of ListView control.  
       With Me.listView1  
          .Dock = System.Windows.Forms.DockStyle.Top  
          .TabIndex = 2  
          .Items.Add("listView")  
       End With  
  
    ' Set properties of RichTextBox control.  
       With Me.richTextBox1  
          .Dock = System.Windows.Forms.DockStyle.Fill  
          .TabIndex = 3  
          .Text = "richTextBox1"  
       End With  
  
        ' Set properties of the first SplitContainer control.  
        With Me.splitContainer1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 1  
            .SplitterWidth = 4  
            .SplitterDistance = 150  
            .Orientation = Orientation.Horizontal  
            .Panel1.Controls.Add(Me.listView1)  
            .Panel2.Controls.Add(Me.richTextBox1)  
    End With  
  
        ' Set properties of the second SplitContainer control.  
        With Me.splitContainer2  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 4  
            .SplitterWidth = 4  
            .SplitterDistance = 100  
            .Panel1.Controls.Add(Me.treeView1)  
            .Panel2.Controls.Add(Me.SplitContainer1)  
    End With  
  
    ' Add the main SplitContainer control to the form.  
        Me.Controls.Add(Me.splitContainer2)  
        Me.Text = "Intricate UI Example"  
    End Sub  
    ```  
  
    ```csharp  
    public void createOutlookUI()  
    {  
        // Create an instance of each control being used.  
        treeView1 = new System.Windows.Forms.TreeView();  
        listView1 = new System.Windows.Forms.ListView();  
        richTextBox1 = new System.Windows.Forms.RichTextBox();  
        splitContainer2 = new System.Windows.Forms.SplitContainer();  
        splitContainer1 = new System.Windows.Forms.SplitContainer();  
  
        // Insert code here to hook up event methods.  
  
        // Set properties of TreeView control.  
        treeView1.Dock = System.Windows.Forms.DockStyle.Fill;  
        treeView1.TabIndex = 0;  
        treeView1.Nodes.Add("treeView");  
  
        // Set properties of ListView control.  
        listView1.Dock = System.Windows.Forms.DockStyle.Top;  
        listView1.TabIndex = 2;  
        listView1.Items.Add("listView");  
  
        // Set properties of RichTextBox control.  
        richTextBox1.Dock = System.Windows.Forms.DockStyle.Fill;  
        richTextBox1.TabIndex = 3;  
        richTextBox1.Text = "richTextBox1";  
  
        // Set properties of first SplitContainer control.  
        splitContainer1.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 1;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 150;  
        splitContainer2.Orientation = Orientation.Horizontal;  
        splitContainer2.Panel1.Controls.Add(this.listView1);  
        splitContainer2.Panel1.Controls.Add(this.richTextBox1);  
  
        // Set properties of second SplitContainer control.  
        splitContainer2.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 4;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 100;  
        splitContainer2.Panel1.Controls.Add(this.treeView1);  
        splitContainer2.Panel1.Controls.Add(this.splitContainer1);  
  
        // Add the main SplitContainer control to the form.  
        this.Controls.Add(this.splitContainer2);  
        this.Text = "Intricate UI Example";  
    }  
    ```  
  
3. <span data-ttu-id="5d3a9-120">V jazyce Visual Basic přidejte volání do procedury, kterou jste právě vytvořili `New()` postup.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-120">In Visual Basic, add a call to the procedure you just created in the `New()` procedure.</span></span> <span data-ttu-id="5d3a9-121">Ve Vizuálu C#, přidejte následující řádek kódu do konstruktoru třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="5d3a9-121">In Visual C#, add this line of code to the constructor for the form class.</span></span>  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5d3a9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d3a9-122">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="5d3a9-123">Ovládací prvek SplitContainer</span><span class="sxs-lookup"><span data-stu-id="5d3a9-123">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
- [<span data-ttu-id="5d3a9-124">Postupy: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5d3a9-124">How to: Create a Multipane User Interface with Windows Forms Using the Designer</span></span>](create-a-multipane-user-interface-with-wf-using-the-designer.md)
