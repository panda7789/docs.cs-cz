---
title: 'Postupy: Otevírání souborů pomocí komponenty OpenFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 87e7640da76205341b9e95310314800ac9dbfe30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678808"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>Postupy: Otevírání souborů pomocí komponenty OpenFileDialog
<xref:System.Windows.Forms.OpenFileDialog> Komponenta umožňuje uživatelům procházet složky jejich počítač nebo všechny počítače v síti a vyberte jeden nebo více souborů otevřete. Dialogové okno vrátí cestu a název souboru v dialogovém okně vyberte uživatele.  
  
 Jakmile uživatel vybral soubor otevřít, se používají dva přístupy mechanismu, který otevírání tohoto souboru. Pokud budete chtít pracovat s datové proudy souborů, můžete vytvořit instanci <xref:System.IO.StreamReader> třídy. Alternativně můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda otevřít vybraný soubor.  
  
 V prvním příkladu níže se zahrnuje <xref:System.Security.Permissions.FileIOPermission> kontrola oprávnění (jak je popsáno v "Zabezpečení poznámku" níže), ale dává vám přístup k souboru. Tento postup můžete použít z místního počítače, intranetu a Internetu zóny. Druhá metoda také provádí <xref:System.Security.Permissions.FileIOPermission> kontrola oprávnění, ale je vhodnější pro aplikace v zóně intranetu nebo Internetu.  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>Pro otevření souboru jako datový proud pomocí komponenty OpenFileDialog  
  
1.  Zobrazení **otevřít soubor** dialogové okno a volání metody otevřít soubor vybraný uživatelem.  
  
     Jedním z přístupů je použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna otevřete soubor a použít instanci <xref:System.IO.StreamReader> třídy k otevření souboru.  
  
     V příkladu níže použití <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevřete instance <xref:System.Windows.Forms.OpenFileDialog> komponenty. Pokud je soubor zvolené a uživatel klikne na tlačítko **OK**, otevře se soubor vybrané v dialogovém okně. V takovém případě obsah se zobrazí v okně se zprávou, pouze k znázornění přečetla datový proud souboru.  
  
    > [!IMPORTANT]
    >  Pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacího prvku a <xref:System.Windows.Forms.OpenFileDialog> komponenty.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  Další informace o čtení ze souborů datových proudů, naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.Read%2A>.  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>Pro otevření souboru jako souboru pomocí komponenty OpenFileDialog  
  
1.  Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogových oken a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody k otevření souboru.  
  
     <xref:System.Windows.Forms.OpenFileDialog> Komponenty <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda vrátí počet bajtů, které ho tvoří. Tyto bajtů umožňují čtení z datového proudu. V následujícím příkladu <xref:System.Windows.Forms.OpenFileDialog> s filtrem "kurzor", které uživateli umožňují vybrat pouze soubory s příponou názvu souboru je vytvořena instance komponenty`.cur`. Pokud`.cur` je vybrán soubor, kurzor formuláře je nastavena na vybrané kurzoru.  
  
    > [!IMPORTANT]
    >  Volání <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.OpenFileDialog>
- [Komponenta OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
