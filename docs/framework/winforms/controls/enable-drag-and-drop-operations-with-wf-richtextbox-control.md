---
title: Povolení operací přetažení pomocí ovládacího prvku RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 27e5c18598552c465ef17f5e58069bc10e401c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182354"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="d25aa-102">Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d25aa-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="d25aa-103">Operace přetažení maže pomocí <xref:System.Windows.Forms.RichTextBox> ovládacího prvku <xref:System.Windows.Forms.RichTextBox.DragEnter> Windows <xref:System.Windows.Forms.RichTextBox.DragDrop> Forms se provádějí zpracováním událostí a.</span><span class="sxs-lookup"><span data-stu-id="d25aa-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="d25aa-104">Proto drag-and-drop operace jsou velmi <xref:System.Windows.Forms.RichTextBox> jednoduché s ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="d25aa-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="d25aa-105">Povolení operací přetažení v ovládacím prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d25aa-105">To enable drag operations in a RichTextBox control</span></span>  
  
1. <span data-ttu-id="d25aa-106">Nastavte <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> vlastnost ovládacího <xref:System.Windows.Forms.RichTextBox> `true`prvku na .</span><span class="sxs-lookup"><span data-stu-id="d25aa-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2. <span data-ttu-id="d25aa-107">Napište kód do obslužné rutiny <xref:System.Windows.Forms.RichTextBox.DragEnter> události.</span><span class="sxs-lookup"><span data-stu-id="d25aa-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="d25aa-108">Pomocí `if` příkazu zajistěte, aby přetahovaná data byla přijatelného typu (v tomto případě text).</span><span class="sxs-lookup"><span data-stu-id="d25aa-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="d25aa-109">Vlastnost <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> může být nastavena na <xref:System.Windows.Forms.DragDropEffects> libovolnou hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="d25aa-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     <span data-ttu-id="d25aa-110">(Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d25aa-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. <span data-ttu-id="d25aa-111">Napište kód <xref:System.Windows.Forms.RichTextBox.DragDrop> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="d25aa-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="d25aa-112">Pomocí <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metody načtěte přetažená data.</span><span class="sxs-lookup"><span data-stu-id="d25aa-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="d25aa-113">V níže uvedeném příkladu <xref:System.Windows.Forms.RichTextBox.Text%2A> kód <xref:System.Windows.Forms.RichTextBox> nastaví vlastnost ovládacího prvku rovnající se přetahovaná data.</span><span class="sxs-lookup"><span data-stu-id="d25aa-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="d25aa-114">Pokud již je v <xref:System.Windows.Forms.RichTextBox> ovládacím prvku text, přetažený text se vloží do kurzoru.</span><span class="sxs-lookup"><span data-stu-id="d25aa-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragDrop  
       Dim i As Int16
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     <span data-ttu-id="d25aa-115">(Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d25aa-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="d25aa-116">Testování funkce přetažení myší v aplikaci</span><span class="sxs-lookup"><span data-stu-id="d25aa-116">To test the drag-and-drop functionality in your application</span></span>  
  
1. <span data-ttu-id="d25aa-117">Uložte a sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d25aa-117">Save and build your application.</span></span> <span data-ttu-id="d25aa-118">Během spuštění spusťte wordpad.</span><span class="sxs-lookup"><span data-stu-id="d25aa-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="d25aa-119">WordPad je textový editor nainstalovaný systémem Windows, který umožňuje operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="d25aa-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="d25aa-120">Je přístupná klepnutím na tlačítko **Start,** výběrem **možnosti Spustit**, `WordPad` zadáním textového pole dialogového okna **Spustit** a následným klepnutím na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="d25aa-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="d25aa-121">Po otevření wordpadu do něj zadejte řetězec textu.</span><span class="sxs-lookup"><span data-stu-id="d25aa-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="d25aa-122">Pomocí myši vyberte text a přetáhněte vybraný text <xref:System.Windows.Forms.RichTextBox> do ovládacího prvku v aplikaci systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d25aa-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="d25aa-123">Všimněte si, že když <xref:System.Windows.Forms.RichTextBox> namíříte myš na <xref:System.Windows.Forms.RichTextBox.DragEnter> ovládací prvek (a v důsledku toho vyvoláte událost), změní se ukazatel myši a vybraný text můžete přetáhnout do ovládacího <xref:System.Windows.Forms.RichTextBox> prvku.</span><span class="sxs-lookup"><span data-stu-id="d25aa-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="d25aa-124">Když uvolníte tlačítko myši, vybraný text je vynechán <xref:System.Windows.Forms.RichTextBox.DragDrop> (to znamená, že událost <xref:System.Windows.Forms.RichTextBox> je aktivována) a je vložen do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d25aa-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d25aa-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d25aa-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="d25aa-126">Postupy: Provádění operací přetažení mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="d25aa-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="d25aa-127">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d25aa-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="d25aa-128">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d25aa-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
