---
title: 'Postupy: volba tiskáren připojených k počítači uživatele'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 7fc2427468540ac0a1480f6140cbb34c3a0f1ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746507"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Postupy: Volba tiskáren připojených k počítači uživatele ve Windows Forms
Uživatelé chtějí často zvolit jinou tiskárnu než výchozí tiskárnu, do které chcete tisknout. Uživatelům můžete umožnit výběr tiskárny z těch, které jsou aktuálně nainstalované, pomocí <xref:System.Windows.Forms.PrintDialog> komponenty. Prostřednictvím součásti <xref:System.Windows.Forms.PrintDialog> je <xref:System.Windows.Forms.DialogResult> součásti <xref:System.Windows.Forms.PrintDialog> zachycena a používána pro výběr tiskárny.  
  
 V následujícím postupu je vybraný textový soubor, který se má vytisknout na výchozí tiskárně. Pak se vytvoří instance třídy <xref:System.Windows.Forms.PrintDialog>.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Výběr tiskárny a následné tisk souboru  
  
1. Vyberte tiskárnu, která má být použita pomocí <xref:System.Windows.Forms.PrintDialog> součásti.  
  
     V následujícím příkladu kódu jsou zpracovávány dvě události. V první <xref:System.Windows.Forms.Button> událost <xref:System.Windows.Forms.Control.Click> ovládacího prvku, je vytvořena instance třídy <xref:System.Windows.Forms.PrintDialog> a tiskárna vybraná uživatelem je zachycena ve vlastnosti <xref:System.Windows.Forms.DialogResult>.  
  
     Ve druhé události <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost <xref:System.Drawing.Printing.PrintDocument> součásti se ukázkový dokument vytiskne na určenou tiskárnu.  
  
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
  
     (Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
