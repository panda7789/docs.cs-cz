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
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox
Operace přetažení maže pomocí <xref:System.Windows.Forms.RichTextBox> ovládacího prvku <xref:System.Windows.Forms.RichTextBox.DragEnter> Windows <xref:System.Windows.Forms.RichTextBox.DragDrop> Forms se provádějí zpracováním událostí a. Proto drag-and-drop operace jsou velmi <xref:System.Windows.Forms.RichTextBox> jednoduché s ovládacím prvkem.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Povolení operací přetažení v ovládacím prvku RichTextBox  
  
1. Nastavte <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> vlastnost ovládacího <xref:System.Windows.Forms.RichTextBox> `true`prvku na .  
  
2. Napište kód do obslužné rutiny <xref:System.Windows.Forms.RichTextBox.DragEnter> události. Pomocí `if` příkazu zajistěte, aby přetahovaná data byla přijatelného typu (v tomto případě text). Vlastnost <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> může být nastavena na <xref:System.Windows.Forms.DragDropEffects> libovolnou hodnotu výčtu.  
  
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
  
     (Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
3. Napište kód <xref:System.Windows.Forms.RichTextBox.DragDrop> pro zpracování události. Pomocí <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metody načtěte přetažená data.  
  
     V níže uvedeném příkladu <xref:System.Windows.Forms.RichTextBox.Text%2A> kód <xref:System.Windows.Forms.RichTextBox> nastaví vlastnost ovládacího prvku rovnající se přetahovaná data. Pokud již je v <xref:System.Windows.Forms.RichTextBox> ovládacím prvku text, přetažený text se vloží do kurzoru.  
  
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
  
     (Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Testování funkce přetažení myší v aplikaci  
  
1. Uložte a sestavte aplikaci. Během spuštění spusťte wordpad.  
  
     WordPad je textový editor nainstalovaný systémem Windows, který umožňuje operace přetažení myší. Je přístupná klepnutím na tlačítko **Start,** výběrem **možnosti Spustit**, `WordPad` zadáním textového pole dialogového okna **Spustit** a následným klepnutím na **tlačítko OK**.  
  
2. Po otevření wordpadu do něj zadejte řetězec textu. Pomocí myši vyberte text a přetáhněte vybraný text <xref:System.Windows.Forms.RichTextBox> do ovládacího prvku v aplikaci systému Windows.  
  
     Všimněte si, že když <xref:System.Windows.Forms.RichTextBox> namíříte myš na <xref:System.Windows.Forms.RichTextBox.DragEnter> ovládací prvek (a v důsledku toho vyvoláte událost), změní se ukazatel myši a vybraný text můžete přetáhnout do ovládacího <xref:System.Windows.Forms.RichTextBox> prvku.  
  
     Když uvolníte tlačítko myši, vybraný text je vynechán <xref:System.Windows.Forms.RichTextBox.DragDrop> (to znamená, že událost <xref:System.Windows.Forms.RichTextBox> je aktivována) a je vložen do ovládacího prvku.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.RichTextBox>
- [Postupy: Provádění operací přetažení mezi aplikacemi](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
