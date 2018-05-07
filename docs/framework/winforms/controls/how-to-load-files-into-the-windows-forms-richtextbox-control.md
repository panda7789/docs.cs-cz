---
title: 'Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: 4d43536cab7806b8cf2de3d63b2d9f7f10024c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> řízení může zobrazit prostého textu, prostého textu ve formátu Unicode nebo soubor formátu formátovaného textu (RTF). Chcete-li tak učinit, zavolejte <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metoda. Můžete také <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodu pro načtení dat z datového proudu. Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a>Načtení souboru do ovládacího prvku RichTextBox  
  
1.  Určete cestu k souboru otevřít pomocí <xref:System.Windows.Forms.OpenFileDialog> součásti. Přehled najdete v tématu [OpenFileDialog – přehled komponenty](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).  
  
2.  Volání <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodu <xref:System.Windows.Forms.RichTextBox> řízení, zadáte soubor načíst a volitelně typu souboru. V následujícím příkladu je soubor načíst převzat ze <xref:System.Windows.Forms.OpenFileDialog> součásti <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost. Pokud jste volali metodu s názvem souboru jako argument pouze, bude považován za RTF typ souboru. Chcete-li určit jiný typ souboru, volejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako druhý argument.  
  
     V následujícím příkladu <xref:System.Windows.Forms.OpenFileDialog> komponenta se zobrazí při stisknutí tlačítka. Vybraný soubor je pak otevřít a zobrazit v <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Tento příklad předpokládá, že formulář obsahuje tlačítko,`btnOpenFile`.  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  Tento proces spustit, vaše sestavení může vyžadovat úroveň oprávnění uděleno pomocí <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
