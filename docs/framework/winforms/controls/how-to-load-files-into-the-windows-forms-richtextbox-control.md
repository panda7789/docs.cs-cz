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
ms.openlocfilehash: 0f52b4ff869d7a2220dd2d40e0ab90bbfb7d24ae
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046171"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox

Ovládací prvek <xref:System.Windows.Forms.RichTextBox> model Windows Forms může zobrazit prostý text, kódování Unicode nebo soubor RTF (Rich-Text-Format). Uděláte to tak, že <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> zavoláte metodu. K načtení dat z datového <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> proudu můžete použít také metodu. Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-load-a-file-into-the-richtextbox-control"></a>Načtení souboru do ovládacího prvku RichTextBox

1. Určete cestu k souboru, který má být otevřen pomocí <xref:System.Windows.Forms.OpenFileDialog> součásti. Přehled naleznete v tématu [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).

2. <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> Zavolejte metodu <xref:System.Windows.Forms.RichTextBox> ovládacího prvku, určete soubor, který se má načíst, a volitelně také typ souboru. V následujícím příkladu se soubor, který se má načíst, převezme <xref:System.Windows.Forms.OpenFileDialog> z <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnosti komponenty. Pokud zavoláte metodu s názvem souboru jako jeho jediným argumentem, typ souboru se bude považovat za RTF. Chcete-li zadat jiný typ souboru, zavolejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako svůj druhý argument.

    V následujícím <xref:System.Windows.Forms.OpenFileDialog> příkladu se komponenta zobrazí při kliknutí na tlačítko. Vybraný soubor se pak otevře a zobrazí v <xref:System.Windows.Forms.RichTextBox> ovládacím prvku. Tento příklad předpokládá, že formulář má tlačítko,`btnOpenFile`.

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

    (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > Chcete-li spustit tento proces, vaše sestavení může vyžadovat úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídou. Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
