---
title: 'Postupy: Ukládání souborů pomocí komponenty SaveFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: 933e049f825bcc8f2afef914f810b52c1cf51245
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638308"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Postupy: Ukládání souborů pomocí komponenty SaveFileDialog
<xref:System.Windows.Forms.SaveFileDialog> Komponenta umožňuje uživatelům procházet systému souborů a vyberte soubory, které se má uložit. Dialogové okno vrací cestu a název souboru, který uživatel vybral v dialogovém okně. Ale musíte napsat kód, který ve skutečnosti soubory zapisují na disk.  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a>Uložte soubor pomocí komponenty SaveFileDialog  
  
- Zobrazení **uložit soubor** dialogové okno a uložte soubor vybraný uživatelem volání metody.  
  
     Použití <xref:System.Windows.Forms.SaveFileDialog> komponenty <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metoda k uložení souboru. Tato metoda poskytuje <xref:System.IO.Stream> můžete zapisovat do objektu.  
  
     V příkladu níže použití <xref:System.Windows.Forms.DialogResult> vlastnost a získat tak název souboru a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda k uložení souboru. <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Metoda poskytuje datového proudu pro zápis souboru.  
  
     V následujícím příkladu je <xref:System.Windows.Forms.Button> ovládací prvek s přiřazenou image. Když kliknete na tlačítko <xref:System.Windows.Forms.SaveFileDialog> s filtrem, který umožňuje soubory typu .gif, .jpeg a .bmp je vytvořena instance komponenty. Pokud v dialogovém okně Uložit soubor byl vybrán soubor tohoto typu, je uložen obrázek na tlačítko.  
  
    > [!IMPORTANT]
    >  Pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).  
  
     Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacím prvkem jeho <xref:System.Windows.Forms.ButtonBase.Image%2A> nastavenou na soubor typu .gif, .jpeg nebo BMP.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog> Třídy <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> vlastnosti (které, z důvodu dědičnosti, je součástí <xref:System.Windows.Forms.SaveFileDialog> třídy) používá indexu se základem 1. To je důležité, pokud píšete kód k uložení dat v určitém formátu (například ukládání souboru ve formátu prostého textu a binárních). Tato vlastnost je mezi vybranými položkami v následujícím příkladu.  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     Další informace o vytváření datové proudy souborů najdete v tématu <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.Write%2A>.  
  
    > [!NOTE]
    >  Některé ovládací prvky, jako například <xref:System.Windows.Forms.RichTextBox> řídit, se budou moct ukládat soubory. Další informace najdete v části "Komponenty SaveFileDialog" technického článku MSDN Online Library [základní kód pro Windows Forms dialogových oknech](https://go.microsoft.com/fwlink/?LinkID=102575).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SaveFileDialog>
- [Komponenta SaveFileDialog](savefiledialog-component-windows-forms.md)
