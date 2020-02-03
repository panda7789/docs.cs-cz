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
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="9149a-102">Postupy: Volba tiskáren připojených k počítači uživatele ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9149a-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="9149a-103">Uživatelé chtějí často zvolit jinou tiskárnu než výchozí tiskárnu, do které chcete tisknout.</span><span class="sxs-lookup"><span data-stu-id="9149a-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="9149a-104">Uživatelům můžete umožnit výběr tiskárny z těch, které jsou aktuálně nainstalované, pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="9149a-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="9149a-105">Prostřednictvím součásti <xref:System.Windows.Forms.PrintDialog> je <xref:System.Windows.Forms.DialogResult> součásti <xref:System.Windows.Forms.PrintDialog> zachycena a používána pro výběr tiskárny.</span><span class="sxs-lookup"><span data-stu-id="9149a-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="9149a-106">V následujícím postupu je vybraný textový soubor, který se má vytisknout na výchozí tiskárně.</span><span class="sxs-lookup"><span data-stu-id="9149a-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="9149a-107">Pak se vytvoří instance třídy <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="9149a-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="9149a-108">Výběr tiskárny a následné tisk souboru</span><span class="sxs-lookup"><span data-stu-id="9149a-108">To choose a printer and then print a file</span></span>  
  
1. <span data-ttu-id="9149a-109">Vyberte tiskárnu, která má být použita pomocí <xref:System.Windows.Forms.PrintDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="9149a-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="9149a-110">V následujícím příkladu kódu jsou zpracovávány dvě události.</span><span class="sxs-lookup"><span data-stu-id="9149a-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="9149a-111">V první <xref:System.Windows.Forms.Button> událost <xref:System.Windows.Forms.Control.Click> ovládacího prvku, je vytvořena instance třídy <xref:System.Windows.Forms.PrintDialog> a tiskárna vybraná uživatelem je zachycena ve vlastnosti <xref:System.Windows.Forms.DialogResult>.</span><span class="sxs-lookup"><span data-stu-id="9149a-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="9149a-112">Ve druhé události <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost <xref:System.Drawing.Printing.PrintDocument> součásti se ukázkový dokument vytiskne na určenou tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="9149a-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
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
  
     <span data-ttu-id="9149a-113">(Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9149a-113">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9149a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9149a-114">See also</span></span>

- [<span data-ttu-id="9149a-115">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9149a-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
