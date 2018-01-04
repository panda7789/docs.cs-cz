---
title: "Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms"
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
helpviewer_keywords:
- SplitContainer control [Windows Forms], examples
- ListView control [Windows Forms], examples
- RichTextBox control [Windows Forms], examples
- Panel control [Windows Forms], examples
- TreeView control [Windows Forms], examples
- Splitter control [Windows Forms], examples
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f29fb5fc4f873431471cd1c037446a5157d5f07c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms
V následujícím postupu vytvoříte více podokny uživatelské rozhraní, které je podobné použít v aplikaci Microsoft Outlook s **složky** seznamu **zprávy** podokně a **Preview** podokně. Toto uspořádání je dosaženo hlavně prostřednictvím ukotvení ovládacích prvků pomocí formuláře.  
  
 V případě ukotvení ovládacího prvku určit, které okraje nadřazeného kontejneru ovládacího prvku je připojen k. Proto pokud nastavíte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Right>, pravý okraj ovládacího prvku bude ukotven na pravý okraj jeho nadřazenému ovládacímu prvku. Kromě toho se změnila ukotveného okraje ovládacího prvku velikost odpovídat jeho ovládacího prvku kontejneru. Další informace o tom, jak <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost funguje, najdete v části [postupy: ukotvení ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Tento postup se zaměřuje na uspořádání <xref:System.Windows.Forms.SplitContainer> a jiných ovládacích prvků na formuláři, nikoli na přidání funkce zpřístupnění aplikace napodobovat Microsoft Outlook.  
  
 Pokud chcete vytvořit toto uživatelské rozhraní, umístěte všechny ovládací prvky v rámci <xref:System.Windows.Forms.SplitContainer> ovládací prvek, který obsahuje <xref:System.Windows.Forms.TreeView> ovládacího prvku v levém panelu. Na pravém panelu <xref:System.Windows.Forms.SplitContainer> ovládací prvek obsahuje druhý <xref:System.Windows.Forms.SplitContainer> řízení s <xref:System.Windows.Forms.ListView> ovládací prvek nahoře <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Tyto <xref:System.Windows.Forms.SplitContainer> ovládací prvky povolit nezávislé změnu velikosti další ovládací prvky na formuláři. Můžete upravit postupy v tomto postupu plavidla vlastní uživatelská rozhraní vlastní.  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>Chcete-li vytvořit uživatelské rozhraní stylu Outlook prostřednictvím kódu programu  
  
1.  Ve formuláři deklarujte každý ovládací prvek, který se skládá z uživatelského rozhraní. V tomto příkladu použijte <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, a <xref:System.Windows.Forms.RichTextBox> ovládacích prvků tak, aby napodoboval uživatelské rozhraní aplikace Microsoft Outlook.  
  
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
  
2.  Vytvoření procedury, která definuje uživatelské rozhraní. Následující kód nastaví vlastnosti tak, aby formuláře budou vypadat podobně jako uživatelské rozhraní v aplikaci Microsoft Outlook. Pomocí další ovládací prvky nebo ukotvení je jinak, je stejně jednoduché vytvořit další uživatelské rozhraní, která se mají stejnou flexibilní.  
  
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
  
3.  V [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], že přidáte volání procedury, kterou jste právě vytvořili `New()` postupu. V [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], přidejte tento řádek kódu do konstruktoru pro třídu formuláře.  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SplitContainer>  
 [Ovládací prvek SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms pomocí Návrháře](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)
