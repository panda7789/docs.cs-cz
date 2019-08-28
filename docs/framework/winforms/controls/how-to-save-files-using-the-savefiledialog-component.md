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
ms.openlocfilehash: 7a3a7d0b12a83b756eb2790a94a95580576a2c32
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046279"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Postupy: Ukládání souborů pomocí komponenty SaveFileDialog

Tato <xref:System.Windows.Forms.SaveFileDialog> součást umožňuje uživatelům procházet systém souborů a vybírat soubory, které mají být uloženy. Dialogové okno vrátí cestu a název souboru, který uživatel vybral v dialogovém okně. Je však nutné napsat kód, který bude ve skutečnosti zapisovat soubory na disk.

### <a name="to-save-a-file-using-the-savefiledialog-component"></a>Uložení souboru pomocí komponenty SaveFileDialog

- Zobrazte dialogové okno **Uložit soubor** a voláním metody uložte soubor vybraný uživatelem.

  K uložení souboru použijte <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metodu komponenty.<xref:System.Windows.Forms.SaveFileDialog> Tato metoda poskytuje <xref:System.IO.Stream> objekt, do kterého lze zapisovat.

  Následující příklad používá <xref:System.Windows.Forms.DialogResult> vlastnost k získání názvu souboru <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> a metody uložení souboru. <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Metoda poskytuje Stream pro zápis souboru do.

  V následujícím příkladu je <xref:System.Windows.Forms.Button> k dispozici ovládací prvek s přiřazenou obrázkem. Po kliknutí na tlačítko <xref:System.Windows.Forms.SaveFileDialog> se vytvoří instance komponenty s filtrem, který umožňuje soubory typu. gif,. jpeg a. bmp. Pokud je vybrán soubor tohoto typu v dialogovém okně Uložit soubor, je obrázek tlačítka uložen.

  > [!IMPORTANT]
  > Chcete-li získat nebo <xref:System.Windows.Forms.FileDialog.FileName%2A> nastavit vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídou. Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).

  V příkladu se předpokládá, že váš <xref:System.Windows.Forms.Button> formulář má ovládací <xref:System.Windows.Forms.ButtonBase.Image%2A> prvek s vlastností nastavenou na soubor typu. gif,. jpeg nebo. bmp.

  > [!NOTE]
  > Vlastnost třídy (která z důvodu dědičnosti je součástí <xref:System.Windows.Forms.SaveFileDialog> třídy) používá index založený na jednom. <xref:System.Windows.Forms.FileDialog> <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> To je důležité, pokud píšete kód pro uložení dat v určitém formátu (například ukládání souboru v prostém textu versus v binárním formátu). Tato vlastnost je vybraná v následujícím příkladu.

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

  (Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  Další informace o zápisu datových proudů souborů naleznete <xref:System.IO.FileStream.BeginWrite%2A> v <xref:System.IO.FileStream.Write%2A>tématu a.

  > [!NOTE]
  > Některé ovládací prvky, například <xref:System.Windows.Forms.RichTextBox> ovládací prvek, mají možnost ukládat soubory. Další informace najdete v části "SaveFileDialog Component" tématu Technické články věnované knihovně MSDN Online Library, [základní kód pro model Windows Forms dialogová okna](https://go.microsoft.com/fwlink/?LinkID=102575).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SaveFileDialog>
- [Komponenta SaveFileDialog](savefiledialog-component-windows-forms.md)
