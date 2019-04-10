---
title: 'Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox'
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
ms.openlocfilehash: e61f7743d984d99b1c6811cb1980b97705c304a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223958"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="4f215-102">Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4f215-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="4f215-103">Operace přetažení myší pomocí Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek provádí zpracování <xref:System.Windows.Forms.RichTextBox.DragEnter> a <xref:System.Windows.Forms.RichTextBox.DragDrop> události.</span><span class="sxs-lookup"><span data-stu-id="4f215-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="4f215-104">Proto jsou velmi jednoduché pomocí operace přetažení myší <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4f215-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="4f215-105">Povolení operací přetažení v ovládacím prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4f215-105">To enable drag operations in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="4f215-106">Nastavte <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou `true`.</span><span class="sxs-lookup"><span data-stu-id="4f215-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2.  <span data-ttu-id="4f215-107">Napište kód v obslužné rutině události <xref:System.Windows.Forms.RichTextBox.DragEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="4f215-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="4f215-108">Použití `if` příkaz, ujistěte se, že data jsou kvůli usnadnění použití vypsány přijatelné typ (v tomto případě text).</span><span class="sxs-lookup"><span data-stu-id="4f215-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="4f215-109"><xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> Vlastnost lze nastavit na libovolnou hodnotu z <xref:System.Windows.Forms.DragDropEffects> výčtu.</span><span class="sxs-lookup"><span data-stu-id="4f215-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
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
  
     <span data-ttu-id="4f215-110">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4f215-110">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
3.  <span data-ttu-id="4f215-111">Napište kód pro zpracování <xref:System.Windows.Forms.RichTextBox.DragDrop> událostí.</span><span class="sxs-lookup"><span data-stu-id="4f215-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="4f215-112">Použití <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metodu pro načtení dat se přetáhnout.</span><span class="sxs-lookup"><span data-stu-id="4f215-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="4f215-113">V následujícím příkladu kódu nastaví <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> řídit rovna data jsou kvůli usnadnění použití vypsány.</span><span class="sxs-lookup"><span data-stu-id="4f215-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="4f215-114">Pokud je již v textu <xref:System.Windows.Forms.RichTextBox> ovládací prvek, přetažené text vložíte na pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="4f215-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
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
  
     <span data-ttu-id="4f215-115">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4f215-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="4f215-116">K testování a přetažení funkce ve vaší aplikaci</span><span class="sxs-lookup"><span data-stu-id="4f215-116">To test the drag-and-drop functionality in your application</span></span>  
  
1.  <span data-ttu-id="4f215-117">Uložit a sestavit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4f215-117">Save and build your application.</span></span> <span data-ttu-id="4f215-118">Když je spuštěn, spusťte program WordPad.</span><span class="sxs-lookup"><span data-stu-id="4f215-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="4f215-119">WordPad je textový editor a nainstalované ve Windows, který umožňuje operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="4f215-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="4f215-120">Je přístupná po kliknutí **Start** tlačítka, výběr **spustit**, zadáním `WordPad` v textovém poli **spustit** dialogové okno a potom kliknete na  **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f215-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="4f215-121">Jakmile WordPad otevře, zadejte v něm textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="4f215-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="4f215-122">Pomocí myši, vyberte text a pak přetáhněte vybraný text na <xref:System.Windows.Forms.RichTextBox> ovládacího prvku v aplikaci Windows.</span><span class="sxs-lookup"><span data-stu-id="4f215-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="4f215-123">Všimněte si, že když umístíte ukazatel myši na <xref:System.Windows.Forms.RichTextBox> ovládacího prvku (a v důsledku toho vyvolat <xref:System.Windows.Forms.RichTextBox.DragEnter> událostí), ukazatel myši se změní a budete lze přetáhnout do vybraného textu <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4f215-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="4f215-124">Po uvolnění tlačítka myši se zahodí vybraný text (to znamená, <xref:System.Windows.Forms.RichTextBox.DragDrop> událost je aktivována) a vložení v rámci <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4f215-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f215-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f215-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="4f215-126">Postupy: Provádění operací přetažení mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="4f215-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="4f215-127">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4f215-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="4f215-128">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f215-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
