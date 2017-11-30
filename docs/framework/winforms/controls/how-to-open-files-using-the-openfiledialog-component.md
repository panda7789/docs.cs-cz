---
title: "Postupy: Otevírání souborů pomocí součásti OpenFileDialog"
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
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52726a770e33bec4b5ec9b24f33deb44ed6379b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>Postupy: Otevírání souborů pomocí součásti OpenFileDialog
<xref:System.Windows.Forms.OpenFileDialog> Součást umožňuje uživatelům procházet složky jejich počítače nebo všechny počítače v síti a vyberte jeden nebo více souborů otevřete. Dialogové okno vrátí cestu a název souboru, vyberte v dialogovém okně vyberte uživatele.  
  
 Jakmile uživatel vybral soubor otevřít, existují dva přístupy mechanismu, který otevírání tohoto souboru. Pokud dáváte přednost práci s datovými proudy souboru, můžete vytvořit instanci <xref:System.IO.StreamReader> třídy. Alternativně můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda otevřít vybraný soubor.  
  
 V prvním příkladu níže zahrnuje <xref:System.Security.Permissions.FileIOPermission> zkontrolujte oprávnění (jak je popsáno v "Zabezpečení poznámku" níže), ale dává vám přístup k názvu souboru. Tento postup můžete použít z místního počítače, intranetu a Internetu zóny. Druhá metoda zajišťuje také <xref:System.Security.Permissions.FileIOPermission> kontrola oprávnění, ale je vhodnější pro aplikací do zóny intranetu nebo Internetu.  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>Otevřete soubor jako datový proud pomocí součásti OpenFileDialog  
  
1.  Zobrazení **otevřít soubor** dialogové okno a volání metody k otevření souboru vybraného uživatelem.  
  
     Jeden z přístupů je použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> má metoda zobrazit dialogové okno otevřít soubor a použít instanci systému <xref:System.IO.StreamReader> třída k otevření souboru.  
  
     V příkladu níže používá <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události otevřete instanci <xref:System.Windows.Forms.OpenFileDialog> součásti. Pokud je soubor zvolený a uživatel klikne na tlačítko **OK**, otevře se soubor vybraný v dialogovém okně. Obsah v tomto případě se zobrazí v okně se zprávou, stačí k zobrazení byl načten datový proud souboru.  
  
    > [!IMPORTANT]
    >  Pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení a <xref:System.Windows.Forms.OpenFileDialog> součásti.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  Další informace o čtení ze souboru datové proudy najdete v tématu <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.Read%2A>.  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>Otevřete soubor jako soubor pomocí součásti OpenFileDialog  
  
1.  Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogových oken a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda k otevření souboru.  
  
     <xref:System.Windows.Forms.OpenFileDialog> Součásti <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda vrátí počet bajtů, které tvoří soubor. Tyto bajtů dát číst z datového proudu. V následujícím příkladu <xref:System.Windows.Forms.OpenFileDialog> s filtrem "kurzoru", které uživateli umožňují zvolit pouze soubory s příponou názvu souboru je vytvořena instance komponenty`.cur`. Pokud`.cur` je vybrán soubor, formuláře kurzor nastavený na vybrané kurzor.  
  
    > [!IMPORTANT]
    >  K volání <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog – komponenta](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
