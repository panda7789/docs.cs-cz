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
ms.openlocfilehash: d1b8f3e1d0ef7d0f83db4a742ab76a05e42f761b
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053685"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox
Operace přetažení myší pomocí Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek provádí zpracování <xref:System.Windows.Forms.RichTextBox.DragEnter> a <xref:System.Windows.Forms.RichTextBox.DragDrop> události. Proto jsou velmi jednoduché pomocí operace přetažení myší <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Povolení operací přetažení v ovládacím prvku RichTextBox  
  
1. Nastavte <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou `true`.  
  
2. Napište kód v obslužné rutině události <xref:System.Windows.Forms.RichTextBox.DragEnter> událostí. Použití `if` příkaz, ujistěte se, že data jsou kvůli usnadnění použití vypsány přijatelné typ (v tomto případě text). <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> Vlastnost lze nastavit na libovolnou hodnotu z <xref:System.Windows.Forms.DragDropEffects> výčtu.  
  
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
  
     (Visual C# a vizuální C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
  
3. Napište kód pro zpracování <xref:System.Windows.Forms.RichTextBox.DragDrop> událostí. Použití <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metodu pro načtení dat se přetáhnout.  
  
     V následujícím příkladu kódu nastaví <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> řídit rovna data jsou kvůli usnadnění použití vypsány. Pokud je již v textu <xref:System.Windows.Forms.RichTextBox> ovládací prvek, přetažené text vložíte na pozici kurzoru.  
  
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
  
     (Visual C# a vizuální C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>K testování a přetažení funkce ve vaší aplikaci  
  
1. Uložit a sestavit aplikaci. Když je spuštěn, spusťte program WordPad.  
  
     WordPad je textový editor a nainstalované ve Windows, který umožňuje operace přetažení myší. Je přístupná po kliknutí **Start** tlačítka, výběr **spustit**, zadáním `WordPad` v textovém poli **spustit** dialogové okno a potom kliknete na  **OK**.  
  
2. Jakmile WordPad otevře, zadejte v něm textového řetězce. Pomocí myši, vyberte text a pak přetáhněte vybraný text na <xref:System.Windows.Forms.RichTextBox> ovládacího prvku v aplikaci Windows.  
  
     Všimněte si, že když umístíte ukazatel myši na <xref:System.Windows.Forms.RichTextBox> ovládacího prvku (a v důsledku toho vyvolat <xref:System.Windows.Forms.RichTextBox.DragEnter> událostí), ukazatel myši se změní a budete lze přetáhnout do vybraného textu <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
     Po uvolnění tlačítka myši se zahodí vybraný text (to znamená, <xref:System.Windows.Forms.RichTextBox.DragDrop> událost je aktivována) a vložení v rámci <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Postupy: Provádění operací přetažení myší mezi aplikacemi](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
