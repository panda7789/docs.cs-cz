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
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox
Operace přetažení pomocí ovládacího prvku model Windows Forms <xref:System.Windows.Forms.RichTextBox> jsou provedeny zpracováním <xref:System.Windows.Forms.RichTextBox.DragEnter> a <xref:System.Windows.Forms.RichTextBox.DragDrop>ch událostí. Operace přetažení jsou tedy velice jednoduché pomocí ovládacího prvku <xref:System.Windows.Forms.RichTextBox>.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Povolení operací přetažení v ovládacím prvku RichTextBox  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox> na `true`.  
  
2. Napište kód v obslužné rutině události <xref:System.Windows.Forms.RichTextBox.DragEnter> události. Použijte příkaz `if`, abyste zajistili, že přetažená data jsou přijatelného typu (v tomto případě text). Vlastnost <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> lze nastavit na libovolnou hodnotu výčtu <xref:System.Windows.Forms.DragDropEffects>.  
  
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
  
     (Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
3. Napište kód pro zpracování události <xref:System.Windows.Forms.RichTextBox.DragDrop>. K načtení přetažených dat použijte metodu <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType>.  
  
     V následujícím příkladu kód nastaví vlastnost <xref:System.Windows.Forms.RichTextBox.Text%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox>, která se rovná přetahování dat. Pokud je v ovládacím prvku <xref:System.Windows.Forms.RichTextBox> již text, přetaženého textu je vloženo na místo vložení.  
  
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
  
     (Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Testování funkcí přetahování myší v aplikaci  
  
1. Uložte a sestavte aplikaci. Když je spuštěný, spusťte WordPad.  
  
     WordPad je textový editor nainstalovaný systémem Windows, který umožňuje operace přetažení. Je přístupná kliknutím na tlačítko **Start** , výběrem možnosti **Spustit**, zadáním `WordPad` v textovém poli dialogového okna **Spustit** a následným kliknutím na tlačítko **OK**.  
  
2. Po otevření programu WordPad zadejte do něj textový řetězec. Pomocí myši vyberte text a přetáhněte vybraný text do ovládacího prvku <xref:System.Windows.Forms.RichTextBox> v aplikaci pro Windows.  
  
     Všimněte si, že při přesunutí ukazatele myši na ovládací prvek <xref:System.Windows.Forms.RichTextBox> (a následně vyvolání události <xref:System.Windows.Forms.RichTextBox.DragEnter>) se změní ukazatel myši a vybraný text lze vyřadit do ovládacího prvku <xref:System.Windows.Forms.RichTextBox>.  
  
     Po uvolnění tlačítka myši je vybraný text vyřazen (to znamená, <xref:System.Windows.Forms.RichTextBox.DragDrop> událost je aktivována) a je vložen do <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.RichTextBox>
- [Postupy: Provádění operací přetažení mezi aplikacemi](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
