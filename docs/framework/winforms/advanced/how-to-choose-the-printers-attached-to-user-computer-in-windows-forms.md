---
title: 'Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: bebb879020e6e45e77f109bf9c377b7322d5e8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184025"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms
Uživatelé často chtějí vybrat tiskárnu jiné než výchozí tiskárna pro tisk. Můžete umožnit uživatelům si vybrat tiskárnu z aktuálně nainstalované pomocí <xref:System.Windows.Forms.PrintDialog> komponenty. Prostřednictvím <xref:System.Windows.Forms.PrintDialog> komponenty, <xref:System.Windows.Forms.DialogResult> z <xref:System.Windows.Forms.PrintDialog> komponenta je zachycena a umožňuje vybrat tiskárnu.  
  
 V následujícím postupu je textový soubor vybraný které se mají vytisknout, použije se výchozí tiskárna. <xref:System.Windows.Forms.PrintDialog> Pak vytvoření instance třídy.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Můžete vybrat tiskárnu a potom tisk souboru  
  
1.  Vyberte tiskárny, kterou chcete použít pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.  
  
     V následujícím příkladu kódu existují dvě události se zpracovávají. V první <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> událostí, <xref:System.Windows.Forms.PrintDialog> je vytvořena instance třídy a jsou zachyceny tiskárny vybraných uživatelem <xref:System.Windows.Forms.DialogResult> vlastnost.  
  
     V druhém případě <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost <xref:System.Drawing.Printing.PrintDocument> komponentu, vytiskne se ukázkový dokument na tiskárně zadaná.  
  
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
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
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

- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
