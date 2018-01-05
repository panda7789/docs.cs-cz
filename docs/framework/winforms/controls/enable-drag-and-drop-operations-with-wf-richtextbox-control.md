---
title: "Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox"
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
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8497f0c13fece9c6a2b3ca2d1d2df0d427c605e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Postupy: Povolení operací přetažení myší pomocí ovládacího prvku Windows Forms RichTextBox
Operace přetažení myší pomocí Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek, provádí zpracování <xref:System.Windows.Forms.RichTextBox.DragEnter> a <xref:System.Windows.Forms.RichTextBox.DragDrop> události. Proto jsou velmi jednoduché s operací přetažení myší <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Pro povolení operací přetažení v ovládacím prvku RichTextBox  
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> řídit k `true`.  
  
2.  Psaní kódu v obslužné rutině události z <xref:System.Windows.Forms.RichTextBox.DragEnter> událostí. Použijte `if` příkaz a zkontrolujte, zda data přetažen přijatelné typu (v tomto případě text). <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> Může být nastavena na jakoukoli hodnotu z <xref:System.Windows.Forms.DragDropEffects> výčtu.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
  
3.  Napsat kód pro zpracování <xref:System.Windows.Forms.RichTextBox.DragDrop> událostí. Použití <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metoda pro načtení dat přetažen.  
  
     V příkladu níže kód nastaví <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> řízení rovna přetažen data. Pokud je již v text <xref:System.Windows.Forms.RichTextBox> je vložen ovládací prvek, taženou text na pozici kurzoru.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>K testování funkcí přetahování myší v aplikaci  
  
1.  Uložit a sestavit aplikaci. Když je spuštěná, spusťte WordPad.  
  
     WordPad je textový editor, nainstalovaná v systému Windows, který umožňuje operací přetažení myší. Je přístupný kliknutím **spustit** tlačítko výběru **spustit**, zadáním `WordPad` v textovém poli **spustit** dialogové okno a potom kliknutím na tlačítko  **OK**.  
  
2.  Jakmile WordPad je otevřený, zadejte řetězec textu v ní. Pomocí myši, vyberte text a poté přetáhněte vybraný text přes k <xref:System.Windows.Forms.RichTextBox> ovládací prvek v aplikaci pro Windows.  
  
     Všimněte si, že když přejděte myší na <xref:System.Windows.Forms.RichTextBox> ovládací prvek (a v důsledku toho vyvolat <xref:System.Windows.Forms.RichTextBox.DragEnter> událostí), aby se změnil a mohou vyřadit vybraný text do <xref:System.Windows.Forms.RichTextBox> ovládací prvek.  
  
     Po uvolnění tlačítka myši se ukončí vybraný text (tedy <xref:System.Windows.Forms.RichTextBox.DragDrop> událost se vyvolá) a je vložen v rámci <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox>  
 [Postupy: Provádění operací přetažení mezi aplikacemi](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
