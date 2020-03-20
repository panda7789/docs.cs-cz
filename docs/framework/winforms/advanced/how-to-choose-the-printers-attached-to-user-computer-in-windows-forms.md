---
title: 'Postup: Volba tiskáren připojených k počítači uživatele'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 2afbccd02ef42a78d5eac1a01841516fca27c92e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182615"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Postupy: Volba tiskáren připojených k počítači uživatele ve Windows Forms
Uživatelé často chtějí zvolit jinou tiskárnu než výchozí tiskárnu, na kterou chcete tisknout. Pomocí <xref:System.Windows.Forms.PrintDialog> součásti můžete uživatelům povolit výběr tiskárny z aktuálně nainstalovaných. Prostřednictvím <xref:System.Windows.Forms.PrintDialog> <xref:System.Windows.Forms.DialogResult> komponenty je <xref:System.Windows.Forms.PrintDialog> komponenta zachycena a použita k výběru tiskárny.  
  
 V následujícím postupu je vybrán textový soubor, který se má vytisknout na výchozí tiskárně. Třída <xref:System.Windows.Forms.PrintDialog> je pak vytvořena instance.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Výběr tiskárny a následné tisku souboru  
  
1. Vyberte tiskárnu, která <xref:System.Windows.Forms.PrintDialog> má být použita pomocí komponenty.  
  
     V následujícím příkladu kódu jsou zpracovávány dvě události. V první události <xref:System.Windows.Forms.Button> ovládacího <xref:System.Windows.Forms.Control.Click> prvku <xref:System.Windows.Forms.PrintDialog> je instance třídy a tiskárna vybraná uživatelem <xref:System.Windows.Forms.DialogResult> je zachycena ve vlastnosti.  
  
     V druhém případě, <xref:System.Drawing.Printing.PrintDocument.PrintPage> v <xref:System.Drawing.Printing.PrintDocument> případě komponenty, je na zadanou tiskárnu vytištěn ukázkový dokument.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také

- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
