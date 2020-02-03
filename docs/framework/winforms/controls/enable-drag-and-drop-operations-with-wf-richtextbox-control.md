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
ms.openlocfilehash: 3c17560dee012912aea2938654f1dc4dc56e0725
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745820"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="4b589-102">Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4b589-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="4b589-103">Operace přetažení pomocí ovládacího prvku model Windows Forms <xref:System.Windows.Forms.RichTextBox> jsou provedeny zpracováním <xref:System.Windows.Forms.RichTextBox.DragEnter> a <xref:System.Windows.Forms.RichTextBox.DragDrop>ch událostí.</span><span class="sxs-lookup"><span data-stu-id="4b589-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="4b589-104">Operace přetažení jsou tedy velice jednoduché pomocí ovládacího prvku <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="4b589-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="4b589-105">Povolení operací přetažení v ovládacím prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4b589-105">To enable drag operations in a RichTextBox control</span></span>  
  
1. <span data-ttu-id="4b589-106">Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox> na `true`.</span><span class="sxs-lookup"><span data-stu-id="4b589-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2. <span data-ttu-id="4b589-107">Napište kód v obslužné rutině události <xref:System.Windows.Forms.RichTextBox.DragEnter> události.</span><span class="sxs-lookup"><span data-stu-id="4b589-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="4b589-108">Použijte příkaz `if`, abyste zajistili, že přetažená data jsou přijatelného typu (v tomto případě text).</span><span class="sxs-lookup"><span data-stu-id="4b589-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="4b589-109">Vlastnost <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> lze nastavit na libovolnou hodnotu výčtu <xref:System.Windows.Forms.DragDropEffects>.</span><span class="sxs-lookup"><span data-stu-id="4b589-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
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
  
     <span data-ttu-id="4b589-110">(Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4b589-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
3. <span data-ttu-id="4b589-111">Napište kód pro zpracování události <xref:System.Windows.Forms.RichTextBox.DragDrop>.</span><span class="sxs-lookup"><span data-stu-id="4b589-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="4b589-112">K načtení přetažených dat použijte metodu <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b589-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="4b589-113">V následujícím příkladu kód nastaví vlastnost <xref:System.Windows.Forms.RichTextBox.Text%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox>, která se rovná přetahování dat.</span><span class="sxs-lookup"><span data-stu-id="4b589-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="4b589-114">Pokud je v ovládacím prvku <xref:System.Windows.Forms.RichTextBox> již text, přetaženého textu je vloženo na místo vložení.</span><span class="sxs-lookup"><span data-stu-id="4b589-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
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
  
     <span data-ttu-id="4b589-115">(Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4b589-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="4b589-116">Testování funkcí přetahování myší v aplikaci</span><span class="sxs-lookup"><span data-stu-id="4b589-116">To test the drag-and-drop functionality in your application</span></span>  
  
1. <span data-ttu-id="4b589-117">Uložte a sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4b589-117">Save and build your application.</span></span> <span data-ttu-id="4b589-118">Když je spuštěný, spusťte WordPad.</span><span class="sxs-lookup"><span data-stu-id="4b589-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="4b589-119">WordPad je textový editor nainstalovaný systémem Windows, který umožňuje operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="4b589-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="4b589-120">Je přístupná kliknutím na tlačítko **Start** , výběrem možnosti **Spustit**, zadáním `WordPad` v textovém poli dialogového okna **Spustit** a následným kliknutím na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b589-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="4b589-121">Po otevření programu WordPad zadejte do něj textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="4b589-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="4b589-122">Pomocí myši vyberte text a přetáhněte vybraný text do ovládacího prvku <xref:System.Windows.Forms.RichTextBox> v aplikaci pro Windows.</span><span class="sxs-lookup"><span data-stu-id="4b589-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="4b589-123">Všimněte si, že při přesunutí ukazatele myši na ovládací prvek <xref:System.Windows.Forms.RichTextBox> (a následně vyvolání události <xref:System.Windows.Forms.RichTextBox.DragEnter>) se změní ukazatel myši a vybraný text lze vyřadit do ovládacího prvku <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="4b589-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="4b589-124">Po uvolnění tlačítka myši je vybraný text vyřazen (to znamená, <xref:System.Windows.Forms.RichTextBox.DragDrop> událost je aktivována) a je vložen do <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b589-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b589-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b589-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="4b589-126">Postupy: Provádění operací přetažení mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="4b589-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="4b589-127">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4b589-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="4b589-128">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b589-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
