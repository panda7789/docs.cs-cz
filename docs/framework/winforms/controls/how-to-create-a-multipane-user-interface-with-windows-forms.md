---
title: Vytvoření uživatelského rozhraní s více podokny
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
ms.openlocfilehash: 4b168a6d566e20814d4403f90e157d80efe3bf12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731334"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms
V následujícím postupu vytvoříte uživatelské rozhraní s více podokny, které je podobné jako v aplikaci Microsoft Outlook, seznam **složek** , podokno **zprávy** a podokno **náhledu** . Toto uspořádání se dosahuje hlavně prostřednictvím ovládacích prvků docking s formulářem.  
  
 Při ukotvení ovládacího prvku určíte, na který okraj nadřazeného kontejneru je ovládací prvek připevněný. Proto pokud nastavíte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Right>, pravý okraj ovládacího prvku bude ukotven k pravému okraji svého nadřazeného ovládacího prvku. Kromě toho je ukotvená hrana ovládacího prvku změněna tak, aby odpovídala jeho ovládacímu prvku kontejneru. Další informace o tom, jak vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A> funguje, naleznete v tématu [How to: Dock Controls on model Windows Forms](how-to-dock-controls-on-windows-forms.md).  
  
 Tento postup se zaměřuje na uspořádání <xref:System.Windows.Forms.SplitContainer> a dalších ovládacích prvků ve formuláři, nikoli při přidávání funkcí, které aplikaci napodobují aplikaci Microsoft Outlook.  
  
 Chcete-li vytvořit toto uživatelské rozhraní, umístěte všechny ovládací prvky v rámci ovládacího prvku <xref:System.Windows.Forms.SplitContainer>, který obsahuje ovládací prvek <xref:System.Windows.Forms.TreeView> na levém panelu. Pravé podokno ovládacího prvku <xref:System.Windows.Forms.SplitContainer> obsahuje druhý ovládací prvek <xref:System.Windows.Forms.SplitContainer> s ovládacím prvkem <xref:System.Windows.Forms.ListView> nad <xref:System.Windows.Forms.RichTextBox> ovládací prvek. Tyto ovládací prvky <xref:System.Windows.Forms.SplitContainer> umožňují nezávislé změny velikosti ostatních ovládacích prvků ve formuláři. Techniky v tomto postupu můžete přizpůsobit a vytvořit vlastní uživatelská rozhraní.  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>Chcete-li vytvořit uživatelské rozhraní ve stylu aplikace Outlook prostřednictvím kódu programu  
  
1. V rámci formuláře deklarujte každý ovládací prvek, který zahrnuje vaše uživatelské rozhraní. V tomto příkladu použijte ovládací prvky <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>a <xref:System.Windows.Forms.RichTextBox> k napodobování uživatelského rozhraní aplikace Microsoft Outlook.  
  
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
  
2. Vytvořte proceduru, která definuje vaše uživatelské rozhraní. Následující kód nastaví vlastnosti tak, aby se formulář podobat uživatelskému rozhraní aplikace Microsoft Outlook. Pokud však použijete jiné ovládací prvky nebo je lze ukotvit jinak, je stejně snadné vytvořit další uživatelská rozhraní, která jsou rovnoměrně flexibilní.  
  
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
  
3. V Visual Basic přidejte volání procedury, kterou jste právě vytvořili v proceduře `New()`. V vizuálu C#přidejte tento řádek kódu do konstruktoru pro třídu Form.  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.SplitContainer>
- [Ovládací prvek SplitContainer](splitcontainer-control-windows-forms.md)
- [Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms pomocí Návrháře](create-a-multipane-user-interface-with-wf-using-the-designer.md)
