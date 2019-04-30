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
ms.openlocfilehash: ffbce7401f068b3d0a7fee4fd8ba04c10cb6f6b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918551"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek mohl zobrazit prostého textu, prostého textu ve formátu Unicode nebo soubor ve formátu RTF. Text Format (RTF). Chcete-li tak učinit, zavolejte <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metody. Můžete také použít <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodu pro načtení dat z datového proudu. Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a>Načíst soubor do ovládacího prvku RichTextBox  
  
1. Určit cestu k souboru otvíraly <xref:System.Windows.Forms.OpenFileDialog> komponenty. Přehled najdete v tématu [OpenFileDialog – přehled komponenty](openfiledialog-component-overview-windows-forms.md).  
  
2. Volání <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodu <xref:System.Windows.Forms.RichTextBox> ovládacího prvku, určení souboru načíst a volitelně typu souboru. V následujícím příkladu je soubor načíst převzata z <xref:System.Windows.Forms.OpenFileDialog> komponenty <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost. Pokud jste volali metodu s názvem souboru jako její jediný argument, typ souboru bude považován za RTF. Chcete-li zadat jiný typ souboru, volejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčet jako druhý argument.  
  
     V následujícím příkladu <xref:System.Windows.Forms.OpenFileDialog> součást se zobrazí po kliknutí na tlačítko. Vybraný soubor je pak otevře a zobrazí v <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Tento příklad předpokládá, že formulář obsahuje tlačítko,`btnOpenFile`.  
  
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
    >  Ke spuštění tohoto procesu, vaše sestavení může vyžadovat úroveň oprávnění poskytnuté <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, procesu může vyvolat výjimku z důvodu dostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
